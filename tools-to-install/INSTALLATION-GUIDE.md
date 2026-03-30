# Kurulum Rehberi - Tüm Araçlar

> Bu dosya, DevSecOps yolculuğunda ihtiyaç duyacağınız TÜM araçların kurulum rehberidir.

## 📋 Kurulum Sırası

### Faz 0: Hazırlık (Hemen kurulacaklar)
- ✅ WSL2
- ✅ Docker Desktop
- ✅ Git
- ✅ VS Code
- ✅ Windows Terminal

### Faz 1: Temeller
- ✅ Essential Linux tools (otomatik gelir)

### Faz 2: Infrastructure
- ✅ Azure CLI
- ✅ Terraform
- ✅ kubectl
- ✅ Helm
- ✅ Minikube/Kind

### Faz 3: CI/CD
- ✅ Azure DevOps CLI
- ✅ GitHub CLI (gh)
- ✅ Jenkins (Docker container olarak)

### Faz 4-5: Security
- ✅ Security scanning tools
- ✅ OWASP ZAP
- ✅ SonarQube (Docker)

### Faz 6-8: Advanced
- ✅ Istio
- ✅ ArgoCD
- ✅ Monitoring stack

---

## 🔧 Faz 0: Temel Araçlar (BUGÜN)

### 1. WSL2 (Windows Subsystem for Linux)

**Neden?** Linux environment Windows'ta.

**Kurulum:**
```powershell
# PowerShell - Admin olarak

# WSL'i kur
wsl --install

# Restart gerekli!
# Restart sonrası otomatik Ubuntu açılır

# Kullanıcı adı ve şifre oluşturun
```

**Test:**
```powershell
wsl --version
wsl -l -v
```

**Ubuntu'ya geçiş:**
```powershell
wsl
# veya
wsl -d Ubuntu-22.04
```

---

### 2. Docker Desktop

**Neden?** Container runtime.

**Kurulum:**
1. https://www.docker.com/products/docker-desktop adresine gidin
2. "Download for Windows" butonuna tıklayın
3. İndirilen `Docker Desktop Installer.exe` dosyasını çalıştırın
4. "Use WSL 2 instead of Hyper-V" seçeneğini seçin
5. Kurulum bitince restart
6. Docker Desktop'ı başlatın

**Ayarlar:**
- Settings → General → "Use WSL 2 based engine" ✅
- Settings → Resources → WSL Integration → Ubuntu ✅

**Test:**
```bash
# WSL içinde
docker --version
docker run hello-world

# Çalışıyorsa ✅
```

---

### 3. Git

**Neden?** Version control.

**Kurulum (Windows):**
https://git-scm.com/download/win

**Kurulum (WSL içinde):**
```bash
# Ubuntu'da zaten yüklü olmalı, kontrol et:
git --version

# Yoksa:
sudo apt update
sudo apt install git -y
```

**Initial configuration:**
```bash
git config --global user.name "Adınız"
git config --global user.email "email@example.com"

# Kontrol
git config --list
```

---

### 4. VS Code

**Neden?** En iyi code editor, extension ecosystem.

**Kurulum:**
https://code.visualstudio.com/

**Zorunlu Extensions:**
1. **Remote - WSL** (ms-vscode-remote.remote-wsl)
2. **Docker** (ms-azuretools.vscode-docker)
3. **GitLens** (eamodio.gitlens)

**Önerilen Extensions:**
- C# Dev Kit (ms-dotnettools.csdevkit)
- YAML (redhat.vscode-yaml)
- Markdown All in One
- PowerShell

**WSL'den VS Code açma:**
```bash
# WSL terminalde
cd ~/project
code .
```

---

### 5. Windows Terminal (Önerilir)

**Neden?** Modern, tabs, customization.

**Kurulum:**
Microsoft Store → "Windows Terminal" ara → Install

**Ayarlar:**
- Default profile: Ubuntu
- Theme: One Half Dark (veya beğendiğiniz)

---

## ☁️ Faz 2: Cloud ve Infrastructure Tools

### 6. Azure CLI

**Kurulum (WSL):**
```bash
# Microsoft'un kurulum script'i
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

# Test
az --version

# Login
az login

# Subscription'ınızı listeleyin
az account list --output table
```

**Başlangıç:**
```bash
# Default subscription ayarlama
az account set --subscription "Subscription Name"

# Resource group oluşturma
az group create --name myResourceGroup --location eastus
```

---

### 7. Terraform

**Kurulum (WSL):**
```bash
# HashiCorp repository ekle
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

# Terraform'u kur
sudo apt update
sudo apt install terraform -y

# Test
terraform --version
```

**İlk kullanım:**
```bash
mkdir terraform-test
cd terraform-test
terraform init
```

