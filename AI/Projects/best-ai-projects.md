Best AI Projects (2026)
The highest-impact AI projects for portfolios, internships, and job interviews — from first model to production systems. Each entry includes idea variations, architecture, evaluation, and implementation phases used by real teams.

How to use this guide: Pick 1 project per skill track, finish it end-to-end, then add a second from a different domain. Three excellent projects beat ten half-finished repos.

Related guides: 10 Beginner AI Projects · 20 Intermediate AI Projects

At a Glance
#	Project	Domain	Level	Time	Hire signal
1
Tabular ML Competition Pipeline
ML
Intermediate
1–2 wk
⭐⭐⭐⭐
2
Fine-Tuned Transformer Classifier
NLP
Intermediate
1 wk
⭐⭐⭐⭐
3
Production RAG Q&A System
LLM
Int–Adv
2–3 wk
⭐⭐⭐⭐⭐
4
Custom Vision API + Demo
CV
Intermediate
1–2 wk
⭐⭐⭐⭐
5
Object Detection (YOLO)
CV
Advanced
2 wk
⭐⭐⭐⭐
6
LoRA LLM Fine-Tune
LLM
Advanced
2 wk
⭐⭐⭐⭐⭐
7
LLM Agent with Tools
Agents
Advanced
2 wk
⭐⭐⭐⭐⭐
8
Semantic / Hybrid Search Engine
Embeddings
Intermediate
1 wk
⭐⭐⭐⭐
9
Churn or Fraud + Explainability
Tabular + XAI
Intermediate
1 wk
⭐⭐⭐⭐
10
Time Series Forecasting Service
TS
Intermediate
1–2 wk
⭐⭐⭐
11
Speech-to-Text + Summarization
Audio
Intermediate
1 wk
⭐⭐⭐
12
MLOps CI Training Pipeline
MLOps
Advanced
2 wk
⭐⭐⭐⭐⭐
13
LLM Eval & A/B Harness
Eval
Advanced
1 wk
⭐⭐⭐⭐
14
Capstone: End-to-End AI Product
Full stack
Advanced
3–4 wk
⭐⭐⭐⭐⭐
Choose by Goal
Your goal	Best projects (order)
ML engineer (tabular)
1 → 9 → 12
NLP / LLM engineer
2 → 8 → 3 → 6 → 7 → 13
Computer vision
4 → 5
MLOps / platform
12 → 3 → 14
Full-stack AI product
3 → 7 → 13 → 14
Student portfolio (fast)
1 → 2 → 4 → 3
Project 1: Tabular ML Competition Pipeline
Idea bank (pick one domain)
Idea	Dataset direction	Why it’s strong
Spaceship Titanic
Kaggle Getting Started
Clean intro to pipelines
Home Credit Default
Credit risk
Real imbalance + leakage lessons
Santander Customer Transaction
Banking
Feature creativity
Store Sales Forecasting
Retail TS-tabular hybrid
Seasonality features
IEEE-CIS Fraud Detection
Fraud
Extreme imbalance, time features
Insurance claim prediction
Healthcare/finance
Regulatory storytelling in README
Variations: ensemble-only repo; AutoML baseline vs hand-crafted features; explainability report for top features.

Description
Build a reproducible Kaggle-style workflow: EDA → feature engineering → cross-validated gradient boosting → submission. The portfolio value is process (leakage prevention, CV discipline, experiment log), not leaderboard rank alone.

Skills learned
Feature engineering, target encoding (inside CV folds only)
XGBoost / LightGBM / CatBoost
Stratified K-fold, metric selection (AUC, RMSE, log loss)
Config-driven experiments (YAML / Hydra)
Writing ablation tables and LB vs CV analysis
Tools needed
Tool	Purpose
Python, Pandas, scikit-learn
Baselines
LightGBM, XGBoost, CatBoost
Main models
Optuna
Hyperparameter search
Kaggle API
Submissions
YAML / Hydra
Reproducible configs
SHAP (optional)
Feature importance
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1–2 weeks

