# whosthere-iot
Whosthere daemon running on raspberry pi

#Instalation

sudo nano /usr/local/bin/checkwifi.sh

```
ping -c4 IP_ADDRESS > /dev/null
if [ $? != 0 ]
then
  sudo /sbin/shutdown -r now
fi
```

sudo chmod 775 /usr/local/bin/checkwifi.sh

sudo crontab -e

Pick your favourite text editor (such as nano) and at the bottom of the file, 
under all of the comments, add @reboot nohup sudo /usr/bin/python /home/pi/presence.py 
& to run the presence.py script. If you named your script something else or put it in 
a different directory, replace /home/pi/presence.py with the correct path. Then, under
that, add */5 * * * * /usr/bin/sudo -H /usr/local/bin/checkwifi.sh >> /dev/null 2>&1 
to run the checkwifi.sh script. Exit crontab and reboot the Pi to run your new presence detector!
