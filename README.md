# FPT-Router-RCE
G-97RG6M and G-97RG3 Remote Command Execution

# Affected device
1. G-97RG6M R4.2.98.035
2. G-97RG3  R4.2.43.078

  instruction:  Since there are no other models of devices and the firmware download address cannot be found, I am not sure if any other devices are affected.
# Description
  There are ping and traceroute tools in the web management page of the device, the user can enter the test target, but the background program does not filter and check the user's input, directly splicing the string and then calling the system function to execute, causing a command injection vulnerability
![image](https://user-images.githubusercontent.com/96364879/146664685-bf4d272c-d454-427d-a5b0-12ab6895579e.png)