Architecture
data/raw → notebooks/EDA → src/features.py → src/train.py → models/
                ↓                                    ↓
         configs/experiment.yaml              submissions/submission.csv
Project structure
tabular-ml-pipeline/
├── configs/
│   ├── baseline.yaml
│   └── lgbm_v2.yaml
├── data/raw/                 # gitignored
├── notebooks/01_eda.ipynb
├── src/
│   ├── features.py
│   ├── train.py
│   └── predict.py
├── models/
├── submissions/
├── experiments.md            # ablation log
├── requirements.txt
└── README.md
Evaluation strategy
Metric	Use
Stratified K-fold CV
Primary tuning metric
Hold-out fold
Never touch until final report
Public LB
Secondary; document gap vs CV
Document 3+ experiments with params, CV score, and one-sentence hypothesis.

Implementation steps
Phase 1 — Data & EDA (days 1–2)

Download data; write leakage checklist (target in features? future info?).
EDA: missingness, class balance, correlations with target.
Phase 2 — Pipeline (days 3–5)
3. features.py: imputation, encodings, interactions, date parts.
4. Baseline LightGBM + 5-fold CV; log mean ± std.

Phase 3 — Iteration (days 6–9)
5. Optuna (≤50 trials); save best config to YAML.
6. Ensemble 2–3 models (average probabilities).

Phase 4 — Ship (days 10–14)
7. predict.py → submission.csv; Kaggle submit.
8. README: CV strategy, feature list, ablation table, LB lessons.

Stretch goals
GitHub Actions: lint + unit tests on features.py
SHAP summary for stakeholders
Pseudo-labeling (only if competition rules allow)
Project 2: Fine-Tuned Transformer Classifier
Idea bank
Idea	Labels	Notes
News topic classifier
4–10 classes
AG News, BBC
Intent detection
user intents
Chatbot routing
Toxic comment detection
binary / multi
Moderation
Email spam / phishing
binary
Security angle
Support ticket routing
department
Enterprise demo
Medical triage (public data only)
urgency
Extra care with ethics section
Variations: multi-label classification; multilingual (mBERT); distill large → small model for latency.

Description
Fine-tune DistilBERT or DeBERTa-v3-small for text classification with proper metrics, export, and a Gradio demo — the standard NLP portfolio piece in 2026.

Skills learned
Hugging Face datasets, Trainer, tokenizers
Learning rate warmup, early stopping, class weights
Macro-F1 for imbalance; confusion matrix per class
Model export + batch inference script
Tools needed
Tool	Purpose
transformers, datasets, evaluate
Training
PyTorch + GPU (Colab)
Compute
Weights & Biases
Experiment logs
Gradio
Demo UI
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1 week

Architecture
CSV/JSON → Tokenizer → DataLoader → Trainer → checkpoint/ → inference.py → Gradio
Project structure
text-classifier/
├── data/
├── configs/train.yaml
├── train.py
├── inference.py
├── app/gradio_app.py
├── eval/
│   └── test_metrics.json
├── requirements.txt
└── README.md
Evaluation strategy
Stratified 70/15/15 train/val/test — test touched once
Report: accuracy, macro-F1, per-class precision/recall
Error analysis: 20 misclassified examples bucketed by reason
Implementation steps
Load data; stratified splits; class distribution plots.
Tokenize (max_length 128–256); define metrics in Trainer.
Fine-tune 3–5 epochs; load_best_model_at_end on val F1.
Threshold tuning for multi-label (if applicable).
save_pretrained + inference.py for batch CSV scoring.
Gradio: text in → label + confidence bars.
README: hyperparameter table, failure cases, latency on CPU.
Stretch goals
ONNX export for CPU inference
Compare full fine-tune vs LoRA adapters
Adversarial test set (typos, slang)
Project 3: Production RAG Q&A System
Idea bank
Idea	Documents	User
Course notes assistant
PDFs / Markdown
Students
Company handbook Q&A
internal policies
HR demo (synthetic data)
Legal clause finder (public corpora)
contracts
Research assist only
API documentation copilot
OpenAPI + markdown
Developers
Medical FAQ (verified sources only)
CDC-style public pages
High-risk → disclaimers
GitHub repo Q&A
clone + chunk README/code
OSS maintainers
Variations: hybrid search (BM25 + vectors); multi-tenant collections; admin UI for re-ingest.

