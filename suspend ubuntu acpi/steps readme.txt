##I fixed with using acpid with the following solution
sudo gedit /etc/acpi/events/lidclose


##copy, paste & save
event=button[ /]lid
action=/etc/acpi/lidclose.sh


##execute
sudo gedit /etc/acpi/lidclose.sh


##copy, paste & save
#!/bin/bash
echo "close" > /home/jesse/close.txt
if grep -q closed /proc/acpi/button/lid/*/state

then
     /usr/sbin/pm-suspend
fi


##execute
sudo chmod ugo+x /etc/acpi/lidclose.sh
