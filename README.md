# Easy English Starter Kit — standalone website

A self-contained static port of the full "Easy English Starter Kit" Space
(v25, reconciled against the final Canva export), rebuilt so it can be
hosted on Olivia's own domain with no Muse branding and no Muse runtime
dependencies. Source: `~/workspace/ts-spaces/easy-english-starter-kit/`.

- **Intended host:** GitHub Pages (or any static host) at **book.thecuriousolive.co** — see the `CNAME` file in this folder.
- **Total size:** 20,117,895 bytes (~20 MB) before this README; 49 files including this README.
- **Structure:** `index.html` (all CSS and JS inline, exactly as the Space's page) + `assets/` (46 files: 32 MP3s, 1 MP4, 12 JPGs, 1 PDF) + `CNAME`.
- Works from `file://` or any static host: every reference is relative. The only external requests are Google Fonts (degrades gracefully offline) and outbound links (YouTube channel, Calendly, mailto).

## What was removed vs the Space

- **Proofread section** (`#proofread`) — the entire "final Canva edition" proofread report, plus the footer's link to it. The footer now simply presents the kit and the sample download.
- **The "Video clips & QR codes" production card** in Listen & Watch — it was a workflow explainer addressed to Olivia (record → upload unlisted → QR steps, "Clip library" status report, "this Space" framing). Replaced with a short learner-facing card keeping the "scan to listen" QR box.
- **Production notes inside the dialogue/drill content:**
  - The three `.dlg-note` paragraphs (Shopping "re-recorded clean…", Social Media "stumbled… clean second take", Cashier "answer your card" note).
  - The "Batch 2 session / split out, cleaned, and leveled" intro paragraph above the 18 dialogue cards — rewritten learner-facing.
  - "Batch 2" parenthetical in the Listen & Watch player card; "Batch 3" heading and session wording above the second drill set.
  - Word Stress drill: the sentence "Olivia's own note: she thinks she stumbled a little on this one — a fresh take can replace it anytime."
  - Listen & Watch intro: the "same clips the QR codes in the Canva book will point to / record once, use it in two places" production sentences.
  - Airport dialogue note: the "same clip the QR code in the printed kit will point to" sentence.
  - Nina & Pip: the "can also be uploaded unlisted to your channel…" production sentence, and the final episode card's record/upload workflow text (rewritten learner-facing; its link now points to the dialogues).
- **Title** changed to "Easy English Starter Kit — Korea Edition | Olivia Patterson". Sample-download buttons no longer say "updated".

Everything else is byte-for-byte the Space's content: hero, contents, all 50
vocabulary cards with Listen buttons, the 10-page viewer, all 20 dialogues
with players, all 11 pronunciation drills (including the fixed TH drill,
0:43), Nina & Pip with the playable episode, the maker panel, the
"Where the kit could go next" ideas panel (kept: it is public-facing
showcase content, not addressed to Olivia), About the Author with the
Canva bio wording, and the "Keep practicing with me!" block (YouTube
@OliviaTeachesEasyEnglish, calendly.com/oliviateaches,
oliviateaches355@gmail.com). The welcome player uses the full Space's own
welcome file (`welcome-take-2.mp3`, 0:20), as in the Space.

## Assets not copied (not referenced by the page)

- `welcome-take-1.mp3` — unused alternate take (the page plays take 2 only).
- `page-dialogue.jpg`, `page-stress.jpg` — present in the Space's assets but referenced nowhere in its page (the viewer uses 10 pages), so left out.
- `icon.webp`, `space.json`, `AGENTS.md`, `.harness/`, `.space-build*/`, `audits/` — Space platform files, not website content.

## Image handling

All kit page images were already web-sized (≤1688×2110, 130–360 KB each) and
are copied unchanged. One exception: `nina-pip.jpg` was 1920 px wide, so it
was resized to 1688×1125 at JPEG quality 80 to meet the size cap.

## Verification performed

- Every local `src`/`href` (37) and every `assets/…` path appearing anywhere in the HTML, including the JS viewer and card data, resolves to an existing file in this folder.
- All 32 labelled audio clips: file exists and its ffprobe duration, rounded to the nearest second, equals the on-page label (welcome 0:20, dialogues 0:08–0:14, drills 0:11–0:55). The Nina & Pip video measures 0:33, matching its "33 seconds / 0:33" labels.
- Visible text grep: no British spellings (organised, practise, favourite, colour, finalise), no "187", no "proofread", no "Batch", no "this Space".
- Raw HTML grep: zero occurrences of "muse" or "hatch" anywhere (text, metadata, comments, code). Title is "Easy English Starter Kit — Korea Edition | Olivia Patterson".
- Section tags balanced (9 open / 9 close) after the proofread-section removal.
- The bundled sample PDF is the corrected 15-page sample: 15 pages, last page is the About the Author page (kit p193) with the "Bachelor's Degree in English" wording.

## Could not be ported / notes

- Nothing failed to port. The Space was already a fully static page (no
  widget-state bridge or Muse runtime calls were present in its source), so
  no functionality was lost in the port.
- The Listen buttons and the "two computer voices" dialogue player use the
  browser's built-in speech synthesis, as in the Space; they work on
  `file://` and any host, with no external service.
- Deployment itself (pushing this folder to GitHub Pages and pointing the
  `book` subdomain's DNS at it) is not done here — this folder is the
  deployable artifact.
