# Linux Command Cheat Sheet

> Hızlı referans için en çok kullanılan komutlar

## 📁 Dosya ve Dizin İşlemleri

```bash
# Navigasyon
pwd                    # Bulunduğun dizini göster
cd /path/to/dir        # Dizine git
cd ~                   # Home dizinine git
cd ..                  # Bir üst dizine git
cd -                   # Önceki dizine dön

# Listeleme
ls                     # Dosyaları listele
ls -l                  # Detaylı liste
ls -lah                # Gizli dosyalar + insan-dostu boyutlar
ls -lt                 # Zamana göre sırala (newest first)

# Dosya oluşturma
touch dosya.txt        # Boş dosya oluştur
mkdir klasor           # Dizin oluştur
mkdir -p a/b/c         # İç içe dizinler oluştur

# Kopyalama ve taşıma
cp kaynak hedef        # Dosya kopyala
cp -r kaynak hedef     # Dizin kopyala (recursive)
mv eski yeni           # Taşı veya yeniden adlandır

# Silme (DİKKAT!)
rm dosya.txt           # Dosya sil
rm -i dosya.txt        # Onay isteyerek sil
rm -r klasor/          # Dizin sil (recursive)
rm -rf klasor/         # Zorla sil (DANGEROUS!)

# Dosya okuma
cat dosya.txt          # Tüm dosyayı göster
head -n 10 dosya.txt   # İlk 10 satır
tail -n 10 dosya.txt   # Son 10 satır
tail -f dosya.log      # Canlı takip (logs için)
less dosya.txt         # Sayfa sayfa oku
more dosya.txt         # Basit pager
```

## 🔍 Arama ve Filtreleme

```bash
# Dosya arama
find . -name "*.txt"              # .txt dosyalarını bul
find . -type f -name "app*"       # app ile başlayan dosyalar
find . -type d -name "test"       # test adlı dizinler
find . -mtime -7                  # Son 7 günde değişenler
find . -size +10M                 # 10MB'dan büyükler

# Text arama
grep "pattern" dosya.txt          # Dosyada ara
grep -r "pattern" .               # Recursive ara
grep -i "pattern" dosya.txt       # Case-insensitive
grep -n "pattern" dosya.txt       # Satır numarasıyla
grep -v "pattern" dosya.txt       # Eşleşmeyenleri göster
grep -c "pattern" dosya.txt       # Eşleşme sayısı

# Gelişmiş grep
grep -E "pattern1|pattern2"       # OR operatörü
grep -A 3 "pattern"               # 3 satır sonrasını göster
grep -B 3 "pattern"               # 3 satır öncesini göster
grep -C 3 "pattern"               # 3 satır önce+sonra
```

## 🔐 İzinler ve Ownership

```bash
# İzinleri görme
ls -l dosya.txt

# chmod - İzin değiştirme (Numeric)
chmod 755 script.sh    # rwxr-xr-x
chmod 644 file.txt     # rw-r--r--
chmod 600 secret.txt   # rw-------
chmod 700 private.sh   # rwx------

# chmod - Symbolic
chmod +x script.sh     # Execute ekle
chmod u+w file.txt     # User write ekle
chmod g-w file.txt     # Group write kaldır
chmod o-rwx file.txt   # Others tüm izinleri kaldır
chmod -R 755 dir/      # Recursive

# chown - Ownership
sudo chown user file.txt           # Owner değiştir
sudo chown user:group file.txt     # Owner ve group
sudo chown -R user:group dir/      # Recursive

# İzin Numaraları
# r=4, w=2, x=1
# 7 = rwx (4+2+1)
# 6 = rw- (4+2+0)
# 5 = r-x (4+0+1)
# 4 = r-- (4+0+0)
```

## ⚙️ Process Yönetimi

