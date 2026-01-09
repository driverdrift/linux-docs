display amount of free and used memory in the system
```sh
free -h
```

add swap memory when necessary
```sh
dd if=/dev/zero of=/swapfile bs=128M count=8
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile  # temporarily swapon, auto swapoff when reboot
```

check if enabled
```sh
swapon --show
```

swapon permanently when reboot
```
grep -q '^/swapfile ' /etc/fstab || echo '/swapfile none swap sw 0 0' >> /etc/fstab
swapon -a  # make all devices marked as "swap" in /etc/fstab available to check errors after configured
```
