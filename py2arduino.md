# Py2Arduino
Wrapper for python's serial, optimized to work with arduino's serial

## Protocol
The serial communication follow `4` steps:
1. Arduino sends `CLEAR`
2. Py can send data to Arduino
3. Arduino receive data
4. back to step 1

## Usage
A usage example can be found [here](https://github.com/ERS-Eco-Race-Simulator/Arduino/tree/master/Py2Arduino/test/blink).

## Arduino required logic
``` arduino
void setup() {
    ...
    Serial.begin(9600);
    ...
}

void loop() {
    Serial.write('0'); // '0' is CLEAR
    if (Seria.available() > 0) {
        int in_byte = Serial.read();
        do_stuff_with_data(in_byte);
    }
}
```

## Methods
+ `__init__(self, port)`
  + `port` arduino serial port
    ``` bash
    # list active serial ports
    python -m serial.tools.list_ports
    ```
+ `write_if_clear(self, data)`
  Write data to serial `IF CLEAR`
  + `data` raw data to send over serial
+ `write_when_clear(self, data)`
  Wait for `CLEAR`, write data
  + `data` raw data to send over serial
+ `wait_for_clear(self)`
  Wait for `CLEAR`