20 Intermediate AI Projects (2026)
Portfolio-grade projects for learners who have finished beginner ML/DL work (scikit-learn, basic PyTorch, one LLM API script). Each project includes system structure, evaluation, and deployment patterns used in real teams.

Prerequisites (all projects): Python 3.11+, Git, Pandas, basic PyTorch or scikit-learn, train/val/test discipline, README writing.

Recommended pacing: 1–2 weeks per project; complete 6–8 for a strong intermediate portfolio.

At a Glance
#	Project	Domain	Difficulty	Time
1
Kaggle Tabular Competition Pipeline
Tabular ML
⭐⭐⭐
1–2 wk
2
Fine-Tuned Transformer Classifier
NLP
⭐⭐⭐
1 wk
3
Production RAG Q&A API
LLM / RAG
⭐⭐⭐⭐
2 wk
4
FastAPI Model Serving + Docker
MLOps
⭐⭐⭐
1 wk
5
Experiment Tracking Dashboard
MLOps
⭐⭐⭐
3–5 d
6
Custom Vision API (Transfer Learning)
CV
⭐⭐⭐
1–2 wk
7
Object Detection (YOLO Fine-Tune)
CV
⭐⭐⭐⭐
2 wk
8
Named Entity Recognition (NER)
NLP
⭐⭐⭐
1–2 wk
9
Semantic Search Engine
Embeddings
⭐⭐⭐
1 wk
10
Multi-Modal CLIP Image Search
CV + NLP
⭐⭐⭐⭐
1–2 wk
11
Time Series Forecasting Service
Tabular / TS
⭐⭐⭐
1–2 wk
12
Credit Fraud Detector (Imbalanced)
Tabular ML
⭐⭐⭐
1 wk
13
Customer Churn + SHAP Explainability
Tabular + XAI
⭐⭐⭐
1 wk
14
LoRA LLM Fine-Tune (Domain Q&A)
LLM
⭐⭐⭐⭐
2 wk
15
LLM Agent with Tools
Agents
⭐⭐⭐⭐
2 wk
16
Speech-to-Text + Summarization
Audio + NLP
⭐⭐⭐
1 wk
17
Recommendation API (Hybrid)
RecSys
⭐⭐⭐⭐
2 wk
18
A/B Evaluation Harness for LLM Apps
Eval
⭐⭐⭐⭐
1 wk
19
Automated ML Training Pipeline (CI)
MLOps
⭐⭐⭐⭐
2 wk
20
Capstone: End-to-End AI Product
Full stack
⭐⭐⭐⭐⭐
3–4 wk
Project 1: Kaggle Tabular Competition Pipeline
Description
Build a reproducible competition workflow on a tabular Kaggle challenge (e.g., Spaceship Titanic, Home Credit, or similar). Focus on feature engineering, ensembling, leakage prevention, and a clean submission pipeline — not just a notebook score.

Skills Learned
Feature engineering and target encoding (with proper CV)
XGBoost / LightGBM / CatBoost
Stratified K-fold cross-validation
Pipeline reproducibility (Makefile, configs)
Leaderboard discipline vs local CV gap
Tools Needed
Tool	Purpose
Python, Pandas, scikit-learn
Baselines
XGBoost, LightGBM, CatBoost
Gradient boosting
Optuna
Hyperparameter search
Kaggle API
Submissions
YAML or Hydra
Config management
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1–2 weeks)

Architecture
data/raw → notebooks/EDA → src/features → src/train → models/ → submissions/
                ↓
         configs/experiment.yaml
Project Structure
tabular-kaggle/
├── configs/
│   └── baseline.yaml
├── data/raw/          # gitignored
├── notebooks/01_eda.ipynb
├── src/
│   ├── features.py
│   ├── train.py
│   └── predict.py
├── models/
├── submissions/
├── requirements.txt
└── README.md
Evaluation Strategy
Primary: stratified K-fold CV score (AUC / RMSE per competition)
Secondary: public vs private LB gap analysis in write-up
Document 3+ experiments in experiments.md
Implementation Steps
Clone competition data; write EDA notebook with leakage checklist.
Implement features.py: imputation, encodings, date parts, interactions.
Baseline: single LightGBM + 5-fold CV; log mean ± std.
Add Optuna search (50 trials max); save best params to YAML.
Ensemble 2–3 models (average probabilities).
predict.py generates submission.csv; submit via Kaggle API.
README: CV strategy, feature list, ablation table, lessons from LB.
Stretch Goals
Pseudo-labeling (only if rules allow)
Feature importance SHAP report
GitHub Actions: lint + unit tests on features.py
Project 2: Fine-Tuned Transformer Text Classifier
Description
Fine-tune DistilBERT or DeBERTa-v3-small for multi-class or multi-label classification (news topics, intent detection, toxic comment detection).

