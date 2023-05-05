Start Nessus Service
```bash
sudo service nessusd start
```

Stop Nessus Service
```bash
sudo service nessusd stop
```

Add Product Key, Activate, and Update Pluggins
```bash
sudo /opt/nessus/sbin/nessuscli fetch --register XXXX-XXXX-XXXX-XXXX
```

Exceptions Rule File Location
```bash
sudo nano /opt/nessus/etc/nessus/nessusd.rules
```

Change Password for Specified User
```bash
sudo /opt/nessus/sbin/nessuscli chpasswd usertoreset
```