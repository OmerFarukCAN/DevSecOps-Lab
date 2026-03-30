# Lab 1: Linux Kurulumu ve İlk Adımlar

**Süre:** 1-2 saat  
**Zorluk:** Kolay 🟢

## Hedef
Windows bilgisayarınızda WSL2 kurarak Linux ortamını hazırlamak ve temel komutlara giriş yapmak.

## Ön Gereksinimler
- Windows 10/11
- Admin yetkisi

---

## Adım 1: WSL2 Kurulumu

### 1.1 PowerShell'i Admin Olarak Açın

### 1.2 WSL'i Kurun
```powershell
# WSL'i etkinleştir
wsl --install

# Bilgisayarı restart edin
```

### 1.3 Linux Dağıtımını Seçin
Restart sonrası:
```powershell
# Mevcut dağıtımları listele
wsl --list --online

# Ubuntu 22.04 LTS'yi kur (önerilen)
wsl --install -d Ubuntu-22.04
```

### 1.4 İlk Kullanıcı Oluşturun
Kurulum sonrası Ubuntu açılacak ve sizden:
- Kullanıcı adı isteyecek
- Şifre isteyecek (yazarken görünmez, normal)

**🎯 Görev:** Kullanıcı adınızı ve şifrenizi kaydedin!

---

## Adım 2: İlk Komutlarınız

### 2.1 Neredesiniz?
```bash
# Bulunduğunuz dizini gösterir
pwd

# Çıktı: /home/kullaniciadi
```