Skills Learned
Hugging Face Dataset, Trainer, tokenizers
Learning rate warmup, weight decay, early stopping
F1 / macro-F1 for imbalanced labels
Model export and inference script
Tools Needed
Tool	Purpose
transformers, datasets, evaluate
Training
PyTorch + GPU (Colab)
Compute
Weights & Biases
Experiment logs
AG News, DBpedia, or custom CSV
Data
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Architecture
CSV → Tokenizer → DataLoader → Trainer → checkpoint/ → inference.py
Evaluation Strategy
Hold-out 15% test set never used during training
Report: accuracy, macro-F1, per-class confusion matrix
Error bucket: false positives on edge cases
Implementation Steps
Load dataset; stratified split; explore class imbalance.
Tokenize with AutoTokenizer; max_length 128–256.
Fine-tune with Trainer: 3 epochs, eval each epoch, load_best_model_at_end.
Threshold tuning for multi-label (if applicable).
Export save_pretrained + inference.py batch predict.
Gradio demo: text in → label + confidence bar chart.
Blog-style README: hyperparameters table + failure cases.
Stretch Goals
ONNX export for faster CPU inference
Compare frozen vs full fine-tune learning curve
Project 3: Production RAG Q&A API
Description
Build a retrieval-augmented generation service over PDFs/Markdown: ingest, chunk, embed, retrieve, generate — with citations, rate limits, and an evaluation set.

Skills Learned
Chunking strategies (size, overlap, headers)
Vector DB (Chroma, pgvector, or Qdrant)
Prompt templates with strict context grounding
RAG failure modes (missed retrieval, hallucination)
Tools Needed
Tool	Purpose
FastAPI
REST API
LangChain or LlamaIndex
Orchestration (pick one)
OpenAI / Cohere / local embeddings
Embeddings + LLM
Chroma or pgvector
Vector store
pypdf, unstructured
Parsing
RAGAS or custom eval script
Quality metrics
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
┌─────────┐    ┌──────────┐    ┌─────────────┐    ┌─────┐
│ Ingest  │───▶│ Chunker  │───▶│ Embedder    │───▶│ VDB │
└─────────┘    └──────────┘    └─────────────┘    └──┬──┘
                                                       │
User Query ──▶ Embed ──▶ Retrieve top-k ──▶ Prompt ──▶ LLM ──▶ Answer + cites
Project Structure
rag-api/
├── app/
│   ├── main.py
│   ├── ingest.py
│   ├── retrieve.py
│   └── prompts.py
├── eval/
│   ├── golden_qa.jsonl
│   └── run_eval.py
├── docker-compose.yml
├── .env.example
└── README.md
Evaluation Strategy
Golden set: 30+ Q&A pairs with expected source doc/section
Metrics: retrieval recall@k, answer faithfulness (LLM-judge or manual)
Log latency p50/p95 per stage
Implementation Steps
Define document schema; implement PDF → text + metadata (page, title).
Chunk (512 tokens, 64 overlap); embed; upsert to vector DB.
/query endpoint: retrieve top-5 → build prompt → stream response.
Return JSON: answer, citations[], chunks_used.
Add guard: “Not found in documents” when max similarity < threshold.
Build golden_qa.jsonl; run batch eval; iterate chunk size.
Docker Compose: API + Chroma; document env vars in .env.example.
README architecture diagram + cost estimate per 1k queries.
Stretch Goals
Hybrid search (BM25 + dense)
Redis cache for repeated queries
Auth API key middleware
Project 4: FastAPI Model Serving + Docker
Description
Take any trained model (tabular, sklearn, or PyTorch) and ship a versioned inference API with validation, health checks, and containerized deployment.

