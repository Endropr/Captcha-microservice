# Captcha Microservice — Pixeldays Security Core

[![Go Version](https://img.shields.io/badge/Go-1.22+-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://go.dev/)
[![Redis](https://img.shields.io/badge/Redis-FF4438?style=for-the-badge&logo=redis&logoColor=white)](https://redis.io/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

### Project Overview
Высокопроизводительный микросервис на **Go**, разработанный специально для защиты экосистемы [Pixeldays](https://pixeldays.ru/) от автоматизированных атак. Сервис генерирует динамические графические капчи с использованием алгоритмов наложения шума, исключающих эффективное распознавание через OCR-системы.

---

### Core Technologies
* **Language:** Go 1.22+ (выбран за высокую скорость обработки конкурентных запросов).
* **Session Storage:** **Redis** (TTL сессий — 5 минут) для обеспечения stateless-архитектуры и быстрого доступа.
* **Security:** Кастомные алгоритмы искажения символов, цветовой шум и динамические линии защиты.
* **Deployment:** Полная контейнеризация через Docker и Docker Compose для CI/CD процессов.

### API Interface
Микросервис предоставляет лаконичный API для интеграции:
* `GET /captcha` — Генерация новой капчи и возврат ID сессии с изображением.
* `POST /captcha/verify` — Валидация введенного пользователем значения.

### Quick Start
Для развертывания всей инфраструктуры (Go-сервис + Redis) выполните:

```bash
docker-compose up --build
```

**Сервис будет доступен по адресу:** ```http://localhost:8080/captcha```

  <p align="left">
    <img src="assets/captcha.jpg?v=2" alt="Captcha interface"/>
  </p>
  <p align="left"><i> An example of a captcha taken from the PixelDays interface </i></p>
