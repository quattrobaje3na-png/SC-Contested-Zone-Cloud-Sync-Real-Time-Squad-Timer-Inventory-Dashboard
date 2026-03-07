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

## BASIC_SETUP_INSTRUCTIONS
1: Launch the tool and enter a a selected unique alphanumeric code in the SQUAD_CODE field. Ensure your entire team uses the exact same code.

2: Enter your handle in the OP_NAME field. This ensures when you move an item, the inventory correctly displays your name next to the asset.

Use the CALIBRATE or ADJ button on the timers when you aquire a item, find a used card/board printer. All squad members will see the countdown adjust immediately.

Player Instructions: Hosting Your Private Squad Database
To use your own private sheet for squad tracking, follow these steps to set up the backend database.

1. Create Your Google Sheet
Open Google Sheets and create a new blank spreadsheet.

Name it something like "Squad_Ops_DB".

You do not need to format the columns; the script will handle data entries automatically in Sheet1.

2. Install the Squad Script
Go to the top menu and select Extensions > Apps Script.

Delete any code in the editor window and paste the "Squad Backend Script" provided below.

Click the Save (disk icon) and name the project "Squad_Sync_Engine".

3. Deploy as a Web App
Click the blue Deploy button at the top right and select New deployment.

Select type: Web app.

Description: Squad Sync v10.

Execute as: Me (Your email).

Who has access: Anyone (This is crucial so your squadmates' browsers can send data to the sheet).

Click Deploy. You will be asked to Authorize Access—click through the prompts (select your account, click "Advanced," and "Go to Squad_Sync_Engine (unsafe)") to allow the script to write to your sheet.

4. Link to the Tool
Once deployed, Google will give you a Web App URL (it ends in /exec). Copy this URL.

Open the Squad Operations Terminal tool.

Scroll to the bottom to [ DATABASE_CONFIGURATION ].

Paste your URL into the box and click [ OVERRIDE_DATABASE ].

Your squad is now running on its own private server!

The Squad Backend Script (.gs)
Copy and paste this exact code into your Google Apps Script editor.

JavaScript
/**
 * Squad Operations Sync Engine v1.0
 * Handles real-time inventory manifest and cooldown timers.
 */

function doGet(e) {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = ss.getSheetByName('Sheet1') || ss.getSheets()[0];
  var data = sheet.getDataRange().getValues();
  var code = e.parameter.groupCode;
  var prefix = e.parameter.prefix;
  
  // Default response if no data found
  var result = { inventory: [], version: 0 };
  
  // Search for existing Squad Code
  for (var i = 1; i < data.length; i++) {
    if (data[i][0] == code) {
      result = {
        inventory: data[i][2] ? JSON.parse(data[i][2]) : [],
        version: data[i][3] || 0, // Column D: Version ID
        vaultRef: data[i][13] || 0, // Column N: Vault Reference
        c1: data[i][4], c2: data[i][5], 
        b1: data[i][6], b2: data[i][7], b3: data[i][8],
        b4: data[i][9], b5: data[i][10], b6: data[i][11], b7: data[i][12]
      };
      break;
    }
  }
  
  var json = JSON.stringify(result);
  return ContentService.createTextOutput(prefix + '(' + json + ')')
    .setMimeType(ContentService.MimeType.JAVASCRIPT);
}

function doPost(e) {
  var body = JSON.parse(e.parameter.payload);
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = ss.getSheetByName('Sheet1') || ss.getSheets()[0];
  var data = sheet.getDataRange().getValues();
  var code = body.groupCode;
  
  var rowIdx = -1;
  for (var i = 1; i < data.length; i++) {
    if (data[i][0] == code) { rowIdx = i + 1; break; }
  }
  
  if (rowIdx == -1) {
    // Create new entry for new Squad Code
    sheet.appendRow([code, new Date(), JSON.stringify(body.inventory), body.version]);
    rowIdx = sheet.getLastRow();
  } else {
    // Update existing Squad entry
    sheet.getRange(rowIdx, 2).setValue(new Date()); // Last Updated
    sheet.getRange(rowIdx, 3).setValue(JSON.stringify(body.inventory));
    sheet.getRange(rowIdx, 4).setValue(body.version);
  }
  
  // Update Cooldown Timers (Columns E through M)
  var timerCols = ['c1','c2','b1','b2','b3','b4','b5','b6','b7'];
  timerCols.forEach((id, idx) => {
    if (body[id]) sheet.getRange(rowIdx, 5 + idx).setValue(body[id]);
  });

  // Update Vault Reference (Column N)
  if (body.vaultRef) sheet.getRange(rowIdx, 14).setValue(body.vaultRef);
  
  return ContentService.createTextOutput("OK");
}

## LEGAL_DISCLAIMER
Star Citizen®, Roberts Space Industries®, and Cloud Imperium Games® are registered trademarks of Cloud Imperium Rights LLC. All rights reserved.

This software is an unofficial fan-made utility. It is not endorsed by, affiliated with, or representative of Cloud Imperium Games or Roberts Space Industries. All game content, terminology, and imagery used within this application are the property of their respective owners.

This tool is provided "as-is" for the Star Citizen community. It does not interact with game memory, modify game files, or provide an unfair advantage. It is a purely web-based coordination tool for tactical synchronization.

## PROPRIETARY_INTEL
Author: CMDR Quattro

Portal: citizen-starter-guide.com

Version: 1.0
