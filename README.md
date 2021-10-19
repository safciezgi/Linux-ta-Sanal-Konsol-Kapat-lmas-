# Ubuntu'da Sanal Konsollar Nasıl Kapatılır?
Sanal Konsollar (TTY'lar) arası geçişleri (Ctrl+Alt+F1…F6) Ubuntu'da nasıl kapatacağımızı araştırmalarım sonucunda karşılaştığım cevaplar üzerinden sizlere Türkçe kaynak olarak anlatacağım.  

## İlk Yöntem:
--------

```cmd
sudo tee -a /etc/init/tty{1..6}.override <<<"manual"
```

## İkinci Yöntem:
--------
[/etc/X11/xorg.conf](https://manpages.ubuntu.com/manpages/impish/en/man5/xorg.conf.5.html) dosyasını aşağıdaki komut ile açıp oluşturuyoruz.

```cmd
sudo -i gedit /etc/X11/xorg.conf
```
Ve aşağıdaki satırları dosyanın içine ekliyoruz:

```cmd
Section "ServerFlags"
    Option "DontVTSwitch" "true"
EndSection
```

## Üçüncü Yöntem:
--------
Aşağıdaki komutları sırası ile uygulayarak Root kullanıcısı olarak aşağıda belirtilen ilgili dizini açıyoruz:

```cmd
sudo su

nano /etc/default/console-setup
```
![tty_ss1](https://user-images.githubusercontent.com/51738775/137868005-960f7114-f8a1-450a-a8f9-2f8ae609dd86.png)

>ACTIVE_CONSOLES="/dev/tty[1-6]" 

kısmını bulduğunuzdan emin olun ve seçeneğinize göre değiştirin.  

Diyelim ki ilk 2'si kalsın istiyorsunuz o zaman ilgili kısmı şu şekilde düzenleyelirisiniz: 
>ACTIVE_CONSOLES="/dev/tty[1-2]"

Son olarak ilgili tty conf dosyalarını bulun(Bu kısım işletim sisteminizin sürümüne göre farklılık gösterecektir.) ve kapattığınız ekranlarla ilgili satırları yorum satırı yaptığınızdan emin olun.