**Карта обучения DevOps-инженера** с дорожной картой (Roadmap), этапами, стикерами для трекинга прогресса и таймингами.  

Я разделил путь на **7 логических блоков** — от основ до продвинутых практик. Для каждого этапа указаны:
- **Примерное время** (в неделях при занятиях 15–20 ч/нед).
- **Стикеры-чекины** (что можно наклеить на доску прогресса).
- **Подпункты** для детального изучения.

---

## 🗺 Общая карта обучения (Roadmap)

```
1. Основы ОС и сетей    (4–5 нед)
        ↓
2. Основы Linux + Bash   (6–8 нед)
        ↓
3. Системы контроля версий (Git) (2–3 нед)
        ↓
4. CI/CD (GitLab CI / GitHub Actions / Jenkins) (4–5 нед)
        ↓
5. Контейнеризация (Docker) + реестры (3–4 нед)
        ↓
6. Оркестрация (Kubernetes) (8–12 нед)
        ↓
7. Инфраструктура как код (Terraform) + конфигурация (Ansible) (5–7 нед)
        ↓
8. Мониторинг и логи (Prometheus, Grafana, ELK) (4–5 нед)
        ↓
9. Облака (AWS/Azure/GCP) + CI/CD интеграция (6–8 нед)
        ↓
10. Безопасность, резервное копирование, продвинутые практики (4–6 нед)
```

---

## 📋 Детальные этапы с подпунктами и таймингами

### **1. Основы ОС и компьютерных сетей**  
⏱ 4–5 недель  
🎯 Результат: понимаю, как пакет идёт по сети, что такое процесс, память, диски.

**Подпункты:**
- Модели OSI и TCP/IP
- IP-адресация, подсети (CIDR), NAT, DNS, HTTP/HTTPS
- Порты, сокеты, TCP vs UDP
- Основы работы ОС (процессы, потоки, ОЗУ, диски, файловые системы)

**Стикеры (наклейки для доски)**  
✅ TCP/IP и OSI  
✅ IP, маска, шлюз  
✅ DNS, HTTP  
✅ Процессы и память  

---

### **2. Linux + Bash**  
⏱ 6–8 недель  
🎯 Результат: уверенно работаю в CLI, пишу скрипты.

**Подпункты:**
- Установка Linux (Ubuntu/CentOS), работа без GUI
- Файловая система (/proc, /sys, права, ownership)
- Команды: ls, cd, grep, awk, sed, find, ps, top, netstat, systemctl, journalctl
- Текстовые редакторы (vim/nano)
- Bash: переменные, циклы, условия, функции, планировщик cron
- Управление пакетами (apt/yum), systemd

**Стикеры**  
✅ Навигация и файлы  
✅ Права и процессы  
✅ Bash-скрипты  
✅ Cron, systemd  
✅ Пакетный менеджер  

---

### **3. Git**  
⏱ 2–3 недели  
🎯 Результат: клонирую, ветвлюсь, мержу, решаю конфликты.

**Подпункты:**
- init, clone, add, commit, push, pull, fetch
- Ветки (branch, checkout, merge, rebase)
- Удалённые репозитории (origin, upstream)
- Разрешение конфликтов
- Git flow / GitHub Flow
- .gitignore, работа с тегами

**Стикеры**  
✅ Основные команды Git  
✅ Ветвление и слияние  
✅ Работа с удалённым репо  
✅ Git flow  

---

### **4. CI/CD**  
⏱ 4–5 недель  
🎯 Результат: собираю простой пайплайн (тест → сборка → деплой).

**Подпункты:**
- Концепции CI/CD (непрерывная интеграция, доставка, развёртывание)
- Настройка GitLab CI / GitHub Actions (или Jenkins)
- Пайплайн: линтер → юнит-тесты → сборка → артефакты → деплой на staging
- Переменные окружения, секреты
- Артефакты и кэширование

**Стикеры**  
✅ Пайплайн из 4 стадий  
✅ Переменные и секреты  
✅ Артефакты  
✅ Деплой на staging  

---

### **5. Docker**  
⏱ 3–4 недели  
🎯 Результат: оборачиваю любое приложение в контейнер.

**Подпункты:**
- Dockerfile (FROM, RUN, COPY, EXPOSE, CMD, ENTRYPOINT)
- Образы, контейнеры, Docker Hub
- docker-compose (многоконтейнерные приложения)
- Volumes (персистентность), сети (bridge, host, none)
- Best practices (многостадийная сборка, .dockerignore)

**Стикеры**  
✅ Написал Dockerfile  
✅ Запустил контейнер  
✅ Собрал compose (app + db)  
✅ Volumes и сети  

---

### **6. Kubernetes**  
⏱ 8–12 недель (самый объёмный этап)  
🎯 Результат: деплою, масштабирую, обновляю приложение в k8s.

