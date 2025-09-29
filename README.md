wa4ya antenna sequencer
===============

### About
Node-Red Keyestudios Relay Shield KS0212 based antenna sequencer switch @WA4YA. Relay shield is hooked up to 4-way antenna switch. Sequencer works for FT8 at this time (or any other 15s interval mode but not FT4 and not CW/Sideband for example). Sequencer allowos to automatically switch between transmit and receive antennas based on 15s interval and picking a TX interval (odd/even). Actual switch happens at t-1s, so sequencer will switch antennas at 14s past the minute for the 0-15 interval, at 29s past the minute for the 15-30s interval and so on.

Based on [WA4YA Antennas](https://github.com/chrbayer84/wa4ya-antennas), so naming as per that sketch and the antennas available in the shack (vertcal, delta loop and fan dipole). Delta Loop is the default and unpowered fallback (there is no unconnected antennas at this point although that would be nice to have) so wiring for the delta loop is different from the other ports.

If you want to the same antenna for TX and RX just set it for both parameters and there will be no switching at all.

Manual selection of 4 antennas possible using node red. One antenna is wired such that it becomes active when there is no power so logic is inverted for that antenna (the deltaloop antenna in this sketch). When an antenna is selected, all other antennas are disabled/disengaged. 
![alt text](https://github.com/chrbayer84/wa4ya-antenna-sequencer/blob/main/Screenshot%202025-09-29%20125405.png?raw=true)

