# 🚀 Hızlı Başlangıç Rehberi

**DevSecOps yolculuğunuza hoş geldiniz!**

## İlk 30 Dakikada Yapılacaklar

### 1️⃣ Gerekli Araçları Kurun (15 dakika)

#### Windows Hazırlığı
```powershell
# PowerShell'i Admin olarak açın

# WSL2 kur
wsl --install

# Bilgisayarı restart edin
# Restart sonrası Ubuntu açılacak, kullanıcı adı/şifre oluşturun
```

#### Docker Desktop Kurulumu
1. [Docker Desktop](https://www.docker.com/products/docker-desktop) indirin
2. Kurun ve başlatın
3. Settings → General → "Use WSL 2 based engine" seçeneğini aktif edin

#### VS Code Hazırlığı
1. VS Code açın
2. Extensions yükleyin:
   - Remote - WSL
   - Docker
   - GitLens
   - PowerShell

---

### 2️⃣ Öğrenme Ortamını Test Edin (5 dakika)

```bash
# Ubuntu (WSL2) açın

# Linux versiyonunu kontrol edin
cat /etc/os-release

# Docker çalışıyor mu?
docker --version
docker run hello-world

# Git kurulu mu?
git --version

# Temel komutları test edin
pwd
ls -la
whoami
```

**Tüm çıktılar çalışıyorsa → Hazırsınız! ✅**

---

### 3️⃣ İlk Lab'ı Başlatın (10 dakika)

```bash
# Bu repo'nun içinde olduğunuzdan emin olun
cd /mnt/c/Users/Ömer\ Faruk/source/repos/DevSecOps

# İlk lab'ı açın
cd 01-fundamentals/linux-basics

# Lab 1'i okuyun
cat LAB-01-setup.md
```

**Şimdi Lab 1'deki görevleri tamamlayın!**

---

## Öğrenme Yaklaşımı

### 📅 Günlük Rutin
1. **Sabah (30-60 dk):** Teori oku, yeni konsept öğren
2. **Öğlen/Akşam (1-2 saat):** Lab'ları yap, pratik yap
3. **Gece (15 dk):** Günü değerlendir, notlarını al

### 📊 Haftalık Hedefler
- **Pazartesi-Çarşamba:** Yeni modül öğren
- **Perşembe-Cuma:** Lab'ları tamamla
- **Cumartesi:** Challenge project'i yap
- **Pazar:** Değerlendirme ve gelecek hafta planlaması

### 🎯 İlk 4 Hafta Hedefi
**Faz 1'i Bitir:** Linux, Networking, Git, Scripting

---

## Sorun mu Yaşıyorsunuz?

### WSL2 Kurulumu İle İlgili
```powershell
# WSL versiyonunu kontrol edin
wsl --version

# WSL durumunu kontrol edin
wsl --status

# Sorun varsa WSL'i güncelle
wsl --update
```

### Ubuntu Açılmıyorsa
```powershell
# Manuel başlat
wsl -d Ubuntu-22.04

# veya default WSL'i başlat
wsl
```

### Docker Çalışmıyorsa
```bash
# WSL içinde Docker'ı test edin
docker ps

# Hata alıyorsanız Docker Desktop'u restart edin
```

---

## Yardım & Destek

### Takıldığınızda
1. `man <komut>` ile dokümantasyona bakın
2. Google'da arayın: "how to X in linux"
3. ChatGPT/AI asistanınıza sorun
4. Stack Overflow

### Önerilen YouTube Kanalları
- NetworkChuck
- TechWorld with Nana
- DevOps Toolkit
- The DevOps Journey

### Önerilen Kitaplar
- "The Phoenix Project" - DevOps novel
- "The Linux Command Line" - William Shotts
- "Practical DevSecOps" - Practical DevSecOps Institute

---

## İlerleme Takibi

Her lab'ı tamamladıktan sonra:
```bash
# PROGRESS.md dosyasını güncelleyin
nano PROGRESS.md

# Git commit yapın (Git'i öğrendikten sonra)
git add .
git commit -m "Lab X tamamlandı"
```

---

## Motivasyon 💪

**9-12 ay sonra şunları yapabileceksiniz:**
- ✅ Sıfırdan Kubernetes cluster'ı kurmak
- ✅ Otomatik CI/CD pipeline'ları oluşturmak
- ✅ Infrastructure as Code ile altyapı yönetmek
- ✅ Security scanning ve vulnerability management
- ✅ Production'da incident response yapmak
- ✅ .NET uygulamalarını cloud'da güvenli deploy etmek

**Bugün küçük adımlar → Yarın büyük başarılar!**

---

## Şimdi Ne Yapmalısınız?

1. ✅ Gerekli araçları kurdunuz mu? → Kurulmadıysa Adım 1'e dönün
2. ✅ Araçlar çalışıyor mu? → Test edin
3. ✅ Hazırsınız! → `01-fundamentals/linux-basics/LAB-01-setup.md` ile başlayın

**Başarılar! 🚀**

---

## Sorularınız
Herhangi bir sorunuz olursa, AI asistanınıza (bana!) sorabilirsiniz:
- "Bu komutu anlamadım, açıklar mısın?"
- "Bu lab'da takıldım, yardım edebilir misin?"
- "Şu konuyu daha derinlemesine anlatır mısın?"
