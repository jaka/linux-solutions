## systemd

### FAQ
If you experience the following two issues:
```
$ timedatectl
Failed to create bus connection: No such file or directory
```
```
$ hostnamectl 
Failed to create bus connection: No such file or directory
```
Then `dbus` is missing, install it.
* Debian & Ubuntu: `apt-get install -y dbus`
