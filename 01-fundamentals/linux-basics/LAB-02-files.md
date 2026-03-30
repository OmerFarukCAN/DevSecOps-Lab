# Lab 2: Dosya Operasyonları ve Text Processing

**Süre:** 2-3 saat  
**Zorluk:** Kolay-Orta 🟢

## Hedef
Linux'ta dosyalarla çalışma, text işleme ve güçlü komut satırı araçlarını kullanma.

---

## Bölüm 1: Gelişmiş Dosya Okuma

### 1.1 cat, head, tail
```bash
# Pratik için test dosyası oluştur
cd ~/labs
seq 1 100 > numbers.txt

# Tüm dosyayı göster
cat numbers.txt

# İlk 10 satırı göster
head numbers.txt

# İlk 5 satırı göster
head -n 5 numbers.txt

# Son 10 satırı göster
tail numbers.txt

# Son 20 satırı göster
tail -n 20 numbers.txt

# Dosyayı sürekli izle (log takibi için)
tail -f numbers.txt
# (Ctrl+C ile durdurun)
```

### 1.2 less ve more
```bash
# Uzun dosyaları sayfa sayfa okuma
less numbers.txt

# less içinde:
# - Space: Sonraki sayfa
# - b: Önceki sayfa
# - /kelime: Arama
# - n: Sonraki eşleşme
# - q: Çık
```

**🎯 Görev:** Sistem log dosyasını inceleyin:
```bash
sudo less /var/log/syslog
# veya Ubuntu'da
sudo less /var/log/kern.log
```

---

## Bölüm 2: Dosya Arama (find)

### 2.1 Temel find Kullanımı
```bash
# Test ortamı oluştur
cd ~/labs
mkdir -p test-find/level1/level2
touch test-find/dosya1.txt
touch test-find/level1/dosya2.log
touch test-find/level1/level2/dosya3.txt

# Tüm dosyaları bul
find test-find/

# Sadece .txt dosyalarını bul
find test-find/ -name "*.txt"

# Sadece .log dosyalarını bul
find test-find/ -name "*.log"

# Case-insensitive arama
find test-find/ -iname "DOSYA*"
```

### 2.2 Dosya Tipine Göre Arama
```bash
# Sadece dosyaları bul
find test-find/ -type f

# Sadece dizinleri bul
find test-find/ -type d

# 7 günden eski dosyaları bul
find test-find/ -type f -mtime +7

# Son 24 saatte değişenleri bul
find test-find/ -type f -mtime -1
```

### 2.3 Bulduklarınızla İşlem Yapma
```bash
# Bulunan dosyaları başka yere kopyala
find test-find/ -name "*.txt" -exec cp {} backup/ \;

# Bulunan dosyaları sil (DİKKATLİ!)
find test-find/ -name "*.log" -delete
```

**🎯 Görev:** Home dizininizde tüm .txt dosyalarını bulun:
```bash
find ~ -name "*.txt" 2>/dev/null
```
*(2>/dev/null hataları gizler)*

---

## Bölüm 3: Text Search (grep)

### 3.1 Temel grep
```bash
# Test dosyası oluştur
cat > users.txt << EOF
alice:admin:active
bob:developer:active
charlie:developer:inactive
david:admin:active
eve:tester:active
frank:developer:inactive
EOF

# Basit arama
grep "admin" users.txt

# Case-insensitive arama
grep -i "ADMIN" users.txt

# Satır numaralarıyla göster
grep -n "developer" users.txt

# Kaç satır eşleşti?
grep -c "active" users.txt

# Eşleşmeyenleri göster (inverse)
grep -v "inactive" users.txt
```

### 3.2 Regular Expressions ile grep
```bash
# 'a' ile başlayanlar
grep "^a" users.txt

# 'e' ile bitenler
grep "e$" users.txt

# 'devel' veya 'test' içerenler
grep -E "devel|test" users.txt

# İki ardışık 'e' içerenler
grep "ee" users.txt
```