---

### 8. kubectl (Kubernetes CLI)

**Kurulum (WSL):**
```bash
# Son stable versiyonu indir
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

# Çalıştırılabilir yap
chmod +x kubectl

# /usr/local/bin'e taşı
sudo mv kubectl /usr/local/bin/

# Test
kubectl version --client
```

**Autocomplete (zaman kazandırır!):**
```bash
# .bashrc'ye ekle
echo 'source <(kubectl completion bash)' >> ~/.bashrc
echo 'alias k=kubectl' >> ~/.bashrc
echo 'complete -F __start_kubectl k' >> ~/.bashrc

# Reload
source ~/.bashrc

# Artık 'k' ile kubectl kullanabilirsiniz
k get pods  # kubectl get pods yerine
```

---

### 9. Helm (Kubernetes Package Manager)

**Kurulum:**
```bash
# Helm'i kur
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Test
helm version
```

---

### 10. Minikube (Local Kubernetes)

**Kurulum (WSL):**
```bash
# Binary indir
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

# Install
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Test
minikube version

# İlk cluster (Docker driver)
minikube start --driver=docker

# Cluster kontrol
kubectl get nodes

# Dashboard
minikube dashboard
```

**Alternatif: Kind (Kubernetes in Docker)**
```bash
# Kind kurulum
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Cluster oluşturma
kind create cluster --name dev-cluster

# Cluster silme
kind delete cluster --name dev-cluster
```

---

## 🔐 Faz 3-5: Security Tools

### 11. OWASP ZAP

**Docker ile (Önerilir):**
```bash
# ZAP'ı Docker container olarak çalıştır
docker run -u zap -p 8080:8080 -i owasp/zap2docker-stable zap.sh -daemon -host 0.0.0.0 -port 8080

# Browser'da: http://localhost:8080
```

**Standalone kurulum:**
https://www.zaproxy.org/download/

---

### 12. SonarQube

**Docker Compose ile:**
```bash
# sonarqube dizini oluştur
mkdir ~/sonarqube
cd ~/sonarqube

# docker-compose.yml oluştur
cat > docker-compose.yml << 'EOF'
version: '3'

services:
  sonarqube:
    image: sonarqube:community
    ports:
      - "9000:9000"
    environment:
      - SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_logs:/opt/sonarqube/logs
      - sonarqube_extensions:/opt/sonarqube/extensions

volumes:
  sonarqube_data:
  sonarqube_logs:
  sonarqube_extensions:
EOF

# Başlat
docker-compose up -d

# Browser: http://localhost:9000
# Default: admin/admin
```

---

### 13. Trivy (Container Scanning)

**Kurulum:**
```bash
# Repository ekle
sudo apt-get install wget apt-transport-https gnupg lsb-release -y

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -

echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list

# Kur
sudo apt-get update
sudo apt-get install trivy -y

# Test
trivy --version

# Kullanım
trivy image nginx:latest
```

---

### 14. Snyk CLI

**Kurulum:**
```bash
# npm gerekli (Node.js)
sudo apt install nodejs npm -y

# Snyk CLI kur
npm install -g snyk

# Authenticate
snyk auth

# Test
snyk test
```

---

## 📊 Faz 7: Monitoring Tools

### 15. ELK Stack

**Docker Compose ile:**
```bash
mkdir ~/elk-stack
cd ~/elk-stack

# docker-compose.yml dosyası hazır
# (Detaylı içerik 07-monitoring/logging/ klasöründe)
```

---

### 16. Prometheus

**Docker ile:**
```bash
# prometheus.yml config dosyası oluştur
mkdir -p ~/prometheus
cd ~/prometheus

cat > prometheus.yml << 'EOF'
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
EOF

# Çalıştır
docker run -d \
  --name prometheus \
  -p 9090:9090 \
  -v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml \
  prom/prometheus

# Browser: http://localhost:9090
```

---

### 17. Grafana

**Docker ile:**
```bash
docker run -d \
  --name grafana \
  -p 3000:3000 \
  grafana/grafana

# Browser: http://localhost:3000
# Default: admin/admin
```

---

## 🚀 Faz 8: Advanced Tools

### 18. ArgoCD

**Kubernetes'te kurulum:**
```bash
# Namespace oluştur
kubectl create namespace argocd

# ArgoCD kur
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Password al
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

# Port forward
kubectl port-forward svc/argocd-server -n argocd 8080:443

# Browser: https://localhost:8080
# Username: admin
# Password: [yukarıdan aldığınız]
```

---

### 19. Istio (Service Mesh)

