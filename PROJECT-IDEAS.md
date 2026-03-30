# Pratik Proje Fikirleri

> Öğrenirken yapabileceğiniz gerçek dünya projeleri

## 🎯 Başlangıç Projeleri (Faz 1-2)

### Proje 1: System Monitor Script
**Seviye:** Başlangıç  
**Teknolojiler:** Bash, Linux  
**Süre:** 4-6 saat

**Görev:**
Sistem kaynaklarını izleyen ve raporlayan bash script.

**Özellikler:**
- CPU, memory, disk kullanımı
- En çok kaynak kullanan process'ler
- Log'lama (dosyaya kaydetme)
- Email/Slack alert (threshold aşıldığında)
- Cronjob ile otomatik çalışma

---

### Proje 2: Automated Backup System
**Seviye:** Başlangıç  
**Teknolojiler:** Bash, rsync, tar  
**Süre:** 6-8 saat

**Görev:**
Önemli dosyaları otomatik backup alan sistem.

**Özellikler:**
- Daily backup (cronjob)
- Compression (tar.gz)
- Rotation (7 günden eskiler silinsin)
- Remote backup (scp ile)
- Restore script'i
- Email notification

---

### Proje 3: Dockerized .NET API
**Seviye:** Başlangıç-Orta  
**Teknolojiler:** .NET, Docker, Docker Compose  
**Süre:** 8-12 saat

**Görev:**
Basit todo API'sini containerize etme.

**Özellikler:**
- .NET 8 Minimal API
- PostgreSQL database
- Multi-stage Dockerfile (optimized)
- Docker Compose (app + db)
- Health checks
- Volume'ler ile data persistence

---

## 🏗️ Orta Seviye Projeler (Faz 3-4)

### Proje 4: Complete CI/CD Pipeline
**Seviye:** Orta  
**Teknolojiler:** Azure DevOps/GitHub Actions, Docker, Azure  
**Süre:** 12-16 saat

**Görev:**
.NET microservices için full CI/CD pipeline.

**Pipeline Stages:**
1. Build (compile)
2. Unit tests
3. SAST (SonarQube)
4. Docker build
5. Image scan
6. Deploy to staging
7. Integration tests
8. Manual approval
9. Deploy to production
10. Smoke tests

**Bonus:**
- Rollback mechanism
- Slack notifications
- Performance tests

---

### Proje 5: Infrastructure as Code
**Seviye:** Orta  
**Teknolojiler:** Terraform, Azure  
**Süre:** 10-14 saat

**Görev:**
Azure'da full network infrastructure oluşturma.

**Infrastructure:**
- Resource Group
- Virtual Network (3 subnet: web, app, db)
- Network Security Groups
- Application Gateway
- Azure Kubernetes Service
- Azure Container Registry
- Key Vault
- Storage Account
- Log Analytics Workspace

**Bonus:**
- Terraform modules
- Multiple environments (dev, staging, prod)
- State management (Azure Storage backend)

---

### Proje 6: Secure Authentication API
**Seviye:** Orta  
**Teknolojiler:** .NET, JWT, Azure AD, Key Vault  
**Süre:** 12-16 saat

**Görev:**
Production-ready authentication service.

**Özellikler:**
- User registration
- Login (JWT token)
- Refresh tokens
- Password hashing (BCrypt)
- Azure AD integration (SSO)
- MFA support
- Rate limiting
- Azure Key Vault for secrets
- OWASP Top 10 compliant

**API Endpoints:**
- POST /api/auth/register
- POST /api/auth/login
- POST /api/auth/refresh
- POST /api/auth/logout
- GET /api/auth/me

---

## 🚀 İleri Seviye Projeler (Faz 6-8)

### Proje 7: Kubernetes Security Hardening
**Seviye:** İleri  
**Teknolojiler:** Kubernetes, Helm, Policy  
**Süre:** 16-20 saat

**Görev:**
Secure Kubernetes cluster setup.

