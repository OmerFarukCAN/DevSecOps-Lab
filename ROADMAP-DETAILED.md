# Detaylı DevSecOps Yol Haritası

> .NET Developer'dan DevSecOps Expert'e Dönüşüm Rehberi

---

## 📍 Mevcut Durumunuz
- ✅ C# programlama dili
- ✅ .NET teknolojileri
- ✅ Backend development tecrübesi
- ❌ DevOps bilgisi
- ❌ Sistem/Network bilgisi
- ❌ Cloud platform tecrübesi

## 🎯 Hedef Durumunuz (9-12 ay sonra)
- ✅ Uzman seviye DevSecOps Engineer
- ✅ Kubernetes ve container orchestration
- ✅ CI/CD pipeline oluşturma ve yönetme
- ✅ Infrastructure as Code (IaC)
- ✅ Cloud security (Azure/AWS)
- ✅ Automated security scanning
- ✅ Monitoring & incident response

---

## 🗺️ Detaylı Yol Haritası

### Faz 1: Temel Beceriler (2-4 hafta) 🟢

**Hedef:** DevOps için gerekli temel bilgileri kazanmak

#### Hafta 1-2: Linux & Networking
**Linux Temelleri** (📁 `01-fundamentals/linux-basics/`)
- WSL2 kurulumu ve yapılandırma
- Linux dosya sistemi ve navigasyon
- Temel komutlar: ls, cd, cp, mv, rm, cat, grep, find
- Dosya izinleri: chmod, chown, umask
- Process yönetimi: ps, top, kill
- Package management: apt, yum
- Text editörler: vim, nano
- Systemd ve service management

**Networking Temelleri** (📁 `01-fundamentals/networking/`)
- OSI ve TCP/IP modelleri
- IP addressing ve subnetting
- DNS çalışma prensibi
- HTTP/HTTPS protokolleri
- Network troubleshooting: ping, traceroute, nslookup, netstat
- Firewall basics: iptables, ufw
- Load balancing kavramları
- SSL/TLS ve sertifikalar

**Pratik Projeler:**
- ✅ Linux VM kurulumu
- ✅ Temel sistem yönetimi
- ✅ Network debugging senaryoları
- ✅ Basit web server setup

#### Hafta 3: Git & Version Control
**Git Mastery** (📁 `01-fundamentals/git/`)
- Git temelleri: clone, add, commit, push, pull
- Branching ve merging
- Branching stratejileri: GitFlow, trunk-based development
- Pull requests ve code review
- Git hooks (pre-commit, pre-push)
- Conflict resolution
- .gitignore ve sensitive data yönetimi
- Git rebase, cherry-pick, stash, bisect

**Pratik Projeler:**
- ✅ Git workflow simülasyonları
- ✅ Pre-commit hook'ları ile security check
- ✅ Merge conflict scenarios

#### Hafta 4: Shell Scripting
**Bash & PowerShell** (📁 `01-fundamentals/scripting/`)
- Bash scripting fundamentals
- PowerShell scripting (.NET ile entegrasyon!)
- Variables, arrays, loops
- Conditionals ve functions
- Error handling ve exit codes
- File operations
- API calls: curl, Invoke-RestMethod
- Automation patterns

**Pratik Projeler:**
- ✅ System health check script
- ✅ Automated backup solution
- ✅ Log parsing ve analysis
- ✅ Simple deployment automation

**🎓 Faz 1 Sonu Projesi:**
Linux üzerinde .NET app deploy eden, health check yapan, log toplayan tam otomatik script sistemi.

---

### Faz 2: Infrastructure & Cloud (4-6 hafta) 🔵

**Hedef:** Cloud infrastructure'ı yönetmeyi ve containerization'ı öğrenmek

#### Hafta 5-6: Azure Fundamentals
**Azure Basics** (📁 `02-infrastructure/azure-basics/`)
- Azure subscription ve resource groups
- Azure Portal ve CLI
- Virtual Machines
- Virtual Networks ve Subnets
- Azure Storage
- Azure Key Vault
- Azure Monitor basics
- Identity and Access Management (IAM)
- **AZ-900 Sertifikasyon Hazırlığı**

