# Jumbo-receipts-analysis

In this script I provided an example of a full workflow where: receipts are downloaded, read by an LLM, categorised by an LLM, simple summary statistics are calculated and finally, the summary is send through email.


## How to run

### Requirements
- Windows with Microsoft Edge and the classic Outlook desktop app (new Outlook does not work), signed in to the email account you want to send from
- Python 3.10+ and Jupyter
- [Ollama](https://ollama.com) installed and running
- A Jumbo account with receipts under "Bestellingen en bonnetjes"

### Setup (once)
1. Install the packages:
   ```
   pip install -r requirements.txt
   ```
2. Download the two models used by the notebook:
   ```
   ollama pull qwen2.5vl      # reads the receipt screenshots
   ollama pull llama3.2       # categorises the items
   ```

### Every time you run it
1. Close all Edge windows. Then open PowerShell and run:
   ```
   & "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --remote-debugging-port=9222 --user-data-dir="C:\edge-debug"
   ```
   If Edge is not found, try the path without "(x86)". This opens a separate Edge window that the script can control. You can check that it worked by opening `http://localhost:9222/json` in a browser, which should show text.
2. In that Edge window, log in to jumbo.com and go to 'Bestellingen en bonnetjes' (`https://www.jumbo.com/bestellingen`). Keep that tab open and leave the window visible, not minimized.
3. Make sure the Ollama app is running and the classic Outlook app is open.
4. Open the notebook and edit the settings at the top:
   - `main_folder`: the folder where the receipt screenshots are saved. Use an empty or new folder for each run, because all PNGs in it are read.
   - the sender and recipient email addresses (the sender must be an account in your Outlook)
5. Run the cells from top to bottom. The last cell starts the whole pipeline:
   ```python
   await run_all(main_folder, number_of_receipts, category_list)
   ```



There is much room for improvement, additions and extensions to this script. Including, but not limited to:
* Making sure it can also handle other websites/receipt types.
* Allowing the user to determine from what date the receipts are analysed, not just the last x receipts.
* Making sure the script also runs correctly if there are multiple receipts on a single day (currently it only keeps a single receipt per day).
* Making sure the script can also get receipts from the next page (by clicking 'Meer' on the Jumbo website).
* Making the script more robust against errors.
* Making sure you don't have to do a lot of setting up when using the script (noted at the start).
* Adding an extra check before running the 'run_all' function that checks if everything is in order, reducing the instances of errors.
* Calculating more and more interesting statistics on the receipts.
* Using a better LLM such that less mistakes are made when reading/categorising the receipts (there are not that many, but still a handfull everytime. This can be mitigated by ever more specific prompts, but is probably easier with a larger, better model)