**Kurulum:**
```bash
# İstioctl binary indir
curl -L https://istio.io/downloadIstio | sh -

# PATH'e ekle
cd istio-*
export PATH=$PWD/bin:$PATH

# Kubernetes'e kur
istioctl install --set profile=demo -y

# Test
kubectl get pods -n istio-system
```

---

## 🛠️ Yardımcı Araçlar

### 20. jq (JSON processor)

```bash
sudo apt install jq -y

# Kullanım
echo '{"name":"John","age":30}' | jq '.name'
```

---

### 21. yq (YAML processor)

```bash
# Snap ile
sudo snap install yq

# Kullanım
yq eval '.metadata.name' pod.yaml
```

---

### 22. httpie (Better curl)

```bash
sudo apt install httpie -y

# Kullanım
http GET https://api.github.com
```

---

### 23. bat (Better cat)

```bash
# Syntax highlighting ile dosya okuma
sudo apt install bat -y

# Kullanım (Ubuntu'da 'batcat')
batcat file.txt
```

---

### 24. fzf (Fuzzy finder)

```bash
sudo apt install fzf -y

# Kullanım
# Ctrl+R: Command history fuzzy search
# Çok kullanışlı!
```

---

### 25. tmux (Terminal multiplexer)

```bash
sudo apt install tmux -y

# Kullanım
tmux                # Session başlat
Ctrl+B, C          # Yeni window
Ctrl+B, %          # Vertical split
Ctrl+B, "          # Horizontal split
Ctrl+B, D          # Detach
tmux attach        # Reattach
```

---

## 📦 Optional but Useful

### 26. Oh My Bash (Terminal beautification)

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"

# Tema değiştir
nano ~/.bashrc
# OSH_THEME="agnoster"
```

---

### 27. kubectx & kubens (K8s context switching)

```bash
sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
sudo ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx
sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens

# Kullanım
kubectx                 # Context'leri listele
kubectx my-cluster      # Context değiştir
kubens                  # Namespace'leri listele
kubens dev              # Default namespace değiştir
```

---

### 28. k9s (Kubernetes TUI)

```bash
# Binary indir
wget https://github.com/derailed/k9s/releases/latest/download/k9s_Linux_amd64.tar.gz

# Extract ve install
tar -xzf k9s_Linux_amd64.tar.gz
sudo mv k9s /usr/local/bin/

# Çalıştır
k9s

# k9s içinde:
# :pods    → Pod'ları görüntüle
# :svc     → Service'leri görüntüle
# :deploy  → Deployment'ları görüntüle
# d        → Describe
# l        → Logs
# q        → Quit
```

---

## 🎨 Development Environment Setup

### .bashrc Optimization

```bash
nano ~/.bashrc
```

**Ekleyin:**
```bash
# Aliases
alias k='kubectl'
alias d='docker'
alias dc='docker-compose'
alias g='git'
alias tf='terraform'
alias ll='ls -lah'
alias ..='cd ..'
alias ...='cd ../..'

# Git aliases
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline'

# Useful functions
function mkcd() {
    mkdir -p "$1" && cd "$1"
}

# Colored prompt
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# History settings
HISTSIZE=10000
HISTFILESIZE=20000
HISTCONTROL=ignoredups

# kubectl completion
source <(kubectl completion bash)
complete -F __start_kubectl k
```

**Reload:**
```bash
source ~/.bashrc
```

---

## 📋 Tool Versiyonları (Referans)

```bash
# Tüm tool'ları ve versiyonlarını kontrol et

cat > ~/check-tools.sh << 'EOF'
#!/bin/bash

echo "=== TOOL VERSIONS ==="
echo ""

echo "OS: $(cat /etc/os-release | grep PRETTY_NAME | cut -d'"' -f2)"
echo ""

echo "Core Tools:"
echo "- Bash: $(bash --version | head -1)"
echo "- Git: $(git --version)"
echo "- Docker: $(docker --version)"
echo ""

echo "Cloud & IaC:"
echo "- Azure CLI: $(az --version | head -1 | awk '{print $2}')"
echo "- Terraform: $(terraform --version | head -1)"
echo ""

echo "Kubernetes:"
echo "- kubectl: $(kubectl version --client --short 2>/dev/null | head -1)"
echo "- Helm: $(helm version --short)"
echo "- Minikube: $(minikube version --short 2>/dev/null)"
echo ""

echo "Other:"
echo "- jq: $(jq --version)"
echo "- Python: $(python3 --version)"
echo ""

echo "✅ All tools installed!"
EOF

