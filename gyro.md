# Gyroscope - Accelerometer
We use an accelrerometer to measure momentary acceleration of the rover.

## mpu6050
[mpu6050](https://playground.arduino.cc/Main/MPU-6050/) is a cheap and accessible Gyro-Accelerometer, easy to interface with both Arduino and RPi.
We interfaced through python, building a simple wrapper around [mpu6050-raspberrypi](https://github.com/m-rtijn/mpu6050) module.

## Accel.py
Simple wrapper around [mpu6050-raspberrypi](https://github.com/m-rtijn/mpu6050)

#### Requirements
``` bash
# on raspberry pi
sudo apt install python3-smbus
pip3 install mpu6050-raspberrypi
```

#### Usage

[Test example](https://github.com/ERS-Eco-Race-Simulator/mpu6050/blob/master/MPU.py)

``` python
mpu = mpu6050(0x68)
acc = Accel(mpu)
```

+ `Accel.calibration` calibrate accelerometer axis
``` python
acc = Accel(mpu, calibration_meas=10000)
acc.calibrate()
```
While calibrating data the chip must be in firm position and aligned with the axes of the theoretical model

+ `Accel.start` start data collection
+ `Accel.stop` stop data collection and clear thread
``` python
acc.start()
time.sleep(5)
acc.stop()
```