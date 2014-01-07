vgaswitcheroo-systemd
=====================

Systemd scripts that turns off discrete graphics in Linux if you use switchable graphics. This script also turns on the discrete graphics before suspend to fix the fan issue.

This is tested under Fedora 20 and with Intel integrated graphics and AMD discrete graphics.


Install
=======

Clone this repository and copy all the service files as root to ```/lib/systemd/system/```

```
# cp *.service /lib/systemd/system
```

Then enable the services as root

```
# systemctl enable vgaswitcheroo-hibernate.service
# systemctl enable vgaswitcheroo-suspend.service
# systemctl enable vgaswitcheroo-resume.service
# systemctl enable vgaswitcheroo-boot.service
```

Usage
=====

To see if it's working properly, after a reboot or suspend run ```# cat /sys/kernel/debug/vgaswitcheroo/switch``` as root and check if DIS is set to Off and not Pwr like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
```