```bash
# Process listeleme
ps                     # Mevcut terminal process'leri
ps aux                 # Tüm process'ler detaylı
ps -ef                 # Alternative format
ps -u kullanici        # Kullanıcıya özel
pstree                 # Process tree

# Canlı izleme
top                    # Basic monitor
htop                   # Advanced monitor (yüklenmeli)

# Process sonlandırma
kill PID               # Process'i sonlandır (SIGTERM)
kill -9 PID            # Zorla öldür (SIGKILL)
killall process_name   # İsme göre öldür
pkill pattern          # Pattern'e göre öldür

# Background/Foreground
komut &                # Background'da çalıştır
jobs                   # Background job'ları listele
fg %1                  # Job 1'i foreground'a al
bg %1                  # Job 1'i background'da devam ettir
Ctrl+Z                 # Process'i duraklat
Ctrl+C                 # Process'i sonlandır
```

## 🔄 Pipes ve Redirection

```bash
# Output redirection
command > file.txt         # Çıktıyı dosyaya yaz (overwrite)
command >> file.txt        # Dosyaya ekle (append)
command 2> error.txt       # Hataları dosyaya yaz
command &> all.txt         # Hem çıktı hem hata
command > /dev/null        # Çıktıyı at

# Pipes
command1 | command2        # command1 çıktısını command2'ye ver
cat file.txt | grep "x"    # Dosyayı oku ve filtrele
ps aux | grep nginx        # Process'leri filtrele
ls -l | wc -l              # Dosya sayısını bul
```

## 📝 Text Processing

```bash
# cat - Concatenate
cat file1.txt file2.txt    # Dosyaları birleştir
cat > newfile.txt          # Yeni dosya oluştur (Ctrl+D ile bitir)

# cut - Sütun ayır
cut -d: -f1 /etc/passwd    # : ile ayır, 1. sütunu al
cut -c1-10 file.txt        # Her satırın ilk 10 karakteri

# sort - Sırala
sort file.txt              # Alfabetik sırala
sort -r file.txt           # Ters sırala
sort -n file.txt           # Sayısal sırala
sort -u file.txt           # Unique ve sırala

# uniq - Tekrarlı satırları kaldır (önce sort!)
sort file.txt | uniq       # Tekrarsız satırlar
sort file.txt | uniq -c    # Tekrar sayısıyla
sort file.txt | uniq -d    # Sadece tekrarlayanlar

# wc - Word count
wc file.txt                # Satır, kelime, karakter
wc -l file.txt             # Satır sayısı
wc -w file.txt             # Kelime sayısı
wc -c file.txt             # Karakter sayısı

# sed - Stream editor
sed 's/eski/yeni/' file.txt           # İlk eşleşmeyi değiştir
sed 's/eski/yeni/g' file.txt          # Tüm eşleşmeleri değiştir
sed -i 's/eski/yeni/g' file.txt       # Dosyayı güncelle
sed -n '10,20p' file.txt              # 10-20 satırları göster

# awk - Pattern scanning
awk '{print $1}' file.txt             # İlk sütunu yazdır
awk -F: '{print $1}' /etc/passwd      # : delimiter
awk '$3 > 100' file.txt               # 3. sütun > 100 olanlar
```

## 📦 Package Management

```bash
# Ubuntu/Debian (apt)
sudo apt update                # Package listesini güncelle
sudo apt upgrade               # Yüklü paketleri güncelle
sudo apt install package       # Paket kur
sudo apt remove package        # Paket kaldır
sudo apt autoremove            # Gereksiz paketleri temizle
apt search keyword             # Paket ara
apt show package               # Paket bilgisi

# RHEL/CentOS (yum/dnf)
sudo yum update
sudo yum install package
sudo yum remove package
```

## 🖥️ Sistem Bilgisi

```bash
# İşletim sistemi
uname -a                   # Kernel bilgisi
cat /etc/os-release        # OS bilgisi
hostnamectl                # Hostname ve sistem bilgisi

# Disk kullanımı
df -h                      # Disk boş alan
du -sh *                   # Dizin boyutları
du -sh /path/to/dir        # Belirli dizin boyutu

# Memory
free -h                    # RAM kullanımı
vmstat                     # Virtual memory stats

# CPU
lscpu                      # CPU bilgisi
top                        # Canlı CPU kullanımı
uptime                     # Sistem uptime ve load

# Network
ip addr                    # IP adresleri
ip route                   # Routing table
ifconfig                   # Network interfaces (eski)
netstat -tuln              # Listening ports
ss -tuln                   # Socket statistics (modern)
```

