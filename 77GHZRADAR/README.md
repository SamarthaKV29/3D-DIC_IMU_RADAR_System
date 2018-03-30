# 77GHZRADAR

### Hardware setup:
1. Connect a suitable antenna(pyramidal horn antenna in this case) to the 77GHZ Radar(RS3400W) and supply 5.5v (+-1.5v)
2. Connect this radar to a controller board(CO1000A/01) through appropriate cable and supply 12v to controller board.
3. Connect this whole setup to a pc/raspberry pi using a RS232 to USB cable.

### Software setup:

1. Install Python 2.7 from [this link](https://www.python.org/downloads/)
2. Once python is downloaded and installed, install pyserial, scipy, numpy, pandas libraries from pip using the following commands:
  - pip install pyserial
  - pip install scipy
  - pip install numpy
  - pip install pandas
3. Open device manager and note down the port number of usbserial device and change the port number in line 14.
4. Navigate to current folder through command prompt and type ``` python rad.py ```
5. You can see the distance as output in the command prompt
  
