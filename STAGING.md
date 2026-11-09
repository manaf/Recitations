# Staging branch — NOT live

The app reads only `main` (jsDelivr `@main`, raw `/main/`). Files here are
prepared but not switched on.

## al-dosari (Yasser Al-Dosari) — whole-surah format, ready
- `al-dosari/audio.json`, `al-dosari/segments.json`: playback from one MP3 per
  surah (download.quranicaudio.com/quran/yasser_ad-dussary/NNN.mp3) with word
  timings, so there is no cut between ayahs. Built 2026-11-08 by finding each
  Tarteel ayah file inside the surah recording (6232 matched + 4 placed
  between neighbours: 39:47, 39:50, 92:14–15) and shifting its word timings.
- `"basmala": false` for surahs 79–114 (those files start straight with ayah 1).
- Switch on only after the app version with surah-format word highlighting
  (app commit 3f7f378, after 1.0.9) is live: copy both files to `main`, change
  the al-dosari entry in Recitation-Index to format "surah" with
  `has_word_segments: true` + fingerprints, purge jsDelivr, and stop QUL-Sync
  overwriting al-dosari (QUL id 103).
