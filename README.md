wa4ya antenna sequencer
===============

### About
Node-Red Keyestudios Relay Shield KS0212 based antenna sequencer switch @WA4YA. Relay shield is hooked up to 4-way antenna switch. Sequencer works for FT8 and other 15s interval modes, and also supports FT4 (7.5s) and 30s intervals via the switch interval control. Sequencer allows to automatically switch between transmit and receive antennas based on the selected interval and picking a TX interval (odd/even). Actual switch happens at t-1s, so for a 15s interval the sequencer will switch antennas at 14s past the minute for the 0-15 interval, at 29s past the minute for the 15-30s interval and so on. For a 7.5s interval, switching happens at 6.5s, 14s, 21.5s, 29s, 36.5s, 44s, 51.5s and 59s past the minute.

Use the `Set Interval = 15s`, `Set Interval = 30s` and `Set Interval = 7.5s` buttons on the flow to change the switch interval at runtime. The 7.5s, 15s and 30s intervals are intended for FT4/FT8 and other digital modes with those periods; CW and Sideband modes use different timing and are not handled by this sequencer.

When WSJT-X reports FT8 or FT4 in its UDP status message, the switch interval is set automatically to 15s or 7.5s. For all other modes no automatic period is applied, so the interval buttons remain in control and the selected interval is honored.

Two sequencing modes are available. `Sequence Mode = timed` (default) uses the interval controls above and switches at t-1s. `Sequence Mode = event` switches antennas on WSJT-X transmit/receive status changes. When `follow bands` is enabled, event mode also re-selects the antenna whenever WSJT-X reports a new frequency, without needing the periodic clock. In event mode use `Force TX antenna` and `Force RX antenna` to manually select an antenna; when `follow bands` is enabled these controls use the band-selected antenna instead. Event mode switches when WSJT-X reports that transmission has started, so use appropriate relay/PTT interlocking to avoid hot switching.

Based on [WA4YA Antennas](https://github.com/chrbayer84/wa4ya-antennas), so naming as per that sketch and the antennas available in the shack (vertcal, delta loop and fan dipole). Delta Loop is the default and unpowered fallback (there is no unconnected antennas at this point although that would be nice to have) so wiring for the delta loop is different from the other ports.

If you want to the same antenna for TX and RX just set it for both parameters and there will be no switching at all.

Manual selection of 4 antennas possible using node red. One antenna is wired such that it becomes active when there is no power so logic is inverted for that antenna (the deltaloop antenna in this sketch). When an antenna is selected, all other antennas are disabled/disengaged. 
![alt text](https://github.com/chrbayer84/wa4ya-antenna-sequencer/blob/main/Screenshot%202025-09-29%20125405.png?raw=true)

