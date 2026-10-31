<div align="center">

# BijoyCharaLikho.app — বিজয় অ্যাপ ছাড়াই বাংলায় লিখুন!

### Browser-Native Bangla (Bijoy Bayanno / Ekushe) & English Typing Tutor and Government Exam Simulator

[![Live App](https://img.shields.io/badge/Live_App-bijoycharalikho.app-14532d?style=for-the-badge&logo=cloudflare&logoColor=white)](https://bijoycharalikho.app)
[![Platform](https://img.shields.io/badge/OS-macOS_%7C_Windows_%7C_Linux-0f172a?style=for-the-badge)](https://bijoycharalikho.app)
[![Backend](https://img.shields.io/badge/Edge_API-Cloudflare_Pages_Functions-f38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://bijoycharalikho.app)

<h2 align="center">
  Try it live: <a href="https://bijoycharalikho.app">🔗 https://bijoycharalikho.app</a>
</h2>

</div>

---

## 🎬 Live Demo Video & Preview

> **Watch the Demo:** *(Drag and drop your `.mp4` or `.mov` screen recording right below this line in GitHub's web editor to embed the native video player, or click the banner to launch the live app)*

<!-- PASTE YOUR GITHUB DRAG-AND-DROP VIDEO URL HERE -->

[![BijoyCharaLikho.app Hero Preview](./assets/og-banner.jpg)](https://bijoycharalikho.app)

---

## 💡 The Problem & Motivation

Every year in Bangladesh, hundreds of thousands of candidates sit for government recruitment practical typing exams (*Computer Operator, Office Assistant cum Computer Typist / অফিস সহকারী কাম-কম্পিউটার মুদ্রাক্ষরিক, Data Entry Operator, Stenotypist, BCC, Ministry & Court exams*).

1. **Mandatory Bijoy Layout:** Exam centers strictly require the **Bijoy (বিজয় বায়ান্ন / একুশে)** keyboard layout for Bangla (phonetic keyboards like Avro are prohibited) and a minimum net speed of **25–30 WPM in Bangla** and **30 WPM in English**.
2. **OS Barrier for Students:** Candidates using **macOS, Linux, or Chromebooks** (or PCs without paid desktop software) cannot easily install or practice the native Windows Bijoy application.
3. **Lack of Authentic Scoring & Memorization Tools:** Standard international typing websites use 5-character stroke rules and do not handle Bijoy's pre-base vowel reordering (`ি`, `ে`, `ৈ` typed *before* the consonant) or Bangladesh government word-deduction scoring.

**BijoyCharaLikho.app** solves all three problems directly in the browser with **zero software installation**.

---

## ✨ Key Features

### 1. Zero-Install In-Browser Bijoy Engine (`js/bijoy.js`)
- Intercepts physical key positions via `KeyboardEvent.code`, allowing users to keep their OS keyboard set to **English (US / ABC)** on Mac, Windows, or Linux while typing authentic **Bijoy Bayanno / Ekushe** keystrokes in real time.
- **Full Pre-Kar Reordering State Machine:** Typing `d` (`ি`), `c` (`ে`), or `Shift+C` (`ৈ`) *before* a consonant or multi-consonant conjunct automatically floats the vowel sign across the entire cluster (`d + j + g + k` $\rightarrow$ `ক্তি`, `c + j + f` $\rightarrow$ `কো`, `c + j + Shift+X` $\rightarrow$ `কৌ`).
- **Complete Conjunct & Modifier Support:** Handles Hasanta link (`g` $\rightarrow$ `্`, `g + g` $\rightarrow$ visible `্‌`), post-cluster Reph (`Shift+A` $\rightarrow$ `র্`, e.g., `j + m + Shift+A` $\rightarrow$ `কর্ম`), Ra-phala (`z` $\rightarrow$ `্র`), Ya-phala (`Shift+Z` $\rightarrow$ `্য`), and independent vowel composition (`g + d` $\rightarrow$ `ই`, `g + f` $\rightarrow$ `আ`).
- **Inverse Keystroke Solver (`toBijoyKeys` & `remainingBijoyKeys`):** Deconstructs any arbitrary Unicode Bangla word into its exact Bijoy key sequence and tracks partial key progress in real time.

### 2. Interactive "Learn & Memorize Bijoy" Tutor (`js/tutor.js`)
- Modeled after the classic **Bijoy Ekushe** step-by-step typing curriculum (`bijoyekushe.net.bd`), upgraded for modern browsers:
  - **14 Progressive Lessons (220+ items):**
    1. স্বরবর্ণ (Vowels `অ` – `ঔ`)
    2. কার-চিহ্ন (Kar Signs `া` – `ৌ`)
    3. হোম রো মুখস্থ কৌশল (Home Row Memory Drill)
    4. ব্যঞ্জনবর্ণ ১ম ও ২য় অংশ (All 39 Consonants & Modifiers)
    5. যুক্তাক্ষর ধাপ ১–৮ (150 Essential Conjuncts / Juktobarnas from `ক্ক, ক্ত, ক্ষ, জ্ঞ` to `হ্ম, হ্ন`)
    6. পূর্ণাঙ্গ বাক্য অনুশীলন (Sentence Drill)
  - **Hand, Finger & Shift Guide:** Tells the student exactly which hand, which finger (*Pinky, Ring, Middle, Index*), and which `Shift` key (*Left Shift vs. Right Shift*) to press for every character.
  - **Instant Mistake Feedback:** Alerts the student immediately if the wrong key or wrong Shift state is pressed and highlights the target key on the virtual keyboard.

### 3. Authentic Government Exam Mock Simulator (`js/stats.js` & `js/app.js`)
- **Dual Scoring Engine:**
  - **Bangladesh Gov Exam Word-Count Method:**
    $$\text{Net WPM} = \frac{\text{Total Words Typed} - (\text{Wrong} + \text{Skipped} + \text{Extra Words})}{\text{Minutes}}$$
  - **International 5-Stroke Method:**
    $$\text{Gross WPM} = \frac{\text{Total Keystrokes}}{5 \times \text{Minutes}}$$
- **Dynamic Programming Word Alignment:** Uses Wagner–Fischer edit-distance alignment over normalized Unicode tokens so that skipping or inserting a single word never desynchronizes the rest of the exam passage.
- **Exam Hall Mode & Combined Bilingual Test:** Supports distraction-free Exam Hall mode (no hints, optional **Strict No-Backspace** lock), back-to-back **Bangla + English Combined Exams**, printable evaluation sheets, and a one-click **"Practice Missed Words"** drill generator.

### 4. Dynamic Cloudflare Edge API (`functions/api/stats.js`)
- Powered by **Cloudflare Pages Functions** (serverless edge workers) with optional **Cloudflare KV** persistence.
- Tracks live daily examinee counts, global test totals, national top-speed leaderboards, and calculates each candidate's real-time percentile rank upon test completion.

### 5. Non-Intrusive Conditional Post-Test Ad Engine (`js/ads.js`)
- Strictly zero ads on page load, hero, tutor, or during typing tests.
- Triggers a sponsored popup modal **only after** a visitor completes a typing test, prioritizing a **Video Ad** first and automatically falling back to an **Image Banner Ad** if no video stream is available.

---

## 🗂️ Project Architecture

```text
bijoycharalikho.app/
├── index.html               # SEO-optimized main application shell + JSON-LD schema
├── css/
│   └── style.css            # Responsive UI, Hero layout, Virtual Keyboard, Dark & Print themes
├── js/
│   ├── bijoy.js             # In-browser Bijoy Bayanno FST engine & inverse keystroke solver
│   ├── tutor.js             # 14-stage Bijoy Ekushe interactive memorization tutor & finger map
│   ├── stats.js             # Word-level DP alignment & dual WPM/Accuracy scoring engine
│   ├── passages.js          # Built-in Bangla & English exam passages, official letters & drills
│   ├── ads.js               # Post-test conditional popup ad controller (Video -> Banner fallback)
│   └── app.js               # Main UI state controller, audio synthesizer & Edge API client
├── functions/
│   └── api/
│       └── stats.js         # Cloudflare Pages Serverless Function for live stats & leaderboard
├── assets/                  # Optimized Hero illustration, brand wordmark & OpenGraph banner
├── tests/
│   └── engine.test.js       # Automated Node.js test suite (FST, round-trip & WPM scoring)
├── sitemap.xml              # Search engine sitemap for bijoycharalikho.app
├── robots.txt               # Crawler directives
└── _headers                 # Cloudflare Pages security & caching headers
```

---

## 🧪 Running Locally & Testing

Requires **Node.js 18+** (zero external npm dependencies):

```bash
# Run automated unit tests + automatically regenerate all 5 route HTML files
npm test

# Start local dev server at http://localhost:8080
npm start
```

---

## 🛠️ Developer & Maintenance Guide

Keep this guide handy whenever you return to the codebase for updates, adding passages, or expanding features.

### 1. The Multi-Route Architecture & Generation
- **Source of Truth:** [`index.html`](file:///Users/utsho/1/index.html) is the master application template.
- **Standalone Route Files:** To ensure direct URL visits (e.g. `/practice`, `/exam`, `/tutor`, `/juktobarna`, `/leaderboard`) return HTTP 200 with unique SEO titles and OpenGraph tags on Cloudflare Pages, route files are generated automatically.
- **Workflow:** Whenever you modify navigation, header, footer, or core layout in `index.html`, simply run:
  ```bash
  npm test
  ```
  This runs [`scripts/generate-routes.js`](file:///Users/utsho/1/scripts/generate-routes.js) first, regenerating:
  - `practice.html` $\rightarrow$ `/practice`
  - `exam.html` $\rightarrow$ `/exam`
  - `tutor.html` $\rightarrow$ `/tutor`
  - `juktobarna.html` $\rightarrow$ `/juktobarna`
  - `leaderboard.html` $\rightarrow$ `/leaderboard`
  ...and then runs all 11 unit test suites in [`tests/engine.test.js`](file:///Users/utsho/1/tests/engine.test.js).

### 2. Adding or Editing Typing Passages (`js/passages.js`)
Passages for practice and government mock tests live in [`js/passages.js`](file:///Users/utsho/1/js/passages.js). To add a new passage, append to `MudraPassages.passages`:

```javascript
{
  id: 'gov-exam-custom-01',
  title: 'বিভাগীয় কম্পিউটার অপারেটর পরীক্ষা অনুচ্ছেদ',
  lang: 'bn',                // 'bn' or 'en'
  level: 'official',         // 'beginner' | 'intermediate' | 'advanced' | 'official'
  durationMinutes: 5,        // 5 or 10 minutes
  text: 'আপনার অনুচ্ছেদ এখানে লিখুন...',
  source: 'সরকারি নিয়োগ পরীক্ষা'
}
```
> [!TIP]
> After adding any Bangla passage, run `npm test`. The test suite automatically runs every single word in every passage through the Bijoy FST engine to guarantee 100% typing validity!

### 3. Updating the Bijoy Memorization Tutor (`js/tutor.js`)
The 14-stage interactive tutor lives in [`js/tutor.js`](file:///Users/utsho/1/js/tutor.js). Each stage defines:
- `char`: The target character, vowel sign, or conjunct.
- `keys`: The exact Bijoy key sequence (e.g. `g + d` for `ই`, `d + j + g + k` for `ক্তি`).
- `hand`: `'left'` or `'right'`
- `finger`: `'pinky'`, `'ring'`, `'middle'`, `'index'`, `'thumb'`
- `shift`: `false`, `'left'`, `'right'`, or `'any'`
- `label`: Friendly Bangla guidance instruction.

### 4. Bilingual UI Localization (`js/app.js`)
The site supports instant switching between Bengali and English:
- **Dictionary:** All translations are defined in `UI_I18N` inside [`js/app.js`](file:///Users/utsho/1/js/app.js) (`UI_I18N.bn` and `UI_I18N.en`).
- **DOM Binding:** Add `data-i18n="key_name"` to any HTML element. Toggling the `বাংলা | EN` pill automatically translates all bound elements.
- **Persistence:** Saved in `localStorage` under key `mudrakkhor_ui_lang_v1`.
- **Query Parameter:** Force language via URL: `https://bijoycharalikho.app/?ui=en` or `?ui=bn`.

### 5. Theme (Light & Dark Mode)
- **Toggle Button:** `#btnTheme` in the sticky topbar toggles `data-theme="dark"` on `document.documentElement`.
- **Persistence:** Saved in `localStorage` under `mudrakkhor_theme_v1`.
- **Hero Artwork Canvas:** `.hero-section` maintains its daylight atmospheric styling across both modes so the detailed Bangladeshi cultural illustration artwork stays natural and vibrant.

### 6. Cloudflare Pages & Cache-Busting Deployment
- **Git Push Deployment:** Pushing any commit to branch `main` on GitHub (`https://github.com/MuntasirMalek/bijoycharalikho.app.git`) automatically triggers a Cloudflare Pages production deployment.
- **Edge Functions:** Serverless API worker lives in [`functions/api/stats.js`](file:///Users/utsho/1/functions/api/stats.js) and serves live examinee stats without a Node backend server.
- **Cache-Busting:** When publishing updates to `css/style.css` or `js/*.js`, increment the version query string (e.g., `?v=15`) in `index.html` and run `npm test`. The `_headers` file enforces `Cache-Control: public, max-age=0, must-revalidate` so visitors always receive the latest version immediately.

---

## 📄 Copyright & Portfolio Notice

**Copyright © 2026 [Utsho](https://bijoycharalikho.app). All Rights Reserved.**

This repository is published as a **software engineering portfolio showcase** for **[bijoycharalikho.app](https://bijoycharalikho.app)**. The source code is proprietary and may not be redistributed, cloned for commercial deployment, or relicensed without explicit written permission from the author.

*Disclaimer: "Bijoy" and "Bijoy Ekushe" are registered trademarks of Ananda Computers. BijoyCharaLikho.app is an independent browser-based educational tool and is not affiliated with or endorsed by Ananda Computers.*
