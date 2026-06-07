**Roadmap для DevOps-инженера 2026 года** 

```markdown
# 🗺️ Полный Roadmap DevOps-инженера 2026 + План Обучения

## 🎯 Ключевые тренды 2026 года

Перед стартом — понимаем, куда движется индустрия:

| Тренд | Почему важно |
|-------|---------------|
| 🤖 **AI-native DevOps** | ИИ пишет код, деплоит и фиксит сам |
| 🔐 **Security as Code** | Безопасность встроена в каждый этап (DevSecOps) |
| 🐳 **Бессерверные технологии (Serverless)** | Меньше забот об инфраструктуре |
| 🌍 **Multi-cloud / Hybrid** | Работа с AWS, Azure, GCP одновременно |
| ⚡ **GitOps** | Вся инфраструктура через Git (ArgoCD, Flux) |
| 📦 **Внутренние платформы (IDP)** | DevOps строит платформы для разработчиков |

---

## 🧱 Фундамент (1–3 месяца) — обязательная база

> 💡 **Без этих знаний ты не сможешь двигаться дальше**

### 🐧 Linux и командная строка

```bash
# Основные темы
- Установка Ubuntu/Debian/CentOS
- Файловая система (/, /home, /etc, /var, /tmp)
- Основные команды: ls, cd, cp, mv, rm, find, grep, awk, sed, chmod, chown
- Работа с процессами: ps, top, htop, kill, systemctl
- Сетевые команды: netstat, ss, curl, wget, ping, traceroute
- Текстовые редакторы: vim/nano
```

**🎓 Ресурсы:**
- Видеокурс: "Linux для начинающих" на YouTube
- Книга: "Как устроен Linux" (Брайан Уорд)

### 🐍 Python + Bash (Автоматизация)

```python
# Python обязательно знать:
- Переменные, циклы, функции, классы
- Работа с файлами (open, read, write)
- Модули: os, sys, subprocess, requests, json, yaml
- Написание простых скриптов для автоматизации
```

```bash
# Bash:
- Переменные, циклы for/while, функции
- Условные операторы if/else
- Работа с кодом возврата ($?)
- Планировщик cron
```

**📚 Практическое задание:**
Написать скрипт, который проверяет свободное место на диске и отправляет уведомление в Telegram, если места < 10%.

### 🌐 Сети (Networking)

```
- OSI и TCP/IP модели
- IP-адресация, маски подсетей, CIDR
- DNS, HTTP/HTTPS, SSH, FTP
- Порты: 22 (SSH), 80 (HTTP), 443 (HTTPS), 3306 (MySQL)
- Балансировщики: Nginx, HAProxy (базово)
- Брандмауэры: iptables, ufw
```

### 📦 Git (система контроля версий)

```bash
git init, add, commit, push, pull, clone
git branch, merge, rebase
git stash, reset, revert
git flow / GitHub Flow
Работа с Pull Requests
```

---

## 🐳 Контейнеризация (2–4 месяца)

### Docker — основа современной разработки

```dockerfile
# Темы:
- Dockerfile (FROM, RUN, COPY, CMD, ENTRYPOINT)
- Образы и слои (image layers)
- docker build, run, ps, exec, logs
- Docker Compose (многоконтейнерные приложения)
- Docker volumes (персистентность)
- Docker networks (bridge, host, none, overlay)
- Docker Registry / Hub
- Best practices (многостадийная сборка, non-root user)
```

**🎓 Проект:**
Запустить WordPress + MySQL через Docker Compose с volumes для хранения данных.

### ☸️ Kubernetes (K8s) — оркестрация контейнеров

```yaml
# Основные концепты:
- Pod, Deployment, ReplicaSet, Service (ClusterIP, NodePort, LoadBalancer)
- ConfigMap, Secret (хранение конфигураций)
- Ingress (внешний доступ)
- PersistentVolume (PV) и PersistentVolumeClaim (PVC)
- Namespaces (изоляция)
- livenessProbe / readinessProbe
- Horizontal Pod Autoscaler (HPA)
- Helm (пакетный менеджер для K8s)
```

**🎓 Проект:**
Развернуть микросервисное приложение (например, микроблог) в minikube с Ingress, Secrets и автоподнятием подов.

---

## 🔄 CI/CD (Непрерывная интеграция и доставка) — 3–4 месяца

### GitLab CI / GitHub Actions

```yaml
# .gitlab-ci.yml или .github/workflows
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - docker build -t myapp .
  only:
    - main

deploy:
  stage: deploy
  script:
    - kubectl apply -f k8s/
  environment: production
```

**🎓 Проект:**
Настроить пайплайн, который при пуше в main:
1. Собирает Docker-образ
2. Пушит его в GitLab/GitHub Container Registry
3. Деплоит на Kubernetes

### Jenkins (всё ещё нужен в корпорациях)

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { sh 'make' }
        }
        stage('Test') {
            steps { sh 'make test' }
        }
        stage('Deploy') {
            steps { sh 'make deploy' }
        }
    }
}
```

