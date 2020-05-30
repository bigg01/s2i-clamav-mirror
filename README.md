


https://support.secureaplus.com/how-to-download-clamav-virus-definitions-without-internet/

```bash
#!/bin/bash
wget http://database.clamav.net/main.cvd
sudo cp main.cvd /var/lib/clamav/
sudo chown clamav:clamav /var/lib/clamav/main.cvd
sudo chmod 644 /var/lib/clamav/main.cvd

https://database.clamav.net/main.cvd
https://database.clamav.net/daily.cvd
https://database.clamav.net/bytecode.cvd

```

```
oc new-project ocp4-clamav-mirror

s2i build https://github.com/bigg01/s2i-clamav-mirror.git centos/nginx-116-centos7:latest clamav-mirror


oc import-image --from="centos/nginx-116-centos7" --scheduled=true ngnix --confirm


oc new-app ngnix~https://github.com/bigg01/s2i-clamav-mirror.git clamav-mirror
```