Description
End-to-end retrieval-augmented generation: ingest → chunk → embed → retrieve → generate with citations, plus eval set, API, and Docker — the flagship LLM engineering project.

Skills learned
Chunking (size, overlap, header-aware splits)
Vector DB (Chroma, pgvector, Qdrant)
Grounded prompts, citation formatting
RAG failure modes: missed retrieval, hallucination, stale docs
Latency and cost per query
Tools needed
Tool	Purpose
FastAPI
REST API
LangChain or LlamaIndex
Orchestration
OpenAI / Cohere / local embeddings
Vectors + LLM
Chroma / pgvector / Qdrant
Vector store
pypdf, unstructured
Parsing
RAGAS or custom eval
Quality metrics
Docker Compose
Local deploy
Difficulty & time
Intermediate–Advanced — ⭐⭐⭐⭐☆ · 2–3 weeks

Architecture
┌─────────┐    ┌──────────┐    ┌─────────────┐    ┌─────┐
│ Ingest  │───▶│ Chunker  │───▶│ Embedder    │───▶│ VDB │
└─────────┘    └──────────┘    └─────────────┘    └──┬──┘
                                                      │
User Query ──▶ Embed ──▶ Retrieve top-k ──▶ Prompt ──▶ LLM ──▶ Answer + cites
Project structure
rag-production/
├── app/
│   ├── main.py
│   ├── ingest.py
│   ├── retrieve.py
│   ├── prompts.py
│   └── auth.py              # optional API keys
├── eval/
│   ├── golden_qa.jsonl
│   └── run_eval.py
├── tests/
├── docker-compose.yml
├── .env.example
└── README.md
Evaluation strategy
Metric	Target
Retrieval recall@k
On golden set with known doc IDs
Answer faithfulness
Manual or LLM-judge on 30 Q&A pairs
Latency p50/p95
Per stage logged
“Not in documents”
5+ questions must correctly abstain
Implementation steps
Week 1 — Core RAG

PDF/Markdown → text + metadata (page, section).
Chunk (512 tokens, 64 overlap); embed; upsert to VDB.
Query pipeline: retrieve top-k → strict context prompt → answer + cite.
Week 2 — API & quality
4. FastAPI: /ingest, /query, health check.
5. Build golden_qa.jsonl (30+ pairs); run run_eval.py.
6. Iterate: hybrid search, reranker, or chunk size ablation.

Week 3 — Production polish
7. Rate limiting, structured logging, request IDs.
8. Docker Compose; .env.example; cost estimate per 1k queries.
9. README architecture diagram + 3-min demo video.

Stretch goals
Reranker (cross-encoder) after vector retrieval
Multi-user document namespaces
Regression CI: eval F1 must not drop on PR
Project 4: Custom Vision API + Demo
Idea bank
Idea	Classes	Deploy story
Plant disease detector
5–20 plants
Agriculture
PPE safety (helmet, vest)
safety gear
Workplace
Food freshness / type
dishes
Restaurant
Wildlife camera trap
species
Conservation
Defect inspection
scratch, crack, ok
Manufacturing QC
Sign language letters (starter)
A–Z limited
Accessibility demo
Description
Transfer learning on a custom image dataset with training notebook, saved weights, FastAPI inference, and Gradio/Streamlit demo — shows CV + deployment.

Skills learned
ImageFolder, augmentations, ImageNet normalization
Freeze → train head → partial fine-tune schedule
TorchScript or ONNX export
Inference API with image upload validation
Tools needed
Tool	Purpose
PyTorch, torchvision
Training
ResNet18 / EfficientNet-B0 / ViT-small
Backbone
FastAPI, python-multipart
API
Gradio
Quick UI
Docker (optional)
Deploy
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1–2 weeks