### ArgoCD (GitOps)

```yaml
# Аргументированное объявление желаемого состояния
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: myapp
spec:
  source:
    repoURL: https://github.com/me/myapp-config
    path: overlays/production
  destination:
    server: https://kubernetes.default.svc
    namespace: production
  syncPolicy:
    automated: {}
```

---

## 🏗️ Инфраструктура как код (IaC) — 2–3 месяца

### Terraform / OpenTofu

```hcl
# main.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "WebServer"
  }
}

resource "aws_s3_bucket" "data" {
  bucket = "my-unique-bucket-name"
}
```

**🎓 Проект:**
Развернуть VPC, EC2, RDS и S3 в AWS с помощью Terraform.

### Провайдеры: AWS / Azure / GCP (хотя бы один глубоко)

**AWS (самый популярный):**
- EC2, S3, VPC, IAM
- RDS, Lambda, EKS, CloudFormation
- CloudWatch, Route53, ALB/ELB

**🎓 Сертификация:**
AWS Certified Solutions Architect — Associate

---

## 🔍 Мониторинг и Логирование — 2–3 месяца

### Prometheus + Grafana

```yaml
# prometheus.yml
scrape_configs:
  - job_name: 'kubernetes-pods'
    kubernetes_sd_configs:
      - role: pod
```

**Метрики:**
- CPU, Memory, Disk, Network
- Пользовательские метрики (например, количество активных пользователей)

```promql
# Примеры запросов PromQL
rate(http_requests_total[5m])
node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes
```

### Loki + Promtail (логирование)

```yaml
# Loki: легковесная альтернатива ELK
- Агрегация логов со всех подов
- Поиск по логам через LogQL
```

### OpenTelemetry (трассировка)

```python
# Автоматическое отслеживание запросов через сервисы
from opentelemetry import trace
tracer = trace.get_tracer(__name__)

with tracer.start_as_current_span("my-operation"):
    # ваш код
    pass
```

**🎓 Проект:**
Настроить дашборд в Grafana с метриками Kubernetes-кластера и алертами в Telegram/Slack.

---

## 🔐 Безопасность (DevSecOps) — 2 месяца

### SAST / DAST сканеры

```yaml
# В CI/CD добавляем проверки безопасности
- Trivy (сканирование Docker-образов)
- Snyk (зависимости)
- OWASP ZAP (пентест API)
- SonarQube (качество кода)
```

### Secrets Management

```bash
# HashiCorp Vault — золотой стандарт
vault kv put secret/myapp db_password=supersecret
vault kv get secret/myapp
```

### Policy as Code

```rego
# Open Policy Agent (OPA)
deny[msg] {
  input.method == "POST"
  not input.user.role == "admin"
  msg = "Only admins can POST"
}
```

### Техники безопасности в K8s

- Network Policies (ограничение трафика между подами)
- Pod Security Standards
- Service Mesh (Istio / Linkerd) — mTLS, авторизация

---

## ☁️ Облака и провайдеры (выбрать один основной)

### AWS (70% вакансий)

| Сервис | Назначение |
|--------|------------|
| EC2 | Виртуальные серверы |
| S3 | Объектное хранилище |
| VPC | Виртуальная сеть |
| IAM | Управление доступом |
| RDS | Управляемая БД |
| EKS | Управляемый Kubernetes |
| Lambda | Serverless функции |

### Альтернативы: Azure / GCP

---

## 🧩 Дополнительные технологии (по желанию)

| Технология | Для чего |
|------------|----------|
| 🐧 **Ansible** | Управление конфигурациями (без агентов) |
| 🔄 **Packer** | Создание кастомных образов VM/контейнеров |
| 📦 **Helm** | Пакетный менеджер для K8s |
| 🎭 **Istio / Linkerd** | Service Mesh (трафик, безопасность) |
| 🤖 **Terraform CDK** | IaC на TypeScript/Python |
| 🧪 **Terratest** | Тестирование Terraform кода |

---

## 🗓️ План обучения по месяцам (минимум 9–12 месяцев)

### Месяц 1–2: 🐧 Фундамент
- [ ] Linux (Ubuntu) — базовые команды, файловая система, процессы
- [ ] Bash scripting — автоматизация рутины
- [ ] Git — полный цикл работы с репозиториями
- [ ] Сети — OSI, DNS, HTTP, SSH, CIDR
- [ ] Python — основы, работа с файлами, requests

### Месяц 3–4: 🐳 Контейнеризация
- [ ] Docker — образы, контейнеры, volumes, сети, compose
- [ ] Docker Registry — публикация образов
- [ ] Kubernetes — основные объекты (Pod, Deployment, Service, Ingress)
- [ ] minikube / kind — локальный кластер
- [ ] Helm — установка приложений чартами

