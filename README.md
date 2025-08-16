# Cysic-Verifier-node-windows
How to Run Cysic Verifier node on windows (automated &amp; background process)

A. **HOW TO SETUP**

**Start your Powershell program on Windows(Run as administrator).**

**Copy the code below, replacing the address placeholder with your reward address, paste the code in your terminal, then press enter to run.**

cd $env:USERPROFILE

Invoke-WebRequest -Uri "https://github.com/cysic-labs/cysic-phase3/releases/download/v1.0.0/setup_windows.ps1" -OutFile "setup_windows.ps1"

.\setup_windows.ps1 -CLAIM_REWARD_ADDRESS "0x-Fill-in-your-reward-address-here"

B. **START THE VERIFIER NODE**

**Wait a while for the setup process script to run. Then copy and paste the below code, press enter to run.**

**# run the verifier**

cd $env:USERPROFILE\cysic-verifier

.\start.ps1



· If you see “err: rpc error”, don’t worry—just wait a few minutes for the verifier to connect.
· Once connected, you’ll see a message like “start sync data from server,” indicating it’s running successfully.


**NOW, HOW TO AUTOMATE THIS AND MAKE IT BACKGROUND PROCESS, SO EVERY TIME RUNS IT AUTOMATICALLY, AND THERE IS A POINT IF THIS PROCESS AUTORUN WHEN NETWORK(INTERNET) CONNECTED.
**

Task Scheduler (Recommended)(Best)
This will run the verifier silently in the background on startup.

press windows key + R from your keyboard, Type taskschd.msc press ok/enter to Open Task Scheduler

Click 'Create Task'

Fill in: ( showing here )

Go to General → Name: Cysic Verifier

Security options: Select Run whether user is logged on or not + check Run with highest privileges

Go to Triggers → New… → Begin the task: At startup

Go to Actions → Start a Program

Program/script: powershell.exe

Add Arguments: ( just copy paste )

-ExecutionPolicy Bypass -WindowStyle Hidden -File "$env:USERPROFILE\cysic-verifier\start.ps1"

(This makes it run hidden in background)

Go to Condition → under network click on Start only if the following network connection is available & in drop down menu choose 'any connection'.
(it it totally optional)

Thats all!

Save → Enter password → Done ✅

Now every time Windows starts, the verifier will run silently in background.

