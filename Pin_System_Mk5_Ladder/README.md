# PIN System Mk5 — WindLDR Ladder
5th Version of the Pin System, now written in WindLDR Ladder Logic

## Status
  - Fully Functional, works the same as Mk4, but the size is halved.
    
## Features
  - 4-digit PIN input system
  - Modes: Set PIN / Set Requirement / Access
  - Step-by-step logic using data registers
  - 30-second lockout after 3 failed attempts
  - LED feedback: red or green flickers 3× based on outcome

## Key Learnings
  - Improved structure using Ladder-specific components
  - Logic is more compact and readable than earlier versions
    
## Notes
  - Used blocks like N Data Set or Load Compare to simulate:
  if( [D0000] == 0 ) { [D0000] = 1; }
