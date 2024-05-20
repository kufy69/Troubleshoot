# ติดตั้ง Queuemetrics กับ Issable Asterisk 18
install Queuemetrics with Espresso
```
wget https://yum.loway.ch/loway.repo -O /etc/yum.repos.d/loway.repo
yum install queuemetrics-espresso
```

แก้ไขไฟล์ Config uniloader ใน ``/etc/sysconfig/`` ให้ชี้ On-premise database
```
# QueueMetrics-Live or QueueMetrics via HTTP
# make sure that user "webqloader" is enabled and has the correct
# password.
#URI=https://CHANGEME.queuemetrics-live.com/CHANGEME
#LOGIN=webqloader
#UPASSWD=CHANGEME
#TOKEN=

# On-premise QueueMetrics instance, connection via database (deprecated)
URI="mysql:tcp(127.0.0.1:3306)/queuemetrics?allowOldPasswords=1"
LOGIN=queuemetrics
PASS=javadude
TOKEN=P001
```

แก้ไข AMISECRET ในไฟล์ Config unitracker ใน ``/etc/sysconfig/`` **สามารดู AMISECRET ที่ ``/etc/asterisk/manager.conf``
```
AMISECRET=แก้ตรงนี้
```

Restart Service
```
systemctl restart  uniloader
systemctl restart  unitracker
```

Install Queuemetrics dialplan 
```
cp /usr/local/uniloader/extensions/extensions_queuemetrics.conf /etc/asterisk/.
```
และ include ``#include extensions_queuemetrics.conf`` ใน ``/etc/asterisk/extensions_custom.conf`` จากนั้น Save และ Reload dialplan
```
asterisk -rx "dialplan reload"
```

จากนั้น login เข้า Queuemetrics ไปที่ Edit system parameters เพื่อลบ Tag HTML  Error Espresso ออก โดย ``Ctrl+F`` ค้นหา Espresso ลบ Tag HTML ออก

# =======END=======
