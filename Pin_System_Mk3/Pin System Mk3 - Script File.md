//## Marker, Data Registry and Timer Summary

// M0100 - Begins the whole program, starts by going to step 1
// M0101-M0104 - Step1-4 Used in all 3 Modes, Requirement, Setting, Accessing to input the PIN
// M0105 - Helps further actions know that all digits of the temp data registers are set
// M0106 - Helps in Setting section
// M0107 - Turns on Timer which flicks the Green LED 3 times
// M0110 - Turns on Timer which flicks the Red LED 3 times
// M0014 - Requirement Mode
// M0015 - Setting Mode
// M0016 - Accessing Mode
// M0017 - When you fail 3 times the marker makes the program stop and prevent you from further actions for 30 seconds
// D0010-D0013 - Temp PIN Digits
// D0014 - Counts number of failed attempts
// D0100-D0103 - PIN Digits
// T0000 - Flicking Green LED
// T0001 - Flicking Red LED
// T0002 - Penalty Timer

//## Program Summary

// This script implements a 4 digit PIN state machine with modes: Setting, Accessing, Requirement, and Penalty. Each mode uses markers M0014-M0017,
// Timers T0000-T0002 handle LEDs and Penalty duration

//## Script

// Setting PIN
if( [M0100] == 0 && [M0017] == 0 ) { [D0010] = 10; [D0011] = 10; [D0012] = 10; [D0013] = 10; SET([M0101]); SET([M0015]); }
if( [M0100] == 0 && [M0014] == 1 && [M0017] == 0 ) { RST([M0015]); }
if( [M0100] == 0 && [M0016] == 1 && [M0017] == 0 ) { RST([M0015]); }

// Digit 1
if( [M0101] == 1 && [M0017] == 0 ) {
SET([M0100]);
if( [I0000] == 1 ) { [D0010] = 1; SET([M0100]); }
if( [I0001] == 1 ) { [D0010] = 2; SET([M0100]); }
if( [I0002] == 1 ) { [D0010] = 3; SET([M0100]); }
if( [I0003] == 1 ) { [D0010] = 4; SET([M0100]); }
if( [I0004] == 1 ) { [D0010] = 5; SET([M0100]); }
if( [I0005] == 1 ) { [D0010] = 6; SET([M0100]); }
if( [I0006] == 1 ) { [D0010] = 7; SET([M0100]); }
if( [I0007] == 1 ) { [D0010] = 8; SET([M0100]); }
if( [I0010] == 1 ) { [D0010] = 9; SET([M0100]); }
if( [I0012] == 1 ) { [D0010] = 0; SET([M0100]); }

if( [D0010] != 10 && [I0000] == 0 && [I0001] == 0 && [I0002] == 0 && [I0003] == 0 && [I0004] == 0 && [I0005] == 0 && [I0006] == 0 && [I0007] == 0 && [I0010] == 0 && [I0012] == 0 ) { SET([M0102]); RST([Q0000]); RST([Q0001]); SET([M0100]); }
if( [I0011] == 1 && [I0013] == 0 ) { RST([M0101]); RST([M0100]); }}

// Digit 2
if( [M0102] == 1 ) {
RST([M0101]);
if( [I0000] == 1 ) { [D0011] = 1; }
if( [I0001] == 1 ) { [D0011] = 2; }
if( [I0002] == 1 ) { [D0011] = 3; }
if( [I0003] == 1 ) { [D0011] = 4; }
if( [I0004] == 1 ) { [D0011] = 5; }
if( [I0005] == 1 ) { [D0011] = 6; }
if( [I0006] == 1 ) { [D0011] = 7; }
if( [I0007] == 1 ) { [D0011] = 8; }
if( [I0010] == 1 ) { [D0011] = 9; }
if( [I0012] == 1 ) { [D0011] = 0; }

if( [D0011] != 10 && [I0000] == 0 && [I0001] == 0 && [I0002] == 0 && [I0003] == 0 && [I0004] == 0 && [I0005] == 0 && [I0006] == 0 && [I0007] == 0 && [I0010] == 0 && [I0012] == 0 ) { SET([M0103]); RST([Q0000]); RST([Q0001]); }
if( [I0011] == 1 && [I0013] == 0 ) { RST([M0102]); RST([M0100]); }}

// Digit 3
if( [M0103] == 1 ) {
RST([M0102]);
if( [I0000] == 1 ) { [D0012] = 1; }
if( [I0001] == 1 ) { [D0012] = 2; }
if( [I0002] == 1 ) { [D0012] = 3; }
if( [I0003] == 1 ) { [D0012] = 4; }
if( [I0004] == 1 ) { [D0012] = 5; }
if( [I0005] == 1 ) { [D0012] = 6; }
if( [I0006] == 1 ) { [D0012] = 7; }
if( [I0007] == 1 ) { [D0012] = 8; }
if( [I0010] == 1 ) { [D0012] = 9; }
if( [I0012] == 1 ) { [D0012] = 0; }

if( [D0012] != 10 && [I0000] == 0 && [I0001] == 0 && [I0002] == 0 && [I0003] == 0 && [I0004] == 0 && [I0005] == 0 && [I0006] == 0 && [I0007] == 0 && [I0010] == 0 && [I0012] == 0 ) { SET([M0104]); RST([Q0000]); RST([Q0001]); }
if( [I0011] == 1 && [I0013] == 0 ) { RST([M0103]); RST([M0100]); }}

