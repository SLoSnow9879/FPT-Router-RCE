# FPT-Router-RCE
G-97RG6M and G-97RG3 Remote Command Execution

# Affected device
1. G-97RG6M R4.2.98.035
2. G-97RG3  R4.2.43.078

  instruction:  Since there are no other models of devices and the firmware download address cannot be found, I am not sure if any other devices are affected.
# Description
  There are ping and traceroute tools in the web management page of the device, the user can enter the test target, but the background program does not filter and check the user's input, directly splicing the string and then calling the system function to execute, causing a command injection vulnerability.
  
  Fortunately, this vulnerability requires authentication before it can be exploited. However, since the user can modify the login password, there is a possibility of being blasted by a weak password.
![image](https://user-images.githubusercontent.com/96364879/146664685-bf4d272c-d454-427d-a5b0-12ab6895579e.png)
![image](https://user-images.githubusercontent.com/96364879/146667918-cf198b68-a914-49f2-a262-970433ab5936.png)
# Recurrent
1. First, log in to the device Web management background, and then enter the Utilities page, click Ping Test or Traceroute.

![image](https://user-images.githubusercontent.com/96364879/146667934-5f5f95bd-2e76-4b59-b8be-b4e56cdf679d.png)

2. Second, enter the target to be tested, and then use the BurpSuite tool to intercept the request package.

![image](https://user-images.githubusercontent.com/96364879/146667944-bd130d9e-1b23-4920-8558-d55c66eb183f.png)

3. Modify the wanIndex field in the HTTP request body to 0, then inject the command to be executed in the url_or_ip field, and finally send the data packet, the command is successfully executed.

![image](https://user-images.githubusercontent.com/96364879/146667954-a3c68657-8dd4-4948-b99d-0e1b135d662e.png)
![image](https://user-images.githubusercontent.com/96364879/146667957-71e97587-0c0d-428d-b2a5-58fc587786ef.png)

# Video


https://user-images.githubusercontent.com/96364879/146670183-77384f27-27db-4cf4-b84e-efdcc610bd74.mp4