Skills Learned
REST API design for ML
Pydantic request/response schemas
Model serialization (joblib, torch.save)
Docker multi-stage builds
Basic load testing
Tools Needed
Tool	Purpose
FastAPI, Uvicorn
Server
Pydantic v2
Validation
Docker
Container
httpx / locust
Tests / load
sklearn or PyTorch model
Artifact
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Architecture
Client → FastAPI → Preprocessor → Model → Postprocessor → JSON Response
              ↓
         /health, /metrics
Implementation Steps
Train model; save artifact + preprocessor.pkl with version tag v1.
Define Pydantic PredictRequest / PredictResponse.
Load model at startup (lifespan); fail fast if artifact missing.
POST /v1/predict with input validation and 422 errors.
GET /health returns model version and load timestamp.
Dockerfile: slim Python image, non-root user, HEALTHCHECK.
docker run -p 8000:8000; test with 20 httpx concurrent requests.
README: OpenAPI screenshot, example curl, latency notes.
Stretch Goals
Prometheus /metrics endpoint
Blue-green: mount models/v2 via env var
Project 5: Experiment Tracking Dashboard
Description
Compare 10+ training runs across hyperparameters using Weights & Biases or MLflow. Treat experiment discipline as the product — essential for team ML and interviews.

Skills Learned
Logging params, metrics, artifacts
Parallel coordinates / sweep analysis
Reproducibility (seed, git commit hash)
Organizing experiments by project
Tools Needed
Tool	Purpose
Weights & Biases or MLflow
Tracking
PyTorch or sklearn training script
Subject
Git
Version pinning
Difficulty
Intermediate — ⭐⭐⭐☆☆ (3–5 days)

Implementation Steps
Refactor training script: argparse for LR, batch size, dropout.
Log train/val loss each epoch; log final F1 and confusion matrix image.
Run grid or random sweep (12+ configs).
Tag best run; export config YAML for reproduction.
Write REPORT.md: what improved, what hurt, surprise findings.
Link W&B dashboard in README (public share if allowed).
Stretch Goals
Log dataset hash (DVC-style)
Auto-early-stop integration with sweep agent
Project 6: Custom Vision API (Transfer Learning at Scale)
Description
Multi-class image classifier (15+ classes) with strong augmentation, mixed precision training, and a deployed Gradio + FastAPI dual interface.

Skills Learned
torchvision training loop or lightning
Mixup / CutMix (intro)
Confusion matrix per class
ONNX or TorchScript export
Tools Needed
Tool	Purpose
PyTorch, torchvision
Training
EfficientNet-B0 or ViT-small
Backbone
Albumentations
Augmentation
Gradio + FastAPI
Serving
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1–2 weeks)

Evaluation Strategy
Stratified split by class
Macro-F1 (penalizes weak minority classes)
Calibration plot (optional)
Implementation Steps
Curate dataset (≥50 images/class); fix mislabeled samples.
Train/val/test 70/15/15; heavy aug on train only.
Fine-tune with discriminative LR (lower for backbone).
Log misclassified grid per epoch in W&B.
Export best checkpoint; TorchScript inference.
FastAPI /classify accepting multipart image.
Gradio demo for portfolio video.
Stretch Goals
Test-time augmentation (TTA) for +accuracy
Quantized INT8 inference benchmark
Project 7: Object Detection (YOLO Fine-Tune)
Description
Fine-tune YOLOv8/v11 (Ultralytics) on a custom dataset (safety gear, parking slots, retail shelves). Move beyond classification to bounding boxes.

Skills Learned
Labeling workflow (CVAT, Roboflow)
YOLO data YAML format
mAP@50, mAP@50-95 metrics
Inference on video frames
Tools Needed
Tool	Purpose
Ultralytics
YOLO training
Roboflow or CVAT
Labels
OpenCV
Video I/O
Colab GPU
Training
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
Images + YOLO labels → Train → weights/best.pt → predict.py → annotated video
Implementation Steps
Collect 200+ images; label bounding boxes per class.
Export YOLO format; write data.yaml paths.
Train nano/small model 50–100 epochs; monitor mAP.
Validate on hold-out; visualize worst false positives.
Run inference on 30s video; save annotated MP4.
README: class list, mAP table, labeling tool link, ethics note.
Stretch Goals
Export to ONNX + run on CPU webcam
Active learning: re-label failure frames
Project 8: Named Entity Recognition (NER)
Description
Train or fine-tune a model to extract entities (person, org, location, product) from text — useful for search, compliance, and knowledge graphs.

