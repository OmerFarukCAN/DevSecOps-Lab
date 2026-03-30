# Faz 2: Infrastructure & Cloud

**Tahmini Süre:** 4-6 hafta  
**Zorluk:** Orta 🟡  
**Ön Koşul:** Faz 1 (Temel Beceriler) tamamlanmış olmalı

## Bu Fazda Ne Öğreneceğiz?

Modern cloud infrastructure'ı yönetmeyi öğreneceksiniz. Container'lar, orchestration, Infrastructure as Code ve Azure cloud platform.

## Neden Bu Faz Önemli?

DevSecOps engineer olarak:
- Uygulamalar artık VM'lerde değil, container'larda çalışıyor
- Infrastructure manuel değil, kod ile yönetiliyor (IaC)
- Kubernetes production ortamların standardı
- Cloud platform bilgisi zorunlu

## Modüller

### 1. Azure Fundamentals (7-10 gün)
📁 `azure-basics/`

**Öğrenilecekler:**
- Azure account ve subscription
- Resource groups ve resources
- Azure Portal, CLI, PowerShell
- Virtual Machines
- Virtual Networks
- Storage accounts
- Azure Key Vault
- Basic monitoring
- Identity and Access Management

**Pratik:**
- Azure free account oluşturma
- İlk VM deployment
- .NET app'i Azure App Service'e deploy
- Azure CLI ile automation

**Sertifika Hazırlık:** AZ-900

---

### 2. Docker & Containerization (7-10 gün)
📁 `docker/`

**Öğrenilecekler:**
- Container nedir? VM vs Container
- Docker architecture (images, containers, volumes, networks)
- Dockerfile yazma
- Multi-stage builds
- Docker Compose
- Container registry (ACR, Docker Hub)
- Best practices

**Pratik:**
- .NET uygulamasını containerize etme
- Multi-container app (web + db)
- Docker Compose ile dev environment
- Optimized production images

---

### 3. Infrastructure as Code - Terraform (7-10 gün)
📁 `terraform/`

**Öğrenilecekler:**
- IaC nedir ve neden?
- Terraform basics
- HCL syntax
- Providers (Azure, AWS, etc.)
- Resources ve data sources
- Variables, outputs, locals
- Modules
- State management
- Remote state (Azure Storage)
- Terraform Cloud basics

**Pratik:**
- Azure'da infrastructure provisioning
- Network infrastructure as code
- Reusable modules
- Terraform ile .NET app deployment

---

### 4. Kubernetes Basics (7-10 gün)
📁 `kubernetes/`

**Öğrenilecekler:**
- Kubernetes nedir ve architecture
- Pods, ReplicaSets, Deployments
- Services (ClusterIP, NodePort, LoadBalancer)
- ConfigMaps ve Secrets
- Namespaces
- kubectl CLI
- YAML manifests
- Local K8s: Minikube veya Kind
- Helm basics

**Pratik:**
- Local Kubernetes cluster
- .NET app'i K8s'e deploy
- Service exposure
- Basic scaling
- ConfigMap kullanımı

---

## Faz 2 Başarı Kriterleri

Bu fazı tamamlamak için:
- [ ] Azure'da VM oluşturup yönetebiliyorum
- [ ] Dockerfile yazabiliyorum
- [ ] Docker Compose ile multi-container app çalıştırabiliyorum
- [ ] Terraform ile Azure infrastructure oluşturabiliyorum
- [ ] Kubernetes'te pod ve deployment oluşturabiliyorum
- [ ] kubectl ile rahatça çalışabiliyorum

## Faz Sonu Projesi

**🎯 Proje: Containerized .NET Microservices on Azure**

**Gereksinimler:**
1. 2 microservice (.NET minimal API)
   - API Gateway
   - Backend Service
2. PostgreSQL database
3. Tüm servisler Docker container olarak
4. Docker Compose ile local development
5. Terraform ile Azure infrastructure:
   - Resource Group
   - Virtual Network
   - AKS (Azure Kubernetes Service) - basic
   - Container Registry
6. Kubernetes'e deployment
7. Full dokümantasyon

**Değerlendirme Kriterleri:**
- ✅ Services çalışıyor
- ✅ Container'lar optimize edilmiş
- ✅ Infrastructure reproducible (Terraform)
- ✅ Kubernetes'te scaling yapılabilir
- ✅ Dokümantasyon tamamlanmış

---

## Haftalık Plan

### Hafta 5: Azure Fundamentals
- Azure account setup
- Portal exploration
- CLI/PowerShell
- İlk VM deployment
- Networking basics
- AZ-900 study başlangıcı

### Hafta 6: Docker
- Docker Desktop kurulum
- Image ve container kavramları
- Dockerfile yazma
- .NET app containerization
- Docker Compose
- Best practices

### Hafta 7: Terraform
- Terraform kurulum
- HCL syntax
- Azure provider
- İlk infrastructure
- Modules
- State management

### Hafta 8: Kubernetes
- Minikube kurulum
- K8s architecture
- Pod ve deployment
- Services
- kubectl mastery
- Helm introduction

### Hafta 9-10: Integration & Project
- Tüm teknolojileri entegre etme
- Faz sonu projesini tamamlama

---

## Kaynaklar

### Online Kurslar
- Microsoft Learn - Azure Fundamentals (ücretsiz)
- Docker Deep Dive - Nigel Poulton
- KodeKloud - Kubernetes for Beginners

### Kitaplar
- "Docker Deep Dive" - Nigel Poulton
- "Kubernetes Up & Running" - Kelsey Hightower
- "Terraform: Up & Running" - Yevgeniy Brikman

### Practice
- Play with Docker: https://labs.play-with-docker.com/
- Play with Kubernetes: https://labs.play-with-k8s.com/
- KillerCoda scenarios

---

## Sertifikasyon Hedefi

**AZ-900: Azure Fundamentals**
- **Ne Zaman:** Hafta 6 sonunda
- **Hazırlık:** Microsoft Learn paths
- **Maliyet:** $99
- **Gerekli mi:** Hayır ama önerilir (CV'ye güzel)

---

## Sonraki Adım

**Faz 2'ye başlamadan önce:**
1. ✅ Faz 1'i tamamladığınızdan emin olun
2. ✅ Linux'ta rahat çalışabiliyorsunuz mu?
3. ✅ Git basics biliyor musunuz?
4. ✅ Bash script yazabiliyor musunuz?

**Hazırsanız:** `azure-basics/README.md` dosyasından başlayın!