## 🌐 Network Komutları

```bash
# Connectivity test
ping google.com            # Host'a erişim testi
ping -c 4 8.8.8.8          # 4 paket gönder

# Route tracing
traceroute google.com      # Route'u izle
mtr google.com             # Canlı traceroute

# DNS lookup
nslookup google.com        # DNS sorgusu
dig google.com             # Detaylı DNS bilgisi
host google.com            # Basit DNS lookup

# Network connections
netstat -an                # Tüm connection'lar
ss -tuln                   # Listening sockets
lsof -i :80                # Port 80'i kim kullanıyor?

# Curl
curl http://example.com    # HTTP GET request
curl -I example.com        # Sadece headers
curl -X POST -d "data"     # POST request
curl -o file.txt url       # Download file
```

## 🛡️ Firewall (UFW)

```bash
# UFW - Uncomplicated Firewall
sudo ufw status            # Firewall durumu
sudo ufw enable            # Firewall'ı aktifleştir
sudo ufw disable           # Firewall'ı kapat

# Kurallar
sudo ufw allow 22          # Port 22'yi aç (SSH)
sudo ufw allow 80/tcp      # Port 80 TCP
sudo ufw allow from 192.168.1.0/24   # IP range'den izin ver
sudo ufw deny 23           # Port 23'ü kapat (telnet)
sudo ufw delete allow 80   # Kuralı sil

# Application profiles
sudo ufw app list          # Mevcut profiller
sudo ufw allow 'Nginx Full'
```

## 🔧 Systemd ve Services

```bash
# Service yönetimi
sudo systemctl start service     # Service başlat
sudo systemctl stop service      # Service durdur
sudo systemctl restart service   # Service restart
sudo systemctl status service    # Service durumu
sudo systemctl enable service    # Boot'ta otomatik başlat
sudo systemctl disable service   # Otomatik başlatmayı kapat

# Service listesi
systemctl list-units --type=service              # Tüm servisler
systemctl list-units --type=service --state=active   # Aktif servisler

# Logs
sudo journalctl -u service       # Service log'ları
sudo journalctl -f               # Canlı log takibi
sudo journalctl --since today    # Bugünün log'ları
```

## 📊 Monitoring ve Logs

```bash
# System logs
sudo tail -f /var/log/syslog     # System log (Ubuntu)
sudo tail -f /var/log/messages   # System log (RHEL)
sudo tail -f /var/log/auth.log   # Authentication logs

# journalctl
sudo journalctl -n 50            # Son 50 satır
sudo journalctl -p err           # Sadece error'lar
sudo journalctl --since "1 hour ago"
sudo journalctl -u nginx         # Nginx logs

# Resource monitoring
top                              # Process monitor
htop                             # Better process monitor
uptime                           # Load average
vmstat 1                         # Virtual memory stats (her 1 sn)
iostat                           # IO statistics
```

## 🔑 User Management

```bash
# Kullanıcı bilgisi
whoami                     # Mevcut kullanıcı
id                         # User ID ve group'lar
groups                     # Kullanıcının group'ları

# User management (sudo gerekli)
sudo useradd username      # Kullanıcı ekle
sudo passwd username       # Şifre ayarla
sudo userdel username      # Kullanıcı sil
sudo usermod -aG group user    # Group'a ekle
```

## 🗜️ Compression

```bash
# tar - Archive
tar -czf archive.tar.gz dir/     # Compress ve arşivle
tar -xzf archive.tar.gz          # Extract
tar -tzf archive.tar.gz          # İçeriği listele

# zip/unzip
zip -r archive.zip dir/          # Zip oluştur
unzip archive.zip                # Unzip
unzip -l archive.zip             # İçeriği listele

# gzip
gzip file.txt                    # Compress (file.txt.gz)
gunzip file.txt.gz               # Decompress
```

