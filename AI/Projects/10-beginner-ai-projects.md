10 Beginner AI Projects (2026)
Hands-on projects for students and new developers. Each builds portfolio-ready skills without requiring a PhD or expensive hardware.

Recommended order: Start with Projects 1–3 if you are new to Python; add Projects 4–6 once comfortable with notebooks; try Projects 7–10 when you want APIs and simple deep learning.

Project 1: Titanic Survival Predictor
Description
Build a binary classifier that predicts whether a passenger survived the Titanic disaster. This is the classic first ML project: tabular data, missing values, and clear metrics.

Skills Learned
Loading CSV data with Pandas
Train/validation/test splits
Handling missing values and categorical features
Training classifiers with scikit-learn
Accuracy, confusion matrix, and basic error analysis
Tools Needed
Tool	Purpose
Python 3.11+
Runtime
Jupyter or Google Colab
Notebook environment
Pandas, scikit-learn
Data + ML
Matplotlib / Seaborn
Plots
Kaggle Titanic dataset
Data
Difficulty
Beginner — ⭐☆☆☆☆ (1–2 days)

Implementation Steps
Download the Titanic train.csv from Kaggle and load it in a notebook.
Explore columns: survival rate by sex, class, age; plot 2–3 charts.
Fill or impute missing Age and Embarked; encode Sex and Embarked (one-hot or label encoding).
Select features (e.g., Pclass, Sex, Age, SibSp, Fare); split 80/20 train/validation.
Train Logistic Regression and Random Forest; compare validation accuracy.
Plot confusion matrix; list 5 misclassified rows and hypothesize why.
Write a README: problem, features, metrics, how to run.
(Optional) Submit predictions to Kaggle.
Project 2: House Price Explorer (Regression)
Description
Predict house prices from features like size, location, and year built. Focus on exploratory data analysis (EDA) and regression — not just the final score.

Skills Learned
Regression vs classification
Correlation and feature vs target plots
RMSE / MAE metrics
Simple feature engineering (e.g., price per sqft)
Communicating insights in a README
Tools Needed
Tool	Purpose
Python, Pandas, scikit-learn
Core stack
Seaborn
pairplot, heatmaps
Ames Housing or California Housing dataset
Public CSV (Kaggle / sklearn)
Difficulty
Beginner — ⭐☆☆☆☆ (1–2 days)

Implementation Steps
Load dataset; print shape, dtypes, missing value counts.
Plot price distribution; identify outliers (cap or document them).
Scatter plots: living area vs price, year built vs price.
Encode categoricals; split train/test (hold out 20%).
Baseline: predict mean price — record RMSE.
Train Linear Regression and Random Forest Regressor; compare RMSE on test set.
Show top 5 feature importances (forest) or coefficients (linear).
Publish notebook + 3-bullet “business insight” summary in README.
Project 3: Personal Data Dashboard
Description
Analyze your own data (steps, sleep, expenses, study hours) or a CSV you care about. No competition — practice the full data → insight pipeline.

Skills Learned
Data cleaning in Pandas (groupby, resample, date parsing)
Visualization storytelling
Asking questions of data before modeling
Optional: simple forecasting or clustering
Tools Needed
Tool	Purpose
Python, Pandas, Matplotlib / Seaborn
Analysis
CSV export from phone app or spreadsheet
Data source
Jupyter / Colab
Notebook
Difficulty
Beginner — ⭐☆☆☆☆ (1 day)

Implementation Steps
Collect 30+ days of data; export to CSV with consistent date column.
Load and parse dates; check duplicates and nulls.
Define 3 questions (e.g., “Which day of week do I spend most?”).
Build 4–6 charts that answer those questions.
Write 200-word narrative: surprises, limitations, next data to collect.
(Optional) Simple linear trend or K-Means on 2 numeric features.
Share README with sample chart screenshots (no sensitive numbers if public).
Project 4: Spam / SMS Text Classifier
Description
Classify messages as spam or ham (legitimate). Introduces text features and NLP basics without transformers on day one.

Skills Learned
Text preprocessing (lowercase, tokenization)
Bag-of-words or TF-IDF features
Naive Bayes or Logistic Regression on text
Precision/recall for imbalanced classes
Tools Needed
Tool	Purpose
Python, scikit-learn
TfidfVectorizer, classifiers
SMS Spam Collection (UCI / Kaggle)
Labeled messages
Jupyter
Development
Difficulty
Beginner — ⭐⭐☆☆☆ (2–3 days)

