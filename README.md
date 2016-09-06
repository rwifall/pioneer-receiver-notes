# pioneer-receiver-notes
Notes about how to connect to and communicate with Pioneer receivers similar to the VSX-1021 K
Hopefully this makes it easier for other people trying to integrate a system with a Pioneer receiver.
If you have any additional info, please make a pull request!

# Access methods

Telnet / Socket - This seems to be the most popular method.  Just connect to the ip address of the receiver and start issuing and listening for commands.  You can find the commands in the pages for [Custom Install IP & RS-232 Codes](https://www.pioneerelectronics.com/PUSA/Support/Home-Entertainment-Custom-Install/RS-232+&+IP+Codes/A+V+Receivers)
  - telnet ipaddress - Issue commands to the receiver over telnet

UPnP - The receiver implements UPnP to expose standard capabilities.
  - http://ipaddress:8080/AVTransport/desc.xml - UPnP description

HTTP - I haven't been able to find any official documentation about these pages:
  - http://ipaddress/StatusHandler.asp - Receiver status
  - http://ipaddress/EventHandler.asp?WebToHostItem=command - Issue a command to the receiver over http
  ```
  Example commands (These seem to be the same as custom install IP & RS-232 commands):
  /EventHandler.asp?WebToHostItem=PO - Power on
  /EventHandler.asp?WebToHostItem=PF - Power off
  /EventHandler.asp?WebToHostItem=VU - Volume up
  /EventHandler.asp?WebToHostItem=VD - Volume down
  /EventHandler.asp?WebToHostItem=MO - Mute on
  /EventHandler.asp?WebToHostItem=MF - Mute off
  /EventHandler.asp?WebToHostItem=**FN - Input change (** = input number)
  /EventHandler.asp?WebToHostItem=***SR - Listening mode (*** = listening mode)
  ```    

HTTPS -
  - https://ipaddress/ - Requires a client certificate.  I haven't been able to access this link.

Normal web pages
  - http://ipaddress -
  - http://ipaddress/MCACC/latest.mcacc - Download mcacc data



# Documentation

RS-232 / IP (Telnet) codes:
- Pioneer custom install links - https://www.pioneerelectronics.com/PUSA/Support/Home-Entertainment-Custom-Install
- Custom Install IP & RS-232 codes for all receivers - https://www.pioneerelectronics.com/PUSA/Support/Home-Entertainment-Custom-Install/RS-232+&+IP+Codes/A+V+Receivers
- VSX-1021 IP & RS-232 codes -
https://www.pioneerelectronics.com/StaticFiles/Custom%20Install/RS-232%20Codes/Av%20Receivers/2011_Pioneer_AVR_IP_&_RS-232_USA%20Models_8.6.xls

Other projects & links:
  - Article about using telnet to control your receiver by Raymond Julin - http://raymondjulin.com/2012/07/15/remote-control-your-pioneer-vsx-receiver-over-telnet/
  - A list of VSX-1022 commands - https://github.com/schaffman5/VSX-1022_Commands/blob/master/Pioneer_VSX-1022_Commands_2012.txt
  - PHP - https://github.com/zuloo/vsxctrl
  - C# - https://github.com/zzattack/pioneer-avr-lib
  - C# - https://github.com/ndsrf/PioneerDesktop
  - Swift - https://github.com/jtonk/vsxMenu
  - Javascript/HomeKit - https://github.com/cellerich/homebridge-pioneeravr
  - Bash - https://github.com/PeterAndreus/PioneerController
  - Python - https://github.com/encinas/pioneeravclient
  - SmartThings / Proxy server - https://github.com/csdozier/device-pioneer-vsx
  - nodejs - https://github.com/dougt/PioneerVolumeControl
  - indigo domotics - http://forums.indigodomo.com/viewtopic.php?t=8737

# Open Ports (VSX-1021 k)

  - Open TCP Port: 	23     		telnet
  - Open TCP Port: 	80     		http
  - Open TCP Port: 	443    		https
  - Open TCP Port: 	1024
  - Open TCP Port: 	1900   		ssdp (Simple service discovery protocol - part of UPnP)
  - Open TCP Port: 	8080   		http-alt
  - Open TCP Port: 	8102
  - Open TCP Port: 	10100  		itap-ddtp
  - Open TCP Port: 	49152
  - Open TCP Port: 	49153
  - Open TCP Port: 	49154
