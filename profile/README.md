<div align="center">

<img src="https://raw.githubusercontent.com/lumio-chat/landing/main/public/favicon.svg" alt="Lumio Logo" width="128" height="128" />

# 🌟 Lumio Chat
### The Sovereign, Ultra-Fast & Modern Communication Platform

[![Organization: Lumio](https://img.shields.io/badge/Organization-lumio--chat-7928CA?style=for-the-badge&logo=github&logoColor=white)](https://github.com/lumio-chat)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg?style=for-the-badge)](https://www.gnu.org/licenses/agpl-3.0)
[![Website: lumio.chat](https://img.shields.io/badge/Website-lumio.chat-00DF89?style=for-the-badge&logo=firefox&logoColor=white)](https://lumio.chat)

**Lumio** is a next-generation open-source messaging and community platform built for privacy, performance, and complete data sovereignty. Designed from first principles to eliminate lag, bloated dependencies, and surveillance capitalism.

[🌐 Official Website](https://lumio.chat) • [📱 Download Clients](https://github.com/lumio-chat/desktop/releases) • [📖 Documentation](https://github.com/lumio-chat)

</div>

---

## ⚡ Why Lumio?

- 🚀 **Sub-Millisecond Speed:** Powered by a high-throughput **Rust** microservices backend and an ultra-reactive **Solid.js** web engine with zero virtual-DOM overhead.
- 🎨 **Adaptive Design Engine:** Full **Material You (M3)** dynamic color matching, custom palette pickers, OLED dark mode, and signature **Monokai Pro** flavors.
- 🇮🇷 **World-Class Persian & RTL Support:** Native Solar Hijri (شمسی) calendar integration, curated Iranian font suite (Vazirmatn, Shabnam, Sahel, Samim, Tanha, Lalezar) with flag indicators (🇮🇷 / 🇬🇧).
- 🎙️ **Crystal-Clear WebRTC Voice & Video:** Low-latency, noise-suppressed group audio and screen-sharing powered by **LiveKit SFU**.
- 👥 **1-Click Multi-Account Switching:** Connect multiple identities and switch seamlessly without logging out.
- 🔒 **Self-Hostable Sovereignty:** Run your own private instance with 1 Docker command. Your servers, your encryption, your data.

---

## 🗺️ Ecosystem Repositories

| Repository | Description | Primary Stack |
| :--- | :--- | :--- |
| 🌐 **[frontend](https://github.com/lumio-chat/frontend)** | Official reactive web client & PWA | Solid.js • TypeScript • Vite |
| ⚙️ **[backend](https://github.com/lumio-chat/backend)** | High-throughput async server microservices | Rust • Rocket • Axum • MongoDB |
| 💻 **[desktop](https://github.com/lumio-chat/desktop)** | Native cross-platform desktop application | Electron • TypeScript • macOS / Win / Linux |
| ⚡ **[desktop-tauri](https://github.com/lumio-chat/desktop-tauri)** | Ultra-lightweight native client (~10MB footprint) | Tauri • Rust • Webview |
| 🛡️ **[admin](https://github.com/lumio-chat/admin)** | Server moderation and instance inspection dashboard | Next.js • React • Tailwind CSS |
| 🚀 **[landing](https://github.com/lumio-chat/landing)** | Marketing landing page & showcase website | Astro • Tailwind CSS |
| 📦 **[sdk](https://github.com/lumio-chat/sdk)** | Type-safe client library & bot development framework | TypeScript |

---

## 🏛️ High-Level Architecture

```mermaid
flowchart TD
    subgraph Clients[" 📱 Client Tier "]
        Web["Web Client (Solid.js)"]
        Electron["Desktop (Electron)"]
        Tauri["Lightweight Desktop (Tauri)"]
        Mobile["Mobile Web App (PWA)"]
    end

    subgraph Gateway[" 🌐 Gateway & Storage "]
        Delta["Delta REST API (Rocket/Axum)"]
        Bonfire["Bonfire WebSocket Gateway"]
        Autumn["Autumn (S3 File Storage)"]
        January["January (Privacy Embed Proxy)"]
    end

    subgraph DataTier[" 💾 Infrastructure Tier "]
        Mongo[("MongoDB Cluster")]
        Redis[("Redis In-Memory Cache")]
        RabbitMQ[("RabbitMQ AMQP Broker")]
        LiveKit[("LiveKit SFU Voice/Video")]
    end

    Clients <-->|HTTPS REST| Delta
    Clients <-->|WSS Events| Bonfire
    Clients <-->|Uploads| Autumn
    Clients <-->|WebRTC Voice| LiveKit

    Delta <--> Mongo
    Delta <--> Redis
    Delta --> RabbitMQ
    RabbitMQ --> Bonfire