Architecture
images/train|val/ → train.py → model.pt → inference_api.py → Gradio
                              ↓
                         metrics.json
Evaluation strategy
Stratified split by class; report accuracy + macro-F1
Confusion matrix; per-class recall for rare classes
Test on phone photos not in training set
Implementation steps
Collect 50–200 images per class; train/val split.
Augmentations: flip, crop, color jitter (train only).
Train ResNet head → unfreeze last block; early stop on val F1.
Error gallery: 25 worst predictions.
FastAPI POST /predict returns label + probabilities.
Gradio wrapper; Dockerfile; README with sample images.
Stretch goals
Grad-CAM visualization for trust
Mobile-friendly ONNX + TFLite export
Active learning loop: flag low-confidence for relabel
Project 5: Object Detection (YOLO)
Idea bank
Idea	Objects
Parking lot occupancy
car, empty slot
Retail shelf gaps
product, empty
Road damage
pothole, crack
Aquarium / pet monitor
species
Sports ball tracking
ball, player
Document layout
table, figure, paragraph
Description
Fine-tune YOLOv8/v11 (Ultralytics) on a custom dataset with bounding boxes; export weights and run inference on video frames.

Skills learned
Labeling (CVAT, Roboflow); YOLO format
mAP, precision/recall per class
Video inference + simple tracking intro
Tools needed
Tool	Purpose
Ultralytics YOLO
Train + infer
Roboflow / CVAT
Labels
OpenCV
Video I/O
Colab GPU
Training
Difficulty & time
Advanced — ⭐⭐⭐⭐☆ · 2 weeks

Architecture
Roboflow export → data.yaml → train.py → runs/detect/ → predict.py (image/video)
Implementation steps
Label 200+ images (or use public Roboflow dataset).
Train nano/small model; monitor mAP50.
Inference on 30s video; save annotated output.
README: label stats, failure modes (occlusion, lighting).
Optional FastAPI: upload image → JSON boxes.
Stretch goals
Export TensorRT for edge
Counting line (vehicles per minute)
Hard-negative mining pass
Project 6: LoRA LLM Fine-Tune
Idea bank
Idea	Data
Domain Q&A (finance, legal summaries)
synthetic + curated Q&A JSONL
Code style adapter
your repos’ patterns
Tutor for one course
lecture Q&A pairs
Customer support tone
ticket → reply pairs
JSON extraction specialist
messy text → schema examples
Description
Fine-tune a 7B-class open model (Llama, Mistral, Qwen) with LoRA/QLoRA on domain instructions; compare base vs adapted on held-out eval set.

Skills learned
Instruction JSONL format; chat templates
LoRA rank, alpha, target modules
GPU memory tricks (4-bit, gradient checkpointing)
Qualitative + quantitative eval
Tools needed
Tool	Purpose
transformers, peft, trl
Fine-tune
bitsandbytes
QLoRA
Unsloth (optional)
Faster training
Weights & Biases
Logs
1× A100 or Colab Pro
GPU
Difficulty & time
Advanced — ⭐⭐⭐⭐☆ · 2 weeks

Architecture
JSONL (instruction, input, output) → Tokenize → SFTTrainer + LoRA → adapter/
                                                      ↓
                                            eval/compare_base_lora.py
Evaluation strategy
100+ held-out Q&A; exact match + LLM-judge score
Side-by-side samples in README
Track train loss vs human eval (avoid overfitting to loss)
Implementation steps
Curate 500–2k high-quality examples; dedupe.
Choose base model; format with correct chat template.
QLoRA train; save adapter only.
Merge or load adapter at inference; run eval script.
Gradio chat demo; document GPU RAM and training time.
Stretch goals
DPO pass on preference pairs
Merge adapters; push to Hugging Face Hub
vLLM serving benchmark
Project 7: LLM Agent with Tools
Idea bank
Idea	Tools
Research assistant
web search, summarize, cite
DevOps helper
run shell (sandbox), read logs
Data analyst agent
Python REPL, plot, CSV
Calendar / email stub
mock APIs for demo
GitHub issue triager
fetch issues, label suggestion
Personal finance (synthetic CSV)
pandas tool, chart
Description
An agent that plans, calls tools (search, calculator, code, DB), and returns a final answer with guardrails and step logging.