Skills Learned
BIO / BIOES tagging
Hugging Face token classification head
seqeval: precision/recall per entity type
Inference on long documents (chunking + merge)
Tools Needed
Tool	Purpose
transformers
Model
CoNLL-2003 or custom annotated data
Training
spaCy (comparison baseline)
Optional
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1–2 weeks)

Implementation Steps
Explore dataset; count entity frequencies; handle O tag imbalance.
Fine-tune bert-base token classifier with DataCollatorForTokenClassification.
Evaluate with seqeval on test; per-entity F1 table.
Build predict.py with sliding window for long text.
FastAPI endpoint: POST text → JSON list of {entity, start, end, label}.
Error analysis: 20 sentences where model fails.
Stretch Goals
Link entities to Wikidata IDs (stub pipeline)
Compare vs spaCy en_core_web_trf
Project 9: Semantic Search Engine
Description
Build embedding-based search over a corpus (docs, products, jobs) with filters, reranking, and a simple web UI — foundation for RAG and enterprise search.

Skills Learned
Sentence transformers (all-MiniLM-L6-v2 or better)
FAISS / HNSW indexing
Metadata filtering
Query expansion (optional)
Tools Needed
Tool	Purpose
sentence-transformers
Embeddings
FAISS
ANN index
FastAPI or Streamlit
UI
CSV/JSON corpus
Data
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Architecture
Corpus → Embed batch → FAISS Index → persist index.faiss
Query → Embed → top-k ANN → (rerank) → results
Implementation Steps
Prepare corpus with id, text, category, date metadata.
Batch-embed; build FAISS index (IVF or Flat for <100k docs).
Implement search with optional category filter post-retrieval.
Add cross-encoder reranker on top-20 → return top-5.
Streamlit: search bar + highlighted snippets.
Benchmark: 50 queries with human relevance labels → nDCG@5.
Stretch Goals
Incremental index updates when new docs arrive
Multilingual embeddings
Project 10: Multi-Modal CLIP Image Search
Description
Text-to-image and image-to-image search using OpenCLIP or Hugging Face CLIP — “find product photos matching this description.”

Skills Learned
Dual encoder models
Normalized embeddings and cosine similarity
Batch indexing pipeline
Zero-shot classification as side effect
Tools Needed
Tool	Purpose
open_clip or transformers CLIP
Model
Image folder + captions CSV
Data
FAISS
Index
Gradio
Demo
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (1–2 weeks)

Implementation Steps
Collect 1k+ images with short captions.
Precompute image embeddings; build FAISS index.
Text query → encode → nearest images.
Image query → encode → similar images (duplicates, styles).
Gradio with two tabs: text search / image search.
README: embedding dim, index size, example queries.
Stretch Goals
Negative prompts / exclude filters
Fine-tune CLIP on domain pairs (advanced)
Project 11: Time Series Forecasting Service
Description
Forecast demand, traffic, or energy usage with Prophet, statsmodels, or LSTM/Temporal Fusion — expose forecasts via API with confidence intervals.

Skills Learned
Train/test splits respecting time (no shuffle leakage)
Seasonality, holidays, trend changepoints
MAPE, RMSE, MAE on rolling origin validation
Serving future horizons
Tools Needed
Tool	Purpose
Prophet or neuralforecast / PyTorch
Models
Pandas
Time index
FastAPI
API
Retail/Energy dataset (M4, store sales)
Data
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1–2 weeks)

Implementation Steps
Plot series; detect missing timestamps; resample consistently.
Rolling-origin CV (3 folds minimum).
Baseline: seasonal naive; beat with Prophet or LSTM.
API: POST /forecast with horizon_days → point + lower/upper.
Visualization endpoint or static Plotly HTML in repo.
Document failure on sudden regime change (COVID-style shock).
Stretch Goals
Multivariate features (weather, promotions)
Alert when error exceeds threshold (monitoring stub)
Project 12: Credit Fraud Detector (Imbalanced Classification)
Description
High-stakes imbalanced tabular problem: fraud is rare; optimize precision-recall, cost-sensitive metrics, and threshold selection — not accuracy.