chmod +x ~/check-tools.sh
~/check-tools.sh
```

---

## 🚨 Sorun Giderme

### WSL Issues

**"WSL has no installed distributions"**
```powershell
wsl --install -d Ubuntu-22.04
```

**WSL güncelleme:**
```powershell
wsl --update
wsl --version
```

**WSL restart:**
```powershell
wsl --shutdown
wsl
```

---

### Docker Issues

**"Cannot connect to Docker daemon"**
- Docker Desktop açık mı kontrol edin
- Settings → Resources → WSL Integration aktif olmalı
- WSL'i restart edin

**Permission denied:**
```bash
# Docker group'a kendinizi ekleyin
sudo usermod -aG docker $USER

# Logout/login gerekli
exit
wsl
```

---

### Network Issues

**WSL'den internet erişimi yok:**
```bash
# DNS ayarlarını kontrol et
cat /etc/resolv.conf

# Eğer problem varsa:
sudo nano /etc/resolv.conf
# nameserver 8.8.8.8 ekleyin
```

---

## 📚 Configuration Files

### ~/.bashrc (Final Version)

Tüm optimization'larınızı buraya ekleyin. Yedek almayı unutmayın!

```bash
# Backup
cp ~/.bashrc ~/.bashrc.backup

# Edit
nano ~/.bashrc
```

### ~/.gitconfig

```bash
# .gitconfig dosyanızı özelleştirin
nano ~/.gitconfig
```

```ini
[user]
    name = Adınız
    email = email@example.com

[core]
    editor = nano
    autocrlf = input

[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    lg = log --oneline --graph --decorate --all

[pull]
    rebase = false

[init]
    defaultBranch = main
```

---

## ✅ Installation Checklist

### Faz 0 (Hemen)
- [ ] WSL2 kuruldu
- [ ] Docker Desktop kuruldu ve çalışıyor
- [ ] Git kuruldu ve config edildi
- [ ] VS Code kuruldu (+ extensions)
- [ ] Windows Terminal kuruldu

### Faz 2 (Hafta 5-6)
- [ ] Azure CLI kuruldu
- [ ] Terraform kuruldu
- [ ] kubectl kuruldu
- [ ] Helm kuruldu
- [ ] Minikube veya Kind kuruldu

### Faz 3-5 (Hafta 12+)
- [ ] OWASP ZAP çalışıyor
- [ ] SonarQube çalışıyor
- [ ] Trivy kuruldu
- [ ] Snyk kuruldu (optional)

### Faz 6-8 (Hafta 30+)
- [ ] Prometheus + Grafana çalışıyor
- [ ] ELK stack çalışıyor
- [ ] ArgoCD kuruldu
- [ ] Istio kuruldu

---

## 🎯 Pro Setup (Tüm araçlar kurulu)

### System Check Script

```bash
cat > ~/system-check.sh << 'EOF'
#!/bin/bash

echo "🔍 DevSecOps System Check"
echo "========================="
echo ""

# Function to check command
check_tool() {
    if command -v $1 &> /dev/null; then
        echo "✅ $1: installed"
        $1 --version | head -1 | sed 's/^/   /'
    else
        echo "❌ $1: NOT installed"
    fi
    echo ""
}

# Core
check_tool bash
check_tool git
check_tool docker

# Cloud & IaC
check_tool az
check_tool terraform

# Kubernetes
check_tool kubectl
check_tool helm
check_tool minikube

# Security
check_tool trivy

# Utilities
check_tool jq
check_tool yq

echo "========================="
echo "Check complete!"
EOF

chmod +x ~/system-check.sh
~/system-check.sh
```

---

## 📅 Kurulum Zamanlaması

**Hepsini birden kurmayın!** İhtiyacınız olduğunda kurun:

- **Şimdi:** WSL2, Docker, Git, VS Code
- **Hafta 5:** Azure CLI
- **Hafta 7:** Terraform
- **Hafta 9:** Kubernetes tools
- **Hafta 12+:** CI/CD tools
- **Hafta 20+:** Security tools
- **Hafta 36+:** Monitoring tools

---

## 💾 Backup Your Config

```bash
# Tüm config'leri backup'la
mkdir ~/dotfiles
cp ~/.bashrc ~/dotfiles/
cp ~/.gitconfig ~/dotfiles/
cp ~/.vimrc ~/dotfiles/ 2>/dev/null || true

# Git'e commit et
cd ~/dotfiles
git init
git add .
git commit -m "Initial dotfiles backup"

# GitHub'a push (optional)
# gh repo create dotfiles --public
# git push -u origin main
```

---

## 🎉 Setup Complete!

Tüm araçlar kurulunca hazırsınız! 🚀

**Test için:**
```bash
~/check-tools.sh
```

**Herhangi bir tool eksikse:**
Bu dosyada ilgili section'ı bulun ve kurun.

---

**Başarılar! Şimdi öğrenmeye odaklanın! 💪**
