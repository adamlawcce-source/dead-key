# Dead Key — one-page spec (Phase 0, Kiroween 2026)

**Product:** Dead Key turns a single button into a voice for people who can move only one finger: tap dots and dashes, the phone decodes them into words, predicts the next word, and speaks it aloud. It stitches 1840s Morse code to modern speech synthesis, with an Arabic Morse mode and a learn mode — and two phones can even exchange messages by sound alone, with no internet and no account.

**Category:** Frankenstein. **Platform:** one web app, runs on a phone in the browser. **Offline, no account, no server.** Core flow works with the network switched off.

## One screen, one button, one message area, one prediction row

| Element | Rule |
|---|---|
| Central button | The only input. Fills most of the screen. Short press = dot, long press = dash. |
| Message area | Above the button. Current message in large type, readable at arm's length. Shows the letter being built as dots/dashes live. |
| Prediction row | Below the message area, above the button. Up to 3 large tap targets. Tap one to accept the whole word. |
| Speak button | One large button, next to the message area. Reads the full message aloud. |
| Mode switch | Latin / العربية toggle. One tap, large target, always visible. |
| Learn + Sound | Two small-but-tappable links at the bottom: Learn mode, Send by sound / Listen. Never inside the typing flow. |

## Input timing (initial defaults — Phase 1 spike validates them with real presses)

- Press under 300 ms = dot. Press 300 ms or over = dash.
- Pause 700 ms after a press = letter accepted. Pause 1,500 ms = word space.
- One speed setting only: Slow / Normal / Fast (Slow doubles the gaps). No adaptive timing — cut-list item.
- Every press gives instant feedback: button flashes, a click sounds (if sound on), dot/dash appears immediately.

## States — every state the app can be in

1. **Waiting** — empty message, button idle, hint text: "Tap: short = dot, long = dash."
2. **Dot recorded** — a dot was just entered; the in-progress letter shows "·" (and any dashes so far). Button returns to idle, listening for the next press.
3. **Dash recorded** — same as dot recorded, with "−" added to the in-progress letter.
4. **Letter accepted** — the pause expired, the dot/dash sequence matched a letter in `morse-tables.json`, the letter is appended to the message, and the prediction row refreshes. If the sequence matches nothing, the app shows "?" once, clears the in-progress letter, and stays in Waiting — it never blocks typing.
5. **Word predicted** — the prediction row shows up to 3 words matching the letters typed so far (prefix lookup in `wordlist.md`, most useful first). Tapping a word replaces the current partial word, adds a space, and returns to Waiting for the next word.
6. **Message spoken** — Speak was tapped, the full message is read aloud with text-to-speech (English or Arabic, matching the mode), and the message stays on screen so it can be spoken again or sent by sound.

Extra states, outside the core loop: **Learn mode** (app shows a letter, user taps its code, app confirms or corrects); **Sending by sound** (message plays as tones); **Listening** (microphone open, decoding tones from another phone). A failed listen never blocks typing.

## Decoding

- Data source: `morse-tables.json` — Latin A–Z, digits 0–9, common punctuation, and the full 28-letter Arabic Morse table (ITU-R M.1677-1, cross-checked letter by letter against two independent sources, 23 Nov 2026).
- Arabic mode: right-to-left text, Arabic letters decode from the Arabic table, prediction uses the Arabic wordlist. Hamza (ء) = single dot, folded forms (ة → ت, ى → ي, أ/إ/آ → ا) map to their base letter. Diacritics are ignored.
- Prediction is a lookup, not a model: match the current partial word as a prefix against the ranked wordlist, return the top 3. No network, no training.

## Sound link (experimental, cut first if the Phase 1 spike fails)

- Send: plays the message as tones (dot = short tone, dash = long tone, letter gap = silence).
- Listen: microphone decodes tones back into text on the second phone.
- Labelled "experimental" in the app. If it fails, the core product (typing, prediction, speech, Arabic, learn) is still complete.

## What is NOT in the product

No account, no server, no second platform, no custom prediction model, no adaptive timing, no marketing site. Cut order if a day slips: sound link, learn exercises beyond the first set, Arabic prediction, extra punctuation/digits, visual polish beyond contrast/button size/readable text.

## Done means

The 10-message test checklist (`test-checklist.md`) passes on a real phone, offline, with the network off. Submission finished evening of 3 Dec 2026; 4 Dec is buffer only; CRMEF exam is 5 Dec.