**Pratik Projeler:**
- ✅ Azure hesabı açma (free tier)
- ✅ VM oluşturma ve yapılandırma
- ✅ .NET app'i Azure'a deploy etme
- ✅ Azure CLI ile otomasyon

#### Hafta 7-8: Docker & Containerization
**Docker Mastery** (📁 `02-infrastructure/docker/`)
- Container nedir ve neden önemli?
- Docker architecture: images, containers, volumes, networks
- Dockerfile yazma (multi-stage builds)
- Docker Compose
- Container networking
- Volume management
- Docker security best practices
- Image optimization
- Container registry (Docker Hub, ACR)

**Pratik Projeler:**
- ✅ .NET uygulamasını containerize etme
- ✅ Multi-container app (frontend+backend+db)
- ✅ Docker Compose ile local dev environment
- ✅ Optimized production Docker images

#### Hafta 9-10: Infrastructure as Code (Terraform)
**Terraform** (📁 `02-infrastructure/terraform/`)
- IaC nedir ve neden kullanılır?
- Terraform basics: providers, resources, state
- HCL (HashiCorp Configuration Language)
- Terraform modules
- State management
- Variables ve outputs
- Terraform ile Azure provisioning
- Best practices ve security

**Pratik Projeler:**
- ✅ Azure resources ile Terraform
- ✅ Network infrastructure as code
- ✅ Reusable modules oluşturma
- ✅ State management strategies

#### Hafta 11: Kubernetes Basics
**K8s Introduction** (📁 `02-infrastructure/kubernetes/`)
- Kubernetes nedir ve mimarisi
- Pods, Deployments, Services
- ConfigMaps ve Secrets
- Namespaces
- kubectl CLI
- YAML manifests
- Local cluster: Minikube veya Kind
- Helm basics

**Pratik Projeler:**
- ✅ Minikube cluster kurulumu
- ✅ .NET app'i K8s'e deploy etme
- ✅ Service exposure ve networking
- ✅ Basic scaling

**🎓 Faz 2 Sonu Projesi:**
Terraform ile Azure'da altyapı oluşturup, Dockerized .NET app'i deploy etme.

---

### Faz 3: CI/CD & Automation (4-5 hafta) 🟣

**Hedef:** Otomatik deployment pipeline'ları kurmak

#### Hafta 12-13: CI/CD Kavramları ve Azure DevOps
**CI/CD Fundamentals** (📁 `03-cicd/concepts/`)
- Continuous Integration nedir?
- Continuous Delivery vs Deployment
- Pipeline anatomy
- Build, test, deploy stages
- Artifacts ve versioning
- Environment management (dev, staging, prod)

**Azure DevOps** (📁 `03-cicd/azure-devops/`)
- Azure DevOps Services overview
- Repos, Pipelines, Artifacts, Boards
- YAML pipelines
- Build agents (Microsoft-hosted vs self-hosted)
- Service connections
- Pipeline templates
- Release management
- **AZ-400 kavramları**

