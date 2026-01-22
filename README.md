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
- Ser AD Convertor mode to "differential" to ignore any ADS1115 WAS signal.  On 'Single' it *should* use the WAS sensor like normal.
- Steering ratio (motor turns to wheel angle) is set through adjusting the Counts Per Degree slider.   it takes that number and divides by 10, so 100 - means 10 degree change in the motor angle = 1 degree change at the axle for the tires.  150 would be 15 motor degrees = 1 degree of tire steer.  There is no adjustment for nonlinearities.

TO DO:
- See if there drift is an issue or if some sort of live drift compensation needs implemented
- Detect which version of the Keya Motor is attached and adjust / work accordingly.
- Add in the smart to detect if a WAS is attached and automatically us if there is one (maybe, would only make it easier / better for developing a universal code base)
