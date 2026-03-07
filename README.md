SC Contested Zone Cloud Sync Real Time Squad Timer Inventory Dashboard is here to deliver Real-Time Tactical Synchronization for Star Citizen Squads.
This is a high-performance, web-based tactical web app designed to synchronize Contested Zone timers and Shared Squad Inventory across multiple clients in real-time so everyone stays up to date. 

## OVERVIEW
In high-stakes Contested Zones, staying on the same page is the difference between a successful extract, preventing waste of time, and a total loss especially if you are operating in seperate groups.
This tool eliminates the need for constant manual callouts by providing a unified, web-based dashboard that every member of the squad can access simultaneously and quickly provide updates to the rest of the team using.
By utilizing a Public Google Sheets API as a lightweight back-end, this tool allows for zero-cost, real-time data persistence without requiring complex database infrastructure or server-side hosting.

## KEY_FEATURES
Synchronize Hangar,Vault, card, and board cycle countdowns between players via grainular reports. When one operator reports grabbing a item, or updates the timer, the information populates across all connected squad members web pages.

Track exactly which operator is carrying or has stored which key or board. Items are grouped by in-game location (Checkmate, Orbituary, Ruin Station) with specific Player Attribution Tag.

Uses Google Sheets as a "Live Database." Enter your unique Squad Code to link your session to your team’s private data stream.

## TECHNICAL_ARCHITECTURE
The tool operates on a decentralized frontend model:

Pure HTML5/JavaScript (No heavy frameworks for maximum compatibility).

Google Sheets for persistent state management.

AJAX/JSONP for cross-origin data fetching.

## HOSTING_YOUR_OWN_DATABASE_INSTRUCTIONS
To use your own private sheet for squad tracking, follow these steps to set up the backend database.

OPERATIONAL INSTRUCTIONS: PRIVATE DATABASE SETUP
Follow these steps to host your own private squad tracking manifest using Google Sheets.

1. CREATE YOUR GOOGLE SHEET
OPEN Google Sheets and create a new blank spreadsheet.

NAME the file something recognizable, such as "Squad_Ops_DB".

CONFIRM that the tab at the bottom is named Sheet1.

2. GET THE LATEST SYNC SCRIPT
NAVIGATE to the repository file: google sheets script.txt.

SELECT the "Raw" button at the top right of the file window to view the plain text.

COPY the entire script by pressing Ctrl+A then Ctrl+C.

3. INSTALL & DEPLOY
ACCESS the script editor in your Google Sheet via Extensions > Apps Script.

WIPE any existing placeholder code and PASTE the script you copied from the repository.

SAVE the project and name it "Squad_Sync_Engine".

INITIATE deployment by clicking Deploy > New deployment.

CONFIGURE the following settings:

TYPE: Web app.

EXECUTE AS: Me.

WHO HAS ACCESS: Anyone. (Required for squad synchronization).

AUTHORIZE the deployment. If a warning appears, click "Advanced" and then "Go to Squad_Sync_Engine (unsafe)" to finish.

4. LINK TO THE TERMINAL
COPY the Web App URL provided in the deployment window (this URL ends in /exec).

OPEN your Squad Operations Terminal and scroll to the bottom.

PASTE your unique URL into the PRIVATE_GOOGLE_SCRIPT_URL field.

SELECT [ OVERRIDE_DATABASE ] to finalize the link.
## LEGAL_DISCLAIMER
Star Citizen®, Roberts Space Industries®, and Cloud Imperium Games® are registered trademarks of Cloud Imperium Rights LLC. All rights reserved.

This software is an unofficial fan-made utility. It is not endorsed by, affiliated with, or representative of Cloud Imperium Games or Roberts Space Industries. All game content, terminology, and imagery used within this application are the property of their respective owners.

This tool is provided "as-is" for the Star Citizen community. It does not interact with game memory, modify game files, or provide an unfair advantage. It is a purely web-based coordination tool for tactical synchronization.

## PROPRIETARY_INTEL
Author: CMDR Quattro

Portal: citizen-starter-guide.com

Version: 1.0
