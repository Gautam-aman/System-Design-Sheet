# 🖥️ SysDesign.track — Interview Prep Dashboard

> A sleek, single-file system design interview preparation tracker. Track your progress across 45+ HLD & LLD topics, study curated resources, and practice the most asked interview questions — all in one place.

<div align="center">

### 🔗 [Live Demo → system-design-sheet.vercel.app](https://system-design-sheet.vercel.app/)

![Live](https://img.shields.io/badge/Live-system--design--sheet.vercel.app-00FF41?style=for-the-badge&logo=vercel&logoColor=white)
![HTML](https://img.shields.io/badge/Built%20With-HTML%2FCSS%2FJS-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-111111?style=for-the-badge)
![Storage](https://img.shields.io/badge/Storage-LocalStorage-00BFFF?style=for-the-badge)

</div>

---

## 📸 Preview

| Tab | Description |
|---|---|
| 📋 All Topics | Full tracker with search, filters, status dropdowns, company tags & resource links |
| 🏗️ High Level Design | 28 HLD topics — scalability, distributed systems, architecture |
| ⚙️ Low Level Design | 17 LLD topics — OOP design, patterns, class modeling |
| 📊 Frequency & Importance | Topics ranked by interview frequency with company breakdown |
| ❓ Interview Questions | 25 most-asked questions with hints and company tags |

---

## ✨ Features

- **45 curated topics** — HLD + LLD, each with importance rating and company tags
- **Progress tracking** per topic — `Not Started` → `Active` → `Completed`
- **Live progress bar** and header stats that update as you study
- **Curated resource links** (educative.io, Medium, system design blogs) per topic
- **Add your own links** to any topic — persisted across sessions
- **25 interview questions** with frequency ratings, company tags, and expandable hints
- **Frequency & Importance tab** — know what to prioritize before your interview
- **Search + multi-filter** — by status, type (HLD/LLD), or keyword
- **Zero setup** — single `.html` file, works offline, no install needed
- **LocalStorage persistence** — progress and custom links saved in your browser

---

## 🚀 Run Locally

```bash
git clone https://github.com/YOUR_USERNAME/sysdesign-track.git
cd sysdesign-track

# Just open the file — no server needed
open system-design-tracker.html        # macOS
start system-design-tracker.html       # Windows
xdg-open system-design-tracker.html   # Linux
```

Or deploy your own in seconds:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Gautam-aman/sysdesign-track)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/Gautam-aman/sysdesign-track)

---

## 📁 File Structure

```
sysdesign-track/
├── system-design-tracker.html   # Entire app — HTML + CSS + JS in one file
└── README.md
```

> No `npm install`. No build step. No backend. Just one file.

---

## 📚 Topics Covered

### 🏗️ High Level Design (28 topics)

| Topic | Importance | Key Companies |
|---|---|---|
| URL Shortener (Bit.ly) | 🔴 Critical | Amazon, Google, Uber |
| Twitter / Social Feed | 🔴 Critical | Twitter, Meta, LinkedIn |
| YouTube / Netflix | 🔴 Critical | Netflix, YouTube, Amazon |
| WhatsApp / Chat System | 🔴 Critical | Meta, Slack, Microsoft |
| Uber / Ride Sharing | 🔴 Critical | Uber, Lyft, DoorDash |
| Google Search | 🔴 Critical | Google, Amazon |
| Rate Limiter | 🔴 Critical | Stripe, Cloudflare, Google |
| Distributed Cache (Redis) | 🔴 Critical | Amazon, Google, Meta |
| Message Queue (Kafka) | 🔴 Critical | LinkedIn, Uber, Netflix |
| Consistent Hashing | 🔴 Critical | Amazon, Google, Cassandra |
| CAP Theorem / BASE / ACID | 🔴 Critical | All FAANG |
| Database Sharding | 🔴 Critical | Amazon, Uber, Airbnb |
| API Gateway / Load Balancer | 🔴 Critical | Amazon, Netflix, Uber |
| Instagram / Photo Sharing | 🟠 High | Meta, Pinterest, Snap |
| Amazon / E-Commerce | 🟠 High | Amazon, Flipkart, Shopify |
| CDN | 🟠 High | Cloudflare, Netflix |
| Notification System | 🟠 High | Apple, Google, Meta |
| Google Maps / Location | 🟠 High | Google, Uber, DoorDash |
| Distributed File Storage (S3) | 🟠 High | Amazon, Dropbox, Google |
| Search Autocomplete | 🟠 High | Google, Amazon, Twitter |
| Ticketmaster / Event Booking | 🟠 High | Ticketmaster, Amazon |
| Google Docs / Collab Editor | 🟠 High | Google, Microsoft, Notion |
| Payment System / Stripe | 🟠 High | Stripe, PayPal, Razorpay |
| Distributed ID Generator | 🟠 High | Twitter, Instagram, Uber |
| Circuit Breaker / Resiliency | 🟠 High | Netflix, Amazon, Uber |
| Recommendation Engine | 🟡 Medium | Netflix, Spotify, Amazon |
| Log / Metrics Aggregation | 🟡 Medium | Datadog, Splunk, Netflix |
| Web Crawler | 🟡 Medium | Google, Amazon, Bing |

### ⚙️ Low Level Design (17 topics)

| Topic | Importance | Key Companies |
|---|---|---|
| LRU Cache | 🔴 Critical | Google, Amazon, Meta |
| Strategy / Factory Patterns | 🔴 Critical | All FAANG |
| SOLID Principles | 🔴 Critical | All FAANG, Atlassian |
| Parking Lot System | 🟠 High | Amazon, Microsoft, Uber |
| Elevator / Lift System | 🟠 High | Amazon, Google, Microsoft |
| Hotel Booking System | 🟠 High | Booking.com, Airbnb |
| Chess / Board Game | 🟠 High | Amazon, Google |
| ATM System | 🟠 High | Amazon, Google, IBM |
| Vending Machine | 🟠 High | Amazon, Uber, Google |
| Splitwise / Expense Sharing | 🟠 High | Airbnb, Uber, Amazon |
| Food Delivery App | 🟠 High | Swiggy, Zomato, DoorDash |
| Movie Ticket Booking | 🟠 High | BookMyShow, Ticketmaster |
| Observer / Pub-Sub Pattern | 🟠 High | All FAANG, Salesforce |
| Library Management System | 🟡 Medium | Amazon, Google |
| Logger / Logging Framework | 🟡 Medium | Amazon, Google |
| Snake & Ladder | 🟡 Medium | Amazon, Microsoft |
| Cricinfo / Live Score | 🟡 Medium | Amazon, Google, ESPN |

---

## ❓ Interview Questions (25 Most Asked)

Includes questions from real interviews at Google, Amazon, Meta, Uber, Microsoft, Stripe, Netflix and more — each with a frequency rating, company tags, and an expandable hint.

Sample questions:
- *"Design a URL shortener. How would you handle 1 billion URLs?"*
- *"How do you design WhatsApp? How does message delivery work offline?"*
- *"Explain consistent hashing. Why is it used in distributed systems?"*
- *"Design an LRU Cache with O(1) get and put."*
- *"How do you prevent two users from booking the same seat simultaneously?"*

---

## 🛠️ Tech Stack

| Layer | Choice |
|---|---|
| Structure | Vanilla HTML5 |
| Styling | Pure CSS (CSS variables, no framework) |
| Logic | Vanilla JavaScript (ES6+) |
| Fonts | JetBrains Mono + Syne (Google Fonts) |
| Persistence | Browser LocalStorage |
| Hosting | Vercel |

---

## 🤝 Contributing

Contributions are welcome! Some ideas:

- Add more topics (Zookeeper, Service Mesh, Saga Pattern...)
- Add more interview questions
- Add better resource links
- Add export/import progress as JSON
- Add a notes field per topic

```bash
# Fork the repo, make your changes, and open a PR
git checkout -b feature/add-new-topics
# edit system-design-tracker.html
git commit -m "feat: add service mesh and saga pattern topics"
git push origin feature/add-new-topics
```

---

## 📄 License

MIT License — free to use, share, and modify.

---

<div align="center">

Made for engineers cracking system design interviews 💻

⭐ **Star this repo if it helped you!**

**[🚀 Open App](https://system-design-sheet.vercel.app/)**

</div>