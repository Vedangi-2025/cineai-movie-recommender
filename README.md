# 🎬 CineAI – AI Movie Recommendation System

> **AI Internship Project** · Movie Recommendation System  
> Built using the Anthropic Claude API with content-based and collaborative filtering techniques

---

## 📌 Project Overview

CineAI is an intelligent movie recommendation web application that uses **Large Language Models (LLMs)** via the Anthropic Claude API to deliver personalised movie suggestions based on user preferences, mood, and viewing history.

Unlike traditional recommendation systems that rely on pre-built similarity matrices, CineAI leverages the Claude LLM as a real-time recommendation engine — combining **content-based filtering** (genre, mood, era, language) with **collaborative filtering** (inferring taste from reference movies the user has loved).

---

## ✨ Features

- 🎭 **Genre Selection** — Multi-select from 12 genre categories
- 🌙 **Mood-Based Filtering** — Pick your current mood (feel good, intense, emotional, etc.)
- 🎞️ **Reference Movie Input** — Add movies you've loved to get better-matched recommendations
- ⭐ **Rating Filter** — Set a minimum IMDb rating threshold
- 📅 **Era Preference** — Filter by release decade (classic to modern)
- 🌍 **Language Filter** — Filter by English, Hindi, Korean, Japanese, and more
- 🤖 **AI-Powered Results** — Real-time recommendations with match reasoning, plot summary, and a "why watch it" hook
- 📱 **Fully Responsive** — Works on mobile, tablet, and desktop

---

## 🧠 How It Works

```
User Preferences
      │
      ▼
Preference State (state.js)
      │
      ▼
Prompt Engineering (claude.js → buildPrompt)
      │
      ▼
Anthropic Claude API (claude-sonnet-4-6)
      │
      ▼
Structured JSON Response (5 movies)
      │
      ▼
UI Rendering (ui.js → renderMovies)
```

### Filtering Logic

| Technique | Implementation |
|---|---|
| Content-Based Filtering | Genre + mood + era + language + rating constraints in the prompt |
| Collaborative Filtering | If reference movies provided, Claude infers patterns in style, tone, and theme |
| Hybrid Approach | Both techniques combine when the user provides both genres and reference movies |

---

## 🗂️ Project Structure

```
cineai-movie-recommender/
├── index.html                  # Main HTML entry point
├── src/
│   ├── app.js                  # Application entry — wires all modules
│   ├── api/
│   │   ├── config.js           # API key and model configuration
│   │   └── claude.js           # Anthropic API client + prompt builder
│   ├── utils/
│   │   ├── state.js            # User preference state management
│   │   └── ui.js               # UI rendering utilities (cards, states)
│   └── styles/
│       └── main.css            # Full stylesheet
├── public/
│   └── favicon.svg             # App favicon
├── docs/
│   └── DEPLOYMENT.md           # Deployment guide & security notes
├── .env.example                # Environment variable template
├── .gitignore                  # Git ignore rules
└── README.md                   # This file
```

---

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Edge, Safari)
- An [Anthropic API key](https://console.anthropic.com/) (free tier available)

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cineai-movie-recommender.git
   cd cineai-movie-recommender
   ```

2. **Add your API key**  
   Open `src/api/config.js` and replace the empty string:
   ```js
   API_KEY: "sk-ant-your-key-here",
   ```
   Or copy `.env.example` to `.env` and fill in your key (for server-side use).

3. **Run the app**  
   Simply open `index.html` in your browser — no build step needed!
   ```bash
   # Or use a local dev server (recommended):
   npx serve .
   # Then visit http://localhost:3000
   ```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML5, CSS3, ES6+ JavaScript (modules) |
| AI Engine | Anthropic Claude API (`claude-sonnet-4-6`) |
| Architecture | No framework — pure modular JS for clarity |
| Styling | Custom CSS with CSS variables, responsive grid |

---

## 📖 Key Files Explained

### `src/api/claude.js`
The heart of the AI system. Contains:
- `buildPrompt(preferences)` — Converts user preferences into a detailed AI prompt that enforces content-based and collaborative filtering
- `fetchRecommendations(preferences)` — Calls the Anthropic API and parses the structured JSON response

### `src/utils/state.js`
Manages all user preference state in a single module. Clean separation of data from UI logic.

### `src/utils/ui.js`
Pure rendering functions — takes data and returns DOM elements. No business logic here.

### `src/app.js`
Wires everything together: attaches DOM event listeners, calls state functions, triggers API, updates UI.

---

## 🔒 Security Note

> ⚠️ **Do not commit your API key to GitHub.**  
> The current setup puts the key in `config.js` for simplicity. For production deployment, use a backend proxy (Node.js/Express) to keep the key server-side. See `docs/DEPLOYMENT.md`.

---

## 📸 Screenshots

> _Add screenshots of your running app here after deployment_

---

## 🎓 Learning Outcomes

Through this project, I learned:
- How to integrate LLM APIs into a real-world frontend application
- Prompt engineering for structured JSON output from an LLM
- The difference between content-based and collaborative filtering, and how to implement both through prompt design
- Modular JavaScript architecture (ES modules, separation of concerns)
- Responsive CSS design and dark-mode UI development

---

## 👩‍💻 Author

**Vedangi** · B.Tech CSE · YCCE  
AI Intern Project · 2024

---

## 📄 License

MIT License — feel free to use, modify, and learn from this project.