**💡 Açıklama:**
- `pwd` = Print Working Directory
- Linux'ta her zaman bir dizinde ("klasör"de) bulunursunuz
- `/home/kullaniciadi` sizin "home" dizininiz (Windows'taki C:\Users\kullaniciadi gibi)

### 2.2 İçeride Ne Var?
```bash
# Mevcut dizindeki dosyaları listele
ls

# Detaylı liste (permissions, boyut, tarih)
ls -l

# Gizli dosyalar dahil
ls -la

# İnsan-dostu boyutlar
ls -lah
```

**🎯 Görev:** Bu komutları çalıştırın ve çıktıları karşılaştırın.

### 2.3 Dizinler Arası Gezinme
```bash
# Root dizine git
cd /

# Nelerin olduğunu gör
ls

# Home dizinine geri dön
cd ~
# veya sadece
cd

# Bir üst dizine çık
cd ..

# Önceki dizine geri dön
cd -
```

**🎯 Görev:** 
1. Root dizine gidin (`cd /`)
2. `/etc` dizinine gidin
3. İçeriği listeleyin
4. Home dizininize dönün

---

## Adım 3: Linux Dosya Sistemi Yapısı

### 3.1 Önemli Dizinler

```bash
# Sistem dizinlerini keşfedelim
ls -l /
```

**Temel Dizinler:**
- `/` - Root dizin (her şeyin başı, Windows'taki C:\ gibi)
- `/home` - Kullanıcı home dizinleri
- `/etc` - Konfigürasyon dosyaları
- `/var` - Değişken data (logs, cache)
- `/tmp` - Geçici dosyalar
- `/usr` - Kullanıcı programları
- `/bin` - Temel komutlar
- `/sbin` - Sistem komutları
- `/opt` - Opsiyonel yazılımlar

**🎯 Görev:** Her dizine gidip içinde ne olduğunu keşfedin:
```bash
cd /etc && ls
cd /var/log && ls
cd /tmp && ls
```

---

## Adım 4: Dosya Oluşturma ve Düzenleme

### 4.1 Boş Dosya Oluşturma
```bash
# Home dizinine git
cd ~

# labs adında klasör oluştur
mkdir labs

# labs dizinine git
cd labs

# Boş dosya oluştur
touch ilk-dosyam.txt

# Kontrol et
ls -l
```

### 4.2 Dosyaya İçerik Yazma
```bash
# Echo ile içerik yaz
echo "Merhaba DevSecOps dünyası!" > ilk-dosyam.txt

# Dosyayı okuma
cat ilk-dosyam.txt

# Dosyaya ekleme yap (overwrite değil, append)
echo "İkinci satırım" >> ilk-dosyam.txt

# Tekrar oku
cat ilk-dosyam.txt
```

**💡 Fark:**
- `>` : Dosyanın içeriğini siler ve yenisini yazar
- `>>` : Dosyanın sonuna ekler

### 4.3 Nano ile Dosya Düzenleme
```bash
# Nano editörü ile aç
nano ilk-dosyam.txt
```

**Nano Kısayolları:**
- `Ctrl + O` : Kaydet
- `Enter` : Kaydetmeyi onayla
- `Ctrl + X` : Çık

**🎯 Görev:** 
1. Dosyaya birkaç satır daha ekleyin
2. Kaydedin ve çıkın
3. `cat` ile içeriği kontrol edin

---

## Adım 5: Dosya Kopyalama ve Taşıma

### 5.1 Kopyalama (cp)
```bash
# Dosyayı kopyala
cp ilk-dosyam.txt ikinci-dosyam.txt

# Kontrol et
ls -l

# Klasör kopyalama (recursive)
mkdir proje1
mkdir proje1/src
echo "kod" > proje1/src/main.cs

# Klasörü kopyala
cp -r proje1 proje2

# Kontrol et
ls -R proje2
```

### 5.2 Taşıma ve Yeniden Adlandırma (mv)
```bash
# Dosyayı taşı
mv ikinci-dosyam.txt proje1/

# Dosyayı yeniden adlandır
mv proje1/ikinci-dosyam.txt proje1/yeni-isim.txt

# Kontrol et
ls proje1/
```

### 5.3 Silme (rm)
```bash
# Dosya sil
rm proje1/yeni-isim.txt

# Boş klasör sil
rmdir proje2/src

# Dolu klasör sil (DİKKAT! Geri alınamaz!)
rm -r proje2

# Onay isteyerek sil (güvenli)
rm -i ilk-dosyam.txt
```

**⚠️ UYARI:** Linux'ta `rm` ile silinen dosyalar geri getirilemiyor! Çöp kutusu yok!

---

## Adım 6: Yardım Alma ve Dokümantasyon

### 6.1 man (Manual) Sayfaları
```bash
# Bir komutun detaylı dokümantasyonunu okuma
man ls
man cp
man grep

# man içinde:
# - Space: Sonraki sayfa
# - q: Çık
# - /kelime: Arama yap
```

### 6.2 --help Parametresi
```bash
# Hızlı yardım
ls --help
cp --help
```

**🎯 Görev:** `man chmod` komutunu çalıştırın ve okuyun (sonraki lab'da lazım olacak)

---

## Adım 7: Sistem Bilgisi

```bash
# İşletim sistemi bilgisi
uname -a
cat /etc/os-release

# Disk kullanımı
df -h

# Bellek kullanımı
free -h

# CPU bilgisi
lscpu

# Network interface'ler
ip addr
# veya eski komut
ifconfig
```

**🎯 Görev:** Sisteminizin özelliklerini öğrenin ve not alın.

---

## Lab Sonrası Değerlendirme

### ✅ Başarı Kriterleri
Aşağıdakileri yapabiliyorsanız lab'ı başarıyla tamamladınız:

1. [ ] WSL2 kurulumu tamamlandı
2. [ ] Temel navigasyon komutlarını kullanabiliyorum
3. [ ] Dosya oluşturup düzenleyebiliyorum
4. [ ] Dosya kopyalama/taşıma/silme yapabiliyorum
5. [ ] man sayfalarını okuyabiliyorum

### 🏆 Challenge
Aşağıdaki görevleri komut satırından yapın:

1. Home dizininizde `devsecops-journey` adında bir klasör oluşturun
2. İçine `day1-notes.txt` dosyası oluşturun
3. Dosyaya "Bugün öğrendiklerim:" yazıp, 5 madde ekleyin
4. Bu dosyayı `notes-backup.txt` olarak kopyalayın
5. `ls -lah` çıktısını bir dosyaya kaydedin

**Çözüm komutları:**
```bash
cd ~
mkdir devsecops-journey
cd devsecops-journey
nano day1-notes.txt
# (İçeriği yaz, kaydet, çık)
cp day1-notes.txt notes-backup.txt
ls -lah > directory-listing.txt
```

---

## Öğrendiklerinizi Pekiştirin

### Günlük Pratik (5-10 dakika)
Her gün bu komutları kullanarak pratik yapın:
```bash
pwd           # Neredeyim?
ls -lah       # Ne var burada?
cd <dizin>    # Başka yere git
cat <dosya>   # Dosya oku
man <komut>   # Yardım al
```

### Cheat Sheet
Sık kullanacağınız komutlar için `cheatsheets/` klasörüne bakın.

---

## Sonraki Adım
✅ Lab 1'i tamamladıktan sonra → `LAB-02-files.md`

## Sorular & Notlar
Aşağıya notlarınızı ekleyin:

```
[Notlarınız buraya]
```

---

## Faydalı Kaynaklar
- [Linux Journey - Command Line](https://linuxjourney.com/lesson/the-shell)
- [Explain Shell](https://explainshell.com/) - Komutları açıklayan web sitesi
- [Ubuntu WSL Tutorial](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10)
