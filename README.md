# Robot Automation Project

This document provides instructions to build a robot that listens to a specific email, reads the nationalities data table from the received email, fetches users’ information from a website, and sends this information via API. Additionally, the robot creates an account on hide.me and enables a desktop VPN before processing the data table records.

## Pre-Requirements

1. **UiPath Studio**: Develop the robot using UiPath Studio.
   - [Download UiPath Studio](https://download.uipath.com/UiPathStudioCommunity.msi)
2. **Hide.me VPN**: Download and install Hide.me VPN desktop application.
   - [Download Hide.me VPN](https://hide.me/en/software/windows/download)
3. **Chrome Browser**: Ensure the bot operates on the Chrome browser.

## Building The Robot

### Step-by-Step Instructions

1. **Read the Config File**
   - Place `config.csv` in Data subfolder the project folder.
   - Ensure all variables used in the process are configurable and included in this file.

2. **Email Monitoring and File Download**
   - Wait for the test email with the subject "maids.cc RPA test".
   - Download the attached Excel file (`test.xlsx`) and save it to the output folder.

3. **Account Creation on Hide.me**
   - Navigate to the [Hide.me sign-up page](https://hide.me/en/).
   - If you don’t have an account, register using your email, activate the account, and log in.
   - If you have an account, reset the password as instructed, then log out and log back in.
   - Handle CAPTCHA attempts up to three times. If unsuccessful, proceed to the next step.

4. **Enable VPN**
   - Open the Hide.me VPN desktop application and enable the VPN.

5. **Read Data Table**
   - Read the data table from the downloaded Excel file (`test.xlsx`).

6. **Process Each Record in the Data Table**
   - For each record, follow these steps:
     a. Generate user information on [Fake Name Generator](https://www.fakenamegenerator.com/).
     b. Save the extracted data in `result.xlsx`.
     c. Create and delete an account on [Automation Exercise](https://automationexercise.com/).
     d. Send user information via API to [Reqres](https://reqres.in/api/users).
     e. Save data in `result.xlsx` and `summary.csv`.

7. **Send Results via Email**
   - Email `result.xlsx` and `summary.csv` files to the designated receiver.

8. **Email Monitoring**
   - Continue monitoring the email inbox for new emails for 5 minutes. If no email is received, stop the process.

### The Process Trigger

- Run the robot using a batch file.
- The robot monitors the email inbox . Upon receiving the test email, it performs steps 2 to 7 and then waits for another email to restart the process. If no new email after 5 minutes, the bot stops

## Important Notes

1. **Development Environment**: Use UiPath Studio to build the robot and do not use the Orchestrator.
2. **Configuration**: Ensure all configurable words in the orange color are variables in the config file.
3. **Publishing**: Publish the robot to the desktop and execute the published package via a batch file.
4. **Error Handling**: Log any errors encountered during each transaction in the `summary.csv` file. The robot should not stop for any reason.
5. **Project Tested in gmail**: but expected to work with other email server, provided correct server and port is provided.


Follow these instructions to ensure the robot operates smoothly and efficiently.