Skills Learned
SMOTE (careful use), class weights
PR-AUC, ROC-AUC, F2-score
Threshold tuning for business cost matrix
Probability calibration
Tools Needed
Tool	Purpose
Credit Card Fraud (Kaggle) or IEEE-CIS
Data
XGBoost / LightGBM
Model
imbalanced-learn
Resampling
scikit-learn calibration
CalibratedClassifierCV
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Evaluation Strategy
Time-based split if timestamps exist
PR curve; precision at recall=0.8
Dollar cost: FP_cost * FP + FN_cost * FN
Implementation Steps
EDA: fraud rate, time patterns, feature correlations.
Baseline logistic regression with class_weight='balanced'.
LightGBM with scale_pos_weight; no leakage from future data.
Calibrate probabilities; sweep thresholds on validation.
SHAP summary for top features (interpretability).
README: chosen threshold and business justification.
Stretch Goals
Isolation Forest anomaly baseline comparison
Model monitoring doc: concept drift indicators
Project 13: Customer Churn + SHAP Explainability
Description
Predict customer churn for a SaaS/telecom dataset; deliver predictions and explanations stakeholders understand.

Skills Learned
Feature engineering for tenure, usage, support tickets
SHAP TreeExplainer
Executive-facing visualizations
Ethical use of predictive scores
Tools Needed
Tool	Purpose
Telco Customer Churn or similar
Data
XGBoost
Model
SHAP
Explanations
Streamlit
Dashboard
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Implementation Steps
Define churn label; explore cohort retention curves.
Train GBM; evaluate AUC + precision at top decile.
Global SHAP beeswarm; local force plot for 3 customers.
Streamlit: upload row → churn probability + top 5 drivers.
Write “Responsible use” section: bias check across segments.
Stretch Goals
Uplift modeling intro (treatment vs control)
Export explanations as PDF report
Project 14: LoRA LLM Fine-Tune (Domain Q&A)
Description
Fine-tune a 7B-class open model (Llama, Mistral, Qwen) with LoRA/QLoRA on domain Q&A (course FAQ, internal docs, support tickets). Compare base vs adapted on held-out questions.

Skills Learned
Dataset format (Alpaca / ShareGPT / chat template)
PEFT, LoRA rank, target modules
GPU memory management (4-bit loading)
Qualitative + LLM-as-judge evaluation
Tools Needed
Tool	Purpose
unsloth or peft + transformers
Training
trl SFTTrainer
Supervised fine-tune
RunPod / Colab Pro / local 24GB GPU
Compute
500–2k high-quality Q&A pairs
Data
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
Raw Q&A → Clean/ dedupe → JSONL → Tokenize (chat template)
    → LoRA SFT → Adapter weights → Merge or load adapter at inference
Implementation Steps
Curate clean Q&A; remove duplicates and PII.
Split train/val/test (80/10/10); never leak test into training.
Configure LoRA (r=16, alpha=32); 4-bit base model.
Train 1–3 epochs; watch val loss for overfitting.
Inference script: same prompt template as training.
Eval: 50 test questions — score helpfulness 1–5 (human or rubric).
README: training cost, GPU used, before/after examples.
Stretch Goals
DPO pass on preference pairs
Merge adapter; benchmark latency vs base
Project 15: LLM Agent with Tools
Description
Build an agent that calls tools: web search (or stub), calculator, Python REPL (sandboxed), and a custom API — orchestrated via LangGraph or similar.

Skills Learned
Tool schemas (JSON function calling)
ReAct loop: think → act → observe
Guardrails and max iteration limits
Logging traces for debugging
Tools Needed
Tool	Purpose
LangGraph / LangChain
Orchestration
OpenAI or Anthropic API
LLM
restrictedpython or subprocess sandbox
Safe code exec
Tavily / SerpAPI (optional)
Search
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
User → Agent Controller → LLM
              ↓
    ┌─────────┼─────────┐
    ▼         ▼         ▼
 Calculator  Search   Code Runner
    └─────────┴─────────┘
              ↓
         Final Answer
