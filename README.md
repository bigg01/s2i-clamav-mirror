


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


oc new-project ocp4-clamav-mirror

s2i 

centos/nginx-116-centos7


oc import-image --from="centos/nginx-116-centos7" --scheduled=true golang --confirm


oc new-app https://github.com/bigg01/go-s2i-centos7.git --docker-image=centos/nginx-116-centos7:latest --context-dir=test-app

  oc new-build . --docker-image=repo/langimage

FILES="https://database.clamav.net/main.cvd
https://database.clamav.net/daily.cvd
https://database.clamav.net/bytecode.cvd"

mkdir database/
cd database
for f  in $FILES
do
wget $f
done


oc new-build database --docker-image=centos/nginx-116-centos7:latest

oc new-app . --docker-image=centos/nginx-116-centos7:latest


oc new-build   --docker-image=centos/nginx-116-centos7:latest --name mirror --binary --strategy docker

oc start-build cookbook --from-dir=.


s2i build https://github.com/bigg01/s2i-clamav-mirror.git --docker-image=centos/nginx-116-centos7:latest clamav-mirror


 s2i build https://github.com/bigg01/s2i-clamav-mirror.git centos/nginx-116-centos7:latest clamav-mirror