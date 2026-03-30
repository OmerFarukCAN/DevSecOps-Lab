# Faz 3: CI/CD & Automation

**Tahmini Süre:** 4-5 hafta  
**Zorluk:** Orta-İleri 🟠  
**Ön Koşul:** Faz 1 ve 2 tamamlanmış olmalı

## Bu Fazda Ne Öğreneceğiz?

Continuous Integration ve Continuous Deployment pipeline'ları oluşturmayı öğreneceksiniz. DevOps'un kalbi!

## Neden CI/CD?

- ✅ **Hız:** Manual deployment yerine otomatik
- ✅ **Güvenilirlik:** Her seferinde aynı şekilde deploy
- ✅ **Kalite:** Otomatik testler, code quality checks
- ✅ **Security:** Her commit'te security scan
- ✅ **Feedback:** Hızlı geri bildirim

## Modüller

### 1. CI/CD Concepts (2-3 gün)
📁 `concepts/`

**Temel Kavramlar:**
- Continuous Integration nedir?
- Continuous Delivery vs Continuous Deployment
- Pipeline anatomy
- Build → Test → Deploy stages
- Artifact management
- Environment management (dev, staging, prod)
- Blue-Green deployment
- Canary releases
- Rollback strategies

---

### 2. Azure DevOps (10-12 gün)
📁 `azure-devops/`

**Öğrenilecekler:**
- Azure DevOps Services overview
- Azure Repos (Git)
- Azure Pipelines (YAML)
- Classic vs YAML pipelines
- Build agents
- Service connections
- Variable groups
- Environments ve approvals
- Release pipelines
- Artifacts

**Pratik Projeler:**
- .NET app için CI pipeline
- Multi-stage pipeline (build, test, deploy)
- Docker image build ve push to ACR
- Azure App Service deployment
- AKS deployment

---

### 3. GitHub Actions (7-10 gün)
📁 `github-actions/`

**Öğrenilecekler:**
- GitHub Actions architecture
- Workflow syntax
- Events, jobs, steps
- Actions marketplace
- Self-hosted runners
- Matrix strategies
- Secrets ve environment variables
- Reusable workflows

**Pratik Projeler:**
- .NET CI/CD with GitHub Actions
- Docker build ve Docker Hub push
- Multi-environment deployment
- Automated testing
- Release automation

---

### 4. Jenkins (7-10 gün)
📁 `jenkins/`

**Öğrenilecekler:**
- Jenkins nedir ve neden hala kullanılır?
- Jenkins kurulumu (Docker)
- Jenkinsfile (declarative pipeline)
- Pipeline stages
- Agents ve nodes
- Plugins
- Credentials management
- Multibranch pipelines
- Blue Ocean UI

**Pratik Projeler:**
- Jenkins Docker container
- .NET build pipeline
- Multibranch pipeline
- Automated deployments
- Integration with Azure

---

## Faz 3 Başarı Kriterleri

- [ ] CI/CD kavramlarını anlıyorum
- [ ] Azure DevOps'ta YAML pipeline yazabiliyorum
- [ ] GitHub Actions workflow oluşturabiliyorum
- [ ] Jenkins pipeline yazabiliyorum
- [ ] Multi-stage pipeline kurabılıyorum
- [ ] Automated testing entegre edebiliyorum
- [ ] Container build ve push edebiliyorum
- [ ] Different environment'lara deploy edebiliyorum

## Faz Sonu Projesi

**🎯 Proje: Complete CI/CD for .NET Microservices**

**Senaryo:** 
E-commerce uygulaması (3 microservice):
1. Product Service (Ürün listesi API)
2. Order Service (Sipariş API)
3. User Service (Kullanıcı yönetimi)

**Görevler:**
Her 3 platform için ayrı pipeline oluşturun:

### Azure DevOps Pipeline
- Build all 3 services
- Run unit tests
- Build Docker images
- Push to Azure Container Registry
- Deploy to AKS (dev environment)
- Deploy to AKS (prod environment) - manual approval
- Smoke tests

### GitHub Actions Pipeline
- Matrix build (3 services paralel)
- Code quality check (SonarQube)
- Docker build ve push
- Deploy to staging
- Integration tests
- Deploy to production (on tag)

### Jenkins Pipeline
- Multibranch pipeline
- PR builds (build + test only)
- Main branch: full deployment
- Scheduled nightly builds
- Slack notifications

**Bonus:**
- Tüm pipeline'larda security scanning
- Automated rollback on failure
- Performance testing

---

## Haftalık Plan

### Hafta 12: CI/CD Concepts + Azure DevOps Basics
- CI/CD teori
- Azure DevOps setup
- İlk basit pipeline
- .NET build pipeline

### Hafta 13: Azure DevOps Advanced
- Multi-stage pipelines
- Deployment strategies
- Variable groups
- Approvals ve gates

### Hafta 14: GitHub Actions
- Workflow creation
- Marketplace actions
- Secrets management
- Multi-environment deployment

### Hafta 15: Jenkins
- Jenkins setup
- Jenkinsfile
- Plugins
- Multibranch pipeline

### Hafta 16: Integration & Project
- 3 platformu karşılaştırma
- Faz sonu projesi
- Best practices dokümantasyonu

---

## 📚 Önerilen Kaynaklar

### Microsoft Learn
- [Build applications with Azure DevOps](https://learn.microsoft.com/training/paths/build-applications-with-azure-devops/)
- [Deploy applications with Azure DevOps](https://learn.microsoft.com/training/paths/deploy-applications-with-azure-devops/)

### YouTube
- TechWorld with Nana - CI/CD Explained
- DevOps Journey - Azure DevOps Tutorial
- GitHub Actions Tutorial

### Dokümantasyon
- [Azure Pipelines Docs](https://learn.microsoft.com/azure/devops/pipelines/)
- [GitHub Actions Docs](https://docs.github.com/actions)
- [Jenkins Docs](https://www.jenkins.io/doc/)

---

## AZ-400 Hazırlığı

Bu faz sonunda AZ-400 sertifikası için iyi bir temel oluşmuş olacak.

**AZ-400 Konuları:**
- ✅ Source control (Git)
- ✅ CI/CD pipelines
- ✅ Container strategies
- ✅ Infrastructure as Code
- 🔲 Security ve compliance (Faz 4-5'te)
- 🔲 Monitoring (Faz 7'de)

**Sınav Tarihi:** Faz 5 sonunda (yaklaşık Haziran 2026)

---

## Sonraki Adım

**Faz 3'e hazır mısınız?**
- ✅ Docker biliyorum
- ✅ Container kavramlarını anlıyorum
- ✅ Azure basics'i tamamladım
- ✅ Git'e hakimim

**Hazırsanız:** `concepts/README.md` ile başlayın!

---

## 💡 Pro Tips

1. **3 Platformu da öğrenin:** İş dünyasında hepsi kullanılıyor
2. **YAML'e hakim olun:** Tüm modern pipeline'lar YAML
3. **Security'yi unutmayın:** Her pipeline'a security scanning ekleyin
4. **Dokümante edin:** Her pipeline için README yazın
5. **Fail fast:** Hata erken tespit edilmeli (build stage'de)

---

## Başarı Metrikleri

### Hafta Sonunda
- [ ] En az 2 working pipeline oluşturdum
- [ ] Otomatik test entegrasyonu yaptım
- [ ] Container build ve push edebiliyorum

### Faz Sonunda
- [ ] 3 platform için pipeline oluşturdum
- [ ] Multi-environment deployment yapabiliyorum
- [ ] Best practices uyguluyorum
- [ ] Troubleshooting yapabiliyorum