Implementation Steps
Define 3 tools with Pydantic input schemas.
Implement agent graph: max 5 tool calls per request.
Add system prompt: cite tool outputs; refuse unsafe code.
Log full trace to JSON for each session.
Test suite: 10 questions requiring 0, 1, and 2+ tools.
Streamlit chat UI with expandable “thinking steps.”
Stretch Goals
Human-in-the-loop approval before code execution
Cost cap per session
Project 16: Speech-to-Text + Summarization Pipeline
Description
Transcribe audio (lectures, meetings) with Whisper, then summarize and extract action items with an LLM — end-to-end multimodal workflow.

Skills Learned
Audio preprocessing (sample rate, chunking long files)
Whisper API or faster-whisper locally
Chunked summarization for long transcripts
Structured output (JSON action items)
Tools Needed
Tool	Purpose
faster-whisper or OpenAI Whisper
ASR
FFmpeg
Audio convert
LLM API
Summarization
pydantic
Structured outputs
Difficulty
Intermediate — ⭐⭐⭐☆☆ (1 week)

Implementation Steps
Convert input to 16kHz WAV; split >30 min into chunks.
Transcribe; merge with timestamps.
Map-reduce summarize: chunk summaries → final summary.
Extract {actions: [], decisions: [], open_questions: []} via JSON schema.
CLI: python pipeline.py --audio lecture.mp3 --out report.md.
README: WER spot-check on 2 min clip; cost per hour of audio.
Stretch Goals
Speaker diarization (pyannote — check license)
Streamlit upload UI
Project 17: Recommendation API (Hybrid)
Description
Combine collaborative filtering (matrix factorization) with content features (embeddings or metadata) in a hybrid recommender served via API.

Skills Learned
Implicit vs explicit feedback
ALS / BPR or Surprise SVD
Cold-start handling with content fallback
Offline eval: recall@k, nDCG@k
Tools Needed
Tool	Purpose
MovieLens 1M / Amazon reviews subset
Data
implicit or Surprise
CF
sentence-transformers
Item embeddings
FastAPI
Serving
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
         ┌── Collaborative (ALS) ──┐
User ID ─┤                           ├─▶ Weighted merge → Top-K items
         └── Content similarity ───┘
Implementation Steps
Build user-item sparse matrix; train ALS.
Embed item descriptions; store item vectors.
Hybrid score: α * CF + (1-α) * content_sim.
Tune α on validation hold-out users.
API: /recommend/{user_id} + cold-start /similar/{item_id}.
Offline eval notebook with recall@10 chart.
Stretch Goals
Session-based rec (last N clicks)
A/B simulation notebook
Project 18: A/B Evaluation Harness for LLM Apps
Description
Framework to compare prompt variants or models on the same dataset with automated + human rubric scores — essential for LLM product quality.

Skills Learned
Golden datasets for LLM apps
Paired comparison, statistical significance (basic)
LLM-as-judge with bias awareness
Versioned prompts in YAML
Tools Needed
Tool	Purpose
Python asyncio
Parallel API calls
YAML prompt registry
Version control
OpenAI / Anthropic APIs
Models under test
pandas
Results tables
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (1 week)

Project Structure
llm-eval/
├── prompts/
│   ├── v1.yaml
│   └── v2.yaml
├── datasets/golden.jsonl
├── run_eval.py
├── judges/rubric.txt
└── reports/
Implementation Steps
Create 40+ golden items with input, reference, tags.
Run prompt v1 and v2; store raw outputs + latency.
Implement rubric judge (1–5 on correctness, tone, safety).
Aggregate: win rate, avg score, cost per query.
HTML/Markdown report with side-by-side examples.
README: when LLM-judge is unreliable; human eval sample plan.
Stretch Goals
Bootstrap confidence intervals on win rate
Integrate RAGAS for RAG-specific metrics
Project 19: Automated ML Training Pipeline (CI)
Description
Git-triggered training: push new data or config → lint → train → evaluate → register model if metric improves — intro to MLOps without enterprise complexity.

