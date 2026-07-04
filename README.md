<div id="header" align="center">
<img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExOWdpMmlvbW9waTJuOHhmbGE1amU5MjdtaDVsZDd2MXFhcmd4OGc2OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1zkb1rxzcc6RNZWo8i/giphy.gif" width="300"/>
</div>

<div id="badges" align="center">
<a href="https://www.linkedin.com/in/ismail-abdullah-a22923229/">
<img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=Linkedin&logoColor=white" alt="LinkedIn Badge"/>
</a>
</div>

<div align="center">
<img src="https://komarev.com/ghpvc/?username=Ismailab1&style=flat-square&color=blue" alt="Profile Views"/>
</div>

<h1 align="center">
Welcome to My Page!
<img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>

## 🌱 About Me

I am a Computer Science Graduate (Class of 2024) from the University of La Verne.

- 💼 **Current Role:** Software Development Intern at SupplyBistro (GustoMarket) (November 2025 - Present)
- 🔭 **Previous Experience:** Software Development Engineer at University of La Verne (2 years) - Data Analysis and Research Initiatives
- 🚀 **Current Focus:** Building full-stack e-commerce solutions with Django, Python, JavaScript, and AWS cloud services
- ⚡ **Interests:** Full-stack development, database architecture, AI/ML applications, system optimization, and creating scalable web applications
- 📫 **How to reach me:** [LinkedIn](https://www.linkedin.com/in/ismail-abdullah-a22923229/)
- 😄 **Pronouns:** He/Him

---

## 💻 Current Software Engineering Role

### Software Development Intern | SupplyBistro (GustoMarket) | November 2025 - Present

### 🎯 Key Achievements

#### Full-Stack Feature Development:

- 🛒 **Anonymous Customer POS System** — Engineered walk-in customer processing with Django signals, achieving zero-friction checkout for suppliers
- 📱 **Mobile Order Management** — Developed unified cart system with localStorage persistence, one-tap checkout, and RFQ (Request for Quote) support
- 🗺️ **Address Management System** — Architected soft-delete solution with audit trails, fixing data leakage affecting 1,082+ addresses
- 📄 **Document Upload System** — Built FormData/Fetch API-based file upload with client/server validation supporting PDF, PNG, JPG formats
- 📋 **Mobile Discrepancy Reporting** — Full audit-and-closure pass against 10 acceptance criteria; rewrote `mobile_discrepancy_list` view (root-caused variable mismatch), added per-type icons/colors, quantity validation clamped to valid range (server + client), photo filename conventions, per-photo error/retry logic, and pre-validation that prevents duplicate pending reports before `transaction.atomic()`
- 🛍️ **Order History & Reorder** — Built paginated, filterable buyer Order History page with color-coded status badges and one-click reorder (skips deleted products, IDOR-protected). Rewrote Purchase Details as a real-data view with live Stripe session status retrieval scoped to connected accounts

#### Stripe Connect & Payments:

- 🏦 **ACH via Financial Connections (8-layer fix)** — Re-enabled ACH bank payments end-to-end: removed blocking early-return guard, added `us_bank_account` to payment methods with FC permissions, wired `stripeAccount` to frontend Stripe.js constructor (fixing 404s on FC modal), added pre-flight capability check, implemented 4 webhook handlers (`checkout.session.completed`, `async_payment_succeeded`, `payment_intent.succeeded`, `payment_intent.payment_failed`), rewrote connected-account routing to read `Stripe-Account` header directly, fixed charge expansion scoping, and added dual-secret verification
- 💳 **Stripe Integration Overhaul (9 improvements)** — Fixed buyer order-confirmation emails with itemized details, hardened receipt email routing, added card capability pre-check at checkout, configured statement descriptors on onboarding completion, and enriched seller Payment Settings with onboarding guidance
- 🔒 **Capability Sync** — Wired `stripe.Account.retrieve_capability()` pre-validation into checkout flow; auto-persists `stripe_capabilities` on onboarding return with zero additional API calls
- 📧 **Receipt & Notification Fixes** — Corrected Stripe receipt email routing (`receipt_email` in `payment_intent_data`) and rebuilt buyer order emails with weight/quantity-based itemized line details
- 🚫 **Fulfillment Blocking** — Added `fulfillment_blocked` guard to 4 seller dashboard functions and mobile fulfillment — sellers cannot advance order status until ACH payment confirms

#### CI/CD & DevOps:

- 🐘 **GitHub Actions PostgreSQL Service** — Added real PostgreSQL 16 service container to PR validation workflow with health checks, enabling DB-dependent tests in CI
- 🔧 **CI Environment Fix** — Set `DJANGO_ENV=dev` to prevent Stripe production key validation from breaking all CI runs (one-line root-cause fix)
- 🚀 **Release Engineering** — Owned full Dev → QA → Stage → Prod branch promotion pipeline; shepherded 5 environment promotion PRs (up to 14,425 additions across 144 files per release)
- 🐳 **Docker Cleanup** — Removed stale Dockerfile/entrypoint.sh from repo; canonicalized docker-compose as build mechanism tracked per branch

#### Database & Architecture:

- 🔧 Fixed critical PostgreSQL query issues in supplier directory (CompanyRelationship schema optimization)
- 📊 Implemented database migrations with rollback strategies for production safety
- 🏗️ Designed dual-column tracking systems for business vs. technical states
- 🔍 Created comprehensive management commands for data synchronization and validation
- 🛡️ **IDOR Guards** — Added server-side authorization checks on all new buyer-facing endpoints (Order History, Purchase Details, Reorder)
- 🗃️ **ACH Payment Model Extension** — Added 11 fields to Order model (`stripe_session_id`, `stripe_payment_intent`, `stripe_mandate_id`, `payment_method_type`, `payment_confirmed_at`, `platform_fee_amount`, `seller_receives_amount`, `fulfillment_blocked`, etc.) with merge migration reconciliation

#### Bug Fixes & System Optimization:

- 🔒 **Data Leakage Prevention** — Resolved critical security issue where 1,082 addresses were visible across all companies; implemented soft-delete with audit trails
- 🗄️ **Database Schema Correction** — Fixed pending supplier invisibility bug by identifying and correcting incorrect column usage (status vs supplier_relationship_status)
- 💳 **Transaction Management** — Resolved TransactionManagementError in multi-vendor order placement by implementing proper atomic transaction handling
- 📊 **Dashboard Analytics Crash** — Fixed TypeError: float(None) across 4 critical locations in seller dashboard analytics
- 🔄 **Checkout Race Condition** — Fixed `payment_status` endpoint returning 404 during redirect-to-webhook race window; now returns `{"processing": true}` gracefully
- 📱 **Discrepancy List Root Cause** — Identified and fixed variable mismatch (`return_status` vs `status`) that caused discrepancy list to return zero results for all users

#### 📊 Impact Metrics

- ✅ 30+ Unit Tests created for POS regression and feature validation
- ✅ 508 Invalid Addresses flagged and hidden from production UI
- ✅ 3,000+ lines of code contributed across Stripe, mobile, and CI features
- ✅ 40+ Pull Requests merged addressing critical bugs and features
- ✅ 5 Environment Promotion PRs managing full Dev → QA → Stage → Prod pipeline
- ✅ 2 CI/CD pipeline fixes unblocking all subsequent team PR merges
- ✅ 11 new database fields + 3 migrations deployed with zero downtime
- ✅ 10 acceptance criteria closed in single discrepancy audit PR

---

## 💼 Professional Experience

### 🛠️ Hardware Test Technician | IDC Logistics
**September 2025 – December 2025**

- 🛠️ **Workflow Optimization:** Analyzed testing workflows and identified a bottleneck in system reboot times; optimized the protocol to eliminate a 1-4 minute delay, increasing daily system throughput
- 🖥️ **Diagnostics:** Diagnosed component-level failures on 120+ enterprise-grade workstations daily, isolating root causes in NVIDIA RTX 40/50 series GPUs and Intel CPUs
- ⚡ **Quality Control:** Enforced strict quality control standards for high-performance computing hardware, preventing DOAs (Dead on Arrival) and reducing RMA rates

### 📶 SAT Information Technology Monitor | College Board
**March 2025 – October 2025**

- 📶 **Uptime:** Maintained 99.9% service availability for digital exam platforms, supporting 3,100+ concurrent users during high-pressure testing windows
- 🚨 **Incident Response:** Triaged and resolved 7+ critical connectivity and hardware incidents in real-time, minimizing disruption for exam participants
- 🔍 **Monitoring:** Proactively monitored network health and system performance metrics to mitigate connectivity anomalies before they impacted operations

### 🎓 Lead Instructor - AI & Machine Learning | iD Tech @ Stanford University
**June 2024 – August 2025**

- 🤖 **Edge AI Deployment:** Deployed computer vision models on NVIDIA Jetson Orin Nano devices for 160+ students, emphasizing optimization for hardware-constrained inference
- 🎓 **Technical Instruction:** Taught Python, OpenCV, and Deep Learning concepts, integrating real-time debugging demonstrations to improve student project completion rates
- 👥 **Leadership:** Mentored a team of 6 instructors on classroom leadership and technical debugging, fostering a collaborative environment
- 🔧 **Hardware Integration:** Guided students in integrating hardware sensors with software logic for automated tracking projects

### 🐍 Software Development Engineer | University of La Verne
**October 2021 – May 2024**

- 🐍 **Automation:** Automated administrative data workflows using Python scripts, replacing manual log processing and saving 10+ hours of weekly staff labor
- 🎥 **IT Support:** Orchestrated IT support for major on-campus conferences, managing live streaming hardware, Zoom configurations, and real-time troubleshooting for speakers
- 🏗️ **ETL Pipelines:** Built Python ETL pipelines to extract and transform data from legacy systems for internal reporting dashboards
- 🔄 **Legacy Maintenance:** Maintained and refactored legacy Python codebases to improve performance, readability, and long-term maintainability

---

## 💼 Recent Projects

### 🧬 Life Orchestrator
**TypeScript | React | Google Gemini AI**

An AI-powered autonomous life management application that acts as a personal Chief Operating Officer (COO) for daily scheduling, relationship tracking, and task optimization.

- **Features:** Local-first privacy architecture (all data in browser localStorage), AI-driven scheduling with temporal modes (Reflection/Active/Planning), Kinship Debt algorithm for relationship health tracking, and proactive task redistribution
- **Tech:** React, TypeScript, Google Gemini API, IndexedDB-ready architecture
- **Last Updated:** May 2026

### ⚔️ Einherjar Combat Demo
**C# | Unity | Game Jam**

A 2D action-combat game set in Norse mythology, built during a game jam. Designed and implemented core gameplay systems from scratch.

- **My Contributions:**
  - ⚔️ **Projectile Parry System** — Full two-script parry mechanic: deflects incoming enemy projectiles mid-swing using `Vector2.Reflect`, redirecting them back at enemies with correct collision logic and audio feedback
  - 💨 **Health-Based Dash** — Dash costs HP and rewards low-HP aggression: distance scales dynamically up to 1.9× at low health, with invincibility frames
  - 🩸 **Lifesteal System** — Fixed and completed broken lifesteal targeting logic, wired to normalized health checks, balanced heal values
  - 🔊 **Audio Engine** — Built singleton `AudioEngine.cs` from scratch: sourced real SFX, wired hit/swing sounds to events, added pitch randomization (0.9–1.1)
  - ✨ **VFX Engine** — Built singleton `VisualFXEngine.cs` for combat visual effects (hit bursts, damage flash) using pooled prefab spawning
  - 🧌 **Frost Giant Enemy** — Created animation controller and tuned prefab movement speed
- **Play it:** [itch.io](https://bluelord22.itch.io/einherjar)
- **Source:** [GitHub](https://github.com/Ismailab1/Gamplay-First-Game-Jam-Einherjar-Combat-Demo)

### 📶 Cisco Network Test Automation
**Python | Network Automation**

A development automation framework for Cisco network testing and validation workflows.

- **Focus:** Automated network configuration testing, infrastructure validation, and development workflow automation
- **Last Updated:** May 2025

### 🧠 Brain Tumor Classification
**Python | TensorFlow | OpenCV | Streamlit**

A high-accuracy Convolutional Neural Network (CNN) designed to classify brain MRI scans.

- **Features:** Deployed as a web app via Streamlit for <2s real-time inference. Integrated Google Gemini API to provide "Explainable AI" (XAI) text summaries alongside visual predictions
- **Status:** Completed

### 🤖 Team Tasks AI
**TypeScript | React | Azure OpenAI**

A collaborative task management web application developed for the Azure AI Developer Hackathon.

- **Features:** AI-powered check-ins and summaries using GPT-4. Built with React.js, TailwindCSS, Node.js, and Azure Functions. Automated CI/CD using GitHub Actions
- **Last Updated:** March 2025

### 🎮 3D Game Engine
**C++ | Low-Level Programming**

Building a game engine from scratch to understand the fundamentals of graphics and memory.

- **Focus:** Low-level memory management, custom allocators, and graphics rendering architecture
- **Status:** In Active Development

### 💾 C++ Memory Manager
**C++ | Systems Programming**

A custom memory manager designed to track dynamic allocations and detect memory leaks.

- **Features:** Custom tracking tools for fragmentation analysis and memory layout optimization. Demonstrates deep understanding of pointers and system resources
- **Status:** Completed

### 📊 XML to Excel Converter
**Python | Data Processing**

A Python script that parses XML files and converts them into easy-to-read CSV/Excel format.

- **Use Case:** Streamlines data processing, reporting, and analysis workflows for legacy data systems
- **Last Updated:** January 2025

### 🧠 My Recognition
**Python | Machine Learning**

A machine learning project focused on recognition tasks and AI model implementation.

- **Last Updated:** July 2025

---

## 🔨 Languages and Tools

### 🔡 Languages

<div>
<img src="https://github.com/devicons/devicon/blob/master/icons/python/python-original.svg" title="Python" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/cplusplus/cplusplus-original.svg" title="C++" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/csharp/csharp-original.svg" title="C#" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/typescript/typescript-original.svg" title="TypeScript" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/javascript/javascript-original.svg" title="JavaScript" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/java/java-original.svg" title="Java" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/kotlin/kotlin-original.svg" title="Kotlin" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/html5/html5-original-wordmark.svg" title="HTML" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/css3/css3-original-wordmark.svg" title="CSS" width="50" height="50"/>&nbsp;
</div>

### 🌐 Frameworks, Cloud & Databases

<div>
<img src="https://github.com/devicons/devicon/blob/master/icons/unity/unity-original.svg" title="Unity" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/django/django-plain.svg" title="Django" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/react/react-original.svg" title="React" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/nodejs/nodejs-original.svg" title="Node.js" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" title="AWS" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/azure/azure-original.svg" title="Azure" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/mysql/mysql-original-wordmark.svg" title="MySQL" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/postgresql/postgresql-original-wordmark.svg" title="PostgreSQL" width="50" height="50"/>&nbsp;
</div>

### 🛠️ Tools & Platforms

<div>
<img src="https://github.com/devicons/devicon/blob/master/icons/git/git-original.svg" title="Git" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/linux/linux-original.svg" title="Linux" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/visualstudio/visualstudio-plain.svg" title="Visual Studio" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/pycharm/pycharm-original.svg" title="PyCharm" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/androidstudio/androidstudio-original.svg" title="Android Studio" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/spyder/spyder-original.svg" title="Spyder" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/figma/figma-original.svg" title="Figma" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/matplotlib/matplotlib-original-wordmark.svg" title="MatPlotLib" width="50" height="50"/>&nbsp;
<img src="https://github.com/devicons/devicon/blob/master/icons/matlab/matlab-original.svg" title="MatLab" width="50" height="50"/>&nbsp;
</div>

---

## 🎯 Technical Highlights

- 🏆 Azure AI Developer Hackathon Participant
- ⚔️ Game Jam Shipped Title (Unity, C#, Gameplay Systems Design)
- 🧬 AI-Powered Life Management (Google Gemini, Local-First Architecture)
- 🔧 Experienced in Full-Stack Development (Django, React, Node.js, TypeScript)
- ☁️ Cloud Development with AWS, Azure OpenAI, and Azure Functions
- 📶 Network Automation & Infrastructure Testing (Cisco)
- 🤖 AI/ML Integration in production applications
- 🛠️ Systems Programming (C++, Low-level memory management)
- 📈 Data Processing & Automation (Python, XML, CSV)
- 🚀 CI/CD Pipelines with GitHub Actions
