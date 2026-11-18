# Jumbo-receipts-analysis

In this script I provided an example of a full workflow where: receipts are downloaded, read by an LLM, categorised by an LLM, simple summary statistics are calculated and finally, the summary is send through email.


For using this script, follow the following steps:
* First, close all edge tabs and execute: & "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --remote-debugging-port=9222 --user-data-dir="C:\edge-debug" in powershell, this opens a microsoft edge tab that the code can recognise in the future.
* In that tab, log into jumbo.com and click on your account on 'Bestellingen en bonnetjes' to arrive to the website 'https://www.jumbo.com/bestellingen'
* Then, paste the path of the folder you want to use to save the screenshots of the receipts into the variable name main_folder at the top of the script.
* Lastly, make sure to have the old version of the outlook app open



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