### 3.3 Recursive grep
```bash
# Tüm alt dizinlerde ara
grep -r "TODO" ~/labs/

# Sadece belirli dosya tiplerinde ara
grep -r --include="*.txt" "error" ~/labs/
```

**🎯 Görev:** Sistemde "error" kelimesini içeren tüm log dosyalarını bulun:
```bash
sudo grep -r "error" /var/log/ 2>/dev/null | head -20
```

---

## Bölüm 4: Pipes ve Redirection

### 4.1 Output Redirection
```bash
# Çıktıyı dosyaya yaz (overwrite)
ls -l > dosya-listesi.txt

# Çıktıyı dosyaya ekle (append)
date >> dosya-listesi.txt

# Hataları başka dosyaya yaz
ls /nonexistent 2> errors.txt

# Hem çıktı hem hata aynı dosyaya
ls -l /etc /nonexistent > all-output.txt 2>&1
```

### 4.2 Pipes (|)
Bir komutun çıktısını diğer komuta girdi olarak verme:

```bash
# ls çıktısını grep'e pipe et
ls -l /etc | grep "conf"

# Satır sayısını bul
cat users.txt | wc -l

# Sırala
cat users.txt | sort

# Unique değerler
cat users.txt | cut -d: -f2 | sort | uniq

# En çok kullanılan komutlar
history | awk '{print $2}' | sort | uniq -c | sort -rn | head -10
```

**💡 Pipe Mantığı:**
```
komut1 | komut2 | komut3
   ↓        ↓        ↓
çıktı → girdi → çıktı → girdi → sonuç
```

**🎯 Görev:** `/etc` dizinindeki "conf" ile biten dosyaları bulun ve sayısını öğrenin:
```bash
ls /etc/*.conf 2>/dev/null | wc -l
```

---

## Bölüm 5: Text Processing Tools

### 5.1 cut - Sütun Ayırma
```bash
# Delimiter ile ayır ve sütun seç
cat users.txt | cut -d: -f1
# Sadece kullanıcı adları

cat users.txt | cut -d: -f2
# Sadece roller

cat users.txt | cut -d: -f1,3
# Kullanıcı adı ve status
```

### 5.2 sort - Sıralama
```bash
# Alfabetik sırala
sort users.txt

# Ters sırala
sort -r users.txt

# Unique sırala
sort -u users.txt
```

### 5.3 wc - Sayma
```bash
# Satır, kelime, karakter sayısı
wc users.txt

# Sadece satır sayısı
wc -l users.txt

# Sadece kelime sayısı
wc -w users.txt
```

### 5.4 uniq - Tekrarlananları Bulma
```bash
# Test dosyası
cat > fruits.txt << EOF
apple
banana
apple
orange
banana
apple
EOF

# Önce sırala, sonra unique yap
sort fruits.txt | uniq

# Tekrar sayısıyla
sort fruits.txt | uniq -c

# En çok tekrarlananlar
sort fruits.txt | uniq -c | sort -rn
```

---

## Bölüm 6: Gerçek Dünya Senaryoları

### Senaryo 1: Log Analizi
```bash
# Fake log oluştur
cat > app.log << EOF
2026-03-30 10:00:00 INFO Application started
2026-03-30 10:00:15 ERROR Database connection failed
2026-03-30 10:00:30 INFO Retrying connection
2026-03-30 10:00:45 INFO Connection established
2026-03-30 10:01:00 WARN Low memory warning
2026-03-30 10:01:15 ERROR Null reference exception
2026-03-30 10:01:30 INFO Request processed
EOF

# Sadece ERROR'ları bul
grep "ERROR" app.log

# ERROR sayısı
grep -c "ERROR" app.log

# Tarih ve mesaj
cat app.log | cut -d' ' -f1,2,4-

# Son 5 log
tail -n 5 app.log
```

