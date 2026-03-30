# Faz 1: Temel Beceriler

**Tahmini Süre:** 2-4 hafta  
**Zorluk:** Başlangıç 🟢

## Bu Fazda Ne Öğreneceğiz?

DevSecOps için gerekli temel becerileri kazanacaksınız. Bu faz, sonraki tüm fazların temelini oluşturur.

## Modüller

### 1. Linux Temelleri (5-7 gün)
📁 `linux-basics/`

**Neden Önemli?**  
DevSecOps dünyasında sunucuların %90'ı Linux üzerinde çalışır. Linux'u öğrenmek zorunludur.

**Öğrenilecekler:**
- Linux dosya sistemi yapısı
- Temel komutlar (ls, cd, cp, mv, rm, cat, grep, find)
- Dosya izinleri ve ownership (chmod, chown)
- Process yönetimi (ps, top, kill)
- Paket yönetimi (apt, yum)
- Text editörleri (vim, nano)
- Systemd ve service yönetimi

**Pratik Projeler:**
- ✅ WSL2 kurulumu
- ✅ Linux sistem yönetimi lab'ları
- ✅ Bash script'leri ile otomasyon

---

### 2. Networking Temelleri (5-7 gün)
📁 `networking/`

**Neden Önemli?**  
DevSecOps engineer olarak network güvenliğini anlamak ve sorunları çözmek zorundasınız.

**Öğrenilecekler:**
- OSI ve TCP/IP modelleri
- IP adresleme, subnetting
- DNS çalışma prensibi
- HTTP/HTTPS protokolleri
- Firewall ve security groups
- Load balancing kavramları
- SSL/TLS sertifikaları

**Pratik Projeler:**
- ✅ Network debugging lab'ları (ping, traceroute, nslookup, curl)
- ✅ Basit web server kurulumu ve güvenliği
- ✅ SSL sertifikası oluşturma ve kurulum

---

### 3. Git & Version Control (3-5 gün)
📁 `git/`

**Neden Önemli?**  
Git, Infrastructure as Code ve GitOps'un temelidir. Her şey git'te versiyonlanır.

**Öğrenilecekler:**
- Git temel konseptler (commit, branch, merge)
- Branching stratejileri (GitFlow, trunk-based)
- Pull requests ve code review
- Git hooks
- .gitignore ve secret yönetimi
- Git rebase, cherry-pick, stash

**Pratik Projeler:**
- ✅ Git workflow simülasyonları
- ✅ Pre-commit hook'ları ile güvenlik kontrolü
- ✅ Merge conflict çözümleme senaryoları

---

### 4. Shell Scripting (5-7 gün)
📁 `scripting/`

**Neden Önemli?**  
Otomasyon DevSecOps'un kalbidir. Bash ve PowerShell ile otomasyon yapabilmek kritik.

**Öğrenilecekler:**
- Bash scripting temelleri
- PowerShell temelleri (.NET background'unuzla kolay!)
- Variables, loops, conditions
- Functions ve error handling
- File operations
- API çağrıları (curl, Invoke-RestMethod)

**Pratik Projeler:**
- ✅ Sistem health check script'i
- ✅ Automated backup script'i
- ✅ Log analiz script'i
- ✅ Basit deployment automation

---

## Faz Tamamlama Kriteri

✅ Tüm modülleri tamamladınız  
✅ Tüm lab'ları başarıyla bitirdiniz  
✅ Faz sonu değerlendirme projesini yaptınız  

**Faz Sonu Projesi:**
"Linux üzerinde çalışan bir .NET uygulamasını, bash script'leri kullanarak otomatik deploy eden ve health check'lerini yapan bir sistem kurmak"

---

## Başlamadan Önce Gerekli Kurulumlar

### Windows Üzerinde Gerekli Araçlar
1. **WSL2 (Windows Subsystem for Linux)**
   ```powershell
   wsl --install
   ```

2. **Git for Windows**
   - https://git-scm.com/download/win

3. **VS Code + Extensions**
   - Remote - WSL
   - Docker
   - GitLens

4. **Docker Desktop**
   - https://www.docker.com/products/docker-desktop

5. **Windows Terminal**
   - Microsoft Store'dan indir

### İlk Adımlar
1. Bu repo'yu local'e klonlayın
2. `01-fundamentals/linux-basics/LAB-01.md` dosyasından başlayın
3. Her lab'ı tamamladıktan sonra `PROGRESS.md` dosyasını güncelleyin

---

## Yardımcı Kaynaklar
- [Linux Journey](https://linuxjourney.com/)
- [Bash Scripting Tutorial](https://www.shellscript.sh/)
- [Git Book](https://git-scm.com/book/en/v2)
- [DevSecOps Roadmap](https://roadmap.sh/devsecops)

## İletişim & Sorular
Takıldığınız yerlerde AI asistanınızdan (benden!) yardım istemeyi unutmayın!
