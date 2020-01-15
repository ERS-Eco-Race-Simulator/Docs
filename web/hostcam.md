# Hostcam
Simple web-cam streaming over LAN

### Requirements
``` bash
# pip requirements
pip3 install -U -r hostcam/requirements.txt
# or manually
pip3 install flask opencv-python
```

### Usage
``` bash
python3 hostcam/hostcam.py [camera]
```
+ `camera` camera index
  ``` bash
  # find camera index
  [sudo] apt install v4l-utils libv4l-dev
  v4l2-ctl --list-devices
  ```
  ``` bash
  # sample output
  USB2.0 HD UVC WebCam: USB2.0 HD (usb-0000:00:14.0-7):
	/dev/video0
	/dev/video1

  # so
  python3 hostcam/hostcam.py 0
  ```