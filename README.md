# StepperMotor_SineWave

Driving a bipolar stepper motor using sine waves

See it in action here
Super resolution: https://youtu.be/qB4mTp6XKKE
Mega resolution: https://youtu.be/HtiUTXUM4Yc

After researching stepper motor design i could see why all designs for stepper motor control uses a series of fixed voltage pulses. They do this to 'snap' to the next step and it increases holding power of the motor. This is useful for hardware such as 3d printers and CNC mills. It also gives stepper motors that characteristic noise (square wave PWM).

It occurred to me that if i generate a 5 volt sine wave and connect it to 1 coil of a stepper motor i would be oscillating through 1 micro step.
Since stepper motors operate with the coils driven in quadrature (90 degrees out of phase) i just added a second output that was ¼ behind the first.

To test this I used a spreadsheet to calculate a sine wave with 512 values.
I put those values in an array. I created a second array and shifted the values by 128 places.

The stepper motors need proper AC to work so I just connected 1 wire of each coil to a pin that was set at 2.5v.
Then when the sine values are output as a range of voltages between 0v and 5v, the stepper motor would get the required positive and negative swings of the AC.

Stepper motors have an almost infinite resolution however the engineering tolerances of the motor really come in to play at such resolutions. You will get stepping errors.
The cheaper the motor – the more stepping errors you will get.

In my code I had to reduce the resolution 4 fold to get an acceptable level of errors. This may not be the case if you use a H-Bridge and drive it with more current.

Using this method I was able to precisely control a laser with the kind of resolution I would only have been able to get using some gears.