// Digit 4
if( [M0104] == 1 ) {
RST([M0103]);
if( [I0000] == 1 ) { [D0013] = 1; }
if( [I0001] == 1 ) { [D0013] = 2; }
if( [I0002] == 1 ) { [D0013] = 3; }
if( [I0003] == 1 ) { [D0013] = 4; }
if( [I0004] == 1 ) { [D0013] = 5; }
if( [I0005] == 1 ) { [D0013] = 6; }
if( [I0006] == 1 ) { [D0013] = 7; }
if( [I0007] == 1 ) { [D0013] = 8; }
if( [I0010] == 1 ) { [D0013] = 9; }
if( [I0012] == 1 ) { [D0013] = 0; }

if( [D0013] != 10 && [I0000] == 0 && [I0001] == 0 && [I0002] == 0 && [I0003] == 0 && [I0004] == 0 && [I0005] == 0 && [I0006] == 0 && [I0007] == 0 && [I0010] == 0 && [I0012] == 0 ) { SET([M0105]); RST([Q0000]); RST([Q0001]); }
if( [I0011] == 1 && [I0013] == 0 ) { RST([M0104]); RST([M0100]); }}

// Requirement
if( [I0011] == 1 && [I0013] == 1 && [M0017] == 0 ) { SET([M0014]); RST([M0016]); }
if( [M0105] == 1 && [M0014] == 1 && [I0013] == 1 && [I0011] == 0 && [M0017] == 0 )
{
// Correct
if( [D0010] == [D0100] && [D0011] == [D0101] && [D0012] == [D0102] && [D0013] == [D0103]) { RST([M0100]); RST([M0105]); RST([M0104]); RST([M0103]); RST([M0102]); RST([M0101]); SET([M0015]); RST([M0014]); SET([M0107]); [D0014] = 0; }
// Wrong
if( [D0010] != [D0100] || [D0011] != [D0101] || [D0012] != [D0102] || [D0013] != [D0103]) { RST([M0100]); RST([M0105]); RST([M0104]); RST([M0103]); RST([M0102]); RST([M0101]); SET([M0110]); [D0014] = [D0014] + 1; }
}

// Accessing
if( [M0016] == 1 && [M0017] == 0 && [I0013] == 1 ) { RST([M0015]); }
if( [M0016] == 1 && [M0105] == 1 && [I0013] == 1 && [I0011] == 0 && [M0017] == 0 ) 
{
// Correct
if( [D0010] == [D0100] && [D0011] == [D0101] && [D0012] == [D0102] && [D0013] == [D0103]) { RST([M0100]); RST([M0105]); RST([M0104]); RST([M0103]); RST([M0102]); RST([M0101]); SET([M0016]); RST([M0015]); SET([M0107]); [D0014] = 0; }
// Wrong
if( [D0010] != [D0100] || [D0011] != [D0101] || [D0012] != [D0102] || [D0013] != [D0103]) { RST([M0100]); RST([M0105]); RST([M0104]); RST([M0103]); RST([M0102]); RST([M0101]); SET([M0110]); [D0014] = [D0014] + 1; }
}

// Setting
if( [M0105] == 1 && [I0013] == 1 && [M0015] == 1 && [M0014] == 0 && [M0017] == 0 && [M0016] == 0 ) { RST([M0015]); RST([M0104]); [D0100] = [D0010]; [D0101] = [D0011]; [D0102] = [D0012]; [D0103] = [D0013]; SET([M0106]); SET([M0107]); }
if( [M0106] == 1 && [M0017] == 0 && [M0016] == 0 ) { RST([M0105]); [D0010] = 10; [D0011] = 10; [D0012] = 10; [D0013] = 10; RST([M0106]); SET([M0016]); RST([M0100]); }

// Red and Green LEDs
if( [TC0000] == 25 ) { SET([Q0001]); }
if( [TC0000] == 20 ) { RST([Q0001]); }
if( [TC0000] == 15 ) { SET([Q0001]); }
if( [TC0000] == 10 ) { RST([Q0001]); }
if( [TC0000] == 5 ) { SET([Q0001]); }
if( [TC0000] == 0 ) { RST([Q0001]); }
if( [TC0001] == 25 ) { SET([Q0000]); }
if( [TC0001] == 20 ) { RST([Q0000]); }
if( [TC0001] == 15 ) { SET([Q0000]); }
if( [TC0001] == 10 ) { RST([Q0000]); }
if( [TC0001] == 5 ) { SET([Q0000]); }
if( [TC0001] == 0 ) { RST([Q0000]); }

// Reset Penalty Counter
if( [TC0002] == 0 ) { [D0014] = 0; }