## 🌐 SSH

```bash
# SSH connection
ssh user@hostname              # Bağlan
ssh -p 2222 user@host          # Custom port
ssh -i key.pem user@host       # Key ile bağlan

# SSH key generation
ssh-keygen -t rsa -b 4096      # RSA key oluştur
ssh-keygen -t ed25519          # Modern key (önerilen)

# SSH copy
ssh-copy-id user@host          # Public key'i kopyala

# SCP - Secure copy
scp file.txt user@host:/path/  # Dosya kopyala
scp -r dir/ user@host:/path/   # Dizin kopyala
scp user@host:/path/file .     # Remote'tan local'e
```

## 💻 System Administration

```bash
# sudo
sudo command               # Root yetkisiyle çalıştır
sudo -i                    # Root shell
sudo -u user command       # Başka kullanıcı olarak

# Disk ve filesystem
df -h                      # Disk kullanımı
du -sh *                   # Dizin boyutları
mount                      # Mount edilmiş filesystems
lsblk                      # Block devices

# Process priority
nice -n 10 command         # Düşük priority ile çalıştır
renice -n 5 -p PID         # Priority değiştir

# Scheduled tasks
crontab -e                 # Cron job'ları düzenle
crontab -l                 # Cron job'ları listele
# Format: * * * * * command
#         │ │ │ │ │
#         │ │ │ │ └─ Day of week (0-7)
#         │ │ │ └─── Month (1-12)
#         │ │ └───── Day (1-31)
#         │ └─────── Hour (0-23)
#         └───────── Minute (0-59)
```

## 🔗 Useful Combinations

```bash
# Top 10 büyük dosya
du -ah ~ | sort -rh | head -10

# En çok CPU kullanan 5 process
ps aux --sort=-%cpu | head -6

# Port 80'i kim kullanıyor?
sudo lsof -i :80

# Sistem bilgisi tek seferde
echo "=== SYSTEM INFO ===" && \
uname -a && \
echo "=== DISK ===" && \
df -h && \
echo "=== MEMORY ===" && \
free -h

# Log'da error'ları say ve göster
grep -i error /var/log/syslog | wc -l
grep -i error /var/log/syslog | tail -5

# Dosya değişikliklerini izle
watch -n 2 'ls -lh file.txt'

# Son 10 komut
history | tail -10

# Belirli komutları history'de ara
history | grep docker
```

## ⌨️ Klavye Kısayolları

```bash
Ctrl + C              # Çalışan process'i sonlandır
Ctrl + Z              # Process'i duraklat
Ctrl + D              # Terminal'den çık (logout)
Ctrl + L              # Ekranı temizle (clear komutu gibi)
Ctrl + A              # Satır başına git
Ctrl + E              # Satır sonuna git
Ctrl + U              # Satır başına kadar sil
Ctrl + K              # Satır sonuna kadar sil
Ctrl + R              # Command history'de ara
Tab                   # Auto-complete
!!                    # Son komutu tekrar çalıştır
!n                    # History'deki n. komutu çalıştır
```

## 🆘 Yardım Alma

```bash
man command            # Manual sayfası
command --help         # Hızlı yardım
info command           # Info dökümanı
which command          # Komut nerede?
whereis command        # Binary, source, manual yerleri
type command           # Komut tipi
```

## 🚀 Yararlı Alias'lar

`.bashrc` veya `.zshrc` dosyanıza ekleyin:

```bash
alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias grep='grep --color=auto'
alias h='history'
alias c='clear'
alias update='sudo apt update && sudo apt upgrade'
alias ports='netstat -tuln'
alias myip='curl ifconfig.me'
```

---

**💡 Pro Tip:** Bu cheat sheet'i yazdırın ve masanızda tutun! İlk 2-3 hafta sürekli ihtiyacınız olacak.

**📚 Daha Fazla:** `man bash` - Bash'in tüm özellikleri için
