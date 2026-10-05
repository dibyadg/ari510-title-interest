# What Makes a Title Interesting?

Predicting Human Interest Across Content Domains Using Machine Learning

**Team:** Adithi Sunke, Bindu Shahi, Dibya Gyawali

**Course:** ARI 510 – Fall 2026, University of Michigan-Flint

## Task Overview

We predict how interesting a content title is (Likert 1–6) and which
clickbait tactics it uses, across 4 domains: YouTube, Reddit, Articles,
and Podcasts. We test whether patterns transfer across domains.

## Dataset

- **Total collected:** 638 English titles
- **Domains:** YouTube, Reddit, Articles, Podcasts
- **Format:** CSV with columns `title_id`, `title`, `domain`, `source`, `source_id`, `url`
- **License:** CC BY 4.0

**Dataset link:** 

### Sources

| Domain | Source | Method |
|--------|--------|--------|
| YouTube | YouTube Data API v3 | mostPopular chart, English-speaking regions |
| Reddit | Reddit RSS | r/all, multiple sort endpoints |
| Articles | Google News RSS | random English word queries |
| Podcasts | iTunes Search API | random search terms |

### English Filter

Titles were filtered to English only using `langdetect`. Symbol-only and
emoji-only titles were removed. Titles with fewer than 3 words were removed.

## Annotation Design

- **Common set:** 30 titles (all 5 annotators label these)
- **Unique set:** 100 titles (20 per annotator, 5 per domain)
- **Each annotator:** 50 titles (30 common + 20 unique)
- **Total annotations:** 250

### Labels

- **Interest:** Likert 1–6 (1 = Very unlikely, 6 = Very likely)
- **Clickbait tactics:** Multi-label (missing details, emotional, exaggeration, curiosity gap, direct address, none)

### Ground Truth

- **Common set:** Mean of 5 Likert scores = ground truth
- **Disagreement:** Variance across annotators
- **Evaluation:** On common set only

## Tools

- **Annotation interface:** Potato
- **Config:** `config.yaml`
- **Deployment:** Cloudflared tunnel

## License

CC BY 4.0 — see [LICENSE](LICENSE)