### Senaryo 2: Sistem Bilgisi Toplama
```bash
# Sistem raporu oluştur
cat > system-report.sh << 'EOF'
#!/bin/bash
echo "=== SİSTEM RAPORU ==="
echo "Tarih: $(date)"
echo ""
echo "=== İŞLETİM SİSTEMİ ==="
cat /etc/os-release | grep PRETTY_NAME
echo ""
echo "=== DISK KULLANIMI ==="
df -h | grep -E "Filesystem|/$"
echo ""
echo "=== BELLEK ==="
free -h
echo ""
echo "=== ÇALIŞAN PROCESS SAYISI ==="
ps aux | wc -l
EOF

# Çalıştırılabilir yap
chmod +x system-report.sh

# Çalıştır
./system-report.sh
```

**🎯 Görev:** Bu script'i çalıştırın ve çıktısını `my-system-info.txt` dosyasına kaydedin.

---

## Lab Sonu Challenge Projesi

### 🎯 Proje: Dosya Organizatör Script

**Senaryo:** Bir dizinde karışık dosyalar var. Bunları uzantılarına göre klasörlere ayıran bir sistem oluşturun.

**Gereksinimler:**
1. `organize-files` adında klasör oluşturun
2. İçine 10 adet farklı uzantılı dosya oluşturun (.txt, .log, .md, .json, .cs)
3. Bir script yazın ki:
   - Tüm .txt dosyalarını `txt-files/` klasörüne taşısın
   - Tüm .log dosyalarını `log-files/` klasörüne taşısın
   - Tüm .md dosyalarını `markdown-files/` klasörüne taşısın
   - Diğerlerini `other-files/` klasörüne taşısın
4. İşlem tamamlandığında rapor yazdırsın

**İpuçları:**
- `mkdir -p` ile klasör oluşturun
- `find` ile dosyaları bulun
- `mv` ile taşıyın
- `echo` ile rapor yazdırın

**Başlangıç:**
```bash
cd ~/labs
mkdir organize-files
cd organize-files

# Test dosyaları oluştur
touch file1.txt file2.log file3.md file4.json file5.cs
touch file6.txt file7.log file8.md file9.txt file10.log

# Şimdi organize eden script'i yazın
nano organize.sh
```

<details>
<summary>💡 Çözüm (Önce kendiniz deneyin!)</summary>

```bash
#!/bin/bash

# Organize script
echo "Dosyalar organize ediliyor..."

# Klasörleri oluştur
mkdir -p txt-files log-files markdown-files other-files

# .txt dosyaları
find . -maxdepth 1 -name "*.txt" -exec mv {} txt-files/ \;

# .log dosyaları
find . -maxdepth 1 -name "*.log" -exec mv {} log-files/ \;

# .md dosyaları
find . -maxdepth 1 -name "*.md" -exec mv {} markdown-files/ \;

# Diğerleri
find . -maxdepth 1 -type f \( ! -name "*.txt" ! -name "*.log" ! -name "*.md" ! -name "organize.sh" \) -exec mv {} other-files/ \;

echo "Organizasyon tamamlandı!"
echo "=== RAPOR ==="
echo "TXT dosyaları: $(ls txt-files/ | wc -l)"
echo "LOG dosyaları: $(ls log-files/ | wc -l)"
echo "MD dosyaları: $(ls markdown-files/ | wc -l)"
echo "Diğer dosyalar: $(ls other-files/ | wc -l)"
```
</details>

---

## Öğrendiklerim

**Bu lab'da öğrendiklerim:**
- [ ] cat, head, tail ile dosya okuma
- [ ] find ile dosya arama
- [ ] grep ile text arama
- [ ] Pipes (|) kullanımı
- [ ] Output redirection (>, >>)
- [ ] Text processing araçları (cut, sort, wc, uniq)

**Notlarım:**
```
[Buraya notlarınızı ekleyin]
```

---

## Sonraki Adım
✅ Lab 2'yi tamamladıktan sonra → `LAB-03-permissions.md`
