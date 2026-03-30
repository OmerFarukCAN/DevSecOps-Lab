# Faz 5: Application Security

**Tahmini Süre:** 6-7 hafta  
**Zorluk:** İleri 🔴  
**Ön Koşul:** Faz 4 (Security Fundamentals) tamamlanmış

## Bu Fazda Ne Öğreneceğiz?

Application security - kod seviyesinde güvenlik! SAST, DAST, dependency scanning ve secure coding practices.

## "Shift Left Security"

**Eski yaklaşım:**  
Kod yaz → Deploy et → Güvenlik testi → Sorun bul → Düzelt (pahalı! 💸)

**Modern yaklaşım (Shift Left):**  
Kod yaz → **Güvenlik testi (automated)** → Deploy et (erken tespit, ucuz düzeltme ✅)

## Modüller

### 1. SAST - Static Application Security Testing (10-12 gün)
📁 `sast/`

**Öğrenilecekler:**
- SAST nedir? (kaynak kod analizi)
- Ne zaman kullanılır? (development/CI aşamasında)
- Avantajları ve dezavantajları
- Tools:
  - **SonarQube** (en popüler)
  - **Checkmarx**
  - **.NET Security Code Scan**
  - **Roslyn Analyzers**
  - **Semgrep**
- Security rules ve patterns
- False positive management
- Quality gates
- CI/CD integration

**Pratik:**
- SonarQube Docker deployment
- .NET projesi analizi
- Custom security rules
- Pipeline'a entegrasyon
- Code quality metrics

---

### 2. DAST - Dynamic Application Security Testing (10-12 gün)
📁 `dast/`

