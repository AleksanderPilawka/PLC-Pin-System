# PIN System Mk3 — WindLDR
This was my third attempt at building Pin System

## Status
  - Functional
    
## Features
  - 4-digit PIN input system
  - Modes: PIN Setting / Set Requirement / Accessing
  - Step-by-step logic using markers.
  - 30 Second Penalty System after 3 wrong inputs
  - Red and Green leds flicker 3 times based on corresponding outcome

## Key Learnings
  - Even More Compact and Readable logic
  - Few Hundreds Bytes of reduction compared to Mk2 due to deletion of obsolete markers
    
## Notes
  - I removed whole section where each input was going into a marker output, now the inputs are directly in the script
