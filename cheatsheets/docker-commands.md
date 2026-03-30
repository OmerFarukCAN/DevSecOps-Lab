# Docker Cheat Sheet

> Docker komutları hızlı referans rehberi

## 🐳 Docker Basics

```bash
# Docker versiyonu
docker --version
docker version              # Detaylı
docker info                 # Sistem bilgisi

# Docker yardım
docker --help
docker <command> --help     # Specific command help
```

## 📦 Image Operations

```bash
# Image'leri listeleme
docker images
docker image ls
docker images -a            # Tüm image'ler (intermediate dahil)

# Image indirme
docker pull nginx
docker pull nginx:1.21      # Specific version
docker pull mcr.microsoft.com/dotnet/aspnet:8.0

# Image silme
docker rmi image_id
docker rmi nginx:latest
docker image prune          # Kullanılmayan image'leri sil
docker image prune -a       # Tüm kullanılmayanları sil

# Image build
docker build -t myapp:1.0 .
docker build -t myapp:latest -f Dockerfile.prod .
docker build --no-cache -t myapp:1.0 .

# Image push (registry'ye)
docker tag myapp:1.0 username/myapp:1.0
docker push username/myapp:1.0

# Image history ve inspect
docker history image_name
docker inspect image_name
```

## 🏃 Container Operations

```bash
# Container çalıştırma
docker run nginx                         # Foreground'da çalıştır
docker run -d nginx                      # Background (detached)
docker run -d --name webserver nginx     # İsim ver
docker run -d -p 8080:80 nginx          # Port mapping
docker run -d -p 8080:80 -v $(pwd):/app nginx   # Volume mount

# Useful flags
docker run -d \
  --name myapp \
  -p 8080:80 \
  -e ENV_VAR=value \
  -v /host/path:/container/path \
  --restart unless-stopped \
  nginx

# Container listeleme
docker ps                   # Çalışan container'lar
docker ps -a                # Tüm container'lar (durmuş olanlar dahil)
docker ps -q                # Sadece container ID'ler

# Container durdurma/başlatma
docker stop container_id
docker start container_id
docker restart container_id

# Container silme
docker rm container_id
docker rm -f container_id   # Çalışıyorsa zorla sil
docker container prune      # Durmuş container'ları temizle

# Container logs
docker logs container_id
docker logs -f container_id         # Follow (canlı takip)
docker logs --tail 100 container_id # Son 100 satır
docker logs --since 1h container_id # Son 1 saat

# Container'a bağlanma
docker exec -it container_id bash
docker exec -it container_id sh
docker exec -it container_id /bin/bash
docker exec container_id ls /app    # Tek komut çalıştır

# Container attach (stdout/stderr'ı göster)
docker attach container_id

# Container stats
docker stats                        # Tüm container'lar
docker stats container_id           # Belirli container
docker top container_id             # Container içindeki process'ler

# Container inspect
docker inspect container_id
docker inspect -f '{{.NetworkSettings.IPAddress}}' container_id
```

## 🗂️ Volume Management

```bash
# Volume listeleme
docker volume ls

# Volume oluşturma
docker volume create myvolume

# Volume ile container çalıştırma
docker run -d -v myvolume:/data nginx
docker run -d --mount source=myvolume,target=/data nginx

# Bind mount (host directory)
docker run -d -v /host/path:/container/path nginx
docker run -d -v $(pwd):/app nginx

# Volume silme
docker volume rm myvolume
docker volume prune         # Kullanılmayan volume'leri sil
```

## 🌐 Network Operations

```bash
# Network listeleme
docker network ls

# Network oluşturma
docker network create mynetwork
docker network create --driver bridge mynetwork

# Container'ı network'e bağlama
docker network connect mynetwork container_id
docker network disconnect mynetwork container_id

# Network ile container çalıştırma
docker run -d --network mynetwork nginx

# Network inspect
docker network inspect mynetwork

# Network silme
docker network rm mynetwork
docker network prune
```

## 🏗️ Dockerfile Syntax

```dockerfile
# Base image
FROM mcr.microsoft.com/dotnet/aspnet:8.0

# Metadata
LABEL maintainer="your@email.com"
LABEL version="1.0"

# Environment variables
ENV ASPNETCORE_ENVIRONMENT=Production
ENV API_URL=https://api.example.com

# Working directory
WORKDIR /app

# Copy files
COPY . .
COPY --chown=user:group src/ /app/

# Run commands (build time)
RUN apt-get update && apt-get install -y curl
RUN dotnet restore

# Expose port
EXPOSE 80
EXPOSE 443

# Volume
VOLUME ["/data"]

# User
USER appuser

# Entry point ve CMD
ENTRYPOINT ["dotnet", "MyApp.dll"]
CMD ["--help"]
# veya
CMD ["dotnet", "MyApp.dll"]
```

## 🎼 Docker Compose

