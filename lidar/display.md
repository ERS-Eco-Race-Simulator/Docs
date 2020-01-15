# Lidar display

Display Lidar input data into pygame canvas.

## Requirements
``` bash
pip3 install RPLidar pygame
```

## Usage
``` bash
python3 display/display.py display/config.yaml
```
+ `config.yaml`
  ``` yaml
  lidar:
    port: [port]
  scale: !!int [scale]
  ```
  + `port` lidar USB port
  + `scale` cartesian scale for the coordinates