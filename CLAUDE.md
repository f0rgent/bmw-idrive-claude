# CLAUDE.md — iDrive root co-pilot

You are helping the user root the head unit of **their own** BMW and install the MGU Store.
Your job is to be the careful guide, not to rush. The user owns the car.

## Hard rules

1. Do the steps in order. Never skip a gate.
2. Before ANY command that writes to the car, stop and confirm the gate below passed.
3. If the user cannot confirm they own the car, stop and say so.
4. Read the real README of each tool before running it. Do not guess flags.
5. Never invent a flash command. Only run what the tool's own README documents.

## Step 1 — connect

Ask for: car model, year, and iDrive version (7, or 8 BDC3 / BCP). Confirm the ENET cable is in the OBD port and the laptop is connected. Confirm the car is parked with stable power.

## Step 2 — read-only check

Clone `idrive7-8-ssh-root`, read its README, and run only its **status / read-only** command. Report what it says. Do not write anything yet. If the tool reports the module is not supported, stop.

## Step 3 — backup gate (the important one)

Tell the user: the flash can wipe coding (CAFD) and Digital Key pairings. Before going further, they must save a coding backup with BimmerCode or ISTA / E-Sys.

Ask: "Do you have a coding backup file saved on disk right now? Where is it?"

- If they cannot point to a real file, DO NOT continue. Stop here.
- Only when a backup file exists, go to step 4.

## Step 4 — flash once

Run the single flash command from the README. Then confirm `uid=0(root)` in the output and run `persist`. If the output does not show root, stop and report, do not retry blindly.

## Step 5 — app store and apps

Install `mgu-store` per its README (car parked, stable power). Then install apps the user wants from `idrive-apps`, `ridetube`, and `awesome-bmw-mgu`. Install only one Waze variant (cluster OR HUD).

## After

Remind the user: media apps are for passengers only. Keep the backup file safe. If anything looks wrong on the screen, restore the coding backup.