Skills learned
Tool schemas (JSON); ReAct / function-calling patterns
Timeouts, max steps, human-in-the-loop
Sandboxing untrusted code execution
Tools needed
Tool	Purpose
LangGraph or LangChain agents
Orchestration
OpenAI / Anthropic function calling
LLM
Docker sandbox / E2B
Safe code run
Tavily or SerpAPI (optional)
Search
Difficulty & time
Advanced — ⭐⭐⭐⭐☆ · 2 weeks

Architecture
User → Planner LLM → [Tool loop: select → execute → observe]* → Final answer
                           ↓
                    trace.json (audit log)
Implementation steps
Define 3–5 tools with strict input schemas.
Implement agent loop with max 10 steps and 60s timeout.
Log every tool call + observation to trace.json.
Golden tasks: 15 scenarios with expected tool sequence.
Guardrails: block PII patterns; refuse destructive shell.
Streamlit UI showing thought trace (collapsible).
Stretch goals
Human approval before run_shell
Memory across sessions (vector store)
Cost cap per session
Project 8: Semantic / Hybrid Search Engine
Idea bank
Idea	Corpus
Personal notes search
Markdown vault
Job listing matcher
job posts + resume
Stack Overflow for one tag
archived Q&A
Product catalog
e-commerce descriptions
Research paper finder
arXiv abstracts
Code snippet search
your repos
Description
Build embedding search with optional BM25 hybrid and filters; expose REST API and simple UI.

Skills learned
Embedding models; cosine similarity
Chunking long documents; metadata filters
Hybrid retrieval fusion
Tools needed
Tool	Purpose
sentence-transformers or API embeddings
Vectors
FAISS / Chroma
Index
rank_bm25 (optional)
Keyword leg
FastAPI + minimal React/HTMX
UI
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1 week

Implementation steps
Ingest corpus; chunk; embed; build FAISS index.
Query endpoint: embed query → top-k + snippets.
Add BM25; reciprocal rank fusion.
Eval: 20 queries with expected doc in top-3.
README: recall@k table before/after hybrid.
Stretch goals
Cross-encoder rerank top-20
Incremental index updates
Multilingual embeddings
Project 9: Churn or Fraud + Explainability
Idea bank
Idea	Problem type
Telco churn
binary classification
Credit card fraud
extreme imbalance
Subscription cancellation
uplift modeling intro
Insurance claim fraud
tabular + rules
Employee attrition
HR analytics (synthetic)
Description
High-stakes tabular problem with XGBoost, proper imbalance handling, and SHAP explanations for stakeholders.

Skills learned
PR-AUC, precision at k, cost-sensitive thresholds
SHAP summary and force plots
Business framing: cost of false positive vs false negative
Tools needed
Tool	Purpose
XGBoost / LightGBM
Model
imbalanced-learn
Resampling (careful)
SHAP
Explainability
Streamlit
Dashboard
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1 week

Implementation steps
EDA + baseline logistic regression.
Train GBM with stratified CV; optimize PR-AUC.
Threshold selection for business cost matrix.
SHAP on 100 hold-out rows; interpret top features.
Streamlit: upload row → score + explanation plot.
Stretch goals
Fairness audit across demographic groups (if ethical to include)
Calibration plot (Platt scaling)
Monitored drift simulation on feature shift
Project 10: Time Series Forecasting Service
Idea bank
Idea	Series
Energy demand
hourly load
Store sales
daily SKU
Website traffic
sessions per hour
Stock / crypto (educational)
disclaim not financial advice
IoT sensor
temperature anomalies
Description
Forecast future values with Prophet, statsforecast, or LSTM/Temporal Fusion — expose API with prediction intervals.

