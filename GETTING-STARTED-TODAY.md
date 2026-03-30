# 🚀 BUGÜN BAŞLAYALIM!

**Tarih:** 30 Mart 2026  
**İlk Gün Hedefi:** DevSecOps yolculuğuna başlamak ve ilk lab'ı tamamlamak

---

## ⏱️ Bugün Yapılacaklar (2-3 saat)

### ☑️ Adım 1: Araçları Kur (30 dakika)

#### 1.1 WSL2 Kurulumu
```powershell
# PowerShell'i **Admin olarak** açın
# Sağ tık → "Run as Administrator"

# WSL'i kur
wsl --install

# Bu komut:
# - WSL2'yi etkinleştirir
# - Ubuntu'yu indirir
# - Virtual Machine Platform'u aktifleştirir

# ⚠️ Bilgisayarınızı restart etmeniz gerekecek!
```

**Restart sonrası:**
- Ubuntu otomatik açılacak
- Kullanıcı adı girin (örnek: omer)
- Şifre girin (yazarken görünmez, normal!)
- Şifreyi tekrar girin

#### 1.2 Docker Desktop Kurulumu
1. Tarayıcıda açın: https://www.docker.com/products/docker-desktop
2. "Download for Windows" butonuna tıklayın
3. İndirilen dosyayı çalıştırın
4. Kurulum tamamlandıktan sonra Docker Desktop'ı başlatın
5. Settings → General → "Use WSL 2 based engine" seçili olmalı ✅

#### 1.3 VS Code (zaten yüklüyse atla)
1. https://code.visualstudio.com/
2. İndirin ve kurun
3. Extensions:
   - Remote - WSL (Microsoft)
   - Docker (Microsoft)
   - GitLens

---

### ☑️ Adım 2: Test Edin (10 dakika)

Windows Terminal veya PowerShell'de:

```powershell
# WSL çalışıyor mu?
wsl --version

# Ubuntu'ya geçiş
wsl
```

Ubuntu içinde (artık Linux terminalindesiniz!):

```bash
# Nerede olduğunuzu görün
pwd

# Linux versiyonu
cat /etc/os-release

# Docker çalışıyor mu?
docker --version
docker run hello-world

# Git var mı?
git --version

# Başarılı! ✅
```

---

### ☑️ Adım 3: Workspace'i Açın (5 dakika)

#### Windows Terminal veya PowerShell'de:
```powershell
# Bu repo'nun dizinine gidin
cd "C:\Users\Ömer Faruk\source\repos\DevSecOps"

# VS Code'da açın
code .
```

#### VS Code içinde:
- Sol altta "Open a Remote Window" ikonuna tıklayın (mavi köşe buton)
- "Reopen in WSL" seçin
- Şimdi VS Code, WSL içinde çalışıyor! ✅

---

### ☑️ Adım 4: İlk Lab'ı Okuyun (10 dakika)

VS Code'da veya terminal'de:

```bash
# Linux terminalde (WSL)
cd /mnt/c/Users/Ömer\ Faruk/source/repos/DevSecOps
cd 01-fundamentals/linux-basics

# Lab 1'i okuyun
cat LAB-01-setup.md
```

**Veya VS Code'da:**
- `01-fundamentals/linux-basics/LAB-01-setup.md` dosyasını açın
- Markdown preview için `Ctrl+Shift+V`

---

### ☑️ Adım 5: İlk Lab'ı Tamamlayın (60-90 dakika)

**LAB-01-setup.md** dosyasındaki tüm adımları takip edin.

**Yapacaklarınız:**
- ✅ Temel Linux komutları (pwd, ls, cd)
- ✅ Dosya oluşturma (touch, mkdir)
- ✅ Dosya düzenleme (nano)
- ✅ Dosya operasyonları (cp, mv, rm)
- ✅ man sayfalarını kullanma
- ✅ İlk bash script'inizi yazma

**Takıldığınızda:**
- Lab dosyasındaki örnekleri dikkatlice okuyun
- Google'da aratın: "linux <komut> nedir"
- Bana sorun: "Bu komutu anlamadım, açıklar mısın?"

---

### ☑️ Adım 6: İlerlemenizi Kaydedin (5 dakika)

```bash
# PROGRESS.md dosyasını açın
cd /mnt/c/Users/Ömer\ Faruk/source/repos/DevSecOps
nano PROGRESS.md

# Veya VS Code'da PROGRESS.md'yi açın ve güncelleyin:
# - Lab 1 tamamlandı olarak işaretleyin
# - Bugünün tarihini ekleyin
# - Kısa notlar alın
```

