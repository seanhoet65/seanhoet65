<div align="center">

# Sean Hoet

*Sales background. Analytics degree. Builds things in between.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/seanhoet)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:seanamir.hoet@alumni.esade.edu)
![Barcelona](https://img.shields.io/badge/📍-Barcelona-lightgrey?style=flat-square)

</div>

---

MSc Business Analytics at ESADE, focused on ML pipelines and agentic AI systems. Most of
what I build ends up as something you can actually click — a deployed endpoint, a
dashboard, a demo — because a model nobody can interact with is a hard thing to argue for.

My capstone was a fraud-detection system for a payments company (written up below). The
rest of the projects here are my own, and each one has a live demo or a written-up finding
rather than just a repo full of code.

---

## Projects

| | Project | What it does |
|---|---|---|
| 🏭 | **[Forging Line Cycle-Time Analysis](https://github.com/seanhoet65/cloud_aws_final_asnm)** | ~1.4M raw PLC sensor signals off a steel forging line → a Postgres medallion pipeline under Flyway migrations → an XGBoost model that predicts a piece's quench-bath time 18 seconds into a 58-second cycle, so a delay can be flagged while the piece is still moving. Deployed two ways: a SageMaker real-time endpoint and a containerised dashboard on ECS Fargate. |
| 🎬 | **[MovieLens Recommender](https://github.com/seanhoet65/movielens-recommender-prototype)** · [live demo](https://movielens-recommender-prototype.streamlit.app/) | Eleven recommendation algorithms — from a random baseline up to an SVD + content-based hybrid — compared side by side on the same user. Scored on coverage, novelty, diversity and popularity bias as well as accuracy, because a recommender tuned only for accuracy just shows everyone the same popular films. Includes a filter-bubble simulation. |
| 🎯 | **[Career Bridge](https://github.com/seanhoet65/career-bridge)** · [live demo](https://skillgapanalyzer-miba.streamlit.app/) | Scores a CV against a target role, ranks what's missing by importance, and builds a learning roadmap ordered by return per hour of study. The chat advisor is an LLM with six Python tools wired to it, so the numbers it quotes are computed rather than guessed. |
| 🏘️ | **[Antwerp Airbnb Analysis](https://github.com/seanhoet65/antwerp-airbnb-analysis)** | The neighbourhoods that charge the most earn the least — price and occupancy pull in opposite directions across the city (r = −0.38), and the priciest district earns roughly a fifth of the best performer. One script regenerates every chart from the raw data. |
| 💸 | **[Talk To Your Finances](https://github.com/seanhoet65/talk_to_your_finances)** | Conversational personal-finance app, four-person team. I built the foundation and data layer — the type system, mock data, LLM client, and the context builder that assembles what the model actually sees. |

---

## Capstone — fraud detection for a payments business

Five-person MSc capstone with an industry partner, under NDA. Written up here at the level
the client agreed to: **no company name, data, code, or results.**

The problem was alert quality. The existing system flagged far more false positives than
real fraud, and since every alert costs an analyst's time to review, precision is a direct
cost driver rather than an abstract metric.

We built two complementary models rather than one. A gradient-boosted classifier scores
individual transactions. A second, graph-based model scores *merchants*, building a
card-to-merchant network and deriving features from its structure. That second view is the
interesting one: coordinated fraud spreads thin — many individually unremarkable
transactions across a set of merchants — and that is a pattern per-transaction scoring
structurally cannot see, no matter how good the classifier gets.

**My contributions:** the feature-engineering pipeline and its leakage controls, the
temporal validation strategy, benchmarking gradient-boosting implementations against each
other, and the hyperparameter search behind the final transaction model. I also built and
evaluated a sequence-model variant that we ended up rejecting — it lost cleanly to the
tree-based approach, and reporting that honestly was worth more than quietly dropping it.

**Methods and tooling:** gradient-boosted trees, graph feature extraction, calibrated
neural networks, strictly chronological splits with expanding-window out-of-time
validation, SHAP for per-decision explanations, and an LLM tool-calling layer giving
analysts a plain-language interface to the scoring models.

---

## Stack

```
Languages   Python · SQL · R
ML          XGBoost · LightGBM · CatBoost · PyTorch · scikit-learn · SHAP
Data        pandas · NumPy · PostgreSQL · Flyway · Parquet
Apps        Streamlit · FastAPI · Plotly
Cloud       AWS (SageMaker, ECR, ECS Fargate, S3) · Docker
Tooling     Git · Jupyter · uv · pytest
```

---

## Background

Grew up between Belgian and Malaysian cultures, mostly in Shanghai. Went to university in
Melbourne. Now based in Barcelona. Speak English natively, Mandarin at HSK4 (B2), and
getting there with Spanish.

Before analytics: 2+ years in sales, 6 months as a student consultant at EY on a SaaS
go-to-market project. The sales background isn't a detour — understanding what someone
actually needs is more useful than most people give it credit for in a technical role.

Outside of work: produce and mix original music in Ableton, PADI-certified advanced scuba
diver. The latter has taken me to some good places.

---