**Подпункты:**
- Архитектура: Pod, Node, Control Plane, etcd, kubelet
- kubectl basics (get, describe, logs, exec, apply, delete)
- Pod, Deployment, ReplicaSet, Service (ClusterIP, NodePort, LoadBalancer)
- ConfigMap, Secret, Ingress, Namespace
- Rolling update, readiness/liveness probes, HPA (Horizontal Pod Autoscaler)
- Хранение: PersistentVolume, PersistentVolumeClaim, StorageClass
- Helm (чарты, шаблоны, управление релизами)

**Стикеры**  
✅ kubectl get pods  
✅ Развернул Deployment  
✅ Настроил Service + Ingress  
✅ ConfigMap + Secrets  
✅ Probes (liveness/readiness)  
✅ Helm chart  

---

### **7. Infrastructure as Code (Terraform) + Configuration Management (Ansible)**  
⏱ 5–7 недель  
🎯 Результат: создаю инфраструктуру кодом и настраиваю серверы.

**Подпункты:**
- **Terraform**: HCL, провайдеры (AWS/GCP), ресурсы, state, plan/apply/destroy, переменные, output, модули
- **Ansible**: inventory, ad-hoc commands, playbooks, roles, переменные, handlers, vault (шифрование секретов)
- Совместное использование: Terraform создаёт VM → Ansible настраивает её

**Стикеры**  
✅ Terraform init/plan/apply  
✅ Remote state (S3/backend)  
✅ Модуль Terraform  
✅ Ansible playbook (nginx)  
✅ Роль в Ansible  

---

### **8. Мониторинг и логи**  
⏱ 4–5 недель  
🎯 Результат: настроил сбор метрик и логов, сделал дашборд.

**Подпункты:**
- **Prometheus**: метрики, target labels, exporters (node, blackbox)
- **Grafana**: подключение datasource, дашборды, алерты
- **ELK / Loki**: сбор и просмотр логов
- Метрики контейнеров и k8s (cAdvisor, kube-state-metrics)

**Стикеры**  
✅ Prometheus собирает метрики  
✅ Дашборд Grafana (CPU, RAM)  
✅ Алерт по CPU  
✅ Централизованные логи (Loki или ELK)  

---

### **9. Облачные провайдеры**  
⏱ 6–8 недель  
🎯 Результат: поднимаю инфраструктуру в облаке + CI/CD деплой.

**Подпункты (выбрать один провайдера как основной):**
- **AWS**: IAM, EC2, VPC, S3, RDS, EKS, ALB, Route53
- **Azure**: Resource Manager, VM, AKS, Blob Storage, VNet
- **GCP**: Compute Engine, GKE, Cloud Storage, VPC, IAM
- Интеграция: Terraform создаёт ресурсы → CI/CD деплоит приложение в облако

**Стикеры**  
✅ Создал VM в облаке по Terraform  
✅ Настроил VPC/подсети  
✅ Облачный managed Kubernetes (EKS/GKE/AKS)  
✅ Деплой из CI/CD в облако  

---

### **10. Безопасность, бэкапы, продвинутые темы**  
⏱ 4–6 недель  
🎯 Результат: автоматизирую сканирование секретов, vulnerability scanning, бэкапы.

**Подпункты:**
- Безопасность: SAST/DAST (Trivy, SonarQube), проверка Docker образа
- Secrets management (HashiCorp Vault, или облачные Key Vaults)
- Резервное копирование etcd, БД, PV в k8s (Velero)
- GitOps (ArgoCD или Flux)
- Service Mesh (istio/linkerd) – обзорно

**Стикеры**  
✅ Trivy scan в CI  
✅ Vault для секретов  
✅ Velero backup k8s  
✅ ArgoCD синхронизирует Git с кластером  

---

## 🧭 Карта прогресса (в виде сводной таблицы)

| Блок | Тема | Примерное время | Стикеров |
|------|------|----------------|-----------|
| 1 | ОС и сети | 4–5 нед | 4 |
| 2 | Linux + Bash | 6–8 нед | 5 |
| 3 | Git | 2–3 нед | 4 |
| 4 | CI/CD | 4–5 нед | 4 |
| 5 | Docker | 3–4 нед | 4 |
| 6 | Kubernetes | 8–12 нед | 7 |
| 7 | Terraform + Ansible | 5–7 нед | 5 |
| 8 | Мониторинг (Prometheus+Grafana) | 4–5 нед | 4 |
| 9 | Облака | 6–8 нед | 4 |
| 10 | Безопасность, GitOps, бэкапы | 4–6 нед | 4 |
| **Итого** | **≈ 46–63 недели** | **~1 год (при ~15 ч/нед)** | **45 стикеров** |

---

## 🧩 Рекомендации по процессу

1. **Клей стикеры на физическую/виртуальную доску** (Trello, Notion, Miro). Перемещай в "Done" после выполнения подпункта.
2. Для **K8s, Terraform, CI/CD** обязательно делай проекты (свой TODO-приложение, блог на Hugo в контейнерах и т.д.).
3. Тайминг – **ориентировочный**. Если работаешь админом или разработчиком, многие блоки пройдут быстрее.
4. **Сертификации** как цель (CKA, Terraform Associate, AWS/Azure DevOps Expert) — увеличат тайминг, но добавят структуру.


