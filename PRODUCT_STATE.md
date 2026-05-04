# Product State — Lion Calculator (מחשבון הארי המקטר)

A Hebrew, mobile-friendly single-page quiz that scores satirical "steam vent"
(קיטור) points from life-situation answers, then shows a verdict and per-
category breakdown.

---

## Architecture

A single `index.html` served by nginx alpine on Cloud Run. All logic inline.

---

## Stack

| Layer | Tech |
|-------|------|
| App | One `index.html` (HTML + CSS + JS), Rubik font from Google Fonts |
| Analytics | GoatCounter (`gc.zgo.at` / `itzikbachar.goatcounter.com`) |
| Hosting | Cloud Run nginx alpine, port `8080`, `europe-west1` |

---

## Repo map

| Path | Purpose |
|------|---------|
| `index.html` | Entire app — landing, quiz, results, analytics snippet |
| `Dockerfile` | nginx + `index.html` |
| `nginx.conf` | Static `:8080`, `/health` |
| `cloudbuild.yaml` | Cloud Run deploy |

---

## Content

- **Landing** — animated lion theme.
- **Quiz** — sequential themed screens (safe room type, family status,
  war-damage humor, reserves, employment jokes, misc, politics) with point
  badges and a "לא רלוונטי" (not relevant) skip.
- **Results** — total נק״ט (points), emoji tier, Hebrew verdict, breakdown
  per category. "Restart" returns to landing.

`CATEGORIES` array in `index.html` defines questions, points, gradients.
There's an optional kids-count multiplier.

---

## External integrations

- Google Fonts (Rubik)
- GoatCounter analytics

---

## Critical files / invariants

- `index.html` — the entire product.
- `cloudbuild.yaml` + `Dockerfile` — production deploy.

---

## Known risks / gotchas

- **Satirical / political content** about Israel-specific situations.
  Sharing widely or rebranding requires understanding the audience and
  compliance context.