Implementation Steps
Load SMS dataset; check class balance (spam vs ham).
Split stratified train/test so both classes appear in each set.
Build pipeline: TfidfVectorizer → MultinomialNB or LogisticRegression.
Evaluate accuracy, precision, recall, F1 on test set.
Test 10 custom messages (your own strings); log false positives/negatives.
Save pipeline with joblib; write predict.py that classifies one string from CLI.
Document in README: why precision matters for spam filters.
Project 5: MNIST Digit Recognizer (Intro Deep Learning)
Description
Train a small neural network to recognize handwritten digits (0–9). First taste of PyTorch or TensorFlow and GPU training.

Skills Learned
Tensors and training loops
Loss (cross-entropy) and optimizers (Adam)
Train/val curves and overfitting
Simple MLP or CNN architecture
Tools Needed
Tool	Purpose
PyTorch or TensorFlow/Keras
Deep learning
MNIST (built into torchvision / keras)
Dataset
Google Colab
Free GPU (optional)
Matplotlib
Loss/accuracy plots
Difficulty
Beginner — ⭐⭐☆☆☆ (2–4 days)

Implementation Steps
Load MNIST; normalize pixels to [0, 1]; create train/val split.
Build MLP: flatten → 128 → 64 → 10 outputs + softmax/logits.
Write training loop: forward, loss, backward, optimizer.step().
Train 5–10 epochs; plot train vs validation loss each epoch.
Report test accuracy; show grid of 16 misclassified images.
(Stretch) Replace MLP with 2-layer CNN; compare accuracy.
README: architecture diagram, final accuracy, lessons learned.
Project 6: Image Classifier with Transfer Learning
Description
Classify images in a small custom category set (e.g., cats vs dogs, or 5 types of plants) using a pretrained ResNet or MobileNet — the standard industry shortcut.

Skills Learned
Transfer learning (freeze backbone, train head)
Image folders, augmentation (flip, crop)
torchvision ImageFolder or similar
Deploying a demo with Gradio
Tools Needed
Tool	Purpose
PyTorch + torchvision
Model + transforms
50–200 images per class (your photos or public dataset)
Training data
Gradio
Web demo
Colab / local GPU
Faster training
Difficulty
Beginner–Intermediate — ⭐⭐☆☆☆ (3–5 days)

Implementation Steps
Organize data: train/cat/, train/dog/, etc.; hold out 20% for validation.
Apply transforms: resize, normalize (ImageNet mean/std), random flip on train.
Load resnet18 pretrained; replace final layer for N classes.
Train only the new head for a few epochs, then fine-tune last block with low LR.
Track val accuracy; stop if overfitting (val drops while train rises).
Evaluate on test images; confusion matrix per class.
Build Gradio app: upload image → label + confidence.
README + 30-second screen recording of demo.
Project 7: LLM API Mini Chatbot
Description
A command-line or simple web chat that calls an LLM API (OpenAI, Anthropic, Google, or a free local model). Learn prompts, tokens, and API keys — core “AI engineer” literacy in 2026.

Skills Learned
Environment variables and API keys (never commit secrets)
System vs user messages
Streaming responses (optional)
Basic error handling and rate limits
Tools Needed
Tool	Purpose
Python 3.11+
Script
openai SDK or anthropic / google-generativeai
API client
.env + python-dotenv
Local secrets
(Optional) Streamlit or Gradio
Simple UI
Difficulty
Beginner — ⭐⭐☆☆☆ (1–2 days)

Implementation Steps
Create API account; generate key; add .env with API_KEY=... (add .env to .gitignore).
Write 20-line script: send “Hello” with a system prompt (“You are a helpful tutor”).
Print assistant reply; log token usage if API returns it.
Add conversation history list (user/assistant turns) for multi-turn chat.
Add CLI loop: user types quit to exit.
Tune system prompt for one use case (e.g., “explain code simply”).
(Optional) Stream tokens to terminal; wrap in Streamlit chat UI.
README: setup, cost note, example conversation — no real API keys.
Project 8: Sentiment Analyzer for Product Reviews
Description
Classify reviews as positive, negative, or neutral using classical ML or a small pretrained transformer. Bridges tabular ML and modern NLP.

