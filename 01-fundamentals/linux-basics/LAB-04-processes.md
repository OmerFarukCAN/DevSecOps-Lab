# Lab 4: Process Management

**Süre:** 2-3 saat  
**Zorluk:** Orta 🟡

## Hedef
Linux process'lerini izleme, yönetme ve kontrol etme - production ortamlarında kritik beceri!

---

## Bölüm 1: Process Nedir?

**Process:** Çalışan bir program. Her process'in:
- **PID** (Process ID): Benzersiz kimlik numarası
- **PPID** (Parent PID): Hangi process tarafından başlatıldı
- **Owner**: Hangi kullanıcıya ait
- **State**: Çalışıyor mu, uyuyor mu, zombie mi?
- **Resources**: CPU, Memory kullanımı

---

## Bölüm 2: Process'leri Görme

### 2.1 ps - Process Status
```bash
# Mevcut terminal'deki process'ler
ps

# Tüm process'ler (detaylı)
ps aux

# Kullanıcıya özel
ps -u $USER

# Process tree (hiyerarşi)
ps auxf
# veya
pstree
```

**ps aux Sütunları:**
- **USER**: Process sahibi
- **PID**: Process ID
- **%CPU**: CPU kullanımı
- **%MEM**: Memory kullanımı
- **VSZ**: Virtual memory
- **RSS**: Physical memory
- **STAT**: Process durumu
- **START**: Başlama zamanı
- **TIME**: CPU zamanı
- **COMMAND**: Komut

### 2.2 top - Canlı İzleme
```bash
# Canlı process izleme
top

# top içinde:
# - k: Process kill et
# - P: CPU'ya göre sırala
# - M: Memory'e göre sırala
# - q: Çık

# htop (daha güzel, önce kurulmalı)
sudo apt update
sudo apt install htop -y
htop
```

**🎯 Görev:** `top` komutunu çalıştırın ve:
1. En çok CPU kullanan 5 process'i bulun
2. En çok memory kullanan process'i bulun

---

## Bölüm 3: Process'leri Yönetme

### 3.1 Foreground ve Background

```bash
# Uzun süren komut (foreground)
sleep 30
# 30 saniye bekler, terminal kilitli

# Ctrl+C ile iptal edin

# Background'da çalıştırma
sleep 30 &
# & karakteri background'a alır

# Birden fazla background job
sleep 100 &
sleep 200 &
sleep 300 &

# Aktif job'ları görme
jobs

# Job'ı foreground'a alma
fg %1
# (Ctrl+Z ile duraklat)

# Duraklatılmış job'ı background'da devam ettir
bg %1
```

### 3.2 Process Control - Signaller

**Temel Signaller:**
- **SIGTERM (15)**: Nazikçe kapat (cleanup yapabilir)
- **SIGKILL (9)**: Hemen öldür (cleanup yok, son çare!)
- **SIGSTOP (19)**: Duraklat
- **SIGCONT (18)**: Devam ettir

```bash
# Test için uzun süren process
sleep 1000 &
# PID'i not alın (örnek: 12345)

# Process'i nazikçe sonlandır
kill 12345

# Hala çalışıyorsa, zorla öldür
kill -9 12345

# Process ismine göre kill
pkill sleep

# Tüm sleep process'lerini öldür
killall sleep
```

**🎯 Görev:**
1. `sleep 500 &` ile 3 tane background process başlatın
2. `jobs` ile listeleyin
3. PID'lerini bulun
4. Hepsini `kill` ile sonlandırın

---

## Bölüm 4: systemd - Service Management

### 4.1 systemctl Temelleri
```bash
# Service durumunu kontrol et
systemctl status ssh
# veya Windows'ta
systemctl status

# Tüm servisleri listele
systemctl list-units --type=service

# Aktif servisleri listele
systemctl list-units --type=service --state=active

# Service başlat
sudo systemctl start ssh

# Service durdur
sudo systemctl stop ssh

# Service restart
sudo systemctl restart ssh

# Service enable (boot'ta otomatik başlasın)
sudo systemctl enable ssh

# Service disable
sudo systemctl disable ssh
```

### 4.2 Kendi Service'inizi Oluşturma

**Senaryo:** Basit bir .NET web API'niz var, bunu systemd service olarak çalıştıracaksınız.

```bash
# Örnek .NET app simülasyonu (mock)
mkdir -p ~/myapp
cat > ~/myapp/run.sh << 'EOF'
#!/bin/bash
while true; do
    echo "$(date): MyApp is running..."
    sleep 5
done
EOF

chmod +x ~/myapp/run.sh

# Service dosyası oluştur
sudo nano /etc/systemd/system/myapp.service
```

**Service dosyası içeriği:**
```ini
[Unit]
Description=My .NET Application
After=network.target

[Service]
Type=simple
User=omer
WorkingDirectory=/home/omer/myapp
ExecStart=/home/omer/myapp/run.sh
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

**Service'i başlat:**
```bash
# systemd'yi reload et
sudo systemctl daemon-reload

# Service'i başlat
sudo systemctl start myapp

# Durumu kontrol et
sudo systemctl status myapp

# Logları izle
sudo journalctl -u myapp -f

