# Lab Notları

> Bu klasörde her lab sonrası kişisel notlarınızı tutun.

## 📝 Not Alma Sistemi

### Her Lab İçin
Lab tamamladıktan sonra:

1. `templates/daily-log-template.md` dosyasını kopyalayın
2. Bu klasöre `YYYY-MM-DD-lab-name.md` formatında kaydedin
3. Lab'da öğrendiklerinizi, zorlandıklarınızı, çözümlerinizi yazın

### Örnek Dosya Adları
```
2026-03-30-linux-basics-lab01.md
2026-03-31-linux-basics-lab02.md
2026-04-01-linux-permissions.md
2026-04-05-docker-basics.md
```

---

## 🗂️ Klasör Yapısı

```
lab-notes/
├── README.md (bu dosya)
├── 2026-03/
│   ├── 2026-03-30-linux-lab01.md
│   ├── 2026-03-31-linux-lab02.md
│   └── week-01-summary.md
├── 2026-04/
│   └── ...
└── templates/
    └── daily-log-template.md
```

---

## 💡 İyi Not Alma İpuçları

### 1. Hemen Yazın
Lab bitince **hemen** not alın. Birkaç saat sonra detayları unutursunuz.

### 2. Code Snippet'leri Ekleyin
Öğrendiğiniz komutları/kodu ekleyin:
```bash
# Örnek: Bugün öğrendiğim komut
find . -name "*.txt" -type f
```

### 3. Hatalarınızı Kaydedin
**En iyi öğrenme:** Yaptığınız hatalardan!

```markdown
## Hata: Permission Denied
Dosyayı çalıştıramadım.

**Çözüm:** chmod +x ile execute izni verdim.
**Öğrendiğim:** Script'ler çalıştırılabilir olmalı.
```

### 4. Screenshots
Önemli çıktıları screenshot alın ve `screenshots/` klasörüne kaydedin.

### 5. "Neden" Sorusunu Sorun
Sadece "ne" değil, "neden" notunu alın:

❌ "docker -d kullanıldı"  
✅ "docker -d (detached mode) kullanıldı çünkü background'da çalışmasını istiyorum"

---

## 🔍 Notlarınızı Arama

### Grep ile
```bash
# Tüm notlarınızda "docker" ara
grep -r "docker" lab-notes/

# Case-insensitive
grep -ri "kubernetes" lab-notes/

# Sadece dosya adlarını göster
grep -rl "terraform" lab-notes/
```

### Tag System
Notlarınıza tag ekleyin:

```markdown
**Tags:** #linux #bash #scripting #permissions

## Öğrendiklerim
...
```

Sonra tag ile arama:
```bash
grep -r "#docker" lab-notes/
```

---

## 📊 Haftalık Summary Template

Her hafta sonu bir summary oluşturun:

```markdown
# Hafta X Summary - [Tarih Aralığı]

## 📊 İstatistikler
- Tamamlanan lab sayısı: X
- Yazılan script sayısı: X
- Çalışma saati: X saat
- GitHub commits: X

## 🎯 Tamamlananlar
- [x] Lab 1
- [x] Lab 2
...

## 💡 En Önemli 5 Öğrenme
1. 
2. 
3. 
4. 
5. 

## 🐛 Zorluklar ve Çözümler
### Zorluk 1
**Problem:** ...
**Çözüm:** ...

## 🚀 Gelecek Hafta Hedefleri
- [ ] ...
- [ ] ...

## 📝 Genel Notlar
...
```

---

## 🎯 Lab Progress Tracker

Hangi lab'ları tamamladığınızı buradan takip edebilirsiniz:

### Faz 1: Fundamentals
- [ ] Linux Basics - Lab 01
- [ ] Linux Basics - Lab 02
- [ ] Linux Basics - Lab 03
- [ ] Linux Basics - Lab 04
- [ ] Linux Basics - Lab 05
- [ ] Linux Basics - Lab 06
- [ ] Linux Basics - Lab 07
- [ ] Linux Basics - Lab 08 (Challenge)
- [ ] Networking - Labs
- [ ] Git - Labs
- [ ] Scripting - Labs

### Faz 2: Infrastructure
- [ ] Azure - Labs
- [ ] Docker - Labs
- [ ] Terraform - Labs
- [ ] Kubernetes - Labs

*(Devamını siz ekleyeceksiniz...)*

---

## 💾 Backup

**Önemli:** Notlarınızı Git'le versiyonlayın!

```bash
cd ~/DevSecOps
git add lab-notes/
git commit -m "Add lab notes for week X"
git push
```

Böylece:
- ✅ Notlarınızı kaybetmezsiniz
- ✅ İlerleme history'niz görünür
- ✅ GitHub'da contribution graph'ınız yeşillenir

---

## 🌟 Not Alma Best Practices

### Cornell Method
```markdown
## Lab: [İsim]

### Main Notes (Sağ taraf - %70)
Detaylı notlar buraya...

### Cues (Sol taraf - %30)
- Key term 1
- Key term 2
- Question 1?

### Summary (Alt - %10)
Bu lab'ın 2-3 cümlelik özeti
```

### Mind Map
Kompleks konular için mind map çizin (paper veya tool):
```
        Docker
          |
    ______|______
   |      |      |
Images  Containers  Networks
   |
   |____
   |    |
Build  Pull
```

---

## 📱 Mobile Access

Notlarınızı GitHub'a push'larsanız, mobilde GitHub app ile okuyabilirsiniz!

---

**Başarılar! İyi notlar, iyi öğrenme demektir! 📝**
