# AGENTS.md — Lion Calculator (מחשבון הארי המקטר)

Extends `~/Projects/Bachar_Israeli_Lab/Itzik_Lab/AGENTS.md` (Lab brief).

Canonical brief: **[`PRODUCT_STATE.md`](./PRODUCT_STATE.md)**.

A single-page satirical Hebrew quiz. Plain HTML, no build step.

---

## Build / Test / Run

| Task | Command |
|------|---------|
| Local dev | Open `index.html` in a browser |
| Build | `docker build -t lion-calculator .` |
| Tests | none |
| Deploy | `cloudbuild.yaml` — docker build → push → `gcloud run deploy lion-calculator` (`europe-west1`) |

---

## Project structure

```
index.html   RTL UI (Rubik font), full app inline:
             - landing
             - multi-step quiz (CATEGORIES drives the questions / points / gradients)
             - results screen with per-category breakdown
             - GoatCounter analytics snippet at the bottom
Dockerfile   nginx:alpine + index.html
nginx.conf   Static :8080 + /health
cloudbuild.yaml
```

---

## Code rules

- **One file.** All HTML/CSS/JS lives in `index.html`. Edit it directly.
- **Add a category** by appending to the `CATEGORIES` array (questions,
  points, gradients).
- **Hebrew RTL** + satirical tone — copy the surrounding voice.
- **GoatCounter** is the only external script.

## Restrictions

- Don't introduce a build pipeline.
- Don't add server logic — this is a client-only joke quiz.
- Don't ship analytics that send PII (GoatCounter does not collect PII; keep
  it that way).
- Sensitive politically-themed content — be careful before changing copy if
  you don't get the cultural context.

## Require approval before

- Changing the GoatCounter site (`itzikbachar.goatcounter.com`).
- Switching off Cloud Run.

---

## Subagents

No per-product PM yet. Route through the Lab's generic Product Manager
(`.lab/agents/product-manager.md`) with `Project: lion_calculator`.
