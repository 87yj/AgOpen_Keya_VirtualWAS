# AgOpen_Keya_VirtualWAS
AgOpen GPS v4 firmware for Keya v3 motor with Virtual WAS based on encoder

This code is a fork from the AgOpenGPS Boards Keya code
It uses the Keya encoder as a virtual WAS

Bench testing for development and leanring. Has not and should not be used on real machinery.

Key Items:
- When the Keya is powered on, the steering must be at zero degrees.  On boot up, the Keya always starts at zero, so the wheels must be there.
- If you forget, you can either set wheel to zero and power cycle the Keya OR adjust the WAS Zero slider (don't use the Zero button) to offset and then press the send and save button to update the zero correction in the Teensy.
- It Current Turn is enabled, it will use that as a soft limit to disable the motor if the reported motor current (amperage) exceeds the value.  Mapping is still being finalized.  Right now 0-100% on the slider is roughly 0-12.5 AMPS.
- The orignal code steering wheel detection based on actual speed not matching commanded speed is still in place and should funcation normally
- This code does account for the Keya motor making multiple turns and the encoder resetting.  Need further tested.
- The ratio from the steering motor to wheel angle is hard coded at 30 currently (30 degrees on steering motor = 1 degree on wheels).  Not right, but a starting point

TO DO:
- See if there drift is an issue or if some sort of live drift compensation needs implemented
- Detect which version of the Keya Motor is attached and adjust / work accordingly.
- FIgure out a way to allow adjustment of the steering ratio (hard coded at 30) from the AgOpenUI.  Thinking about using the counts per degree slider.  i.e. instead of it representing counts per degree, when working in this mode, have the slider represent the steering ratio of handwheel angle to tire steering angle.
