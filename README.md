# 📄 Brochure Automation System

> Multi-country, multi-threaded brochure scraping & upload automation platform with remote control via Telegram bot.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=selenium&logoColor=white)
![Telegram Bot](https://img.shields.io/badge/Telegram_Bot-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![Threading](https://img.shields.io/badge/Multi--Threading-FF6F00?style=for-the-badge&logo=speedtest&logoColor=white)

---

## 🎯 Overview

A production-grade automation system that **scrapes digital brochures** from multiple retail websites across different countries, processes the content, and **uploads them to a content management panel** — all running autonomously with real-time monitoring.

The system currently operates across **6+ countries** with support for **50+ retail brands**, processing hundreds of brochures daily.

---

## ✨ Key Features

### 🌍 Multi-Country Support
- Parallel processing for multiple country pipelines
- Country-specific date parsing (French, German, Norwegian, Portuguese, etc.)
- Timezone-aware publication date filtering

### 🤖 Telegram Bot Integration
- Remote start/stop/status commands per country
- Real-time progress notifications
- Error alerts with detailed failure context
- Interactive automation menu on startup

### 🧵 Multi-Threaded Architecture
- Thread-safe concurrent browser sessions
- Isolated download directories per channel to prevent race conditions
- Duplicate detection to avoid re-uploading existing brochures

### 🔄 Robust Error Handling
- 10-minute patient wait system for slow-loading content
- Automatic retry logic with graceful degradation
- Skip-and-continue on failure (never crashes the full pipeline)
- Telegram alerts on timeout or upload errors

### 🖼️ Intelligent Image Processing
- Waits for all brochure page images to fully load before capture
- Validates image integrity before upload
- Handles signed/protected CDN URLs (CloudFront, etc.)

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────┐
│                  Telegram Bot (Control)               │
│         /start  /status  /stop  /bildirim             │
└──────────────┬───────────────────────────────────────┘
               │
    ┌──────────▼──────────┐
    │   Orchestrator       │
    │   (Main Controller)  │
    └──┬───┬───┬───┬───┬──┘
       │   │   │   │   │
    ┌──▼┐┌─▼┐┌─▼┐┌─▼┐┌─▼──┐     ← Each runs in its own thread
    │DE ││FR││NO││PT││AU  │        with isolated browser session
    └──┬┘└─┬┘└─┬┘└─┬┘└─┬──┘
       │   │   │   │   │
    ┌──▼───▼───▼───▼───▼──┐
    │   Selenium Browsers  │
    │   (Chrome Headless)  │
    └──────────┬───────────┘
               │
    ┌──────────▼──────────┐
    │   CMS Upload Panel   │
    └──────────────────────┘
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Core Language** | Python 3.10+ |
| **Browser Automation** | Selenium WebDriver + Chrome |
| **Remote Control** | python-telegram-bot |
| **HTTP Requests** | Requests + Session management |
| **HTML Parsing** | BeautifulSoup4 |
| **Concurrency** | Threading + Thread-safe queues |
| **Date Parsing** | Custom locale-aware parsers |
| **Notifications** | OneSignal API integration |

---

## 📊 Scale & Performance

| Metric | Value |
|--------|-------|
| Countries supported | 6+ |
| Retail brands tracked | 50+ |
| Daily brochures processed | 100+ |
| Pages downloaded per run | 500+ |
| Uptime | Runs autonomously 24/7 |

---

## ⚠️ Note

> This is a **private repository**. The source code is not publicly available as it contains proprietary business logic and integration details. This README serves as a portfolio showcase of the project's architecture and capabilities.

---

## 📄 License

Proprietary — All rights reserved.
