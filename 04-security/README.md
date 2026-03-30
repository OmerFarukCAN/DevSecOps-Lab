# Faz 4: Security Fundamentals

**Tahmini Süre:** 5-6 hafta  
**Zorluk:** Orta-İleri 🔴  
**Ön Koşul:** Faz 1, 2, 3 tamamlanmış

## DevSecOps'taki "Sec" Buradan Başlıyor!

Bu faza kadar Dev ve Ops kısımlarını öğrendiniz. Şimdi **Security**'yi öğrenme zamanı!

## Bu Fazda Ne Öğreneceğiz?

Güvenlik temellerini, yaygın güvenlik açıklarını ve bunlardan nasıl korunacağınızı öğreneceksiniz.

## Modüller

### 1. Security Basics (7-10 gün)
📁 `basics/`

**Öğrenilecekler:**
- CIA Triad (Confidentiality, Integrity, Availability)
- Authentication vs Authorization
- Encryption fundamentals
  - Symmetric vs Asymmetric
  - TLS/SSL
  - Certificates
- Hash functions ve digital signatures
- Security principles:
  - Least privilege
  - Defense in depth
  - Zero trust
  - Fail secure
- Threat modeling basics
- Common attack vectors

**Pratik:**
- Encryption hands-on labs
- Certificate generation
- SSH key management
- TLS configuration

---

### 2. OWASP Top 10 (10-14 gün)
📁 `owasp/`

**Öğrenilecekler:**
OWASP Top 10 2021 - Web application security:

1. **A01: Broken Access Control**
2. **A02: Cryptographic Failures**
3. **A03: Injection**
4. **A04: Insecure Design**
5. **A05: Security Misconfiguration**
6. **A06: Vulnerable Components**
7. **A07: Authentication Failures**
8. **A08: Software and Data Integrity**
9. **A09: Security Logging Failures**
10. **A10: Server-Side Request Forgery**

**.NET'te bu açıklıklar nasıl önlenir?**

**Pratik:**
- Intentionally vulnerable .NET app oluşturma
- Her OWASP kategorisi için exploit senaryosu
- Security patch'leri uygulama
- Secure coding patterns

---

### 3. Secret Management (5-7 gün)
📁 `secrets/`

**Öğrenilecekler:**
- Secrets neden critical?
- Yaygın hatalar (hardcoded passwords, .env in git)
- Azure Key Vault deep dive
- HashiCorp Vault basics
- Environment variables best practices
- Secret rotation
- Git'te secret leak prevention
- Pre-commit hooks

**Pratik:**
- Azure Key Vault setup
- .NET app'te Key Vault entegrasyonu
- Secret rotation automation
- git-secrets tool kullanımı
- Pre-commit hook implementasyonu

---

### 4. Authentication & Authorization (5-7 gün)
📁 `auth/`

**Öğrenilecekler:**
- Authentication methods
- Password hashing (bcrypt, Argon2)
- JWT (JSON Web Tokens)
- OAuth 2.0 flows
- OpenID Connect
- Azure AD / Entra ID
- RBAC (Role-Based Access Control)
- Claims-based authorization
- API security

**Pratik:**
- JWT authentication (.NET)
- Azure AD integration
- OAuth 2.0 implementation
- RBAC system
- API key management

---

## Faz 4 Başarı Kriterleri

- [ ] Security temellerini anlıyorum
- [ ] OWASP Top 10'u biliyorum
- [ ] .NET'te güvenli kod yazabiliyorum
- [ ] Secret management yapabiliyorum
- [ ] Authentication ve authorization implement edebiliyorum
- [ ] Security scan tool'larını kullanabiliyorum

## Faz Sonu Projesi

**🎯 Proje: Secure .NET REST API**

**Gereksinimler:**

1. **API Özellikleri:**
   - User registration/login
   - JWT authentication
   - RBAC (Admin, User, Guest roles)
   - CRUD operations
   - Input validation
   - SQL injection koruması
   - XSS koruması

2. **Security Implementation:**
   - Azure Key Vault entegrasyonu
   - Secrets (DB connection string, JWT secret)
   - Password hashing (BCrypt)
   - Rate limiting
   - CORS configuration
   - Security headers
   - HTTPS enforcement

3. **OWASP Compliance:**
   - Her OWASP Top 10 kategorisine karşı korunmuş
   - Security checklist tamamlanmış

4. **Documentation:**
   - Security architecture diagram
   - Threat model
   - Security testing results
   - Deployment guide

**Test Kriterleri:**
- ✅ OWASP ZAP scan (kritik bug yok)
- ✅ Dependency scan (güncel paketler)
- ✅ Penetration test senaryoları
- ✅ Load test (rate limiting test)

---

## Haftalık Plan

### Hafta 17: Security Fundamentals
- Encryption basics
- TLS/SSL
- Certificate management
- Security principles

### Hafta 18: OWASP Top 10 (Part 1)
- A01-A05 kategorileri
- .NET examples
- Exploit ve remediation

### Hafta 19: OWASP Top 10 (Part 2)
- A06-A10 kategorileri
- Vulnerable app project
- Security testing

### Hafta 20: Secret Management
- Azure Key Vault
- Secret rotation
- Git security

### Hafta 21: Auth & RBAC
- JWT implementation
- Azure AD
- Authorization patterns

### Hafta 22: Integration & Project
- Secure API projesi
- Security testing
- Dokümantasyon

---

## 🛡️ Security Mindset

DevSecOps engineer olarak **Security First** düşünmelisiniz:

### Her Zaman Sorun:
- ❓ Bu güvenli mi?
- ❓ Secrets exposed mu?
- ❓ Input validate ediliyor mu?
- ❓ Least privilege uygulanmış mı?
- ❓ Loglar sensitive data içeriyor mu?

### Security Checklist (Her proje için)
- [ ] No hardcoded secrets
- [ ] Input validation
- [ ] Output encoding
- [ ] Authentication implemented
- [ ] Authorization checked
- [ ] HTTPS enforced
- [ ] Security headers set
- [ ] Error messages safe (no sensitive info)
- [ ] Logging implemented (but safe)
- [ ] Dependencies updated
- [ ] Security scan yapıldı

---

## 📚 Kaynaklar

### Kurslar
- **Practical DevSecOps Certified Professional (CDP)**
- **OWASP Top 10 Course** - Udemy
- **Web Application Security** - Pluralsight

### Kitaplar
- "Web Application Security" - Andrew Hoffman
- "The Tangled Web" - Michal Zalewski
- ".NET Security" - Microsoft docs

### Pratik Sites
- **OWASP WebGoat** - Vulnerable app for learning
- **DVWA (Damn Vulnerable Web Application)**
- **TryHackMe** - Security challenges
- **HackTheBox** - Advanced pentesting

---

## ⚠️ Etik Uyarı

**Öğrendiğiniz güvenlik bilgilerini:**
- ✅ Kendi uygulamalarınızda kullanın
- ✅ Şirketinizin sistemlerini korumak için
- ✅ Ethical hacking (izinle)
- ❌ Başkalarının sistemlerine saldırmak için ASLA!

**Etik kurallar:**
- İzin olmadan test yapmayın
- Bug bounty programlarına katılın
- Responsible disclosure yapın

---

## Sonraki Adım

**Faz 4'e hazır mısınız?**
- ✅ CI/CD pipeline oluşturabılıyorum
- ✅ Container ve Kubernetes biliyorum
- ✅ Infrastructure as Code yapabiliyorum

**Hazırsanız:** `basics/README.md` ile başlayın!