---

## 🎉 İlk Günü Tamamladınız!

Tebrikler! İlk adımı attınız. 

### Bugün Öğrendikleriniz:
- ✅ Linux terminal'de çalışmayı öğrendiniz
- ✅ Temel dosya operasyonlarını yaptınız
- ✅ İlk bash script'inizi yazdınız
- ✅ DevSecOps yolculuğuna başladınız

### Yarın (31 Mart):
- [ ] LAB-02: Dosya operasyonları ve text processing
- [ ] Süre: 2-3 saat

---

## 💪 Motivasyon

Bugün çok basit şeyler öğrenmiş gibi gelebilir, ama:
- Her büyük yolculuk küçük adımlarla başlar
- 3 ay sonra Kubernetes cluster kuruyor olacaksınız
- 6 ay sonra CI/CD pipeline'ları yazıyor olacaksınız
- 12 ay sonra DevSecOps expert olacaksınız!

**Önemli:** Her gün biraz ilerleyin. Consistency is key!

---

## 📅 Bu Hafta Plan

### Bugün (30 Mart) ✅
- Setup ve LAB-01

### Yarın (31 Mart)
- LAB-02 + LAB-03

### Çarşamba (1 Nisan)
- LAB-04 + LAB-05

### Perşembe (2 Nisan)
- LAB-06 + LAB-07

### Cuma (3 Nisan)
- LAB-08 (Challenge)

### Hafta Sonu (4-5 Nisan)
- Review ve Networking modülüne başlangıç

---

## 🆘 Sorun Giderme

### WSL açılmıyor
```powershell
# PowerShell'de (Admin)
wsl --status
wsl --update
wsl --set-default-version 2
```

### Docker çalışmıyor
- Docker Desktop'ın açık olduğundan emin olun
- Settings → Resources → WSL Integration → Ubuntu seçili olmalı

### Komutlar çalışmıyor
- WSL (Linux terminal) içinde mi çalışıyorsunuz?
- PowerShell değil, Ubuntu terminalinde olmalısınız

---

## 📝 Günlük Notlar Şablonu

Her gün sonunda doldurun:

```markdown
## 30 Mart 2026

**Çalışma Süresi:** 2.5 saat

**Tamamladıklarım:**
- ✅ WSL2 kurulumu
- ✅ Docker Desktop kurulumu
- ✅ LAB-01 tamamlandı

**Öğrendiklerim:**
- Linux komut satırı temelleri
- pwd, ls, cd komutları
- nano ile dosya düzenleme
- touch, mkdir ile dosya oluşturma

**Zorluklar:**
- WSL2 kurulurken restart gerekti
- Docker Desktop ayarlarını bulmak biraz zaman aldı

**Yarın Yapacaklarım:**
- LAB-02: Dosya operasyonları
- LAB-03: Permissions

**Sorular:**
- [Varsa sorularınız]
```

---

## 🎯 Hafta Sonu Hedefi

**5 Nisan Pazar akşamı şunları söyleyebiliyor olacaksınız:**

> "Linux komut satırında rahatça çalışabiliyorum. Dosya operasyonları, izinler, process yönetimi ve bash scripting'in temellerini öğrendim. İlk hafta 8 lab'ı tamamladım ve 25+ saat çalıştım!"

---

## 🚀 Şimdi Başlayın!

**1. Araçları kurdunuz mu?**
- Hayır → Adım 1'e gidin
- Evet → Adım 4'e gidin

**2. LAB-01 dosyasını açın:**

VS Code'da: `01-fundamentals/linux-basics/LAB-01-setup.md`

Veya terminal'de:
```bash
cd /mnt/c/Users/Ömer\ Faruk/source/repos/DevSecOps
cd 01-fundamentals/linux-basics
cat LAB-01-setup.md | less
```

**3. Lab'daki adımları TAKİP EDİN!**

**Başarılar! İlk adımı atmaya hazırsınız! 💪**

---

## 📞 Yardım Lazımsa

Bana (AI asistanına) sorabilirsiniz:
- "WSL2 kurarken hata aldım, yardım eder misin?"
- "Bu komutu anlamadım: [komut]"
- "Lab-01'de şu kısımda takıldım"
- "Daha fazla örnek verebilir misin?"

**Yalnız değilsiniz! Hadi başlayalım! 🚀**