# Durdur
sudo systemctl stop myapp
```

**🎯 Görev:** Kendi mock uygulamanız için bir systemd service oluşturun.

---

## Bölüm 5: Log'ları İnceleme

### 5.1 journalctl - Systemd Logs
```bash
# Tüm log'lar
sudo journalctl

# Son 50 satır
sudo journalctl -n 50

# Canlı takip (tail -f gibi)
sudo journalctl -f

# Belirli bir service
sudo journalctl -u ssh

# Bugünün log'ları
sudo journalctl --since today

# Son 1 saatin log'ları
sudo journalctl --since "1 hour ago"

# Belirli zaman aralığı
sudo journalctl --since "2026-03-30 10:00:00" --until "2026-03-30 11:00:00"

# Sadece ERROR'lar
sudo journalctl -p err
```

### 5.2 Geleneksel Log Dosyaları
```bash
# Önemli log dosyaları
sudo tail -f /var/log/syslog      # Sistem log'ları (Ubuntu/Debian)
sudo tail -f /var/log/messages    # Sistem log'ları (RHEL/CentOS)
sudo tail -f /var/log/auth.log    # Authentication log'ları
sudo tail -f /var/log/kern.log    # Kernel log'ları
```

---

## Bölüm 6: Resource Monitoring

### 6.1 CPU ve Memory İzleme
```bash
# CPU bilgisi
lscpu

# Memory kullanımı
free -h

# Disk kullanımı
df -h

# Dizin boyutları
du -sh ~/*

# En büyük dosyaları bul
du -ah ~ | sort -rh | head -20
```

### 6.2 uptime ve load average
```bash
# Sistem ne kadar süredir açık?
uptime

# Load average'ı anlamak
# Örnek: load average: 0.52, 0.48, 0.45
#         1 dk    5 dk   15 dk
# 0-1 arası: İyi
# 1-2 arası: Yoğun
# 2+: Aşırı yük
```

---

## Pratik Senaryo: Production Troubleshooting

### Senaryo 1: High CPU Kullanımı
```bash
# CPU'yu en çok kullanan process
ps aux --sort=-%cpu | head -10

# veya top ile
top
# (P tuşuna basın)

# Problematic process'i kill et
# (Önce PID'i bulun)
kill -15 <PID>
```

### Senaryo 2: Memory Leak
```bash
# Memory kullanımına göre sırala
ps aux --sort=-%mem | head -10

# Belirli bir process'in memory kullanımı
ps -p <PID> -o pid,vsz,rss,cmd

# Memory doluysa ne yapılır?
free -h
# Eğer swap doluysa: memory leak var!
```

### Senaryo 3: Stuck Process
```bash
# Process yanıt vermiyor

# 1. Önce nazikçe dene (SIGTERM)
kill <PID>

# 2. 10 saniye bekle

# 3. Hala varsa zorla öldür (SIGKILL)
kill -9 <PID>

# Tüm zombie process'leri bul
ps aux | grep defunct
```

---

## Lab Challenge: Process Monitor Script

**🎯 Proje:** Sistem kaynaklarını izleyen ve alarm veren bir script yazın.

**Gereksinimler:**
1. Her 5 saniyede bir CPU ve memory kullanımını kontrol etsin
2. CPU > %80 ise uyarı versin
3. Memory > %90 ise uyarı versin
4. En çok kaynak kullanan 5 process'i logla
5. Sonuçları `monitor.log` dosyasına kaydetsin
6. Ctrl+C ile temiz bir şekilde kapansın

**Başlangıç:**
```bash
cd ~/labs
nano process-monitor.sh
```

<details>
<summary>💡 Çözüm (Önce kendiniz deneyin!)</summary>

```bash
#!/bin/bash

LOG_FILE="monitor.log"

echo "Process Monitor başlatıldı (Ctrl+C ile dur)" | tee -a $LOG_FILE

# Cleanup trap
trap "echo 'Monitor durduruluyor...'; exit 0" INT

while true; do
    # CPU ve Memory kullanımı
    CPU_USAGE=$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | cut -d'%' -f1)
    MEM_USAGE=$(free | grep Mem | awk '{printf("%.0f", $3/$2 * 100)}')
    
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
    
    echo "[$TIMESTAMP] CPU: ${CPU_USAGE}% | Memory: ${MEM_USAGE}%" | tee -a $LOG_FILE
    
    # Uyarı kontrolü
    if (( $(echo "$CPU_USAGE > 80" | bc -l) )); then
        echo "⚠️  UYARI: Yüksek CPU kullanımı!" | tee -a $LOG_FILE
    fi
    
    if [ "$MEM_USAGE" -gt 90 ]; then
        echo "⚠️  UYARI: Yüksek Memory kullanımı!" | tee -a $LOG_FILE
    fi
    
    # Top 5 process
    echo "Top 5 Processes:" >> $LOG_FILE
    ps aux --sort=-%cpu | head -6 >> $LOG_FILE
    echo "---" >> $LOG_FILE
    
    sleep 5
done
```
</details>

---

## Sonraki Adım
✅ Lab 4'ü tamamladıktan sonra → `LAB-05-packages.md`

## Notlarınız
```
[Buraya notlarınızı ekleyin]
```