### Месяц 5–6: 🔄 CI/CD
- [ ] GitLab CI / GitHub Actions — пайплайны
- [ ] Тестирование в пайплайнах (unit, integration, e2e)
- [ ] ArgoCD — GitOps для Kubernetes
- [ ] Jenkins (опционально, для legacy проектов)

### Месяц 7–8: 🏗️ Облака + IaC
- [ ] AWS (EC2, S3, VPC, IAM, RDS)
- [ ] Terraform — написание и применение конфигураций
- [ ] Terraform state (remote backend)
- [ ] Развертывание полноценного окружения через Terraform

### Месяц 9–10: 📊 Мониторинг + Логи
- [ ] Prometheus — сбор метрик
- [ ] Grafana — дашборды и алерты
- [ ] Loki — логирование
- [ ] OpenTelemetry — трассировка

### Месяц 11–12: 🔐 Безопасность + Продвинутые темы
- [ ] Trivy, Snyk — сканирование уязвимостей
- [ ] HashiCorp Vault — управление секретами
- [ ] Network Policies в Kubernetes
- [ ] Service Mesh (Linkerd / Istio)

---

## ✅ Проекты для портфолио (обязательны!)

1. **Чат-приложение** с реальным обменом сообщениями, развёрнутое через GitLab CI на Kubernetes с Prometheus + Grafana.

2. **Сайт на WordPress** с полной инфраструктурой в AWS:
   - Terraform → VPC, EC2, RDS, S3
   - Docker Compose для локальной разработки
   - GitHub Actions для деплоя

3. **Микросервисная архитектура** (например, интернет-магазин на FastAPI + React) с:
   - Helm-чартами
   - ArgoCD (GitOps)
   - Мониторингом и алертами

4. **Автоматизация бекапов** в S3 с периодичностью, отправкой уведомлений и проверкой целостности.

---

## 📚 Лучшие ресурсы 2026

### Книги
📖 "The DevOps Handbook" (Kim, Humble)  
📖 "Kubernetes: The Hard Way" (Kelsey Hightower)  
📖 "Terraform: Up & Running" (Yevgeniy Brikman)  
📖 "Site Reliability Engineering" (Google) — бесплатно онлайн

### Курсы (бесплатные)
🎥 **TechWorld with Nana** — YouTube (Docker, K8s, CI/CD)  
🎥 **DevOps Journey** — YouTube  
📘 **KodeKloud** (много бесплатных тем)  
📘 **Roadmap.sh/devops** — интерактивная карта

### Практика
🔧 **Katacoda / Killercoda** — интерактивные сценарии  
🔧 **Advent of Code** — алгоритмические задачи на Python  
🔧 **Civo.com** — бесплатный K8s кластер на 1 час

---

## 🎖️ Сертификации (для резюме)

| Уровень | Сертификация |
|---------|---------------|
| Начальный | AWS Cloud Practitioner |
| Средний | **CKA** (Certified Kubernetes Administrator) |
| Продвинутый | **AWS Certified DevOps Engineer** |
| Экспертный | **HashiCorp Certified: Terraform Associate** |

---

## 💼 Что писать в резюме DevOps-инженера

```markdown
## Технологии
🐧 Linux (Ubuntu, CentOS)
🐍 Python / Bash
🐳 Docker / Docker Compose
☸️ Kubernetes (CKA in progress)
📦 Helm, ArgoCD
🔧 Terraform (OpenTofu)
☁️ AWS (EC2, S3, VPC, IAM, RDS)
🤖 GitLab CI / GitHub Actions
📊 Prometheus + Grafana
🔐 Trivy, Vault
📝 Git, GitHub/GitLab

## Проекты (пример)
✅ Настроил GitOps для K8s кластера через ArgoCD (30+ микросервисов)
✅ Оптимизировал пайплайн CI/CD, сократив время деплоя с 15 до 4 минут
✅ Разработал Terraform модули для AWS инфраструктуры (prod/stage)
✅ Внедрил мониторинг и алерты, что снизило MTTR на 40%
```

---

## 🧠 Главные советы 2026 года

1. **Не учи всё сразу** — выбери стек: AWS + Terraform + K8s + GitLab CI + Prometheus.
2. **Практика каждый день** — 30 минут теории, 1 час практики.
3. **Заведи блог или GitHub** — покажи свои проекты (работодатели смотрят).
4. **Участвуй в Open Source** — хотя бы доку в популярных проектах.
5. **Следи за AI-тулами** — Copilot, Cursor AI сильно ускоряют рутину (но не заменяют понимание).

---

> 🚀 **DevOps — это не про инструменты, а про автоматизацию, надёжность и скорость доставки ценности пользователю.**

**Удачи на пути! 🎉**
```


