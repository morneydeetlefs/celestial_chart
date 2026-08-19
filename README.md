# 🌌 Celestial Profile — Multi-System Astrology App

A beautiful, single-file astrology web app that combines **Western, Vedic, Chinese, Tibetan, and Astrocartography** systems into one unified reading. Chart calculations run entirely in the browser — no backend, no server. AI-powered predictions stream live via the **Groq API** (free tier, no credit card required).

![Celestial Profile Screenshot](https://img.shields.io/badge/Single%20File-HTML-c8a96e?style=flat-square) ![No Backend](https://img.shields.io/badge/No%20Backend-Pure%20JS-7b6fe0?style=flat-square) ![Groq Powered](https://img.shields.io/badge/AI-Groq%20Free%20Tier-5db89a?style=flat-square) ![License](https://img.shields.io/badge/License-MIT-c97b8a?style=flat-square)

---

## ✨ Features

### 🔭 Five Astrological Systems (toggle any on/off)
- **Western** — Sun sign, Moon sign, Rising sign, element, modality, ruling planet
- **Vedic (Jyotish)** — Sidereal sign, Nakshatra, current Dasha period and timeline
- **Chinese BaZi** — Birth animal, element, polarity, month pillar, clash animal, year energy
- **Tibetan** — Animal year, element, Mewa (life force number), Parkha trigram
- **Astrocartography** — Compares birth and current location, identifies active planet line

### 🗺️ Interactive Maps
- Click anywhere on the **OpenStreetMap** map to set birth and current locations
- Auto reverse-geocodes to city and country name
- "Detect my location" button via browser geolocation
- Pin markers styled per location type

### 🤖 AI Predictions via Groq (Free)
- Streams a personalised reading using your selected Groq model
- Covers: Soul Signature, Next 12 Months, 3–5 Year Outlook, Location influence, One Key Practice
- Live model list fetched directly from Groq's API — always shows what's actually available to your account
- Model dropdown includes name, owner, and context window size
- Falls back gracefully if a model is unavailable

### 💫 Pure-JS Chart Calculations (no API needed)
All astrological calculations happen locally in your browser:

| Calculation | Method |
|---|---|
| Western Sun Sign | Date boundary lookup table |
| Moon Sign | Lunar cycle approximation (~13.2°/day from J2000 epoch) |
| Rising Sign | Solar hour offset from birth time |
| Vedic Sidereal | Ayanamsa shift (~23° / 1 sign) from tropical |
| Nakshatra | Moon longitude divided into 27 equal mansions |
| Vedic Dasha | Nakshatra-based planetary period sequencing |
| Chinese Animal | Year cycle (adjusted for Chinese New Year ~Feb 4) |
| Chinese Element | 10-year stem cycle (5 elements × 2 polarities) |
| Tibetan Mewa | 9-year life force cycle |
| Tibetan Parkha | 8-year trigram cycle |
| Astrocartography | Longitude delta → planet line theme mapping |

---

## 🚀 Getting Started

### 1. Download the app
Just grab the single file:
```
astrology-app.html
```
No npm install. No build step. No dependencies to manage.

### 2. Get a free Groq API key
1. Go to [console.groq.com/keys](https://console.groq.com/keys)
2. Sign up with email, Google, or GitHub — **no credit card required**
3. Click **Create API Key** and copy it (starts with `gsk_`)

### 3. Open the app
Open `astrology-app.html` in any modern browser. That's it.

### 4. Paste your key
- Paste your Groq key into the **🔑 Groq API Key** field at the top
- Click **Save Key** — the app fetches the live model list instantly
- Your key is stored only in your browser's `localStorage`, never sent anywhere except Groq's API

### 5. Cast your reading
- Enter your birth details and pin your locations on the maps
- Toggle which astrological systems to include
- Click **✦ Cast My Celestial Profile ✦**

---

## 🔑 Groq Free Tier

Groq's free tier is genuinely generous for personal use:

| Model | Requests/day | Tokens/min |
|---|---|---|
| Llama 3.3 70B | 1,000 | 12,000 |
| Llama 4 Scout | 1,000 | varies |
| Qwen3 32B | varies | 6,000 |
| GPT-OSS 120B | 1,000 | 8,000 |

No credit card. No expiry. See [Groq rate limits](https://console.groq.com/docs/rate-limits) for the current full list.

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| UI & calculations | Vanilla HTML, CSS, JavaScript |
| Maps | [Leaflet.js](https://leafletjs.com/) + OpenStreetMap |
| Reverse geocoding | [Nominatim](https://nominatim.openstreetmap.org/) (free, no key) |
| AI predictions | [Groq API](https://console.groq.com/) (OpenAI-compatible, streaming) |
| Fonts | Google Fonts — Cormorant Garamond + Inter |
| Storage | Browser `localStorage` (key + model preference only) |

**Zero runtime dependencies** beyond Leaflet (loaded from CDN). No framework. No build tools.

---

## 📁 Project Structure

```
celestial-profile/
├── astrology-app.html   # The entire app — one file
├── README.md            # This file
└── LICENSE              # MIT License
```

---

## 🔒 Privacy

- Your Groq API key is stored **only in your browser's localStorage**
- Birth data and location data **never leave your device** except for:
  - The Groq API call (your chart data is sent as part of the prediction prompt)
  - Nominatim reverse geocoding (lat/lng sent to OpenStreetMap's servers to look up city name)
- No analytics, no tracking, no cookies, no server of any kind

---

## 🌍 Browser Support

Any modern browser works — Chrome, Firefox, Safari, Edge. No polyfills needed.

The app uses: `fetch`, `async/await`, `ReadableStream` (for streaming), `localStorage`, and `navigator.geolocation` — all widely supported since 2018+.

---

## 🤝 Contributing

Contributions are very welcome! Some ideas for improvement:

- **More accurate Moon/Rising calculations** using full ephemeris data (e.g. integrate [Astronomia](https://github.com/commenthol/astronomia) or [Swiss Ephemeris WASM](https://github.com/aloistr/swisseph))
- **Japanese astrology** (9 Star Ki / Onmyōdō)
- **Mayan Tzolk'in** calendar system
- **Celtic tree calendar**
- **PDF export** of the full reading
- **Share link** that encodes birth data in URL params
- **Dark/light theme toggle**
- **Compatibility reading** for two people

To contribute:
1. Fork the repo
2. Make your changes to `astrology-app.html`
3. Test in a browser
4. Open a Pull Request with a clear description

Please keep the single-file architecture — it's one of the best things about this project.

---

## ⚠️ Disclaimer

Astrology is an ancient symbolic system and is **not scientifically validated**. The readings generated by this app — both the chart calculations and the AI predictions — are intended for **entertainment, reflection, and personal exploration only**. They should not be used to make medical, financial, legal, or other important life decisions.

The Moon sign, Rising sign, Nakshatra, and Dasha calculations are **approximations**. For precise professional readings, consult a qualified astrologer using full ephemeris software.

---

## 📜 License

MIT — see [LICENSE](LICENSE) for details.

---

<div align="center">
  <p>Made with ✦ and curiosity about the cosmos</p>
  <p><em>The stars incline, they do not compel.</em></p>
</div>