**Öğrenilecekler:**
- DAST nedir? (çalışan app'i test etme)
- SAST vs DAST karşılaştırma
- Ne zaman DAST?
- Tools:
  - **OWASP ZAP** (free, popüler)
  - **Burp Suite Community**
  - **Nikto**
  - **Arachni**
- API security testing
- Automated scanning
- Penetration testing basics
- Vulnerability reporting

**Pratik:**
- OWASP ZAP kurulum ve kullanım
- .NET API'sini scan etme
- Automated scan (ZAP Docker)
- CI/CD integration
- Vulnerability remediation
- Security testing reports

---

### 3. Dependency Scanning & SCA (8-10 gün)
📁 `dependency-scan/`

**Öğrenilecekler:**
- Software Composition Analysis (SCA)
- Open source risk'leri
- Vulnerability databases (NVD, CVE)
- Tools:
  - **Snyk**
  - **WhiteSource/Mend**
  - **GitHub Dependabot**
  - **OWASP Dependency-Check**
  - **dotnet list package --vulnerable**
- License compliance
- Automated patching
- Supply chain security

**Pratik:**
- NuGet package scanning
- Vulnerable dependency detection
- Automated update PRs (Dependabot)
- License compliance checking
- SCA pipeline integration
- SBOM (Software Bill of Materials) generation

---

### 4. Secure Coding Practices (8-10 gün)
📁 `secure-coding/`

**Öğrenilecekler:**
- Secure coding principles
- Input validation strategies
- Output encoding
- Parameterized queries (SQL injection prevention)
- Authentication best practices
- Cryptography dos and don'ts
- Logging best practices (no sensitive data!)
- Error handling (safe error messages)
- API security best practices
- Code review checklists

**.NET Specific:**
- Data annotations validation
- Entity Framework security
- ASP.NET Core security features
- Anti-forgery tokens
- Content Security Policy
- Security middleware

**Pratik:**
- Secure vs insecure code comparison
- Refactoring insecure code
- Security unit tests
- Code review exercises
- Secure API design

---

### 5. Security Testing Integration (7-10 gün)
📁 `integration/`

**Öğrenilecekler:**
- DevSecOps pipeline architecture
- Security gates
- Tool orchestration
- Triage ve remediation workflow
- Metrics ve reporting
- Security champions program

**Pratik:**
- Full security pipeline:
  - Pre-commit: Secret scanning
  - Build: SAST
  - Test: Unit security tests
  - Package: Dependency scan + Image scan
  - Deploy: DAST
  - Runtime: Monitoring
- Dashboard oluşturma
- Alert configuration

---

## Faz 5 Başarı Kriterleri

- [ ] SAST tool'ları kullanabiliyorum (SonarQube)
- [ ] DAST tool'ları kullanabiliyorum (OWASP ZAP)
- [ ] Dependency scanning yapabiliyorum
- [ ] Secure code yazabiliyorum
- [ ] Security scan'leri CI/CD'ye entegre edebiliyorum
- [ ] Vulnerability'leri triage edip fix edebiliyorum
- [ ] Security metrics raporlayabiliyorum

## Faz Sonu Projesi

**🎯 Proje: Complete Application Security Pipeline**

**Senaryo:**
Enterprise .NET microservices application için tam security pipeline.

**Application:**
- 3 microservices (.NET 8)
- React frontend
- PostgreSQL database
- Redis cache

**Security Pipeline Stages:**

1. **Pre-Commit:**
   - git-secrets (secret scanning)
   - pre-commit hooks

2. **Pull Request:**
   - SonarQube analysis
   - Code quality gate
   - Security hotspots review
   - Dependency scan (Snyk)
   - License compliance check

3. **Main Branch CI:**
   - Full SAST scan
   - Unit tests (including security tests)
   - Build Docker images
   - Image vulnerability scan (Trivy)
   - Push to registry

4. **Staging Deployment:**
   - DAST scan (OWASP ZAP)
   - API security testing
   - Integration tests
   - Performance tests

5. **Production Deployment:**
   - Security approval gate
   - Blue-green deployment
   - Smoke tests
   - Security monitoring enabled

**Deliverables:**
- ✅ Working application
- ✅ Full security pipeline (Azure DevOps or GitHub Actions)
- ✅ Security scan reports
- ✅ Vulnerability remediation documentation
- ✅ Security dashboard (Grafana)
- ✅ Runbook (incident response)

**Success Metrics:**
- Zero critical vulnerabilities
- Zero high vulnerabilities
- <5 medium vulnerabilities (with remediation plan)
- 90%+ code coverage
- <2% false positive rate

---

## Haftalık Plan

### Hafta 23-24: SAST
- SonarQube mastery
- .NET analysis
- Custom rules
- Quality gates

### Hafta 25-26: DAST
- OWASP ZAP deep dive
- API testing
- Automated scanning
- Vulnerability management

### Hafta 27-28: Dependencies
- SCA tools
- Vulnerable dependencies
- Automated updates
- License compliance

### Hafta 29: Secure Coding
- Best practices
- Code review
- Security patterns
- Testing

### Hafta 30: Integration
- Full pipeline setup
- Dashboard
- Faz sonu projesi

---

## 🛡️ Security Tools Ecosystem

```
┌─────────────────────────────────────────┐
│         DevSecOps Pipeline              │
├─────────────────────────────────────────┤
│                                         │
│  Pre-Commit:                            │
│  ├─ git-secrets                         │
│  ├─ detect-secrets                      │
│  └─ pre-commit framework                │
│                                         │
│  SAST (Code):                           │
│  ├─ SonarQube                           │
│  ├─ Checkmarx                           │
│  ├─ Semgrep                             │
│  └─ Security Code Scan (.NET)          │
│                                         │
│  SCA (Dependencies):                    │
│  ├─ Snyk                                │
│  ├─ WhiteSource/Mend                    │
│  ├─ Dependabot                          │
│  └─ OWASP Dependency-Check             │
│                                         │
│  Container Scanning:                    │
│  ├─ Trivy                               │
│  ├─ Clair                               │
│  └─ Snyk Container                      │
│                                         │
│  DAST (Runtime):                        │
│  ├─ OWASP ZAP                           │
│  ├─ Burp Suite                          │
│  └─ Acunetix                            │
│                                         │
└─────────────────────────────────────────┘
```

---

## 📊 Security Metrics

### Takip Edilmesi Gerekenler
- **Vulnerability Count** (Critical, High, Medium, Low)
- **Mean Time to Remediate (MTTR)**
- **False Positive Rate**
- **Code Coverage**
- **Security Debt**
- **Compliance Score**

### Dashboard Example
```
╔═══════════════════════════════════╗
║   Application Security Dashboard  ║
╠═══════════════════════════════════╣
║                                   ║
║  Critical: 0  ✅                  ║
║  High:     2  ⚠️                  ║
║  Medium:   8  ⚠️                  ║
║  Low:      23                     ║
║                                   ║
║  Code Coverage: 87%               ║
║  Outdated Packages: 3             ║
║  OWASP Compliance: 95%            ║
║                                   ║
║  Last Scan: 2 hours ago           ║
║  MTTR: 1.2 days                   ║
║                                   ║
╚═══════════════════════════════════╝
```

---

## 🚨 Vulnerability Management Process

```
1. DETECT (Automated scan)
   ↓
2. TRIAGE (Is it real? Priority?)
   ↓
3. ASSIGN (Developer/Team)
   ↓
4. FIX (Remediation)
   ↓
5. TEST (Verify fixed)
   ↓
6. DEPLOY (Patch to production)
   ↓
7. VERIFY (Re-scan)
```

**SLA (Service Level Agreement):**
- Critical: 24 hours
- High: 7 days
- Medium: 30 days
- Low: 90 days

---

## 📚 Önerilen Kaynaklar

### Online Training
- **Practical DevSecOps** - https://www.practical-devsecops.com/
- **OWASP Top 10 Training**
- **PentesterLab** - Hands-on pentesting

### Books
- "Alice and Bob Learn Application Security"
- "The Web Application Hacker's Handbook"
- "Security Engineering" - Ross Anderson

### Labs
- **OWASP Juice Shop** - Vulnerable web app
- **WebGoat** - Security lessons
- **Damn Vulnerable Web Application (DVWA)**

### Communities
- OWASP Slack
- r/netsec
- r/AskNetsec

---

## 🎓 Certifications

**After This Phase:**
- Practical DevSecOps Certified Professional (CDP)
- OWASP certifications

**Later:**
- Certified Ethical Hacker (CEH)
- Offensive Security Certified Professional (OSCP) - advanced

---

## Sonraki Adım

Faz 5 tamamlandıktan sonra → **Faz 6: Infrastructure Security**

Infrastructure'ı nasıl güvenli hale getireceğinizi öğreneceksiniz:
- Network security
- Container security
- Kubernetes security
- Cloud security

**Hazırsanız:** `basics/README.md` ile başlayın!
