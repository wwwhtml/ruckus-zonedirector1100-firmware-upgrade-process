
<h2> Ruckus Zone Director 1100 Firmware Upgrade Steps, Via SSH.</h2>
<br>
If the ZoneDirector 1100 has been factory reset,  upgrading from the lowest version one at the time all the way to the last one worked for me. Bloody slow process, but works. Each upgrade takes about 15 minutes or so. There are 15 versions, starting from zd1100_9.1.2.0.8.ap_9.1.2.0.8.img to zd1100_9.10.2.0.114.ap_9.10.2.0.114.img. This process assumes that you already have a TFTP server with the firmware ready for connections. Important to know, the Access Points will be automatically upgraded by the Controller once it gets upgraded.<br>
<br>
SSH into it: If you Zone Director firmware version is under 9.8.3.0 built 44 use this ssh connection format (replace IP for your ZD’s IP):<br><br>
<b>ssh -o KexAlgorithms=diffie-hellman-group1-sha1 -o Ciphers=aes256-cbc 192.168.0.186</b>
<br>
Or if you ZD firmware is version 9.8.3.0 built 44 and up (replace IP for your own ZD’s IP):<br>
<b>ssh  192.168.0.186</b><br>
<br>
The default username: admin <br>
The default password: admin <br>
<br>
<b>enable</b><br>
<b>show sysinfo</b><br>
<b>debug</b><br>
<br>
Connecting to the TFTP server to download the firmware image into the Zone Director. Change zd1100_9.10.2.0.114.ap_9.10.2.0.114.img for the image version that you want to get.:<br>
<b>fw_upgrade -p tftp -s 192.168.0.193 -n zd1100_9.10.2.0.114.ap_9.10.2.0.114.img</b><br>
<br>
Press "y" to initiate the upgrade. Slow process, probably 20 minutes or so, you may want to have another window pinging the ZD’s IP to see it going down and when it is up:<br><br>
<b>y</b>
<br><br>
The upgrade takes place, the status light will be green when ready.
<br>
<br>
Screenshot example of the process:<br>
<br>
<center><img src="https://github.com/wwwhtml/ruckus-zonedirector1100-firmware-upgrade-process/blob/main/Ruckus_ZoneDirector-1100_firmware-upgrade-via-SSH.png?raw=true" alt="Screenshot showing the process of the Ruckus Zone Director firmware upgrade process" /></center>


## Web Browser Configuration
----------------------------
Once the ZD firmware has updated/upgraded to 9.8.3.0 built 44 or greater, now its web server can accept new browsers to continue the password change, SSID, etc configuration. Replace IP with your own ZD’s.

https://YourZoneDirectorIP

The default username: admin 
The default password: admin

Don't forget to change that password.

Hope it helps someone up there.


