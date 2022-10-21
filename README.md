#  *CAN Fuzzing Simplified*

> _"The good news is that it’s easy to make a CAN fuzzer. The bad news is that it’s rarely useful."_ 

<!-- Unless you understand reverse-engineering that is.... -->

##### Requirements: Linux OS, Bash Shell
 
## Steps:
  1) Install Can-Utils
  2) Setup Virtual CAN
  3) Generate Random CAN Traffic
  4) Save CAN Data to Logfile
  5) Format to User-Friendly Version (Logfile)
  6) Replay Logfile Data to CAN 
  7) Sniff CAN Traffic for Results

 ## CAN-Utils
 
```
  > sudo apt-get install can-utils -y
```
 
 ## Virtual CAN Network

```
  > sudo modprobe can
  > sudo modprobe vcan
  > sudo ip link add dev vcan0 type vcan
  > sudo ip link set up vcan0
```
  
 ## Random CAN Traffic
 
```
  > cangen vcan0 -v
```
  
 ## Record CAN Data
  
```
  > candump -l vcan0
```

 ## Format Log for Readibility
  
```
  > log2asc -I candump.log vcan0
```

 ## Replay Recorded CAN Data
  
```
  > canplayer -I candump.log
  
  > canplayer vcan0=can1 -v -I candump.log
```

 ## Results

```
  > cansniffer vcan0
```

 --------------------------
 ### *Additional Information*
 --------------------------
  
  - SocketCAN Tools for Linux
    (https://github.com/linux-can/can-utils)
  
  - Car Hacker's Handbook by Craig Smith
    (http://opengarages.org/handbook/)
  
  - Instrument Cluster Simulator
    (https://github.com/zombieCraig/ICSim)
  
  - CaringCaribou: Friendly Car Security Exploration Tool
    (https://github.com/CaringCaribou/caringcaribou)
  
  - Controller Area Network Support for Python
    (https://python-can.readthedocs.io/en/master/)
  
  - WireShark: Open Source Network Traffic Analyzer
    (https://gitlab.com/wireshark/wireshark)