Skills learned
Train/test split by time (no shuffle)
Seasonality, holidays, lag features
MAPE, RMSE, coverage of prediction intervals
Tools needed
Tool	Purpose
prophet or statsforecast or PyTorch
Models
Pandas
Time index
FastAPI
Serve forecasts
Plotly
Interactive charts
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1–2 weeks

Implementation steps
Plot series; detect trend/seasonality; handle missing timestamps.
Baseline: seasonal naive; record RMSE.
Fit main model; rolling-origin validation.
API: series ID → 7-day forecast + intervals.
README: when model fails (regime change).
Stretch goals
Anomaly detection layer on residuals
Multi-series global model
Backtesting dashboard
Project 11: Speech-to-Text + Summarization
Idea bank
Idea	Pipeline
Meeting notes
transcribe → bullet summary
Lecture capture
timestamps + key concepts
Podcast chapterizer
segment + titles
Voice memo organizer
tag + summary
Interview highlights
Q&A extraction
Description
Whisper (or cloud STT) → chunk transcript → LLM summary with timestamps — multimodal portfolio piece.

Skills learned
Audio preprocessing; chunking long files
STT word error rate basics
Summarization prompts; hallucination checks
Tools needed
Tool	Purpose
openai-whisper or faster-whisper
STT
FFmpeg
Audio convert
LLM API
Summarize
Gradio
Upload UI
Difficulty & time
Intermediate — ⭐⭐⭐☆☆ · 1 week

Implementation steps
Transcribe 10-min sample; inspect WER qualitatively.
Chunk by speaker or time; map summaries to timestamps.
Prompt: “summary must only use transcript quotes.”
UI: upload audio → transcript + summary + download MD.
Stretch goals
Speaker diarization (pyannote)
Translate then summarize
Keyword search within transcript
Project 12: MLOps CI Training Pipeline
Idea bank
Idea	Trigger
Nightly retrain on new data
cron
PR runs fast subset train
CI
Model registry promotion
metric gate
Data validation fails build
Great Expectations
Shadow deploy new model
A/B stub
Description
Git push → test → train → evaluate → register only if metric improves — proves engineering maturity.

Skills learned
GitHub Actions; pytest on features
Model registry pattern; rollback
Reproducible seeds and configs
Tools needed
Tool	Purpose
GitHub Actions
CI
MLflow or registry.json
Versions
pytest
Unit tests
DVC (optional)
Data versioning
Difficulty & time
Advanced — ⭐⭐⭐⭐☆ · 2 weeks

Architecture
git push → CI: lint + test → train → eval → if metric ≥ best → register v{N}
                                              else → fail + report
Implementation steps
Refactor train/eval into src/ with config YAML.
Unit tests: no NaN outputs, fixed seed reproducibility.
CI: fast train on 10% data sample.
Nightly: full train; promote if F1 improves.
README: rollback procedure to v{N-1}.
Stretch goals
DVC remote; data diff on PR
Slack alert on promotion/failure
Project 13: LLM Eval & A/B Harness
Idea bank
Idea	Compare
Prompt A vs B
same golden set
GPT-4 vs local model
cost/quality
RAG chunk sizes
retrieval quality
Agent vs single-shot
task success rate
Fine-tune vs base
domain Q&A
Description
Framework to run golden prompts, score outputs (rule-based + LLM-judge), and export comparison reports — critical for LLM teams.

Skills learned
Golden datasets; regression testing for prompts
LLM-as-judge pitfalls; human spot-checks
Cost and latency tracking per variant
Tools needed
Tool	Purpose
Python
Runner
pytest or custom CLI
Harness
OpenAI / Anthropic
Models
pandas
Results tables
Difficulty & time
Advanced — ⭐⭐⭐⭐☆ · 1 week

