# Lab 3: Dosya İzinleri ve Ownership

**Süre:** 2-3 saat  
**Zorluk:** Orta 🟡

## Hedef
Linux dosya izinlerini anlamak ve yönetmek - DevSecOps'ta güvenlik için kritik!

---

## Bölüm 1: İzinleri Anlamak

### 1.1 ls -l Çıktısını Okuma
```bash
cd ~/labs
touch test-file.txt
ls -l test-file.txt
```

**Çıktı örneği:**
```
-rw-r--r-- 1 omer omer 0 Mar 30 10:00 test-file.txt
│││││││││  │  │    │   │      │          │
│││││││││  │  │    │   │      │          └─ Dosya adı
│││││││││  │  │    │   │      └─ Zaman
│││││││││  │  │    │   └─ Boyut
│││││││││  │  │    └─ Grup
│││││││││  │  └─ Sahip (owner)
│││││││││  └─ Link sayısı
└┬┬┬┬┬┬┬┬─ İzinler
 │││││││└─ Others (Diğer kullanıcılar)
 ││││││└── Group (Grup)
 │││││└─── Owner (Sahip)
 ││││└──── Others execute
 │││└───── Others write
 ││└────── Others read
 │└─────── (Group izinleri benzer)
 └──────── Dosya tipi (- = file, d = directory)
```

### 1.2 İzin Tipleri
- **r** (read = 4) : Okuma
- **w** (write = 2) : Yazma
- **x** (execute = 1) : Çalıştırma

**Örnekler:**
- `rwx` = 7 (4+2+1)
- `rw-` = 6 (4+2+0)
- `r--` = 4 (4+0+0)
- `r-x` = 5 (4+0+1)

---

## Bölüm 2: chmod - İzinleri Değiştirme

### 2.1 Numeric (Sayısal) Mod
```bash
# Script oluştur
cat > myscript.sh << 'EOF'
#!/bin/bash
echo "Merhaba DevSecOps!"
EOF

# İzinleri kontrol et
ls -l myscript.sh

# Çalıştırmayı dene (HATA verecek)
./myscript.sh

# Çalıştırma izni ver
chmod +x myscript.sh

# Tekrar dene (Başarılı!)
./myscript.sh

# Sayısal mod ile izin ver
chmod 755 myscript.sh
# 755 = rwxr-xr-x (owner: rwx, group: r-x, others: r-x)

chmod 644 test-file.txt
# 644 = rw-r--r-- (owner: rw, group: r, others: r)

chmod 600 secret.txt
# 600 = rw------- (sadece owner okuyabilir/yazabilir)
```

### 2.2 Symbolic (Sembolik) Mod
```bash
# Herkese execute izni ekle
chmod +x myscript.sh

# Owner'dan write izni kaldır
chmod u-w test-file.txt

# Group'a write izni ekle
chmod g+w test-file.txt

# Others'tan tüm izinleri kaldır
chmod o-rwx secret.txt

# Birden fazla
chmod u+rwx,g+rx,o-rwx myscript.sh
```

**💡 Semboller:**
- `u` = user (owner)
- `g` = group
- `o` = others
- `a` = all (hepsi)
- `+` = ekle
- `-` = kaldır
- `=` = tam olarak ayarla

### 2.3 Recursive İzin Değiştirme
```bash
# Test ortamı
mkdir -p secure-project/{src,config,logs}
touch secure-project/src/app.cs
touch secure-project/config/settings.json

# Tüm klasöre izin ver
chmod -R 755 secure-project/

# Kontrol et
ls -lR secure-project/
```

**⚠️ GÜVENLİK NOTU:**
```bash
# ASLA BUNU YAPMAYIN! (Güvenlik riski)
chmod 777 -R /

# 777 = Herkes her şeyi yapabilir (çok tehlikeli!)
```

---

## Bölüm 3: chown - Sahipliği Değiştirme

### 3.1 Owner Değiştirme
```bash
# Yeni kullanıcı oluştur (root gerekli)
sudo useradd testuser

# Dosya sahibini değiştir
sudo chown testuser test-file.txt

# Kontrol et
ls -l test-file.txt

# Geri al
sudo chown $USER test-file.txt
```

### 3.2 Group Değiştirme
```bash
# Group değiştir
sudo chown :testuser test-file.txt

# Hem owner hem group
sudo chown testuser:testuser test-file.txt

# Recursive
sudo chown -R $USER:$USER secure-project/
```

---

## Bölüm 4: Güvenli Dosya Yönetimi - DevSecOps Perspektifi

### 4.1 Sensitive Dosyaları Koruma
```bash
# Secret dosya oluştur
cat > ~/.env << EOF
DATABASE_PASSWORD=SuperSecret123
API_KEY=abc123xyz789
EOF

# Sadece siz okuyabilir
chmod 600 ~/.env

# Kontrol et
ls -l ~/.env

# Başkası okuyamaz
cat ~/.env  # Başarılı (siz owner'sınız)
```

