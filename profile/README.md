
# 🏛️ nexaCampus — The Unified Institutional Operating System

[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://github.com/nexaCampus/backend)
[![Next.js](https://img.shields.io/badge/Web-Next.js%2014-000000?style=for-the-badge&logo=next.js&logoColor=white)](https://github.com/nexaCampus/web)
[![Android](https://img.shields.io/badge/Mobile-Android%20Kotlin-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://github.com/nexaCampus/android-app)
[![iOS](https://img.shields.io/badge/Mobile-iOS%20Swift-FA7343?style=for-the-badge&logo=swift&logoColor=white)](https://github.com/nexaCampus/iOS-app)
[![Supabase](https://img.shields.io/badge/Database-Supabase%20PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![Mistral AI](https://img.shields.io/badge/AI-Mistral%20AI-FF7000?style=for-the-badge)](https://mistral.ai)

**nexaCampus** is an institutional operating system connecting students, faculty, department chairs (HODs), and campus administrators into a unified, high-performance ecosystem. Built on a low-latency binary wire protocol, it combines enterprise academic ERP capabilities, hardware-locked anti-cheat examination engines, real-time role-badged communications, and AI academic assistance.

---

## 🏗️ System Architecture
```

                              nexaCampus Organization
                                         │
         ┌───────────────────────────────┼───────────────────────────────┐
         ▼                               ▼                               ▼
   [ web ] repo                   [ android-app ]                  [ iOS-app ]
  Next.js 14 SSR                  Kotlin + Compose               Swift + SwiftUI
 CampusOS Desktop                Hardened Kiosk Mode            UIScreen Protection
         │                               │                               │
         └───────────────────────┬───────┴───────────────────────────────┘
                                 │ HTTPS / Binary WebSocket (Protobuf v3)
                                 ▼
                        [ backend ] repo
                      FastAPI Core Engine
                      ├── Protobuf Serializer / Router
                      ├── Aegis Proctor Violation Pipeline
                      ├── Sandboxed LaTeX Compilation
                      └── Mistral AI Academic Proxy
                                 │
                ┌────────────────┴────────────────┐
                ▼                                 ▼
         Supabase Cloud                      Mistral AI
   PostgreSQL 15 (RLS Enforced)         `mistral-small-latest`
   Realtime Engine & Drive S3           Academic Copilot
```
---

## 📦 Repository Matrix

The **nexaCampus** ecosystem is decoupled across modular repositories:

| Repository | Tech Stack | Role & Core Capabilities |
| :--- | :--- | :--- |
| [`backend`](https://github.com/nexaCampus/backend)[cite: 2] | Python 3.11, FastAPI, `asyncpg`, Protobuf v3 | High-throughput asynchronous REST/WebSocket server, role-based access control (RBAC), proctoring violation tripwires, and database migrations[cite: 2]. |
| [`web`](https://github.com/nexaCampus/web)[cite: 2] | Next.js 14 (App Router), TypeScript, Tailwind CSS | Pixel-perfect CampusOS administrative cockpit, dual-rail navigation shell, triage action table ("Needs you now"), and split-screen LaTeX resume compiler[cite: 1, 2]. |
| [`android-app`](https://github.com/nexaCampus/android-app)[cite: 2] | Kotlin, Jetpack Compose, Material 3, Ktor | Native Android client with hardware-enforced kiosk security (`FLAG_SECURE`, `startLockTask`), camera QR scanning, and interactive student dashboard[cite: 2]. |
| [`iOS-app`](https://github.com/nexaCampus/iOS-app) | Swift 5.9+, SwiftUI, Combine | Native iOS client featuring zero-latency `UIScreen.isCaptured` shield protection against screen recording and AirPlay mirroring during exams. |

---

## ✨ Core Pillars & Platform Capabilities

### 1. 🛡️ Aegis Hardened Anti-Cheat Exam Engine
* **Native Display Locking:** Mobile clients enforce Android `FLAG_SECURE` and lock-task pinning to suppress incoming calls, notifications, split-screen modes, and background multitasking.
* **Screen Recording Defense:** Native observers terminate visual rendering and send blur events if screenshot or display capture attempts are detected.
* **Web Proctored Kiosk:** Enforces fullscreen mode, intercepts inspect-element key combinations (`F12`, `Ctrl+Shift+I`), and tracks tab-focus shifts.
* **Three-Strike Policy:** Real-time violation streams trigger automatic disqualification and submission upon reaching the strike threshold.

### 2. 🎛️ CampusOS Desktop Interface
* **Dual-Rail Navigation:** Persistent 64px global rail paired with a contextual secondary navigation sidebar[cite: 1].
* **Priority Action Triage:** The *"Needs You Now"* queue highlights pending approvals, student record updates, and admissions processing[cite: 1].
* **Global Command Palette:** Instant `⌘K` spotlight search across students, faculty rosters, timetables, and administrative directives[cite: 1].

### 3. 📄 Sandboxed LaTeX Resume & Identity Engine
* **Dynamic Student ID Cards:** Time-based, rotating cryptographic QR tokens generated with an Ed25519 signature to eliminate proxy attendance.
* **LaTeX CV Builder:** In-browser Monaco editor paired with an isolated, secure compiler rendering vector PDFs.

### 4. ⚡ Low-Latency Binary Messaging & WebSockets
* **Role Verification:** Real-time chat streaming with enforced identity tags:
  `[STUDENT]`, `[TEACHER]`, `[CR]`, `[MONITOR]`, `[HOD]`, `[DEAN]`, `[PRINCIPAL]`, `[ADMIN]`.
* **Binary Transport:** High-frequency exam telemetry and chat run over Protocol Buffers (`application/x-protobuf`) to minimize mobile payload footprint.

### 5. 🤖 AI Academic Assistant
* Integrated with Mistral AI (`mistral-small-latest`) for homework summarization, institutional FAQ triage, and context-aware administrative draft generation.

---

## 🚀 Quickstart & Local Setup

### 1. Backend Service (`backend`)[cite: 2]

```bash
git clone [https://github.com/nexaCampus/backend.git](https://github.com/nexaCampus/backend.git)
cd backend

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env

# Run FastAPI with hot-reloading
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload

```

### 2. Web Portal (`web`)



```bash
git clone [https://github.com/nexaCampus/web.git](https://github.com/nexaCampus/web.git)
cd web

# Install packages
npm install  # or pnpm install / bun install

# Start Next.js development server
npm run dev

```

Open [http://localhost:3000](http://localhost:3000) to view the portal.

### 3. Android Application (`android-app`)



```bash
git clone [https://github.com/nexaCampus/android-app.git](https://github.com/nexaCampus/android-app.git)
cd android-app

# Build debug APK using Gradle wrapper
./gradlew assembleDebug

```

Open the project directory in Android Studio (Giraffe/Hedgehog or newer) and run on a target device or emulator.

---

## 🔒 Security & Data Isolation

All data paths strictly adhere to Row Level Security (RLS) policies within Supabase:

* Student profiles are publicly unlisted; access is scoped strictly by institutional and classroom memberships.
* Exam question solutions and answer keys remain concealed until proctor evaluation concludes.
* Scheduled GitHub Actions workflows automatically execute health checks to maintain active database availability.

---

## 📄 License

Distributed under the Apache 2.0 License. See `LICENSE` for more information.

```

---

### How to Add This to Your Organization Profile

To make this display on your main **nexaCampus** GitHub overview page:

1. Click **Create new repository** inside the `nexaCampus` organization[cite: 2].
2. Name the repository `.github` (public).
3. Create a folder named `profile/` and add `README.md` inside it (i.e. `.github/profile/README.md`).
4. Commit and push the Markdown code above. It will render across the organization dashboard.

```