Implementation steps
golden.jsonl: input, expected_contains, tags.
Run variants; store raw outputs + metadata.
Scorers: exact match, regex, embedding similarity, optional LLM judge.
HTML/Markdown report: win rate per variant.
CI gate: no >5% regression on critical set.
Stretch goals
Pairwise Elo ranking
Human review UI (label studio lite)
Project 14: Capstone — End-to-End AI Product
Idea bank (full products)
Product	Stack highlight
Domain RAG copilot
ingest + chat + citations + eval admin
Vision QC inspector
upload → YOLO → defect log dashboard
Churn dashboard
batch score + SHAP + alert webhook stub
Forecasting ops panel
API + charts + scenario slider
Support agent
tickets + tools + human handoff
Research digest
RSS ingest → summarize → email digest
Description
Combine data + model + API + UI + eval + deploy into one cohesive product with architecture doc and demo video — top interview artifact.

Skills learned
System design tradeoffs (latency, cost, accuracy)
MVP scoping; integration testing
Demo storytelling
Tools needed
Compose from prior projects: FastAPI, React or Streamlit, Docker, cloud host (Railway, Fly.io, Render), your model stack.

Difficulty & time
Advanced — ⭐⭐⭐⭐⭐ · 3–4 weeks

Required components
Component	Deliverable
Data
Ingestion + schema doc
Model
Artifact + offline metrics
API
Versioned REST + OpenAPI
UI
Minimal usable frontend
Eval
Golden set + regression script
Ops
Health check, logging, .env.example
Docs
Architecture diagram, ADR, 3-min demo video
Suggested architecture (RAG copilot example)
┌──────────┐   ┌─────────┐   ┌─────┐   ┌─────┐   ┌──────────┐
│ Upload UI│──▶│ Ingest  │──▶│ VDB │◀──│Retriever│◀──│ Chat UI │
└──────────┘   └─────────┘   └─────┘   └──┬──┘   └────┬─────┘
                                          │           │
                                          └─────▶ LLM ◀┘
                                                    │
                                              Eval admin UI
4-week implementation plan
Week	Deliverable
1
Problem spec, data, baseline model, metrics defined
2
API + model integrated; unit tests
3
UI + eval harness; fix top 10 failure cases
4
Docker deploy, README, demo video, short blog post
Evaluation strategy
North-star metric: task success (user can complete job), not vanity accuracy
20+ golden scenarios; zero regressions before release
Post-mortem: 3 failures and fixes
Stretch goals
OAuth; role-based access
Observability (request IDs, structured logs)
LLM cost dashboard
Cross-Project Standards (Best Practices)
Standard repo layout (intermediate+)
project/
├── .github/workflows/ci.yml
├── configs/
├── data/                 # gitignored
├── src/ or app/
├── tests/
├── notebooks/            # EDA only — not production path
├── models/ or artifacts/
├── eval/
├── docker-compose.yml
├── requirements.txt
├── .env.example
└── README.md
README checklist (every project)

 Problem and user story (2–3 sentences)

 Architecture diagram

 How to install and run (copy-paste commands)

 Metrics table with baseline comparison

 Limitations and failure cases (honesty builds trust)

 Demo GIF or video link
Evaluation checklist

 Held-out test set never used for tuning

 Baseline compared (naive model or smaller approach)

 Error analysis on 20+ failures

 Latency and cost documented (APIs / LLMs)

 Reproducibility: seed, config, dependency versions
Interview prep (2-minute pitch per project)
Prepare: problem → approach → metric → biggest failure → what you’d do next.

Suggested Portfolio Combinations
Profile	3-project combo
ML engineer
1 + 9 + 12
NLP / LLM
2 + 3 + 6 + 13
Computer vision
4 + 5 + 14 (vision QC)
Full-stack AI
3 + 7 + 14
Student (semester)
1 + 2 + 4 → then 3
What Makes a Project “Best”
Criterion	Weak project	Best project
Scope
Notebook only
API + eval + README
Metrics
Accuracy only
Right metric + baseline + ablation
Honesty
Hides failures
Error analysis section
Reproducibility
“Run my notebook”
requirements.txt, config, seed
Story
Tech dump
User problem + demo video
Pick one project from the table, block 10 hours this week, and ship Phase 1. The best AI portfolio is built one finished repo at a time.