### 4.2 Script'leri Güvenli Çalıştırma
```bash
# Deployment script
cat > deploy.sh << 'EOF'
#!/bin/bash
echo "Deploying application..."
echo "Using secret key: $SECRET_KEY"
EOF

# Sadece owner çalıştırabilir
chmod 700 deploy.sh

# Veya execute izni ekle
chmod +x deploy.sh
```

### 4.3 Log Dosyalarını Koruma
```bash
# Log dizini oluştur
mkdir -p ~/logs

# Sadece owner yazabilir, diğerleri okuyabilir
chmod 644 ~/logs/*.log 2>/dev/null || true

# Log dizini: owner her şeyi, diğerleri sadece okuyabilir
chmod 755 ~/logs
```

---

## Bölüm 5: sudo ve Privilege Escalation

### 5.1 sudo Nedir?
**sudo** = "SuperUser DO" - Root yetkisiyle komut çalıştırma

```bash
# Normal kullanıcı olarak /etc'ye yazamazsınız
echo "test" > /etc/test.txt
# Permission denied!

# sudo ile yapabilirsiniz
sudo echo "test" > /etc/test.txt

# Dikkat: Redirection sudo'dan sonra çalışır, bu yüzden:
echo "test" | sudo tee /etc/test.txt

# Root olarak shell açma (DİKKATLİ!)
sudo -i
exit  # Çıkmayı unutmayın!
```

### 5.2 sudo Best Practices (DevSecOps)
```bash
# Hangi sudo yetkiniz var?
sudo -l

# Şifre timeout'u kontrol et
sudo -v

# sudo ile tek komut çalıştır (güvenli)
sudo apt update

# sudo shell açma (riskli, avoid)
# sudo su -
```

**🔒 Güvenlik İpuçları:**
- ❌ `chmod 777` ASLA kullanmayın
- ❌ Root olarak sürekli çalışmayın
- ✅ Minimum privilege principle: Sadece gerekli izinleri verin
- ✅ Secret dosyalar için `600` izni kullanın
- ✅ Script'ler için `700` veya `755` kullanın

---

## Pratik Egzersizler

### Egzersiz 1: Güvenli Web App Deployment
```bash
# Senaryo: Bir web app deploy ediyorsunuz
mkdir -p ~/webapp/{app,config,logs,secrets}

# App dosyaları - herkes okuyabilir
touch ~/webapp/app/index.html
chmod 644 ~/webapp/app/index.html

# Config - sadece app grubu okuyabilir
touch ~/webapp/config/appsettings.json
chmod 640 ~/webapp/config/appsettings.json

# Secrets - sadece owner
touch ~/webapp/secrets/connection-string.txt
chmod 600 ~/webapp/secrets/connection-string.txt

# Logs - append edilebilir
touch ~/webapp/logs/app.log
chmod 644 ~/webapp/logs/app.log

# Kontrol et
ls -lR ~/webapp/
```

### Egzersiz 2: Permission Audit Script
```bash
# Güvensiz izinlere sahip dosyaları bulan script
cat > permission-audit.sh << 'EOF'
#!/bin/bash

echo "=== GÜVENLİK AUDIT ==="
echo "777 izinli dosyalar (TEHLİKELİ!):"
find ~ -type f -perm 0777 2>/dev/null

echo ""
echo "World-writable dosyalar (RİSKLİ!):"
find ~ -type f -perm -002 2>/dev/null

echo ""
echo "SUID dosyalar:"
find ~ -type f -perm -4000 2>/dev/null
EOF

chmod +x permission-audit.sh
./permission-audit.sh
```

---

## Lab Sonrası Değerlendirme

### ✅ Başarı Kriterleri
- [ ] `ls -l` çıktısını okuyup anlayabiliyorum
- [ ] chmod ile izinleri değiştirebiliyorum (hem numeric hem symbolic)
- [ ] chown ile ownership değiştirebiliyorum
- [ ] Güvenli dosya izinleri ayarlayabiliyorum
- [ ] sudo'yu güvenli kullanabiliyorum

### 📝 Quiz

1. `chmod 755 script.sh` ne anlama gelir?
2. Bir secret dosya için en güvenli izin nedir?
3. `sudo` ne zaman kullanılmalı?
4. `-rw-r--r--` izin notasyonunu sayısal olarak yazın.

<details>
<summary>Cevaplar</summary>

1. Owner: read+write+execute (7), Group: read+execute (5), Others: read+execute (5)
2. `600` (sadece owner okuyabilir/yazabilir)
3. Sadece system-level işlemler için (package install, system file edit)
4. 644
</details>

---

## Önemli Komutlar Özeti

```bash
# İzinleri görme
ls -l [dosya]

# İzin değiştirme (sayısal)
chmod 755 dosya.sh
chmod 600 secret.txt

# İzin değiştirme (sembolik)
chmod +x script.sh
chmod u+w,g-w,o-rwx dosya.txt

# Ownership değiştirme
sudo chown user:group dosya.txt

# Recursive işlemler
chmod -R 755 klasor/
sudo chown -R user:group klasor/
```

---

## Sonraki Adım
✅ Lab 3'ü tamamladıktan sonra → `LAB-04-processes.md`

## Notlarınız
```
[Buraya notlarınızı ekleyin]
```
