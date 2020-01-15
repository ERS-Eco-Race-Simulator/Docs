# Object detection
Facility to detect near object with RPlidar

## Requirements
No additional modules are required.
We use RPLidar for test and usage:
``` bash
pip3 install rplidar
```

## Usage
A test usage can be found [here](https://github.com/ERS-Eco-Race-Simulator/Lidar/blob/master/ObjectDetector/od_test.py)

#### Class instances
``` python
obd = ObjectDetector(ObjectDetector.gen_segments(
    right = ObjectDetector.segment_range(30, 90),
    front = ObjectDetector.segment_range(-30, 30),
    left =  ObjectDetector.segment_range(-90, -30)
))
```

+ `@staticmethod ObjectDetector.gen_segments`
  Generate a class-compatible dict of segments, given any number of segment_range tuples
+ `@staticmethod ObjectDetector.segment_range`
  Generate a class-compatible tuple rappresenting a range of degrees. Any object detected in that range will match with the key.

#### Detection
``` python
for data in lidar.iter_measurements():
    if obd.update(data):
        print(obd.detect())
```
+ `ObjectDetector.update`
  Update data pool, return `True` if pool dim reached `DATA_MAX_LEN`
+ `ObjectDetector.detect`
  Detect near object in given segments.
  Return a dict `{key: boolean}`, with a key for every segment. `boolean` is `True` if there are object in the segment, otherwise `False`

With the previous class instantiation, the results will be like:
```
...
{'right': False, 'front': False, 'left': False}
{'right': False, 'front': False, 'left': False}
...
```