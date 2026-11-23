# Dead Key — product steering (Kiro)

Dead Key is a single-button Morse communication app. One web app, runs on a phone in the browser, fully offline, no account, no server.

## Core rules (never break these)

- One screen, one button, one message area, one prediction row. No menus, no settings page.
- Short press = dot, long press = dash. Press under 300 ms = dot, 300 ms or over = dash (initial defaults; Phase 1 spike validates).
- Letter accepted after a 700 ms pause; word space after 1,500 ms.
- States: waiting, dot recorded, dash recorded, letter accepted, word predicted, message spoken.
- Prediction is a lookup from `wordlist.md`, top 3 matches, never a trained model.
- Morse data comes only from `morse-tables.json`. Arabic table is ITU-R M.1677-1, verified letter by letter — do not change a code without checking two sources.
- Arabic mode: right-to-left text, Arabic table, Arabic wordlist. Fold ة → ت, ى → ي, أ/إ/آ → ا. Ignore diacritics.
- Dark background (#0B0B0F), one bright accent (amber #FFB000). No text smaller than 18px. Everything tappable at least 56px tall.
- Every sound has a visual twin; every visual change has a sound twin. Works with volume off.
- A wrong Morse sequence shows "?" once and never blocks typing.
- The sound link (two phones by sound) is experimental and cut first if it fails. It must never block typing.
- Cut order if a day slips: sound link, learn exercises beyond the first set, Arabic prediction, extra punctuation/digits, visual polish beyond contrast/button size/readable text.
- Submission finished evening of 3 Dec 2026. 4 Dec is buffer only. CRMEF exam is 5 Dec.
