# Home: starting-screen prototype

**Design question:** Which starting screen best combines a quick life overview with finding household knowledge?

This is a throwaway UI exploration, not a production implementation. All records are invented. No accounts, credentials, personal data, APIs, database, persistence, telemetry, or third-party assets are used.

## Selected direction\n\nAntonio selected **B — Domain dashboard** on September 27, 2026. The three variants remain for comparison, but further prototyping should deepen B rather than continue treating A/B/C as equally open.\n\n## Compare three structures

- **A — Daily brief:** decisions and waiting items first, with household lookup below and upcoming context alongside.
- **B — Domain dashboard:** navigate Housebook, Projects, Commitments, and Systems through a domain rail and overview tiles.
- **C — Searchable index:** keyword search and grouped records across all domains.

Each variant exposes the same underlying fictional records. Open a record to inspect its evidence and related household/project context. The intentionally stale calendar example covers assistant-managed commitments only; it is not an availability calendar. A sample reading delivery distinguishes provider acceptance from device receipt.

## Run

Open `home-navigation.html` directly in a browser, or serve the repository root:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/prototype/home-navigation.html?variant=A`.

Use the floating arrows to cycle A/B/C. The `variant` query parameter selects the initial variant when served. Keyboard arrows cycle only when focus is outside text-entry controls. Changes live in memory and reset on refresh.

## Review tasks

1. Find a decision needing attention.
2. Find the ventilation unit's fictional replacement-filter size.
3. Determine whether the displayed calendar information is current.

Compare the layouts by these tasks, not just appearance. No direction has yet been selected or validated by the owner.

## Verification — 2026-09-27

Chromium DOM-content rendering checked all three variants at 375, 390, and 1280 CSS-pixel widths. A mobile layout overflow was corrected. Search, record details, related-record navigation, variant switching/wraparound, and text-input keyboard behavior passed. No JavaScript page errors or external network requests were observed in this check.

Limitations: this was embedded browser rendering, not a live HTTP deployment. The runtime blocked file and localhost navigation; query-parameter reload behavior on a served origin was not exercised. Actual iPhone/Safari/WebKit behavior remains unverified. The connected Vercel deployment action returned `Tool deploy_to_vercel not found`; no hosted preview was created.

## Method and lifecycle

Used Matt Pocock's **prototype** skill, specifically its **UI** workflow, read from upstream source rather than claimed as an installed ChatGPT skill:

- https://github.com/mattpocock/skills/blob/main/skills/engineering/prototype/SKILL.md
- https://github.com/mattpocock/skills/blob/main/skills/engineering/prototype/UI.md

The standalone-page shape is appropriate because this repository had only an initial README and no existing application page. This study deliberately uses plain HTML/CSS/JavaScript to avoid production-framework provisioning. It does not change the proposed production stack.

Keep the runnable exploration on `prototype/home-navigation`, out of `main`. Record the selected direction and rationale after review, then implement it with production engineering practices; do not merge this prototype wholesale into production.
