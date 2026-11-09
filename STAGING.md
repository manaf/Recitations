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

## al-shatri, alafasy, minshawi — whole-surah format, ready (2026-11-09)
Same reason as Yasser: their Tarteel ayah files end/start while the voice is
sounding (Al-Shatri clearly, Alafasy and Minshawi slightly), so the switch
between files is heard as a cut. Audio: quran.com (QDC) whole-surah MP3s
(download.quranicaudio.com/qdc/<reciter>/murattal/N.mp3), which have no
basmala (`"basmala": false` except 1 and 9; the app plays the reciter's own
Al-Fatihah 1:1 first).
- Word timings = the app's current Tarteel ones, placed where each ayah file
  was found in the surah recording by sound (Al-Shatri 6182, Alafasy 6176,
  Minshawi 6231 ayahs; a few placed between neighbours: Alafasy 35:44;
  Minshawi 3:113, 4:88, 6:95, 9:93, 31:11).
- Other full-surah file where QDC's is a different recording: Alafasy 37 →
  quran/mishaari_raashid_al_3afaasee/037.mp3, Minshawi 13 →
  quran/muhammad_siddeeq_al-minshaawee/013.mp3 (both open with a basmala).
- No matching recording anywhere: Al-Shatri 41, Alafasy 78 and 82 — word
  times carried over by sound alignment (DTW on MFCCs; reproduces known
  timings within ~2 ms on a same-recording test).
- Checked on the test phone 2026-11-09 (Ar-Rahman, An-Naba, Ar-Ra'd,
  Fussilat): no cuts, highlight on time.
- al-dosari/segments.json updated: 1339 word ends trimmed to their ayah end.
Switch on together with al-dosari (same steps), only after the app version
with surah-format word highlighting is live. Users' ayah downloads of these
reciters are deleted by the app on the switch (re-download as whole surahs).