**Implementation:**
- Network policies (pod-to-pod communication)
- RBAC (roles ve bindings)
- Pod Security Standards (restricted)
- Admission controllers (OPA Gatekeeper)
- Image policy (sadece approved registry'den)
- Secret management (External Secrets Operator)
- mTLS (Istio)
- Security scanning (Falco)

**Deliverables:**
- Security hardened cluster
- Policy definitions
- Security audit report
- Compliance checklist

---

### Proje 8: GitOps Deployment Platform
**Seviye:** İleri  
**Teknolojiler:** ArgoCD, Kubernetes, Git  
**Süre:** 16-20 saat

**Görev:**
GitOps ile tamamen otomatik deployment sistemi.

**Architecture:**
- Git as single source of truth
- ArgoCD (automated sync)
- Multiple environments (namespaces)
- Helm charts
- App of Apps pattern
- Automated rollback

**Workflow:**
```
Git commit → ArgoCD detects → Auto deploy → Health check → Rollback if fail
```

---

### Proje 9: Complete Monitoring Stack
**Seviye:** İleri  
**Teknolojiler:** ELK, Prometheus, Grafana, Alertmanager  
**Süre:** 20-24 saat

**Görev:**
Full observability platform.

**Components:**
1. **Logging:** ELK Stack (Elasticsearch, Logstash, Kibana)
2. **Metrics:** Prometheus + Grafana
3. **Tracing:** Jaeger (distributed tracing)
4. **Alerting:** Alertmanager + PagerDuty
5. **Dashboards:** Grafana

**Integration:**
- .NET app instrumentation (Serilog, OpenTelemetry)
- Log aggregation
- Custom dashboards
- Alert rules
- On-call rotation

---

## 🏆 Capstone Project (Faz 9)

### Proje 10: Enterprise E-Commerce Platform
**Seviye:** Expert  
**Teknolojiler:** ALL TECHNOLOGIES  
**Süre:** 80-120 saat (8-10 hafta)

**Görev:**
Production-ready, fully secure microservices platform.

**Architecture:**

#### Microservices (.NET 8)
1. **API Gateway** (YARP / Ocelot)
2. **User Service** (Authentication, profiles)
3. **Product Service** (Catalog)
4. **Order Service** (Order processing)
5. **Payment Service** (Payment integration)
6. **Notification Service** (Email/SMS)

#### Infrastructure
- **Kubernetes:** AKS (Azure Kubernetes Service)
- **Service Mesh:** Istio (mTLS, traffic management)
- **Database:** Azure SQL + Cosmos DB
- **Cache:** Redis
- **Message Queue:** Azure Service Bus
- **Storage:** Azure Blob Storage

#### CI/CD
- **Platform:** GitHub Actions
- **Stages:**
  - Lint & Format
  - SAST (SonarQube)
  - Unit tests
  - Build Docker images
  - Image scan (Trivy)
  - SCA (Snyk)
  - Deploy to Dev (auto)
  - Integration tests
  - DAST (OWASP ZAP)
  - Deploy to Staging (auto)
  - E2E tests
  - Performance tests
  - Security approval gate
  - Deploy to Prod (manual approval)
  - Smoke tests

#### Security
- mTLS between services (Istio)
- JWT authentication
- RBAC authorization
- Azure Key Vault integration
- WAF (Azure Application Gateway)
- DDoS protection
- Network policies
- Pod security standards
- Secret rotation
- Audit logging

#### Monitoring
- ELK stack (centralized logging)
- Prometheus + Grafana (metrics)
- Jaeger (distributed tracing)
- Application Insights
- Alertmanager + PagerDuty
- Custom dashboards

#### IaC
- Terraform (full infrastructure)
- Helm charts (K8s deployments)
- GitOps (ArgoCD)

#### Documentation
- Architecture diagrams
- API documentation (Swagger)
- Deployment guide
- Runbooks
- Incident response playbooks
- Security policies
- Disaster recovery plan

**Success Criteria:**
- ✅ All services running in production
- ✅ Zero downtime deployments
- ✅ Sub-second response times (99th percentile)
- ✅ 99.9% uptime
- ✅ Zero critical security vulnerabilities
- ✅ Full observability
- ✅ Automated everything
- ✅ Compliance ready (SOC 2)

---

## 🎨 Mini Projeler (Herhangi Bir Zamanda)

### Quick Win Projects (2-4 saat)

#### 1. Dotfiles Manager
Bash script ile development environment setup otomasyonu.

#### 2. GitHub Profile README
Otomatik güncellenen GitHub profile (GitHub Actions ile).

#### 3. Personal Dashboard
Docker Compose ile çalışan kişisel dashboard (Grafana + InfluxDB).

#### 4. Log Analyzer
Nginx/Apache log'larını parse eden ve raporlayan script.

#### 5. SSL Certificate Monitor
SSL sertifikalarının expiry'sini kontrol eden ve alert veren sistem.

#### 6. Docker Image Cleaner
Eski Docker image'leri temizleyen scheduled script.

#### 7. Git Commit Analyzer
Git history'yi analiz eden ve istatistik veren tool.

#### 8. API Health Checker
Multiple API endpoint'leri kontrol eden monitoring tool.

#### 9. Terraform Module Library
Reusable Terraform modules (network, VM, AKS, etc.).

#### 10. Security Audit Script
Sistem security ayarlarını kontrol eden automated audit tool.

---

## 🌟 Portfolio İçin Projeler

### Must-Have (CV/GitHub için)
1. ✅ **Multi-tier application** (frontend + backend + db)
2. ✅ **CI/CD pipeline** (visible, well-documented)
3. ✅ **Infrastructure as Code** (Terraform modules)
4. ✅ **Kubernetes deployment** (Helm charts)
5. ✅ **Security implementation** (SAST + DAST integrated)
6. ✅ **Monitoring setup** (dashboards)

### Bonus Points
- 📝 Technical blog posts
- 🎥 Tutorial videos
- 🗣️ Conference talks
- 🤝 Open source contributions
- 🏆 Certifications

---

## 📅 Proje Seçim Stratejisi

### Her Faz Sonunda
Faz sonu projesini yapın (zorunlu).

### Hafta Sonları
Mini bir proje yapın (opsiyonel ama önerilir).

### Ayda Bir
Medium/büyük boy portfolio projesi.

---

## 💡 Proje Yaparken İpuçları

### 1. Start Small, Iterate
❌ Baştan mükemmel yapmaya çalışma  
✅ MVP (Minimum Viable Product) ile başla → İyileştir

### 2. Document Everything
- README.md (nasıl çalıştırılır?)
- Architecture diagram
- Decisions log (neden böyle yaptın?)
- Lessons learned

### 3. Version Control
Her anlamlı değişiklikte commit:
```bash
git commit -m "feat: Add user authentication"
git commit -m "fix: Resolve SQL injection vulnerability"
git commit -m "docs: Update deployment guide"
```

### 4. Test Your Project
- Manuel test
- Automated tests
- Security tests
- Load tests (optional)

### 5. Deploy It!
Local'de çalışıyor ✅ → Deploy et (Azure, AWS, wherever)

Portfolio'da "deployed project" çok değerli!

---

## 🎯 Örnek Proje Roadmap

### .NET Microservices Project (10 hafta)

**Hafta 1:** Planning ve architecture
**Hafta 2-3:** Microservice geliştirme  
**Hafta 4:** Dockerization  
**Hafta 5:** Kubernetes manifests  
**Hafta 6:** CI/CD pipeline  
**Hafta 7:** Security implementation  
**Hafta 8:** Monitoring setup  
**Hafta 9:** Testing ve optimization  
**Hafta 10:** Documentation ve deploy  

---

## 🚀 Portfolio Project Showcase Template

### README.md Example
```markdown
# E-Commerce Microservices Platform

Production-ready e-commerce system built with .NET 8, Kubernetes, and full DevSecOps practices.

## 🏗️ Architecture
![Architecture Diagram](docs/architecture.png)

## 🛠️ Tech Stack
- **Backend:** .NET 8, gRPC, REST
- **Database:** PostgreSQL, Redis
- **Infrastructure:** Kubernetes (AKS), Istio
- **CI/CD:** GitHub Actions
- **Monitoring:** Prometheus, Grafana, ELK
- **Security:** SAST (SonarQube), DAST (ZAP), Snyk

## 🔒 Security Features
- mTLS between services
- JWT authentication
- RBAC authorization
- Secret management (Azure Key Vault)
- WAF protection
- Network policies

## 🚀 Quick Start
```bash
# Clone repo
git clone https://github.com/username/ecommerce-platform

# Start local environment
docker-compose up

# Deploy to Kubernetes
kubectl apply -k k8s/
```

## 📊 Metrics
- Response time: <100ms (99th percentile)
- Uptime: 99.9%
- Code coverage: 85%
- Zero critical vulnerabilities

## 📚 Documentation
- [Architecture Decision Records](docs/adr/)
- [API Documentation](docs/api/)
- [Deployment Guide](docs/deployment.md)
- [Security Policy](docs/security.md)

## 🎥 Demo
[Live Demo](https://demo.example.com)  
[Video Walkthrough](https://youtube.com/...)

## 📄 License
MIT
```

---

## 🎨 GitHub Profile Enhancement

### Pinned Repositories
En iyi 6 projenizi pin'leyin:
1. Capstone project
2. CI/CD pipeline example
3. Terraform modules
4. Security tools
5. Kubernetes manifests
6. Monitoring setup

### Profile README
Otomatik güncellenen GitHub profile:
- Latest blog posts
- GitHub stats
- Tech stack badges
- Current learning focus

---

**Proje yapmaya başlayın! Teori önemli ama pratik daha önemli! 🚀**
