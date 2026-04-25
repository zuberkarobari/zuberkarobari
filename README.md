<div align="center">
  
  # ⚡ Hi, I'm Md Zuber
  ### Senior Backend Engineer | Distributed Systems Architect | Cloud Specialist

  <p align="center">
    Building high-throughput, fault-tolerant microservices and cloud-native event-processing pipelines. Proven track record of owning end-to-end backend systems in the fintech, gig-economy, and industrial domains at production scale.
  </p>

  <p align="center">
    <a href="mailto:rafeeqzuberkarobari@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
    <a href="https://linkedin.com/in/md-Zuber"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
    <a href="tel:+919449995532"><img src="https://img.shields.io/badge/Call-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="Phone" /></a>
  </p>
</div>

---

## 🚀 Professional Experience & Impact

**Deloitte — Consultant** *(Client: J.P. Morgan)* | `Oct 2024 – Present`
* **Ops Intelligence & Monitoring System:** Architected cloud-native event-processing pipelines on AWS (ECS, SQS, S3) handling **300k daily events** with 99.9% uptime across US regions.
* **Latency Reduction:** Engineered reactive microservices via Spring WebFlux/WebClient, cutting inter-service p99 latency by **25%**.
* **DevOps & IaC:** Delivered Terraform modules cutting environment provisioning to under 20 mins, and declarative Jenkins CI/CD pipelines reducing deployment cycles from 40 mins to 12 mins.

**Infosys — Senior Systems Engineer** *(Client: VISA)* | `Mar 2022 – Sep 2024`
* **Real-Time Payment System:** Owned core reconciliation modules achieving ~99.99% accuracy across **50K+ daily financial settlements**.
* **Performance:** Re-engineered settlement batch processors using parallel stream processing, cutting execution time by **~67%**.
* **Event-Driven:** Scaled Kafka event pipelines for VISA notification triggers handling **10K+ events/hour** with exactly-once delivery semantics.
* *🏆 Awards: Star Performer (Feb 2024) | Client Excellence Award*

---

## 🛠️ Technical Arsenal

<p align="center">
  <img src="https://img.shields.io/badge/Java_21-%23ED8B00.svg?style=flat-square&logo=openjdk&logoColor=white" alt="Java"/>
  <img src="https://img.shields.io/badge/Spring_Boot_3.2-%236DB33F.svg?style=flat-square&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Spring_WebFlux-%236DB33F.svg?style=flat-square&logo=spring&logoColor=white" alt="WebFlux"/>
  <img src="https://img.shields.io/badge/Apache_Kafka-%23231F20.svg?style=flat-square&logo=apachekafka&logoColor=white" alt="Kafka"/>
  <img src="https://img.shields.io/badge/PostgreSQL-%23316192.svg?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Redis-%23DC382D.svg?style=flat-square&logo=redis&logoColor=white" alt="Redis"/>
  <br/>
  <img src="https://img.shields.io/badge/AWS_(ECS/SQS/S3)-%23FF9900.svg?style=flat-square&logo=amazon-aws&logoColor=white" alt="AWS"/>
  <img src="https://img.shields.io/badge/Terraform-%23844FBA.svg?style=flat-square&logo=terraform&logoColor=white" alt="Terraform"/>
  <img src="https://img.shields.io/badge/Jenkins-%23D24939.svg?style=flat-square&logo=jenkins&logoColor=white" alt="Jenkins"/>
  <img src="https://img.shields.io/badge/React_Native_(Expo)-%2320232a.svg?style=flat-square&logo=react&logoColor=%2361DAFB" alt="React Native"/>
  <img src="https://img.shields.io/badge/Firebase-%23FFCA28.svg?style=flat-square&logo=firebase&logoColor=black" alt="Firebase"/>
</p>

---

## 🏗️ Featured Architecture & System Designs

As a Senior Engineer, I focus heavily on High-Level (HLD) and Low-Level Design (LLD). *Click on any project below to expand the architectural details and domain expertise.*

<details>
  <summary><b>🏦 J.P. Morgan UPI Payment System v2</b></summary>
  <br/>
  <blockquote>
    <p><b>Architecture:</b> Lean Modular Monolith (9 Modules)</p>
    <p><b>Tech Stack:</b> Java 21, Spring Boot 3.2, PostgreSQL, Redis, PhonePe UPI 2.0</p>
    <h4>Domain Expertise & Low-Level Design (LLD):</h4>
    <ul>
      <li><b>ACID Compliance & Settlement:</b> Implemented <code>@Transactional(SERIALIZABLE)</code> isolation with <code>SELECT FOR UPDATE</code> row-level pessimistic locks to prevent race conditions during ledger debits/credits.</li>
      <li><b>Event-Driven Internal Bus:</b> Decoupled 9 internal modules using 5 named <code>Spring ApplicationEvents</code> (e.g., <code>PaymentConfirmedEvent</code>), replacing external Kafka overhead for atomic internal transactions.</li>
      <li><b>Idempotency & Security:</b> Designed an idempotency layer using Redis (24h TTL) and enforced SHA256 webhook checksum validation to prevent double-charging and payload spoofing.</li>
      <li><b>Automated Reconciliation:</b> Built <code>@Scheduled</code> cron jobs to fetch daily PSP reports, executing EOD break-detection matching against internal settlement records.</li>
    </ul>
  </blockquote>
