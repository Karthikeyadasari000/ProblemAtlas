# AI Learning Roadmap 2026

A structured 6-month path from zero to job-ready AI skills — updated for 2026.

---

## What is AI

**Artificial Intelligence (AI)** is the field of building systems that perform tasks that normally require human intelligence: recognizing patterns, understanding language, making decisions, and learning from data.

In 2026, AI usually means one or more of these:

| Layer | What it is | Examples |
|-------|------------|----------|
| **Classical ML** | Models trained on data with explicit features | Regression, random forests, XGBoost |
| **Deep Learning** | Neural networks with many layers | CNNs, RNNs, Transformers |
| **Generative AI** | Models that create text, images, audio, code | GPT-class LLMs, diffusion models, multimodal agents |
| **AI Systems** | End-to-end products combining models + software | RAG pipelines, agents, copilots, autonomous workflows |

**Core subfields:**

- **Machine Learning (ML)** — learning from data without hard-coded rules  
- **Deep Learning (DL)** — ML using neural networks  
- **Natural Language Processing (NLP)** — text and speech  
- **Computer Vision (CV)** — images and video  
- **Reinforcement Learning (RL)** — learning via reward and trial  
- **MLOps / AI Engineering** — deploying, monitoring, and scaling models in production  

**How it works (simplified):**

```
Data → Preprocessing → Model Training → Evaluation → Deployment → Monitoring
```

You do not need a PhD to build useful AI. Most industry roles focus on **applying** models (APIs, fine-tuning, RAG, agents) rather than inventing new architectures.

---

## Why Learn AI

### Market demand
- AI-related roles (ML engineer, data scientist, AI engineer, prompt engineer, MLOps) remain among the fastest-growing tech careers in 2026.  
- AI skills amplify almost every role: software engineering, product, design, marketing, finance, healthcare, research.

### Practical impact
- Automate repetitive knowledge work (drafting, summarization, classification).  
- Build products users actually want: search, chatbots, recommendations, code assistants.  
- Make better decisions with data-driven predictions.

### Intellectual payoff
- Combines math, programming, statistics, and domain knowledge.  
- Teaches you to think in terms of **uncertainty**, **experiments**, and **iterative improvement** — useful beyond AI.

### Accessibility in 2026
- Free courses, open-source libraries (PyTorch, Hugging Face), and cloud credits lower the barrier.  
- Pre-trained models (LLMs, vision models) let beginners ship real projects in weeks, not years.

---

## Beginner Stage (0–30 Days)

**Goal:** Python fluency, basic math, first ML model, and one small AI-powered project.

### Skills

| Area | What to learn |
|------|----------------|
| **Python** | Variables, loops, functions, lists/dicts, file I/O, `venv`, pip |
| **Data handling** | NumPy, Pandas, basic plotting (Matplotlib / Seaborn) |
| **Math (essentials)** | Algebra, functions, basic calculus intuition, mean/variance, linear regression idea |
| **Statistics** | Probability basics, distributions, train/test split, overfitting concept |
| **ML fundamentals** | Supervised vs unsupervised, classification vs regression, scikit-learn workflow |
| **Tools** | Jupyter Notebook or Google Colab, Git basics, README writing |
| **AI literacy** | What LLMs are, tokens, prompts, limitations (hallucinations, bias) |

### Resources

