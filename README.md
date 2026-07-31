<div align="center">

# Sean Hoet

*Sales background. Analytics degree. Builds things in between.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/seanhoet)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:seanamir.hoet@alumni.esade.edu)
![Barcelona](https://img.shields.io/badge/📍-Barcelona-lightgrey?style=flat-square)

</div>

---

MSc Business Analytics at ESADE, focused on ML pipelines and agentic AI systems. Most of
what I build ends up as something you can actually click — a dashboard, a demo, a chart
that answers something — because a model nobody can interact with is hard to argue for.

My capstone was a fraud-detection system for a payments company (written up below). The
rest of the projects here are my own, and each one has a live demo or a written-up finding
rather than just a repo full of code.

---

## Projects

| | Project | What it does |
|---|---|---|
| 🛡️ | **[Fraud Triage Economics](https://github.com/seanhoet65/fraud-triage-economics)** | Fraud courses teach you to optimise recall. On a real alert queue that can lose money on every alert — this works out where the profitable operating point actually is, and it's about a quarter of the review team's capacity. |
| 🍸 | **[Bar Layout Optimisation](https://github.com/seanhoet65/bar-layout-optimisation)** | Works out where a bartender should put the bottles, by building a network of which ingredients get used together. The layout it produces doubles as a staffing plan. R. |
| 🎬 | **[MovieLens Recommender](https://github.com/seanhoet65/movielens-recommender-prototype)** · [live demo](https://movielens-recommender-prototype.streamlit.app/) | Eleven recommendation algorithms compared side by side on the same user — scored on diversity and novelty, not just accuracy. |
| 🎯 | **[Career Bridge](https://github.com/seanhoet65/career-bridge)** · [live demo](https://skillgapanalyzer-miba.streamlit.app/) | Scores a CV against a target role and builds a learning roadmap ranked by return per hour of study. The chat advisor calls real Python tools, so its numbers are computed rather than guessed. |
| 💸 | **[Talk To Your Finances](https://github.com/seanhoet65/talk_to_your_finances)** · [live demo](https://talk-to-your-finances.vercel.app) | Conversational personal-finance app, four-person team. I built the data layer the LLM reasons over. |
| 🏘️ | **[Antwerp Airbnb Analysis](https://github.com/seanhoet65/antwerp-airbnb-analysis)** | The neighbourhoods that charge the most earn the least. One script regenerates every chart from the raw data. |

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

**What I actually took from it** was not a modelling lesson. Fraud detection is taught as a
recall problem — a missed fraud costs far more than a false positive, so catch everything.
That reasoning assumes reviews are close to free. When a capable review team is already
working the queue, the realistic contribution of a model isn't catching everything; it's
making the alerts that team already reviews more likely to be worth reviewing. That reframes
the target from recall to precision at a capacity bound, and it changes what "success" means.
I rebuilt that argument from scratch on synthetic data in
[Fraud Triage Economics](https://github.com/seanhoet65/fraud-triage-economics), so it can be
shown rather than described.

**Methods and tooling:** gradient-boosted trees, graph feature extraction, calibrated
neural networks, strictly chronological splits with expanding-window out-of-time
validation, SHAP for per-decision explanations, and an LLM tool-calling layer giving
analysts a plain-language interface to the scoring models.

---

## Stack

```
Languages   Python · SQL · R
ML          XGBoost · LightGBM · CatBoost · PyTorch · scikit-learn · SHAP
Networks    igraph · tidygraph · centrality · MDS
Data        pandas · NumPy · Parquet
Apps        Streamlit · FastAPI · Plotly · LLM tool-calling
Cloud       AWS (SageMaker, ECS Fargate, S3) · Docker
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
