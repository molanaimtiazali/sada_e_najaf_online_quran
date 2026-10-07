# Sada-e-Najaf Islamic Online Institute

A single-page marketing website for **Sada-e-Najaf Islamic Online Institute**, a Shia Muslim online academy directed by Molana Imtiaz Ali (Hawza Najaf al-Ashraf). The site promotes 1-on-1 online classes in Quran with Tajweed, Fiqh-e-Jafariya, Usool-e-Deen, Nahjul Balagha, and Ahlulbayt (AS) studies for students in Pakistan and worldwide.

## Features

- **Hero section** with institute overview, trust indicators, and direct WhatsApp CTA
- **Course catalog** with category filtering (Quran & Tajweed vs. Fiqh-e-Jafariya & Ahlulbayt Studies) and per-course pricing
- **Free trial booking form** that composes a pre-filled WhatsApp message to the institute upon submission
- **Multi-currency pricing** (PKR, USD, GBP, EUR) switchable at runtime via data attributes
- **Multi-language hero** (English, Urdu, Arabic) with RTL support
- **Interactive Quran reader** with Arabic text, Urdu and English translations, and Alafasy recitation audio
- **Dark mode** toggle, sticky navigation, and a floating WhatsApp widget with a dynamically generated QR code

## Technologies

- Plain HTML/CSS/vanilla JavaScript — no build step or framework
- Tailwind CSS (CDN) with a small inline config for custom fonts and colors
- Lucide Icons (CDN) for iconography
- QRCode.js (CDN) for in-browser QR generation
- Google Fonts: Plus Jakarta Sans, Amiri, Scheherazade New, Noto Nastaliq Urdu

## Running Locally

The site is static — open `index.html` directly in a browser, or serve it with any static server:

```bash
npx serve .
# or
python3 -m http.server 8080
```

Deployed automatically as a static site on Netlify; no build command is required.