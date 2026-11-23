# Dead Key

Dead Key turns a single button into a voice for people who can move only one finger: tap dots and dashes, the phone decodes them into words, predicts the next word, and speaks it aloud. It stitches 1840s Morse code to modern speech synthesis, with an Arabic Morse mode and a learn mode — and two phones can even exchange messages by sound alone, with no internet and no account.

**Kiroween 2026 hackathon entry — category: Frankenstein.**

## What it does

- One-button Morse typing: short press = dot, long press = dash.
- Text prediction from a ranked wordlist (lookup, not a model).
- Speech: reads the message aloud, English or Arabic.
- Arabic Morse (ITU-R M.1677-1) + learn mode.
- Two phones by sound (experimental).
- No internet, no account. Core flow works fully offline.

## Demo

[Demo video — to be added, under 3 minutes, public on YouTube.]

Live app: [to be added]

## Files

- `spec.md` — one-page spec: one screen, one button, one message area, one prediction row.
- `morse-tables.json` — Latin, digits, punctuation, and the full Arabic Morse table (verified letter by letter, 23 Nov 2026).
- `wordlist.md` — prediction wordlists, English + Arabic, ranked by everyday usefulness.

## How it was built with Kiro

[To be completed during the build, slice by slice.]

## Status

Phase 0 (spec, tables, wordlist, wireframe, Devpost draft, video script, test checklist) — done 23 Nov 2026. Build starts when the Kiro credits code lands, or 29 Nov at the latest using the free allowance.
