# SSH PORTU NASIL DEĞİŞTİRİLİR
İlk olarak değişiklik yapmak istediğiniz sunucu ile SSH bağlantısı kurun. Bunu sağlamak için,  
 
```
ssh root@{host}
```
komutu ile aşağıdaki örnekteki gibi bağlantı sağladığınızdan emin olun:    

![Screenshot from 2021-10-18 15-02-31](https://user-images.githubusercontent.com/51738775/137726580-5421edcf-90f4-466b-b295-f08edcdfbbd4.png)

Gerekli düzenlemeleri yapmamız için konfigürasyon dosyasına erişmemiz gerekecek. Bunun için terminalde, 

```
nano /etc/ssh/sshd_config
```

komutunu girmemiz gerek. Aşağıdaki gibi bir dosya açılacak. Bu kısımda **#Port** yazısını aşağıda görseldeki gibi bulduğunuzdan emin olun:  

![port22](https://user-images.githubusercontent.com/51738775/137727324-5d42f75d-fc24-4c72-a8ce-462d7487de05.png)  

**#Port 22** kısmını değiştirmek istediğimiz port ile (ben 2222 yazdım)örnekteki gibi düzenliyoruz:

```
Port 2222
```

Burada dikkat etmemiz gereken kısım başındaki **#** sembolünün kalktığından emin olun. İşlem bitince kaydedip çıkın.

Son olarak şağıdaki komut ile portu aktifleştirin:

```
sudo service ssh restart
```# Linux-ta-Sanal-Konsol-Kapat-lmas-
