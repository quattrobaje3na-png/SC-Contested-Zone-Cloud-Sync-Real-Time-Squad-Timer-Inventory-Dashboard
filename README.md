SC Contested Zone Squad Sync: Timer & Inventory
[ Real-Time Tactical Synchronization for Star Citizen Teams ]
A high-performance, web-based tactical overlay designed to synchronize Contested Zone timers and Shared Squad Inventory across multiple clients in real-time. Built for specialized squad operations in the Stanton and Pyro systems.

## OVERVIEW
In high-stakes Contested Zones, information parity is the difference between a successful extract and a total loss. This tool eliminates the "desync" of manual callouts by providing a unified, web-based dashboard that every member of the squad can access simultaneously.

By utilizing a Public Google Sheets API as a lightweight back-end, this tool allows for zero-cost, real-time data persistence without requiring complex database infrastructure or server-side hosting.

## KEY_FEATURES
UNIFIED_ZONE_TIMERS: Synchronize Hangar and Vault cycle countdowns. When one operator calibrates the timer, the update reflects across all connected squad members instantly.

ISOLATED_SQUAD_INVENTORY: Track exactly which operator is carrying which key or board. Items are grouped by in-game location (Checkmate, Orbituary, Ruin Station) with specific Player Attribution Tags.

CLOUDSYNC_DATA: Uses Google Sheets as a "Live Database." Enter your unique Squad Code to link your session to your team’s private data stream.

LOW_LATENCY_HEARTBEAT: Optimized 5-second polling ensures your squad is never more than a few heartbeats away from the latest tactical data.

## TECHNICAL_ARCHITECTURE
The tool operates on a decentralized frontend model:

Frontend: Pure HTML5/JavaScript (No heavy frameworks for maximum compatibility).

Backend: Google Apps Script (GAS) acting as a REST API.

Storage: Google Sheets for persistent state management.

Communication: AJAX/JSONP for cross-origin data fetching.

## SETUP_INSTRUCTIONS
SQUAD_CODE: Launch the tool and enter a unique alphanumeric code in the SQUAD_CODE field. Ensure your entire team uses the exact same code.

OP_NAME: Enter your handle in the OP_NAME field. This ensures when you move an item, the inventory correctly displays [ YOUR_NAME ] next to the asset.

CALIBRATE: Use the CALIBRATE button on the Primary Hangar timer when the in-game event triggers. All squad members will see the countdown begin immediately.

## LEGAL_DISCLAIMER
Star Citizen®, Roberts Space Industries®, and Cloud Imperium Games® are registered trademarks of Cloud Imperium Rights LLC. All rights reserved.

This software is an unofficial fan-made utility. It is not endorsed by, affiliated with, or representative of Cloud Imperium Games or Roberts Space Industries. All game content, terminology, and imagery used within this application are the property of their respective owners.

This tool is provided "as-is" for the Star Citizen community. It does not interact with game memory, modify game files, or provide an unfair advantage. It is a purely web-based coordination tool for tactical synchronization.

## PROPRIETARY_INTEL
Author: CMDR Quattro

Portal: citizen-starter-guide.com

Version: 1.2.0_STABLE
