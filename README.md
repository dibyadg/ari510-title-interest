# What Makes a Title Interesting?

Predicting Human Interest Across Content Domains Using Machine Learning

**Team:** Adithi Sunke, Bindu Shahi, Dibya Gyawali

**Course:** ARI 510 – Fall 2026

**University:** University of Michigan-Flint

---

## Task Overview

We predict how interesting a content title is using a 1–6 Likert scale and identify which clickbait tactics the title uses.

Our dataset contains titles from four content domains:

- YouTube
- Reddit
- Articles
- Podcasts

The goal is to investigate whether patterns associated with human interest and clickbait transfer across different content domains.

---

## Dataset

- **Total collected:** 638 English titles
- **Domains:** YouTube, Reddit, Articles, Podcasts
- **Format:** CSV
- Each row represents one content title.

### Dataset Columns

| Column | Description |
|--------|-------------|
| `title_id` | Unique identifier for the title |
| `title` | Text of the content title |
| `domain` | Content domain: YouTube, Reddit, Article, or Podcast |
| `source` | Platform/source from which the title was collected |
| `source_id` | Original identifier provided by the source |
| `url` | URL associated with the original content |

### Dataset Link

[Google Drive](https://drive.google.com/file/d/1HVghd9onHMDDt1a4nk5TVvfbpOO4RWs9/view?usp=drive_link)

### Collection Dates

October 2026

### Sampling Procedure

- **YouTube:** YouTube Data API v3, mostPopular chart, English-speaking regions
- **Reddit:** Reddit RSS, r/all, multiple sort endpoints
- **Articles:** Google News RSS, random English word queries
- **Podcasts:** iTunes Search API, random search terms

Per-domain counts:

| Domain | Count |
|--------|-------|
| Article | 199 |
| Podcast | 172 |
| Reddit | 160 |
| YouTube | 107 |
| **Total** | **638** |

### Missing Data

No known missing data. All 638 titles have a title, domain, source, and URL.

### English Filter

Titles were filtered to English using `langdetect`. The following were removed:

- Symbol-only titles
- Emoji-only titles
- Titles with fewer than 3 words
- Non-English titles

---

## Annotation Design

The annotation setup contains a **shared agreement set** and a **distributed unique set**.

### Common Set

30 titles are labeled by all five annotators. This allows us to measure inter-annotator agreement and derive ground truth.

### Unique Set

Each annotator labels an additional 20 unique titles. This increases overall coverage.

### Per-Annotator Workload

- 30 common titles
- 20 unique titles
- **50 titles total**

With five annotators:

- 250 total annotations
- 30 common titles labeled by all 5 annotators

---

## Labels

### Interest (1–6 Likert)

| Score | Meaning |
|-------|---------|
| 1 | Very unlikely to consume |
| 2 | Unlikely to consume |
| 3 | Slightly unlikely to consume |
| 4 | Slightly likely to consume |
| 5 | Likely to consume |
| 6 | Very likely to consume |

### Clickbait Tactics (multi-label)

- **Missing details** — important information is withheld
- **Emotional** — strong emotional language
- **Exaggeration** — exaggerated or sensational claim
- **Curiosity gap** — creates an unanswered question about the outcome
- **Direct address** — speaks directly to the reader ("you")
- **None** — none of the listed tactics apply

---

## Estimated Annotation Time

~45–60 seconds per title. Each annotator labels 50 titles (~1 hour total).

---

## Annotation Guidelines

Complete annotation instructions:

[guidelines.md](guidelines.md)

---

## Annotation Interface

We use Potato.

- Config: [config.yaml](config.yaml)
- Deployment: Cloudflared tunnel

---

## Ground Truth

For the common set:

- **Ground truth** = mean of 5 Likert scores
- **Disagreement** = variance across annotators
- **Evaluation** = on common set only

---

## Tools

- YouTube Data API v3
- Reddit RSS
- Google News RSS
- iTunes Search API
- langdetect
- Potato
- Cloudflared
- GitHub

---

## Changes from Proposal

See [changes_from_proposal.md](changes_from_proposal.md).

---

## License

CC BY 4.0 — see [LICENSE](LICENSE).
