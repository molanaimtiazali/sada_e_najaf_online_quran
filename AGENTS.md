# AGENTS.md

## Project Overview

Static single-page website for **Sada-e-Najaf Islamic Online Institute**, a Shia Muslim online academy. Everything lives in one file: `index.html` (markup, inline CSS, and all JavaScript). There is no build step, no package.json, no framework.

## Architecture

- `index.html` — the entire site. Sections in order: top contact bar, sticky nav, hero, daily reminders (ayah/hadith/dua), course catalog, free-trial booking form, pricing plans, interactive Quran reader, about/contact, footer, floating WhatsApp/QR widget.
- All JS is inline in a single `<script>` block at the bottom of `index.html`. Key functions: `toggleDarkMode()`, `changeCurrency()`, `changeLanguage()`, `filterCourses()`, `handleTrialSubmit()`, `openTrialModal()`, `loadSurah()`, `toggleAudio()`, `toggleWhatsAppPopup()`, `setWhatsAppTab()`.
- Course/pricing data is embedded in the DOM via `data-usd`/`data-pkr`/`data-gbp`/`data-eur` attributes; currency switching rewrites badge text from these attributes.
- Quran verse content (Surah Al-Fatihah and Al-Ikhlas) is embedded in the `quranVersesData` JS object; the surah dropdown only serves surahs present there (others fall back to Al-Fatihah).
- The trial form does not submit anywhere server-side; it reveals a confirmation panel and builds a `wa.me` deep link with the form values.

## Conventions & Non-Obvious Decisions

- **CDN-only dependencies**: Tailwind CSS, Lucide Icons, and QRCode.js load from CDNs, configured via an inline `tailwind.config` script (custom `arabic`/`urdu` font families, custom emerald-850/950 and gold shades). Keep this setup if editing styles.
- **Custom color note**: classes like `dark:bg-stone-850` appear in the markup but Tailwind's default palette has no `stone-850`; the config only extends `emerald.850`. This is inherited from the user's original code — do not "fix" silently.
- **RTL handling**: `changeLanguage()` toggles `document.documentElement.dir` and swaps only the hero title/subtitle text and font classes; the rest of the page stays English.
- **Contact details are content, not config**: phone numbers (03148681093, 03357671661) and email are hardcoded throughout and used in `wa.me` links, `tel:` links, and the generated QR code text.
- Images are hotlinked from Unsplash; Quran audio from cdn.islamic.network (Mishary Alafasy, 128kbps).

## Editing Guidance

- Preserve the inline `tailwind.config` block when touching the `<head>`.
- After adding a course card, give it a `course-card quran` or `course-card islamic` class so filtering works, plus a `price-badge` element with all four currency data attributes.
- Icons require `lucide.createIcons()` (already called once at script start); dynamically injected HTML containing `data-lucide` icons needs a re-run of that call.