| Resource | Type | Link / Notes |
|----------|------|----------------|
| **Python for Everybody** (Dr. Chuck) | Course | [py4e.com](https://www.py4e.com/) |
| **Kaggle Learn — Python** | Micro-course | [kaggle.com/learn/python](https://www.kaggle.com/learn/python) |
| **Kaggle Learn — Pandas** | Micro-course | [kaggle.com/learn/pandas](https://www.kaggle.com/learn/pandas) |
| **3Blue1Brown — Linear Algebra** | Video series | YouTube: essence of linear algebra |
| **StatQuest (Josh Starmer)** | YouTube | ML concepts explained simply |
| **scikit-learn documentation** | Docs | [scikit-learn.org](https://scikit-learn.org/stable/user_guide.html) |
| **fast.ai — Practical Deep Learning** (Part 1, first lessons) | Course | [course.fast.ai](https://course.fast.ai/) — skim after week 2 |
| **Google Colab** | Environment | Free GPU notebooks |

### Projects

1. **Titanic Survival Predictor** — classification with scikit-learn; practice train/test split and accuracy.  
2. **House Price Explorer** — regression on a public dataset; visualize features vs price.  
3. **Personal Data Dashboard** — analyze your own CSV (steps, expenses, habits); Pandas + charts.  
4. **Prompt + API Mini Chat** — call an LLM API (OpenAI, Anthropic, or free tier) from a 50-line Python script.  
5. **Kaggle submission** — complete one “Getting Started” competition (e.g., Titanic or Spaceship Titanic).

**Exit criteria:** You can load a CSV, train a model in scikit-learn, interpret basic metrics, and explain overfitting in your own words.

---

## Intermediate Stage (30–90 Days)

**Goal:** Deep learning fundamentals, NLP or CV specialty, experiment tracking, and one portfolio-grade project.

### Skills

| Area | What to learn |
|------|----------------|
| **Deep Learning** | Tensors, autograd, training loops, loss functions, optimizers (SGD, Adam) |
| **PyTorch** | `nn.Module`, DataLoader, GPU training, saving/loading checkpoints |
| **Neural architectures** | MLPs, CNNs (vision), Transformers (high-level), embeddings |
| **NLP (choose one track)** | Tokenization, fine-tuning with Hugging Face, RAG basics, evaluation |
| **CV (alternate track)** | Image classification, transfer learning (ResNet, ViT) |
| **Experimentation** | Train/val/test, cross-validation, hyperparameters, Weights & Biases or MLflow |
| **Data engineering lite** | Cleaning pipelines, feature stores concept, SQL for analytics |
| **LLM applications** | Prompt design, structured outputs, chunking, vector DBs (Chroma, FAISS, pgvector) |
| **Ethics & safety** | Bias, privacy, PII handling, responsible AI guidelines |

### Resources

| Resource | Type | Notes |
|----------|------|-------|
| **fast.ai — Practical Deep Learning** | Course | Top-down, project-first |
| **DeepLearning.AI — Deep Learning Specialization** | Course | Andrew Ng; theory + practice |
| **Hugging Face Course** | Course | [huggingface.co/learn](https://huggingface.co/learn) |
| **PyTorch Tutorials** | Docs | [pytorch.org/tutorials](https://pytorch.org/tutorials/) |
| **Full Stack Deep Learning** (short course) | Course | Production-minded overview |
| **Papers With Code** | Reference | SOTA models and benchmarks |
| **LangChain / LlamaIndex docs** | Docs | RAG and agent patterns (pick one framework) |

### Projects

1. **Fine-tuned Text Classifier** — sentiment or topic classification with a small transformer (DistilBERT).  
2. **RAG Q&A over Your Docs** — PDF/Markdown ingestion, chunking, embeddings, retrieval + LLM answer.  
3. **Image Classifier with Transfer Learning** — custom dataset (10+ classes), deploy with Gradio.  
4. **Kaggle tabular or NLP competition** — aim for top 50% then iterate features/model.  
5. **End-to-end ML notebook → API** — FastAPI endpoint serving your model; Docker optional.  
6. **Experiment report** — document 3+ hyperparameter runs with metrics tables and conclusions.

**Exit criteria:** You can train a neural network in PyTorch, fine-tune a Hugging Face model, build a simple RAG app, and write a technical blog post explaining your approach.

---

## Advanced Stage (90–180 Days)

**Goal:** Production AI systems, specialization, research literacy, and interview-ready portfolio.

### Skills

| Area | What to learn |
|------|----------------|
| **MLOps** | CI/CD for ML, model versioning (DVC), monitoring, drift detection |
| **Scaling** | Batch vs real-time inference, caching, quantization, LoRA/QLoRA fine-tuning |
| **Agents & orchestration** | Tool use, planning, multi-step workflows, guardrails |
| **Evaluation** | LLM benchmarks, human eval, RAGAS-style metrics, A/B tests |
| **Cloud** | One provider deeply (AWS SageMaker, GCP Vertex, or Azure ML) |
| **Systems design** | Latency, cost, reliability, fallbacks, rate limits |
| **Research skills** | Read arXiv papers, reproduce small results, implement ablations |
| **Specialization** | Pick 1–2: NLP/LLMs, CV, RL, recsys, bio/medical AI, robotics |

### Resources

| Resource | Type | Notes |
|----------|------|-------|
| **Made With ML — MLOps** | Course / book | [madewithml.com](https://madewithml.com/) |
| **Full Stack Deep Learning** | Course | Production and team practices |
| **DeepLearning.AI — LLMOps / Gen AI courses** | Short courses | Deployment and application patterns |
| **Chip Huyen — Designing Machine Learning Systems** | Book | Industry system design |
| **Stanford CS229 / CS231n / CS224n** (lecture playlists) | University | Pick aligned with specialty |
| **NeurIPS / ICML / ACL proceedings** | Papers | Skim; deep-read 1 paper/month |
| **Open-source contributions** | Practice | Hugging Face, LangChain, PyTorch ecosystem |

### Projects

1. **Production RAG or Agent Service** — auth, logging, eval suite, cost tracking, deployed on cloud.  
2. **Fine-tune + Evaluate an LLM** — LoRA on domain data; compare base vs fine-tuned with held-out Q&A set.  
3. **MLOps pipeline** — automated retraining trigger, model registry, monitoring dashboard.  
4. **Open-source contribution** — bug fix or small feature in an ML library you use.  
5. **Capstone with write-up** — problem, data, baselines, architecture, results, limitations, future work (README + demo video).  
6. **Mock system design** — design YouTube recommendations, fraud detection, or copilot backend (diagram + tradeoffs doc).

**Exit criteria:** You can design, deploy, and monitor an AI feature; explain tradeoffs; and walk through 2–3 portfolio projects in a 30-minute technical interview.

---

## Best Free Courses

| Course | Provider | Best for | Link |
|--------|----------|----------|------|
| **Machine Learning** | Stanford / Andrew Ng (Coursera audit) | ML foundations | Coursera |
| **Practical Deep Learning for Coders** | fast.ai | Hands-on DL | [course.fast.ai](https://course.fast.ai/) |
| **Deep Learning Specialization** | DeepLearning.AI | Structured DL path | Coursera |
| **Hugging Face NLP Course** | Hugging Face | Transformers & NLP | [huggingface.co/learn](https://huggingface.co/learn) |
| **Kaggle Learn** | Kaggle | Python, ML, intro DL | [kaggle.com/learn](https://www.kaggle.com/learn) |
| **MIT 6.S191 Introduction to Deep Learning** | MIT | DL theory + labs | [introtodeeplearning.com](https://introtodeeplearning.com/) |
| **Google ML Crash Course** | Google | Tabular ML + TensorFlow intro | developers.google.com/machine-learning/crash-course |
| **LLM University** | Cohere / community | LLM apps | Search “LLM University Cohere” |
| **Microsoft Generative AI for Beginners** | Microsoft | Gen AI roadmap | GitHub: `microsoft/generative-ai-for-beginners` |
| **Made With ML** | Goku Mohandas | MLOps + engineering | [madewithml.com](https://madewithml.com/) |

> **Tip:** Finish one course end-to-end before starting three more. Depth beats certificate collecting.

---

## Best YouTube Channels

| Channel | Focus |
|---------|--------|
| **3Blue1Brown** | Math intuition (linear algebra, calculus, neural nets) |
| **StatQuest with Josh Starmer** | Statistics & ML concepts |
| **Andrej Karpathy** | Deep learning, LLMs, training from scratch |
| **Yannic Kilcher** | Paper breakdowns |
| **Two Minute Papers** | Research news & demos |
| **sentdex** | Python, ML, practical coding |
| **freeCodeCamp.org** | Full-length bootcamp-style courses |
| **Krish Naik** | ML/DL tutorials (beginner-friendly) |
| **AssemblyAI** | NLP, speech, developer tutorials |
| **Weights & Biases** | MLOps, experiment tracking |
| **AI Explained** | LLM news and concepts |
| **NeuralNine** | Python + ML projects |

---

## Best Books

| Book | Author | Level | Why read it |
|------|--------|-------|-------------|
| **Hands-On Machine Learning** | Aurélien Géron | Beginner → Intermediate | Scikit-learn + TensorFlow/PyTorch projects |
| **Python Machine Learning** | Sebastian Raschka | Beginner → Intermediate | Clear ML + DL foundations |
| **Deep Learning** | Goodfellow, Bengio, Courville | Intermediate → Advanced | Theory reference (free online) |
| **Designing Machine Learning Systems** | Chip Huyen | Advanced | Production ML architecture |
| **Natural Language Processing with Transformers** | Tunstall et al. | Intermediate | Hugging Face ecosystem |
| **Speech and Language Processing** | Jurafsky & Martin | Advanced NLP | Classic NLP textbook (free drafts online) |
| **Pattern Recognition and Machine Learning** | Bishop | Advanced | Probabilistic ML |
| **The Hundred-Page Machine Learning Book** | Burkov | Beginner | Quick conceptual map |
| **Artificial Intelligence: A Modern Approach** | Russell & Norvig | All levels | AI breadth (textbook) |

---

## Common Mistakes

| Mistake | Why it hurts | Fix |
|---------|--------------|-----|
| **Skipping Python fundamentals** | You fight syntax instead of learning ML | 2 weeks solid Python before heavy ML |
| **Tutorial hell** | No proof of skill | One project per fortnight; publish on GitHub |
| **Ignoring math entirely** | You cannot debug models or read papers | 30 min/day: linear algebra + stats basics |
| **Jumping straight to LLMs** | Weak ML foundations | Learn classical ML + one DL project first |
| **No validation strategy** | False confidence, leakage | Always hold out test set; use cross-validation |
| **Chasing every new model** | Shallow knowledge | Master one stack (e.g., PyTorch + Hugging Face) |
| **No documentation** | Employers cannot assess your work | README with problem, method, results, how to run |
| **Training on full data without a test set** | Overfitting illusion | Split before any preprocessing that learns from data |
| **Ignoring data quality** | “Garbage in, garbage out” | EDA first; clean labels and handle imbalance |
| **Not measuring business metrics** | Technically correct but useless | Define success: accuracy vs latency vs cost |
| **Copy-paste without understanding** | Fails in interviews | Reimplement core tutorial code from scratch once |
| **Neglecting ethics & security** | Legal/reputational risk | Learn PII handling, bias checks, prompt injection basics |

---

## AI Career Paths

```
                    ┌─────────────────┐
                    │   Data Analyst   │
                    └────────┬────────┘
                             │
         ┌───────────────────┼───────────────────┐
         ▼                   ▼                   ▼
┌────────────────┐  ┌────────────────┐  ┌────────────────┐
│ Data Scientist │  │  ML Engineer   │  │  AI Engineer   │
└───────┬────────┘  └───────┬────────┘  └───────┬────────┘
        │                   │                   │
        └───────────────────┼───────────────────┘
                            ▼
                   ┌────────────────┐
                   │  MLOps Engineer │
                   └────────┬───────┘
                            ▼
                   ┌────────────────┐
                   │  AI Architect  │
                   └────────────────┘
```

| Role | What you do | Key skills |
|------|-------------|------------|
| **Data Analyst** | Dashboards, SQL, reporting | SQL, Excel/BI, basic stats |
| **Data Scientist** | Experiments, models, insights | Python, ML, stats, storytelling |
| **ML Engineer** | Train and ship models | PyTorch/TF, feature pipelines, APIs |
| **AI Engineer** | LLM apps, RAG, agents | Prompting, embeddings, cloud, eval |
| **MLOps Engineer** | Deploy, monitor, scale | Docker, K8s, CI/CD, monitoring |
| **Research Scientist** | New methods, papers | Math, PyTorch, reading papers |
| **Prompt / Applied AI Specialist** | Product integration of LLMs | UX, eval, guardrails, domain knowledge |
| **AI Product Manager** | Roadmap, metrics, ethics | Domain + technical literacy |

**Salary drivers (general):** production experience > Kaggle medals; portfolio > certificates; communication > raw theory.

---

## 30-Day Action Plan

### Week 1 — Foundations
| Day | Task |
|-----|------|
| 1 | Install Python 3.11+, VS Code/Cursor, Git; create GitHub account |
| 2 | Python basics: variables, types, loops (2 hrs) |
| 3 | Functions, lists, dicts; 10 small exercises |
| 4 | NumPy arrays: shape, indexing, broadcasting |
| 5 | Pandas: load CSV, filter, groupby |
| 6 | Matplotlib: 3 charts from a public dataset |
| 7 | **Project:** Personal data or public CSV exploration notebook |

### Week 2 — Math & Statistics
| Day | Task |
|-----|------|
| 8 | 3Blue1Brown: vectors & matrices (2 videos) |
| 9 | Mean, median, variance; normal distribution intuition |
| 10 | Linear regression by hand + with scikit-learn |
| 11 | Train/test split, accuracy, confusion matrix |
| 12 | Overfitting vs underfitting; regularization concept |
| 13 | StatQuest: logistic regression video |
| 14 | **Project:** Predict Titanic survival (Kaggle starter) |

### Week 3 — Machine Learning
| Day | Task |
|-----|------|
| 15 | scikit-learn pipeline: fit, predict, evaluate |
| 16 | Try 2 classifiers (Logistic Regression, Random Forest) |
| 17 | Feature engineering on Titanic dataset |
| 18 | Cross-validation and hyperparameter basics |
| 19 | Kaggle Learn: Intro to ML (complete) |
| 20 | Read one ML blog post; summarize in 200 words |
| 21 | **Project:** Improve Titanic score; push to GitHub |

### Week 4 — AI Applications & Next Steps
| Day | Task |
|-----|------|
| 22 | What are LLMs? Tokens, context window, temperature |
| 23 | Build a CLI chatbot using an LLM API |
| 24 | Prompt engineering: system prompt, few-shot examples |
| 25 | Watch fast.ai Lesson 1 or Andrew Ng Week 1 |
| 26 | Join Kaggle + Hugging Face; star 5 repos to study later |
| 27 | Write portfolio README: goals, projects, stack |
| 28 | **Project:** Combine ML + LLM (e.g., classify reviews then summarize with LLM) |
| 29 | Mock explain: “How does supervised learning work?” |
| 30 | Plan days 31–60: pick NLP **or** CV track; enroll in one intermediate course |

### Daily habits (30 minutes minimum)
- [ ] Code every day (even 20 minutes counts)  
- [ ] One concept note in Obsidian/Notion/Google Doc  
- [ ] Weekly: push one commit to GitHub  

### End-of-month checklist
- [ ] 2+ projects on GitHub with READMEs  
- [ ] Comfortable with Pandas and scikit-learn  
- [ ] Can explain train/test split and overfitting  
- [ ] Built at least one LLM-powered script  
- [ ] Enrolled in intermediate course for month 2  

---

## Suggested 6-Month Timeline (Summary)

| Phase | Days | Focus |
|-------|------|--------|
| Beginner | 0–30 | Python, stats, scikit-learn, first projects |
| Intermediate | 30–90 | PyTorch, Hugging Face, RAG or CV, Kaggle |
| Advanced | 90–180 | MLOps, production, specialization, capstone |

---

## Final Advice

1. **Build in public** — GitHub, blog posts, or short demos beat passive consumption.  
2. **Specialize after month 3** — depth in one area gets you hired faster than shallow breadth.  
3. **Learn to evaluate** — metrics, error analysis, and user feedback separate professionals from hobbyists.  
4. **Stay current selectively** — follow 2–3 trusted sources; ignore hype cycles.  
5. **The best roadmap is the one you finish** — start today with Day 1 of the 30-day plan.