```bash
# docker-compose.yml çalıştırma
docker-compose up
docker-compose up -d                    # Background
docker-compose up --build               # Rebuild images
docker-compose up --force-recreate      # Container'ları yeniden oluştur

# Durdurma ve silme
docker-compose down                     # Stop ve remove
docker-compose down -v                  # Volume'leri de sil
docker-compose stop                     # Sadece durdur

# Logs
docker-compose logs
docker-compose logs -f                  # Follow
docker-compose logs service_name        # Specific service

# Service yönetimi
docker-compose ps                       # Running services
docker-compose restart service_name
docker-compose exec service_name bash   # Service içine gir

# Build
docker-compose build
docker-compose build --no-cache

# Scale
docker-compose up -d --scale web=3      # 3 web instance
```

## 🧹 Cleanup Commands

```bash
# Tüm durdurulmuş container'ları sil
docker container prune

# Kullanılmayan image'leri sil
docker image prune
docker image prune -a       # Tüm kullanılmayanlar

# Kullanılmayan volume'leri sil
docker volume prune

# Kullanılmayan network'leri sil
docker network prune

# HER ŞEYİ TEMİZLE (DİKKATLİ!)
docker system prune
docker system prune -a      # Image'ler dahil
docker system prune -a --volumes   # Volume'ler de dahil

# Disk kullanımı
docker system df            # Docker disk kullanımı
```

## 🔍 Debugging

```bash
# Container içindeki dosyaları listeleme
docker exec container_id ls /app

# Container'dan dosya kopyalama
docker cp container_id:/app/file.txt ./local/
docker cp ./local/file.txt container_id:/app/

# Container process'leri
docker top container_id

# Container değişikliklerini görme
docker diff container_id

# Container'ı image olarak kaydetme
docker commit container_id myimage:tag

# Container export/import
docker export container_id > container.tar
docker import container.tar myimage:tag

# Image save/load (offline transfer)
docker save -o nginx.tar nginx:latest
docker load -i nginx.tar
```

## 🛡️ Security Commands

```bash
# Image vulnerability scan (Docker Scout)
docker scout cves image_name

# Container'ı read-only çalıştırma
docker run -d --read-only nginx

# Security options
docker run -d --security-opt no-new-privileges nginx
docker run -d --cap-drop ALL nginx

# User olarak çalıştır (non-root)
docker run -d --user 1000:1000 nginx

# Resource limits
docker run -d --memory="512m" --cpus="0.5" nginx
```

## 📝 Useful Combinations

```bash
# Tüm container'ları durdur
docker stop $(docker ps -q)

# Tüm container'ları sil
docker rm $(docker ps -aq)

# Tüm image'leri sil
docker rmi $(docker images -q)

# Çalışan container'ların IP'lerini listele
docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -q)

# Container log'larını dosyaya kaydet
docker logs container_id > container.log 2>&1

# Container içindeki spesifik process'i kill et
docker exec container_id pkill -f process_name

# Image size'ları sırala
docker images --format "{{.Repository}}:{{.Tag}}\t{{.Size}}" | sort -k2 -h
```

## 🏷️ Image Tagging Best Practices

```bash
# Semantic versioning
docker tag myapp:latest myapp:1.0.0
docker tag myapp:latest myapp:1.0
docker tag myapp:latest myapp:1

# Environment tags
docker tag myapp:latest myapp:dev
docker tag myapp:latest myapp:staging
docker tag myapp:latest myapp:prod

# Git commit hash
docker tag myapp:latest myapp:$(git rev-parse --short HEAD)

# Date-based
docker tag myapp:latest myapp:$(date +%Y%m%d)
```

## 🔧 Docker Compose Example (.NET)

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8080:80"
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ConnectionStrings__Default=Server=db;Database=mydb;
    depends_on:
      - db
    volumes:
      - ./logs:/app/logs
    networks:
      - app-network

  db:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
      - POSTGRES_DB=mydb
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - app-network

volumes:
  postgres-data:

networks:
  app-network:
    driver: bridge
```

## 🎯 Production Best Practices

```bash
# 1. Always use specific versions
FROM nginx:1.21.0  # ✅ Good
FROM nginx:latest  # ❌ Bad

# 2. Multi-stage builds için
docker build --target production -t myapp:prod .

# 3. Health checks
docker run -d \
  --health-cmd="curl -f http://localhost/ || exit 1" \
  --health-interval=30s \
  --health-timeout=3s \
  --health-retries=3 \
  nginx

# 4. Resource limits (always!)
docker run -d \
  --memory="512m" \
  --memory-swap="1g" \
  --cpus="0.5" \
  --pids-limit=100 \
  myapp:prod

# 5. Restart policy
docker run -d --restart=unless-stopped nginx

# 6. Logging driver
docker run -d --log-driver json-file --log-opt max-size=10m nginx
```

## 📊 Monitoring

```bash
# Container stats (canlı)
docker stats

# Tüm container'ların resource kullanımı
docker ps -q | xargs docker stats

# Container events
docker events
docker events --filter 'type=container'

# System-wide info
docker system df            # Disk kullanımı
docker system events        # System events
```

---

**💡 Pro Tip:** Bu cheat sheet'i terminal'de hızlıca aramak için:
```bash
# grep ile komut ara
cat docker-cheat-sheet.md | grep "logs"
```

**🔗 Official Docs:** https://docs.docker.com/reference/