Skills Learned
GitHub Actions (or GitLab CI)
DVC or simple data versioning
Model registry pattern (folder or MLflow)
Fail build if metric regresses
Tools Needed
Tool	Purpose
GitHub Actions
CI
MLflow or models/registry.json
Registry
sklearn/PyTorch training script
Train
pytest
Unit tests on features
Difficulty
Intermediate–Advanced — ⭐⭐⭐⭐☆ (2 weeks)

Architecture
git push → CI: lint + test → train → eval → if improved → register v{N}
                                              else → fail with report
Implementation Steps
Modularize train.py, evaluate.py, features.py.
Unit tests: feature shapes, no NaN after pipeline, deterministic seed.
CI workflow: install deps, run pytest, run train on subset for speed.
Nightly workflow: full data train; compare val F1 to registry.json.
Promote model only if F1 ≥ previous − ε tolerance.
Artifact upload: model.pkl + metrics.json.
README: diagram + how to rollback to v{N-1}.
Stretch Goals
DVC remote for data
Slack webhook on promotion
Project 20: Capstone — End-to-End AI Product
Description
Combine data pipeline + model + API + UI + eval + docs into one cohesive product. Examples: domain RAG assistant, vision QC tool, churn dashboard with alerts, or forecasting ops panel.

Skills Learned
System design and tradeoff documentation
Integration testing across components
Demo storytelling for interviews
Scope management (MVP vs nice-to-have)
Tools Needed
Tool	Purpose
Your stack from projects 1–19
Compose
FastAPI + React or Streamlit
Full product
Docker Compose
Local deploy
Cloud (Railway, Fly.io, Render)
Optional hosting
Difficulty
Advanced Intermediate — ⭐⭐⭐⭐⭐ (3–4 weeks)

Required Components (all capstones)
Component	Deliverable
Data
Ingestion script + schema doc
Model
Trained artifact + eval metrics
API
Versioned REST with OpenAPI
UI
Minimal usable frontend
Eval
Golden set + regression script
Ops
Logging, health check, .env.example
Docs
Architecture diagram, ADR, demo video
Suggested Architectures (pick one)
A. Domain RAG Copilot

Upload docs → Ingest → VDB → Chat UI → Citations → Admin eval page
B. Vision Quality Inspector

Camera/upload → YOLO detect defects → alert API → dashboard history
C. Churn + Action Recommender

Batch scoring nightly → SHAP explanations → CRM webhook stub
Implementation Steps (4-week plan)
Week	Deliverable
1
Problem spec, data, baseline model, metrics defined
2
API + core model integrated; unit tests
3
UI + eval harness; fix top 10 failure cases
4
Docker deploy, README, 3-min demo video, blog post
Evaluation Strategy
Define north-star metric (user task success, not just model accuracy)
20+ golden scenarios; zero regressions before release
Post-mortem doc: 3 things that broke and how you fixed them
Stretch Goals
Auth (OAuth or API keys)
Basic observability (structured logs + request IDs)
Cost dashboard for LLM calls
Cross-Project Patterns (Use Everywhere)
Standard repo layout (intermediate+)
project/
├── .github/workflows/ci.yml
├── configs/
├── data/              # gitignored
├── src/ or app/
├── tests/
├── notebooks/         # EDA only, not production path
├── models/ or artifacts/
├── eval/
├── docker-compose.yml
├── requirements.txt
├── .env.example
└── README.md
Evaluation checklist

 Held-out test set never used for tuning

 Baseline compared (naive, smaller model, or previous version)

 Error analysis on 20+ failures

 Latency and cost documented (for APIs/LLMs)

 Reproducibility: seed, config file, dependency versions
Interview talking points
For any project, prepare 2 minutes on: problem → approach → metric → failure mode → what you'd do next.

Suggested Learning Paths
Goal	Projects (in order)
ML engineer (tabular)
1 → 12 → 13 → 4 → 19
NLP / LLM
2 → 9 → 3 → 14 → 15 → 18
Computer vision
6 → 7 → 10
MLOps focus
4 → 5 → 19 → 20
Full-stack AI
3 → 15 → 18 → 20
Prerequisites by Project
Requires prior completion of
Projects 1, 4, 12, 13
Projects 2, 8, 14
Projects 3, 9, 15, 18
Projects 6, 7, 10
Project 20