Skills Learned
Labelled text datasets
Train/test discipline on text
Comparing TF-IDF + logistic regression vs DistilBERT fine-tune
Error analysis on ambiguous reviews
Tools Needed
Tool	Purpose
Amazon reviews or IMDB subset (Kaggle)
Data
scikit-learn or Hugging Face transformers
Two difficulty paths
Pandas, Jupyter
Workflow
Difficulty
Beginner–Intermediate — ⭐⭐☆☆☆ (3–4 days)

Implementation Steps
Load 2k–5k labelled reviews; explore length and class balance.
Path A: TF-IDF + Logistic Regression → F1 score on test set.
Path B: Fine-tune distilbert-base-uncased with Hugging Face Trainer (Colab GPU).
Compare both approaches in a table (accuracy, F1, training time).
Collect 20 hard reviews (sarcasm, mixed); test both models.
Write error analysis: 5 patterns where models fail.
README with metrics table and “when to use which approach.”
Project 9: Movie or Book Recommender (Collaborative Filtering Lite)
Description
Build a simple recommendation system: “users who liked X also liked Y” or item similarity from ratings. Introduces matrices and similarity without deep learning.

Skills Learned
User-item rating matrices
Cosine similarity / nearest neighbors
Cold-start problem (new user with no history)
Evaluating recsys (hold-out one rating)
Tools Needed
Tool	Purpose
Python, Pandas, NumPy
Data manipulation
scikit-learn cosine_similarity or Surprise library
Similarity / MF
MovieLens 100k (small)
Classic dataset
Difficulty
Beginner–Intermediate — ⭐⭐☆☆☆ (2–4 days)

Implementation Steps
Download MovieLens 100k; load ratings and titles.
Build user-item pivot (sparse matrix) or use Surprise dataset loader.
Implement item-item: for a given movie, find top 5 similar by cosine on rating vectors.
Given a user’s watched list, aggregate similar items not yet seen.
Hold out 1 rating per user; predict with nearest-neighbor average; compute RMSE on held-out.
CLI: enter movie title → print top 5 recommendations.
README: explain cold-start and how Netflix uses more than this baseline.
Project 10: Document Q&A with Embeddings (Mini-RAG)
Description
Upload a short PDF or Markdown notes; chunk, embed, and retrieve relevant passages to answer questions with an LLM. A portfolio-friendly intro to RAG (retrieval-augmented generation).

Skills Learned
Text chunking strategies
Embedding vectors and similarity search
Prompting LLM with retrieved context
Reducing hallucinations with citations
Tools Needed
Tool	Purpose
Python
Orchestration
chromadb or faiss + local JSON
Vector store
OpenAI / open-source embeddings API
Embeddings
LLM API
Answer generation
pypdf or paste Markdown
Document input
Difficulty
Beginner–Intermediate — ⭐⭐⭐☆☆ (4–6 days)

Implementation Steps
Pick one document (course notes, 10-page PDF); extract plain text.
Split into chunks (~500 tokens, 50 overlap); store text + metadata (page/section).
Embed each chunk; save to Chroma or FAISS index.
On user question: embed query → retrieve top 3 chunks.
Prompt LLM: “Answer only from context below; say ‘not in document’ if missing” + paste chunks.
Return answer with chunk IDs or quotes as “citations.”
Test 5 questions: 3 answerable from doc, 2 not — verify honest “not found.”
README: architecture diagram Doc → Chunks → Embed → Store → Query → Retrieve → LLM.
Comparison at a Glance
#	Project	Focus	Difficulty
1
Titanic Survival
Tabular classification
⭐
2
House Prices
Regression + EDA
⭐
3
Personal Dashboard
Data storytelling
⭐
4
Spam Classifier
NLP + classical ML
⭐⭐
5
MNIST Digits
Neural networks
⭐⭐
6
Image Classifier
Transfer learning + Gradio
⭐⭐
7
API Chatbot
LLM APIs
⭐⭐
8
Sentiment Analysis
NLP + optional transformers
⭐⭐
9
Recommender
Collaborative filtering
⭐⭐
10
Mini-RAG
Embeddings + LLM apps
⭐⭐⭐
Portfolio Checklist (All Projects)

 Public GitHub repo with README

 Problem statement and how to run (pip install -r requirements.txt)

 Metrics or screenshots of results

 What you learned + what you’d improve

 No secrets in git history
