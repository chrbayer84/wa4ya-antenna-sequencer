wa4ya antenna sequencer
===============

### About
Node-Red Keyestudios Relay Shield KS0212 based antenna sequencer switch @WA4YA. Relay shield is hooked up to 4-way antenna switch. Sequencer works for FT8 and other 15s interval modes, and also supports FT4 (7.5s) and 30s intervals via the switch interval control. Sequencer allows to automatically switch between transmit and receive antennas based on the selected interval and picking a TX interval (odd/even). Actual switch happens at t-1s, so for a 15s interval the sequencer will switch antennas at 14s past the minute for the 0-15 interval, at 29s past the minute for the 15-30s interval and so on. For a 7.5s interval, switching happens at 6.5s, 14s, 21.5s, 29s, 36.5s, 44s, 51.5s and 59s past the minute.

Use the `Set Interval = 15s`, `Set Interval = 30s` and `Set Interval = 7.5s` buttons on the flow to change the switch interval at runtime. The 7.5s, 15s and 30s intervals are intended for FT4/FT8 and other digital modes with those periods; CW and Sideband modes use different timing and are not handled by this sequencer.

Based on [WA4YA Antennas](https://github.com/chrbayer84/wa4ya-antennas), so naming as per that sketch and the antennas available in the shack (vertcal, delta loop and fan dipole). Delta Loop is the default and unpowered fallback (there is no unconnected antennas at this point although that would be nice to have) so wiring for the delta loop is different from the other ports.

If you want to the same antenna for TX and RX just set it for both parameters and there will be no switching at all.

Use the `hold antenna` button to use the manually selected TX/RX antennas (the sequencer still alternates between them at the selected interval), and `follow bands` to select the antenna automatically from the WSJT-X frequency.

Manual selection of 4 antennas possible using node red. One antenna is wired such that it becomes active when there is no power so logic is inverted for that antenna (the deltaloop antenna in this sketch). When an antenna is selected, all other antennas are disabled/disengaged. 
![alt text](https://github.com/chrbayer84/wa4ya-antenna-sequencer/blob/main/Screenshot%202025-09-29%20125405.png?raw=true)

