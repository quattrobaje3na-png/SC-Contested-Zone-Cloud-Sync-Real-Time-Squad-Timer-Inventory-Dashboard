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

1. Create Your Google Sheet
Open Google Sheets and create a new blank spreadsheet.

Name it something like "Squad_Ops_DB".

Ensure your first sheet is named Sheet1.

2. Get the Latest Sync Script
Go to the repository file: google sheets script.txt (or your specific path).

Click the "Raw" button at the top right of the file view to see the plain text code.

Press Ctrl+A then Ctrl+C to copy the entire script.

3. Install & Deploy
In your Google Sheet, go to Extensions > Apps Script.

Delete any existing code and paste the script you copied.

Click Save and name it "Squad_Sync_Engine".

Click Deploy > New deployment.

Select Web app.

Set Execute as: "Me" and Who has access: "Anyone".

Note: This must be "Anyone" so your squadmates can send data to your sheet.

Click Deploy and authorize the permissions (Click "Advanced" > "Go to Squad_Sync_Engine (unsafe)" if prompted).

4. Link to the Terminal
Copy the Web App URL provided by Google (ends in /exec).

Open the Squad Operations Terminal, scroll to the bottom, and paste your URL into the PRIVATE_GOOGLE_SCRIPT_URL box.

Click [ OVERRIDE_DATABASE ].

## LEGAL_DISCLAIMER
Star Citizen®, Roberts Space Industries®, and Cloud Imperium Games® are registered trademarks of Cloud Imperium Rights LLC. All rights reserved.

This software is an unofficial fan-made utility. It is not endorsed by, affiliated with, or representative of Cloud Imperium Games or Roberts Space Industries. All game content, terminology, and imagery used within this application are the property of their respective owners.

This tool is provided "as-is" for the Star Citizen community. It does not interact with game memory, modify game files, or provide an unfair advantage. It is a purely web-based coordination tool for tactical synchronization.

## PROPRIETARY_INTEL
Author: CMDR Quattro

Portal: citizen-starter-guide.com

Version: 1.0