**Pratik Projeler:**
- ✅ Azure DevOps projesi oluşturma
- ✅ .NET app için CI pipeline
- ✅ CD pipeline (Azure App Service'e deploy)
- ✅ Multi-stage pipelines

#### Hafta 14: GitHub Actions
**GitHub Actions** (📁 `03-cicd/github-actions/`)
- Actions vs Azure Pipelines
- Workflow syntax
- Events, jobs, steps
- Actions marketplace
- Self-hosted runners
- Secrets management
- Matrix builds

**Pratik Projeler:**
- ✅ GitHub Actions workflow
- ✅ .NET build ve test otomasyonu
- ✅ Docker image build ve push
- ✅ Automated deployment

#### Hafta 15-16: Jenkins
**Jenkins** (📁 `03-cicd/jenkins/`)
- Jenkins kurulumu (Docker container)
- Jenkinsfile (declarative vs scripted)
- Plugins ve integration'lar
- Build agents ve distributed builds
- Pipeline as Code
- Jenkins security

**Pratik Projeler:**
- ✅ Jenkins'i Docker'da çalıştırma
- ✅ Multibranch pipeline
- ✅ Automated testing integration
- ✅ Deployment pipeline

**🎓 Faz 3 Sonu Projesi:**
Aynı .NET app için 3 farklı platformda (Azure DevOps, GitHub Actions, Jenkins) tam otomatik CI/CD pipeline'ları kurmak.

---

### Faz 4: Security Fundamentals (5-6 hafta) 🔴

**Hedef:** Güvenlik temellerini ve best practice'leri öğrenmek

#### Hafta 17-18: Security Basics
**Security Fundamentals** (📁 `04-security/basics/`)
- CIA Triad (Confidentiality, Integrity, Availability)
- Authentication vs Authorization
- Encryption (symmetric vs asymmetric)
- Hash functions
- Security principles (least privilege, defense in depth)
- Common vulnerabilities
- Threat modeling basics

**Pratik Projeler:**
- ✅ Encryption örnekleri
- ✅ SSH key management
- ✅ Certificate management

#### Hafta 19-20: OWASP Top 10
**Web Application Security** (📁 `04-security/owasp/`)
- OWASP Top 10 2021 detaylı inceleme
- Injection attacks (SQL, Command, etc.)
- Broken authentication
- Sensitive data exposure
- XML External Entities (XXE)
- Broken access control
- Security misconfigurations
- XSS, CSRF, Deserialization
- .NET'te bu güvenlik açıklarından korunma

**Pratik Projeler:**
- ✅ Vulnerable .NET app (intentionally insecure)
- ✅ Her OWASP kategorisi için exploit ve fix
- ✅ Secure coding practices implementation

#### Hafta 21: Secret Management
**Secrets & Credentials** (📁 `04-security/secrets/`)
- Secret management neden önemli?
- Azure Key Vault
- HashiCorp Vault
- Environment variables
- .env dosyaları ve güvenliği
- Secret rotation
- Git'te secret leak prevention

**Pratik Projeler:**
- ✅ Azure Key Vault entegrasyonu
- ✅ Secret rotation automation
- ✅ Git hooks ile secret scanning

#### Hafta 22: Authentication & Authorization
**Auth** (📁 `04-security/auth/`)
- JWT tokens
- OAuth 2.0 ve OpenID Connect
- Azure AD / Entra ID
- RBAC (Role-Based Access Control)
- API authentication
- Service-to-service auth

**Pratik Projeler:**
- ✅ JWT authentication implementation (.NET)
- ✅ Azure AD integration
- ✅ RBAC implementation

**🎓 Faz 4 Sonu Projesi:**
Secure .NET API: OWASP Top 10'a karşı korumalı, Azure Key Vault entegre, JWT auth, RBAC implement edilmiş.

---

### Faz 5: Application Security (6-7 hafta) 🟠

**Hedef:** Uygulama güvenliğini kod seviyesinde sağlamak

#### Hafta 23-24: SAST (Static Application Security Testing)
**Static Analysis** (📁 `05-app-security/sast/`)
- SAST nedir ve ne zaman kullanılır?
- SonarQube
- .NET Security Code Scan
- ESLint security plugins
- Security rules ve policies
- False positive yönetimi
- CI/CD entegrasyonu

**Pratik Projeler:**
- ✅ SonarQube kurulumu
- ✅ .NET projesi analizi
- ✅ Custom security rules
- ✅ Pipeline'a SAST entegrasyonu

#### Hafta 25-26: DAST (Dynamic Application Security Testing)
**Runtime Security Testing** (📁 `05-app-security/dast/`)
- DAST nedir? SAST vs DAST
- OWASP ZAP
- Burp Suite Community
- Automated security scanning
- API security testing
- Penetration testing basics

**Pratik Projeler:**
- ✅ OWASP ZAP ile scan
- ✅ API endpoint'leri test etme
- ✅ Vulnerability remediation
- ✅ DAST pipeline entegrasyonu

#### Hafta 27-28: Dependency Scanning
**Supply Chain Security** (📁 `05-app-security/dependency-scan/`)
- Dependency vulnerabilities
- NuGet package security
- npm/yarn security
- Snyk, WhiteSource, Dependabot
- SCA (Software Composition Analysis)
- License compliance
- Automated updates

**Pratik Projeler:**
- ✅ Dependency scanning tools
- ✅ Vulnerable dependency detection
- ✅ Automated patching
- ✅ SCA pipeline integration

#### Hafta 29: Secure Coding
**Security Best Practices** (📁 `05-app-security/secure-coding/`)
- Secure coding guidelines (.NET)
- Input validation
- Output encoding
- Parameterized queries
- Cryptography best practices
- Logging best practices (no sensitive data!)
- Error handling

**Pratik Projeler:**
- ✅ Code review checklist
- ✅ Secure vs insecure code karşılaştırma
- ✅ Security unit tests

**🎓 Faz 5 Sonu Projesi:**
Full security scanning pipeline: SAST + DAST + SCA entegre edilmiş, automated remediation.

---

### Faz 6: Infrastructure Security (5-6 hafta) 🟤

**Hedef:** Altyapı güvenliğini sağlamak

#### Hafta 30-31: Network Security
**Network Hardening** (📁 `06-infra-security/network/`)
- Network segmentation
- Security groups ve NSGs (Azure)
- Firewall rules
- VPN ve private networks
- DDoS protection
- Web Application Firewall (WAF)
- Network monitoring

**Pratik Projeler:**
- ✅ Azure NSG yapılandırma
- ✅ Network isolation architecture
- ✅ WAF rules

#### Hafta 32-33: Container Security
**Docker Security** (📁 `06-infra-security/containers/`)
- Container security threats
- Image scanning: Trivy, Clair
- Base image selection
- Dockerfile security best practices
- Runtime security
- Docker Bench Security
- Rootless containers

**Pratik Projeler:**
- ✅ Image vulnerability scanning
- ✅ Secure Dockerfile patterns
- ✅ Container runtime security policies

#### Hafta 34-35: Kubernetes Security
**K8s Hardening** (📁 `06-infra-security/k8s-security/`)
- K8s security architecture
- RBAC in Kubernetes
- Pod Security Standards
- Network policies
- Secrets management in K8s
- Security contexts
- Admission controllers
- Image policy enforcement
- **CKS (Certified Kubernetes Security Specialist) hazırlık**

**Pratik Projeler:**
- ✅ RBAC implementation
- ✅ Network policies
- ✅ Pod security policies
- ✅ Secure K8s cluster setup

**🎓 Faz 6 Sonu Projesi:**
End-to-end secure infrastructure: Network security, container scanning, K8s hardening.

---

### Faz 7: Monitoring & Observability (4-5 hafta) 📊

**Hedef:** Production monitoring ve incident response

#### Hafta 36-37: Logging (ELK Stack)
**Centralized Logging** (📁 `07-monitoring/logging/`)
- ELK Stack: Elasticsearch, Logstash, Kibana
- Log aggregation
- Log parsing ve structuring
- Kibana dashboards
- Alert rules
- Log retention policies

**Pratik Projeler:**
- ✅ ELK stack kurulumu (Docker Compose)
- ✅ .NET app log'larını ELK'ya gönderme
- ✅ Custom dashboards
- ✅ Alert configuration

#### Hafta 38: Monitoring & Alerting
**Metrics & Alerts** (📁 `07-monitoring/monitoring/`)
- Prometheus
- Grafana
- Application Insights (Azure)
- Metrics collection
- Dashboard creation
- Alerting rules
- On-call rotations

**Pratik Projeler:**
- ✅ Prometheus + Grafana setup
- ✅ .NET app metrics export
- ✅ Custom dashboards
- ✅ Alert manager configuration

#### Hafta 39-40: Security Monitoring
**Security Operations** (📁 `07-monitoring/incident-response/`)
- SIEM basics
- Security event monitoring
- Threat detection
- Incident response process
- Playbooks ve runbooks
- Forensics basics

**Pratik Projeler:**
- ✅ Security dashboard
- ✅ Attack simulation ve detection
- ✅ Incident response playbook

**🎓 Faz 7 Sonu Projesi:**
Complete observability platform: Logs, metrics, traces, security events.

---

### Faz 8: Advanced Topics (6-8 hafta) ⚡

**Hedef:** Advanced DevSecOps practices

#### Hafta 41-42: Security Automation
**Automated Security** (📁 `08-advanced/automation/`)
- Security as Code
- Policy as Code (OPA - Open Policy Agent)
- Automated compliance checking
- Security testing automation
- Automated remediation
- ChatOps for security

**Pratik Projeler:**
- ✅ OPA policies
- ✅ Automated security gates
- ✅ Self-healing security

#### Hafta 43-44: Compliance & Governance
**Regulatory Requirements** (📁 `08-advanced/compliance/`)
- Compliance frameworks: ISO 27001, SOC 2, GDPR
- Audit logging
- Policy enforcement
- Azure Policy
- Cost management
- Tagging strategies

**Pratik Projeler:**
- ✅ Compliance dashboard
- ✅ Automated policy enforcement
- ✅ Audit reports

#### Hafta 45-46: GitOps
**GitOps Methodology** (📁 `08-advanced/gitops/`)
- GitOps principles
- ArgoCD veya Flux
- Declarative infrastructure
- Git as single source of truth
- Automated sync ve rollback

**Pratik Projeler:**
- ✅ ArgoCD setup
- ✅ GitOps workflow
- ✅ Automated deployments

#### Hafta 47-48: Service Mesh & Advanced
**Service Mesh** (📁 `08-advanced/service-mesh/`)
- Istio veya Linkerd
- Traffic management
- Security (mTLS)
- Observability
- Chaos engineering basics

**Pratik Projeler:**
- ✅ Istio installation
- ✅ Traffic routing rules
- ✅ mTLS implementation

**🎓 Faz 8 Sonu Projesi:**
GitOps-based deployment with policy enforcement, service mesh, automated security.

---

### Faz 9: Capstone Project (8-10 hafta) 🏆

**Hedef:** TÜM bilgileri kullanarak production-ready sistem

#### Proje: E-Commerce Microservices Platform
(📁 `09-capstone/`)

**Uygulama:**
- .NET 8 microservices (5-6 servis)
- API Gateway
- gRPC communication
- Event-driven architecture (RabbitMQ/Azure Service Bus)
- SQL + NoSQL databases

**Infrastructure:**
- Azure Kubernetes Service (AKS)
- Terraform ile full infrastructure
- Service mesh (Istio)
- Azure Application Gateway + WAF

**CI/CD:**
- GitHub Actions veya Azure DevOps
- Multi-environment pipelines
- Automated testing (unit, integration, e2e)
- Canary deployments

**Security:**
- SAST + DAST + SCA in pipeline
- Container scanning
- K8s security policies
- Azure Key Vault integration
- mTLS between services
- WAF rules
- Secret rotation

**Monitoring:**
- ELK stack for logs
- Prometheus + Grafana for metrics
- Application Insights
- Security dashboards
- Alert rules

**Compliance:**
- Automated compliance checking
- Audit logging
- Policy enforcement

**Deliverables:**
1. Fully documented GitHub repository
2. Infrastructure as Code (Terraform)
3. Complete CI/CD pipelines
4. Security scanning integrated
5. Monitoring dashboards
6. Incident response playbooks
7. Architecture documentation

---

## 📚 Sertifikasyon Yol Haritası

### Öncelikli Sertifikalar
1. **AZ-900: Azure Fundamentals** (Hafta 6 sonrası)
2. **AZ-400: Azure DevOps Engineer Expert** (Hafta 16 sonrası)
3. **CKA: Certified Kubernetes Administrator** (Hafta 35 sonrası)
4. **CKS: Certified Kubernetes Security Specialist** (Hafta 46 sonrası)

### İsteğe Bağlı
- AWS Certified DevOps Engineer
- HashiCorp Certified: Terraform Associate
- Docker Certified Associate

---

## 🛠️ Araç Yığını (Tool Stack)

### Öğrenecekleriniz
**Version Control:** Git, GitHub, Azure Repos  
**CI/CD:** Azure DevOps, GitHub Actions, Jenkins  
**Containers:** Docker, containerd  
**Orchestration:** Kubernetes, Helm, ArgoCD  
**IaC:** Terraform, Ansible  
**Cloud:** Azure (primary), AWS basics  
**Scripting:** Bash, PowerShell, Python (basics)  
**Security Scanning:** SonarQube, OWASP ZAP, Trivy, Snyk  
**Monitoring:** Prometheus, Grafana, ELK Stack, Application Insights  
**Service Mesh:** Istio  
**Policy:** Open Policy Agent (OPA)  

---

## 📈 İlerleme Metrikleri

### Her Hafta
- ✅ Planlanan lab'lar tamamlandı mı?
- ✅ Pratik projeler çalışıyor mu?
- ✅ Notlar alındı mı?

### Her Ay
- ✅ Bir önceki ay tekrar edildi mi?
- ✅ GitHub'da commit activity var mı?
- ✅ Bir sertifika alındı mı?

### Her 3 Ay
- ✅ Portfolio projesi tamamlandı mı?
- ✅ LinkedIn profili güncellendi mi?
- ✅ Blog post yazıldı mı?

---

## 💡 Öğrenme Taktikleri

### Feynman Technique
Her yeni konsepti:
1. Öğrenin
2. Birine anlatıyormuş gibi yazın
3. Anlamadığınız yerlere geri dönün
4. Basitleştirin ve organize edin

### 20/80 Kuralı
- Her konunun %20'sini öğrenin → %80 kullanım senaryosunu çözebilirsiniz
- Derin detaylara gerektiğinde girin

### Spaced Repetition
- Gün 1: Öğren
- Gün 2: Tekrar et
- Gün 7: Tekrar et
- Gün 30: Tekrar et

### Public Learning
- GitHub'da her şeyi paylaşın
- LinkedIn'de haftalık güncellemeler
- Blog yazın (Medium, dev.to)
- Twitter/X'te #100DaysOfDevOps

---

## 🤝 Topluluklar

- **r/devops** - Reddit
- **DevOps Türkiye** - Telegram/Discord
- **Kubernetes Türkiye** - Telegram
- **Azure Türkiye** - LinkedIn Group
- **OWASP Turkey Chapter**

---

## 📖 Önerilen Okuma Sırası

### Başlangıç (Faz 1-2)
1. "The Phoenix Project" - Gene Kim
2. "The Linux Command Line" - William Shotts
3. "Docker Deep Dive" - Nigel Poulton

### Intermediate (Faz 3-5)
4. "The DevOps Handbook" - Gene Kim
5. "Kubernetes Up & Running" - Kelsey Hightower
6. "Web Application Security" - Andrew Hoffman

### Advanced (Faz 6-9)
7. "Practical DevSecOps" - PDSOps Institute
8. "Site Reliability Engineering" - Google
9. "Terraform: Up & Running" - Yevgeniy Brikman

---

## 🚦 Başarı Göstergeleri

### 3 Ay Sonra
- Linux'ta rahatça çalışabiliyorum
- Docker ile uygulama çalıştırabiliyorum
- Basit CI/CD pipeline kurabılıyorum
- Git ile rahatça çalışabiliyorum

### 6 Ay Sonra
- Kubernetes cluster yönetebiliyorum
- Terraform ile infrastructure oluşturabiliyorum
- Security scanning araçlarını kullanabiliyorum
- Azure'da production deployment yapabılıyorum

### 9 Ay Sonra
- End-to-end DevSecOps pipeline kurabılıyorum
- Security incident'lara müdahale edebiliyorum
- Compliance requirements'ları sağlayabılıyorum
- Best practices'leri uygulayabılıyorum

### 12 Ay Sonra
- Uzman seviye DevSecOps Engineer
- Complex microservices architectures
- Advanced security implementations
- Mentoring ve knowledge sharing

---

## 🎯 Kariyer Hedefleri

### Pozisyonlar
1. **Junior DevSecOps Engineer** (3-6 ay sonra)
2. **Mid-level DevSecOps Engineer** (6-9 ay sonra)
3. **Senior DevSecOps Engineer** (12+ ay sonra)

### Maaş Beklentileri (Türkiye - 2026)
- Junior: 40K-60K TL
- Mid: 60K-100K TL
- Senior: 100K-180K TL
- Remote international: $60K-$150K

### Portfolio Gereksinimleri
- ✅ GitHub'da aktif repo'lar
- ✅ CI/CD pipeline örnekleri
- ✅ Infrastructure as Code examples
- ✅ Security implementations
- ✅ Documentation
- ✅ Blog posts / technical writing

---

## 🔄 Sürekli Gelişim

DevSecOps öğrenmek bir yolculuktur, hedef değil. Sürekli öğrenmeye devam edin:
- Yeni araçları takip edin
- Conference'lara katılın
- Toplulukta aktif olun
- Blog yazın ve paylaşın
- Open source'a contribute edin

**Başarılar! 🚀**