</details>

<details>
  <summary><b>💳 VISA Real-Time Settlement Engine</b></summary>
  <br/>
  <blockquote>
    <p><b>Architecture:</b> Event-Driven High-Throughput Pipeline</p>
    <p><b>Tech Stack:</b> Core Java, Spring Boot, Apache Kafka</p>
    <h4>Domain Expertise & Low-Level Design (LLD):</h4>
    <ul>
      <li><b>High-Volume Reconciliation:</b> Owned reconciliation modules processing 50K+ daily financial settlements, achieving ~99.99% transaction accuracy.</li>
      <li><b>Kafka Topic Partitioning:</b> Scaled event pipelines to handle 10K+ events/hour with consumer group partitioning and exactly-once delivery semantics to prevent duplicate customer notifications.</li>
      <li><b>Parallel Stream Processing:</b> Re-engineered legacy batch processors using parallel streams and optimized connection pools, reducing end-of-day SLA execution time from ~2 hours to ~15 minutes.</li>
    </ul>
  </blockquote>
</details>

<details>
  <summary><b>👷‍♂️ GetWork - Hyperlocal Gig Economy Platform</b></summary>
  <br/>
  <blockquote>
    <p><b>Architecture:</b> Two-sided Marketplace & Distributed Wallet Engine</p>
    <p><b>Tech Stack:</b> Spring Boot 3.2, Firebase Cloud Functions, React Native 0.81, PostgreSQL / Firestore</p>
    <h4>Domain Expertise & Low-Level Design (LLD):</h4>
    <ul>
      <li><b>Gig-Oriented Task Management:</b> Engineered a 6-stage bidirectional state machine for the task lifecycle (Open ➔ Applied ➔ Assigned ➔ In-Progress ➔ Completion_Requested ➔ Completed) allowing users to easily "Get Work Done".</li>
      <li><b>Atomic Financial Ledger:</b> Designed a multi-tier wallet economics system utilizing immutable, append-only ledger transactions for 10% platform commission auto-deductions.</li>
      <li><b>Geospatial Intelligence:</b> Implemented Haversine formula-based worker proximity matching and utilized Geohash (Precision 6) for caching Google Maps API route/distance results.</li>
      <li><b>Dynamic Pricing Algorithms:</b> Built real-time budget calculators accounting for city-specific base pay, travel allowances, and dynamic worker counts.</li>
    </ul>
  </blockquote>
</details>

<details>
  <summary><b>🪨 Karobari Stone Management System</b></summary>
  <br/>
  <blockquote>
    <p><b>Architecture:</b> Industrial Logistics Suite & Digital Ledger</p>
    <p><b>Tech Stack:</b> Full-Stack (React, Backend Services)</p>
    <h4>Domain Expertise & Low-Level Design (LLD):</h4>
    <ul>
      <li><b>Digital Ledger Transformation:</b> Digitized complex physical ledger systems with a UI that feels familiar but offers the power of industrial automation.</li>
      <li><b>Wallet-Based Labor System:</b> Architected a prepaid credit wallet system for workers instead of direct employer billing, auto-debiting job values securely.</li>
      <li><b>Automated Logistics Math:</b> Engineered specific calculation algorithms for stone production outputs (e.g., strictly automating item counts `nag * 3` to determine total footage) and tracking truck expenses.</li>
    </ul>
  </blockquote>
</details>

<details>
  <summary><b>🤖 TrackR v2 - AI Finance App</b></summary>
  <br/>
  <blockquote>
    <p><b>Architecture:</b> Offline-first React Native Application</p>
    <p><b>Tech Stack:</b> Expo, Zustand, MMKV, Claude Vision API, Firebase</p>
    <h4>Domain Expertise & Low-Level Design (LLD):</h4>
    <ul>
      <li><b>Offline-First Architecture:</b> Built an encrypted, offline-first sync queue using MMKV and Zustand for zero-latency UI updates, paired with background Firestore cloud synchronization.</li>
      <li><b>AI/LLM Integration:</b> Integrated Claude 3.5 Sonnet Vision API via secured Firebase Cloud Functions for instant receipt parsing and Natural Language (NL) categorization.</li>
      <li><b>High-Performance UI:</b> Transitioned legacy list rendering to FlashList (60fps) and integrated React Native Reanimated for complex gesture-based transaction management.</li>
    </ul>
  </blockquote>
</details>
<br/>

---

## 📈 GitHub Analytics

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=zuberkarobari&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&count_private=true" alt="Zuber's GitHub Stats" />
</p>
<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=zuberkarobari&theme=radical&hide_border=true&background=0D1117&count_private=true" alt="GitHub Streak" />
</p>

---
<p align="center">
  <i>"Designing systems that survive the chaotic reality of production."</i>
</p>
