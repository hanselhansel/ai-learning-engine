# Machine Learning: Learning Curriculum

**Owner:** [Your Name]
**Goal:** Build production-ready ML skills as a software engineer transitioning to ML engineering
**Timeline:** 8 weeks, ~2-3 hours/day
**Start Date:** TBD
**Created:** 2026-03-19

---

## TLDR

This curriculum takes a software engineer from ML fundamentals to building production ML systems in 40 sessions. Four phases: Foundations (math, statistics, classical ML), Deep Learning (neural nets through transformers), Applied ML (system design, MLOps, end-to-end pipelines), and Portfolio (Kaggle, paper implementation, interview prep). You'll leave with a GitHub portfolio of ML projects and system design fluency for ML interviews.

---

## How This Curriculum Works

### Daily Session Format (2-3 hours)

| Block | Duration | What |
|-------|----------|------|
| **Learn** | 60-90 min | Read/code assigned material, then discuss with Claude |
| **Drill** | 20 min | Concept quiz, math derivation, or code challenge |
| **Build** | 60-90 min | Jupyter notebook implementation or system design exercise |
| **Reflect** | 10 min | Log what you learned, update your "explain it simply" notes |

### How to Use with Claude

Type **"let's learn"** to start. Claude auto-resumes from `SESSION-STATE.md`. Type **"done learning"** to end early.

### Assessment System

| Assessment | When | Format | Pass Threshold |
|-----------|------|--------|---------------|
| **Phase 1 Gate** | End of Week 2 | 25 term quiz + implement logistic regression from scratch | 80% quiz, working code |
| **Phase 2 Gate** | End of Week 4 | 20 term quiz + train a transformer on a toy task | 80% quiz, model converges |
| **Phase 3 Gate** | End of Week 6 | ML system design review + pipeline code review | 4/5 on both |
| **Phase 4 Gate** | End of Week 8 | Full mock ML interview (coding + system design + math) | Pass 2/3 rounds |

### Folder Structure

```
machine-learning/
+-- CURRICULUM.md
+-- CURRICULUM-CONFIG.md
+-- SESSION-STATE.md
+-- progress.md
+-- assessments/
+-- build-project/
+-- sessions/
+-- notebooks/
```

---

## Phase 1: Foundations (Weeks 1-2, Days 1-10)

**Objective:** Build the mathematical foundation and classical ML toolkit. Understand the core algorithms, when to use them, and how to evaluate them.

### Week 1: Math & Classical ML

#### Day 1: Linear Algebra for ML

**Core question:** Why does ML run on linear algebra?

| Topic | Details |
|-------|---------|
| Vectors and matrices | Representation of data points and features |
| Matrix multiplication | The core operation in neural networks |
| Eigenvalues & eigenvectors | PCA, understanding what transformations preserve |
| Norms (L1, L2) | Distance measures, regularization |
| Broadcasting | NumPy convention that makes batch operations work |

**Reading:**
- 3Blue1Brown, *Essence of Linear Algebra* (YouTube series, ~3 hours total)
- Goodfellow et al., *Deep Learning*, Chapter 2 (free at deeplearningbook.org)

**Exercise:** Implement matrix multiplication from scratch in Python (no NumPy). Then compare performance with NumPy's implementation. Measure the speedup. Why is NumPy faster? (Answer: BLAS/LAPACK, C under the hood.)

**Bridge to your experience:** As a software engineer, you work with arrays and data structures daily. Vectors are just arrays. Matrices are 2D arrays. ML is applying transformations (functions) to these data structures at scale.

---

#### Day 2: Statistics & Probability for ML

**Core question:** What statistical concepts does every ML engineer need?

| Topic | Details |
|-------|---------|
| Probability distributions | Normal, Bernoulli, Poisson -- when each appears in ML |
| Bayes' theorem | P(A|B) = P(B|A)P(A)/P(B), foundation of probabilistic ML |
| Maximum likelihood estimation | How most ML models are trained: find parameters that maximize P(data|params) |
| Bias-variance tradeoff | Underfitting vs overfitting, the central tension |
| Hypothesis testing | p-values, confidence intervals -- for A/B tests and model comparison |
| Correlation vs causation | Simpson's paradox, confounders, why ML models aren't causal |

**Reading:**
- StatQuest with Josh Starmer (YouTube) -- Probability, Bayes, MLE videos
- James et al., *Introduction to Statistical Learning* (ISLR), Chapter 2

**Exercise:** Generate 1000 samples from a normal distribution. Estimate mean and variance using MLE. Plot the distribution. Now add an outlier cluster. How does MLE change? Implement in a Jupyter notebook.

---

#### Day 3: Python ML Stack

**Core question:** What are the essential tools and how do they fit together?

| Tool | Purpose | Key Operations |
|------|---------|---------------|
| **NumPy** | Numerical computing | Arrays, linear algebra, random sampling |
| **pandas** | Data manipulation | DataFrames, groupby, merge, missing values |
| **scikit-learn** | Classical ML | fit/predict/transform API, preprocessing, model selection |
| **matplotlib/seaborn** | Visualization | Line plots, histograms, heatmaps, confusion matrices |
| **Jupyter** | Interactive development | Notebooks for exploration, visualization, documentation |

**Exercise:** Load the California Housing dataset (sklearn). Explore with pandas (distributions, correlations, missing values). Visualize 5 key relationships with matplotlib. Write a 1-paragraph summary of what you found. All in one Jupyter notebook.

---

#### Day 4: Supervised Learning - Regression

**Core question:** How do you predict a continuous value from features?

| Algorithm | How It Works | When to Use |
|-----------|-------------|-------------|
| Linear regression | Fit a line (hyperplane) minimizing squared errors | Baseline, interpretable, linear relationships |
| Ridge (L2) | Linear regression + L2 penalty on coefficients | Many features, prevent overfitting |
| Lasso (L1) | Linear regression + L1 penalty (sparse solutions) | Feature selection, many irrelevant features |
| Decision tree regressor | Recursive binary splits on features | Non-linear, interpretable, handles mixed types |
| Random forest | Ensemble of decorrelated trees | Strong baseline, robust, handles noise |
| Gradient boosting (XGBoost) | Sequential trees correcting predecessors' errors | Best performance on tabular data |

**Reading:**
- ISLR, Chapters 3 (Linear Regression), 6 (Regularization), 8 (Tree-Based)
- XGBoost documentation tutorial

**Exercise:** Predict house prices on the California Housing dataset. Train all 6 models. Compare RMSE, MAE, and R-squared. Plot actual vs predicted. Which model wins and why? Document in a notebook.

---

#### Day 5: Supervised Learning - Classification (Synthesis)

**Core question:** How do you predict categories, and how do you measure success?

| Algorithm | Key Concept |
|-----------|------------|
| Logistic regression | Linear model + sigmoid, outputs probabilities |
| SVM | Maximum margin classifier, kernel trick for non-linear |
| k-NN | Classify by majority vote of nearest neighbors |
| Random forest classifier | Ensemble voting across trees |
| XGBoost classifier | Gradient boosting for classification |

| Evaluation Metric | What It Measures | When to Use |
|-------------------|-----------------|-------------|
| Accuracy | Overall correctness | Balanced classes only |
| Precision | Of predicted positives, how many are correct | When false positives are costly (spam filter) |
| Recall | Of actual positives, how many did you find | When false negatives are costly (disease detection) |
| F1 score | Harmonic mean of precision and recall | Imbalanced classes |
| AUC-ROC | Probability ranking quality | Model comparison, threshold-agnostic |
| Confusion matrix | Full breakdown of predictions | Always useful for diagnosis |

**Exercise:** Build a credit card fraud detector using the Kaggle Credit Card Fraud dataset. Handle class imbalance (SMOTE or class weights). Compare 3 models. Plot ROC curves. Write a 1-page report: which model would you deploy and why?

---

### Week 2: Unsupervised Learning & ML Workflow

#### Day 6: Unsupervised Learning

**Core question:** How do you find structure in unlabeled data?

| Algorithm | What It Does | Use Case |
|-----------|-------------|----------|
| K-means | Partition data into k clusters | Customer segmentation, anomaly detection |
| DBSCAN | Density-based clustering, finds arbitrary shapes | Spatial data, noise handling |
| Hierarchical clustering | Build a tree of clusters | Taxonomy, biology, small datasets |
| PCA | Reduce dimensions while preserving variance | Visualization, noise reduction, preprocessing |
| t-SNE | Non-linear dimensionality reduction for visualization | Exploring high-dimensional data |
| UMAP | Faster t-SNE alternative, preserves global structure | Production visualization |

**Exercise:** Take the MNIST digits dataset. Apply PCA (reduce to 50 dims), then t-SNE (reduce to 2 dims). Visualize the clusters. Apply K-means (k=10) to the PCA-reduced data. How well do clusters match actual digits? Calculate adjusted Rand index.

---

#### Day 7: Feature Engineering & Preprocessing

**Core question:** Why is feature engineering often more important than model selection?

| Technique | When to Use | Example |
|-----------|-----------|---------|
| One-hot encoding | Categorical features with few values | Country, color |
| Target encoding | Categorical with many values | ZIP code, product ID |
| Standardization (z-score) | Features on different scales | Age (0-100) vs income (0-1M) |
| Log transformation | Right-skewed distributions | Income, house prices |
| Binning | Convert continuous to categorical | Age groups, price ranges |
| Interaction features | Capture feature combinations | Price x quantity, height x weight |
| Time-based features | Datetime columns | Day of week, month, holiday flags |

**Exercise:** Take the Titanic dataset (Kaggle). Engineer 10+ features from raw data (title extraction from name, family size, fare per person, deck from cabin, etc.). Compare model performance with raw features vs engineered features. Document the impact of each feature.

---

#### Day 8: Model Selection & Validation

**Core question:** How do you pick the right model and know it will generalize?

| Topic | Details |
|-------|---------|
| Train/validation/test split | 70/15/15 or 80/10/10, never touch test until final evaluation |
| K-fold cross-validation | More robust estimate of generalization, standard is k=5 |
| Stratified splits | Preserve class distribution in each fold |
| Hyperparameter tuning | Grid search, random search, Bayesian optimization (Optuna) |
| Learning curves | Diagnose bias vs variance by plotting train/val error vs data size |
| Ensemble methods | Stacking, blending, voting -- combining models for better performance |

**Exercise:** Take your best model from Day 5 (fraud detection). Apply 5-fold stratified cross-validation. Tune hyperparameters with Optuna (20 trials). Plot learning curves before and after tuning. Did tuning help? By how much?

---

#### Day 9: ML Project Lifecycle

**Core question:** How does an ML project go from idea to production?

| Stage | Activities | Key Outputs |
|-------|-----------|-------------|
| Problem framing | Define business metric, ML formulation, success criteria | Problem statement doc |
| Data collection | Sources, labeling, quality assessment, bias audit | Dataset + data card |
| EDA & preprocessing | Distributions, correlations, cleaning, feature engineering | Notebook + pipeline code |
| Modeling | Baseline, experimentation, evaluation | Model + experiment tracking |
| Evaluation | Offline metrics, error analysis, fairness checks | Evaluation report |
| Deployment | Model serving, monitoring, A/B test | Production endpoint |
| Monitoring | Data drift, model drift, performance degradation | Alerts + dashboards |

**Reading:**
- Google's "Rules of ML" (developers.google.com/machine-learning/guides/rules-of-ml)
- Sculley et al., "Hidden Technical Debt in ML Systems" (NeurIPS 2015)

**Exercise:** Write an ML project plan for: "Build a model to predict which users will churn from a SaaS product in the next 30 days." Cover all 7 stages. Include: problem framing (what metric?), data requirements, baseline approach, evaluation plan, and deployment considerations.

---

#### Day 10: Synthesis - End-to-End ML Project

**Core question:** Can you execute a complete ML project from raw data to evaluation?

**Exercise:** Complete end-to-end ML project on the Ames Housing dataset (Kaggle):
1. EDA notebook with 10+ visualizations
2. Feature engineering (15+ engineered features)
3. 5+ models compared with cross-validation
4. Hyperparameter tuning on top 2 models
5. Final evaluation on held-out test set
6. 1-page summary: approach, results, what you'd do differently

This is your Phase 1 portfolio artifact. Push to GitHub.

---

## Phase 2: Deep Learning (Weeks 3-4, Days 11-20)

**Objective:** Understand neural networks from perceptrons to transformers. Build working implementations of key architectures.

### Week 3: Neural Network Fundamentals

#### Day 11: Neural Network Basics

**Core question:** How does a neural network learn?

| Topic | Details |
|-------|---------|
| Perceptron | Single neuron: weighted sum + activation = output |
| Multi-layer perceptron (MLP) | Stack of layers, universal approximation theorem |
| Activation functions | ReLU (standard), sigmoid (output), softmax (multi-class) |
| Loss functions | MSE (regression), cross-entropy (classification) |
| Backpropagation | Chain rule to compute gradients through the network |
| Gradient descent | SGD, momentum, Adam optimizer |

**Reading:**
- 3Blue1Brown, *Neural Networks* (YouTube series)
- Goodfellow et al., *Deep Learning*, Chapters 6-8

**Exercise:** Implement a 2-layer neural network from scratch in NumPy (no PyTorch/TF). Train it on MNIST. Achieve >90% accuracy. Then rewrite in PyTorch and compare the code. What does PyTorch automate?

---

#### Day 12: Training Deep Networks

**Core question:** Why is training deep networks hard, and how do we fix it?

| Problem | Solution |
|---------|----------|
| Vanishing gradients | ReLU activation, residual connections, batch norm |
| Overfitting | Dropout, weight decay, data augmentation, early stopping |
| Slow convergence | Learning rate schedulers, Adam optimizer, warm-up |
| Batch effects | Batch normalization, layer normalization |
| Hyperparameter sensitivity | Learning rate finder, automated HPO (Optuna) |

**Exercise:** Train a 10-layer MLP on CIFAR-10. First without any tricks (observe poor training). Then add batch norm, dropout, learning rate scheduling, and data augmentation one at a time. Plot training curves for each addition. Document the impact of each technique.

---

#### Day 13: CNNs for Computer Vision

**Core question:** How do convolutional neural networks understand images?

| Component | What It Does |
|-----------|-------------|
| Convolution layer | Learns local spatial patterns (edges, textures, objects) |
| Pooling layer | Downsamples, provides translation invariance |
| Feature hierarchy | Layer 1: edges, Layer 2: textures, Layer 3: parts, Layer 4+: objects |
| Key architectures | LeNet (1998), AlexNet (2012), ResNet (2015), EfficientNet (2019) |
| Transfer learning | Use ImageNet-pretrained features, fine-tune for your task |

**Reading:**
- Stanford CS231n, Lecture 5: Convolutional Neural Networks
- He et al., "Deep Residual Learning" (ResNet paper, 2015)

**Exercise:** Fine-tune a pretrained ResNet-50 on the Stanford Dogs dataset (120 breeds). Compare: (1) training from scratch, (2) freezing all but last layer, (3) fine-tuning all layers with low LR. Plot accuracy curves. Write up which approach works best and why.

---

#### Day 14: RNNs and Sequence Modeling

**Core question:** How do neural networks process sequential data?

| Architecture | Key Innovation | Limitation |
|-------------|---------------|------------|
| Vanilla RNN | Hidden state carries information forward | Vanishing gradients on long sequences |
| LSTM | Gate mechanism (forget, input, output) controls information flow | Slow (sequential computation), complex |
| GRU | Simplified LSTM with 2 gates | Slightly faster, comparable performance |
| Bidirectional | Process sequence in both directions | Can't be used for generation (needs future) |
| Seq2seq + attention | Encoder-decoder with attention over input | Breakthrough for translation, still sequential |

**Exercise:** Build a character-level language model with LSTM in PyTorch. Train on Shakespeare text. Generate 500 characters of new text. Then implement the same with GRU. Compare training speed and generation quality.

---

#### Day 15: Transformers and Attention (Synthesis)

**Core question:** Why did transformers replace everything, and how do they work?

| Component | What It Does |
|-----------|-------------|
| Self-attention | Each token attends to all other tokens, captures long-range dependencies |
| Multi-head attention | Multiple attention patterns in parallel |
| Positional encoding | Injects sequence order information (sine/cosine or learned) |
| Layer normalization | Stabilizes training |
| Feedforward network | Non-linear transformation after attention |
| Encoder vs decoder | Encoder: bidirectional (BERT). Decoder: autoregressive (GPT) |

**Reading:**
- Vaswani et al., "Attention Is All You Need" (2017) -- the original paper
- Jay Alammar, "The Illustrated Transformer" (blog post, jalammar.github.io)

**Exercise:** Implement a single-head self-attention mechanism from scratch in PyTorch. Then build a minimal transformer (2 layers, 4 heads) and train it on a simple sequence task (copy, reverse, or sort). Visualize the attention patterns.

---

### Week 4: Modern Architectures

#### Day 16: BERT and Encoder Models

**Core question:** How do bidirectional models understand language?

| Topic | Details |
|-------|---------|
| Masked language modeling (MLM) | Predict randomly masked tokens, learns bidirectional context |
| Next sentence prediction (NSP) | Predict if two sentences follow each other |
| Fine-tuning BERT | Add task-specific head, fine-tune on labeled data |
| Variants | RoBERTa (better training), DeBERTa (disentangled attention), ALBERT (parameter sharing) |
| Use cases | Classification, NER, question answering, semantic similarity |

**Exercise:** Fine-tune a DistilBERT model on the IMDB sentiment dataset using HuggingFace Transformers. Compare to a TF-IDF + logistic regression baseline. Measure accuracy, F1, and inference time.

---

#### Day 17: GPT and Decoder Models

**Core question:** How do autoregressive models generate text?

| Topic | Details |
|-------|---------|
| Causal (autoregressive) attention | Each token only attends to previous tokens |
| Next-token prediction | Training objective: predict the next token |
| Scaling laws | Performance improves predictably with more data, compute, parameters |
| In-context learning | GPT-3's discovery: task performance from examples in the prompt |
| RLHF | Reinforcement learning from human feedback (ChatGPT's secret) |
| Key models | GPT-3 (175B), GPT-4, Claude, LLaMA, Mistral |

**Exercise:** Fine-tune GPT-2 (small) on a custom text corpus (pick a subreddit, book, or code repo). Generate samples. Evaluate perplexity before and after fine-tuning. Compare generation quality with temperature 0.5, 1.0, and 1.5.

---

#### Day 18: Vision Transformers & Multimodal Models

**Core question:** How do transformers handle images and multiple modalities?

| Model | What It Does |
|-------|-------------|
| ViT (Vision Transformer) | Split image into patches, treat as token sequence |
| CLIP (OpenAI) | Jointly train image and text encoders, zero-shot classification |
| DALL-E / Stable Diffusion | Text-to-image generation via diffusion |
| LLaVA | Vision-language model: image understanding + text generation |
| Whisper | Audio-to-text transformer |

**Exercise:** Use CLIP (via HuggingFace) to build a zero-shot image classifier. Test on 100 images across 10 categories. Compare to a fine-tuned ResNet. When does CLIP win? When does it lose?

---

#### Day 19: Diffusion Models & Generative AI

**Core question:** How do diffusion models generate images (and why not GANs anymore)?

| Topic | Details |
|-------|---------|
| Forward diffusion | Gradually add noise to data until it's pure noise |
| Reverse diffusion | Learn to denoise step-by-step, recovering the data |
| U-Net architecture | Encoder-decoder with skip connections, the backbone of diffusion |
| Conditioning | Text (CLIP), class label, image (img2img) |
| GANs vs diffusion | GANs: faster but mode collapse. Diffusion: slower but stable, diverse |
| Latent diffusion | Diffuse in latent space (Stable Diffusion), much faster |

**Reading:**
- Lilian Weng, "What are Diffusion Models?" (blog, lilianweng.github.io)

**Exercise:** Use the HuggingFace Diffusers library to generate images with Stable Diffusion. Experiment with: different prompts, guidance scale (1-20), number of inference steps (10-50). Write a 1-page summary of how each parameter affects quality and speed.

---

#### Day 20: Synthesis - Architecture Comparison

**Core question:** Given a problem, how do you choose the right architecture?

| Problem Type | Best Architecture | Why |
|-------------|-------------------|-----|
| Tabular data | XGBoost / LightGBM | Still beats deep learning on most tabular tasks |
| Image classification | ViT or EfficientNet (pretrained) | Transfer learning is king |
| Text classification | Fine-tuned BERT/DeBERTa | Bidirectional understanding |
| Text generation | GPT/LLaMA fine-tuning or prompting | Autoregressive modeling |
| Object detection | YOLO v8 or DETR | Speed vs accuracy tradeoff |
| Recommendation | Two-tower model (user + item encoders) | Scalable retrieval |
| Time series | Temporal Fusion Transformer or N-BEATS | Handles multiple horizons |

**Exercise:** Write a 2-page "ML Architecture Decision Guide" covering 7 problem types. For each: recommended architecture, when it fails, key hyperparameters, and compute requirements. This is your Phase 2 portfolio artifact.

---

## Phase 3: Applied ML (Weeks 5-6, Days 21-30)

**Objective:** Learn to build ML systems that work in production. Design data pipelines, deploy models, monitor performance.

### Week 5: ML Systems

#### Day 21: ML System Design

**Core question:** How do you design an ML system end-to-end?

| Component | Details |
|-----------|---------|
| Data pipeline | Collection, validation, transformation, feature store |
| Feature store | Centralized feature repository (Feast, Tecton) |
| Training pipeline | Experiment tracking, hyperparameter tuning, distributed training |
| Model registry | Version control for models (MLflow, Weights & Biases) |
| Serving infrastructure | Batch vs real-time, latency requirements, scaling |
| Monitoring | Data drift, model drift, performance degradation |

**Reading:**
- Chip Huyen, *Designing Machine Learning Systems* (O'Reilly, 2022), Chapters 1-4

**Exercise:** Design an ML system for "personalized product recommendations on an e-commerce site." Draw the architecture diagram. Define: data sources, feature engineering, model choice, serving strategy (batch vs real-time), and monitoring plan.

---

#### Day 22: MLOps & Experiment Tracking

**Core question:** How do you manage ML experiments and deploy models reliably?

| Tool | Purpose |
|------|---------|
| MLflow | Experiment tracking, model registry, deployment |
| Weights & Biases | Experiment tracking, visualization, collaboration |
| DVC | Data version control (git for data) |
| Docker | Containerize models for reproducible environments |
| GitHub Actions | CI/CD for ML pipelines |

**Exercise:** Set up an MLflow experiment. Train 5 model variations on a dataset. Log parameters, metrics, and artifacts. Register the best model. Write a 1-page guide: "How to set up MLflow for a small team."

---

#### Day 23-25: Build Project - End-to-End ML Pipeline

**Exercise:** Build a complete ML pipeline for a real problem. Choose one:
- **Churn prediction**: Predict SaaS customer churn, deploy as REST API
- **Content moderation**: Classify text as toxic/non-toxic, deploy with monitoring
- **Demand forecasting**: Predict product demand, batch predictions with alerts

Requirements:
- Data pipeline with validation (Great Expectations or Pandera)
- Feature engineering pipeline (reproducible)
- Model training with experiment tracking (MLflow or W&B)
- Model serving (FastAPI or BentoML)
- Monitoring dashboard (Grafana or simple plots)
- README with architecture diagram

Day 23: Data pipeline + feature engineering.
Day 24: Model training + experiment tracking.
Day 25: Serving + monitoring + documentation.

---

### Week 6: Advanced Topics

#### Day 26: Fine-Tuning & Transfer Learning

**Core question:** When should you fine-tune vs train from scratch vs prompt?

| Approach | When | Data Needed | Compute |
|----------|------|-------------|---------|
| Prompt engineering | Quick experiments, general tasks | 0-10 examples | Minimal |
| Few-shot in-context | Specific format, no training infra | 5-50 examples | Minimal |
| LoRA / QLoRA | Domain adaptation, cost-sensitive | 100-10K examples | 1 GPU |
| Full fine-tuning | Maximum performance, custom domain | 10K+ examples | Multi-GPU |
| Train from scratch | Unique architecture, massive data | 100K+ examples | GPU cluster |

**Exercise:** Fine-tune LLaMA 3.2 (1B) using LoRA on a custom dataset (pick a domain: legal, medical, or code). Compare: base model, 100-example fine-tune, 1000-example fine-tune. Measure on a held-out test set.

---

#### Day 27: Evaluation & Debugging ML Models

**Core question:** Your model's accuracy is 85%. Is that good enough, and how do you improve it?

| Technique | What It Reveals |
|-----------|----------------|
| Error analysis | Systematic patterns in failures (certain classes, edge cases) |
| Slice analysis | Performance on subgroups (by geography, device, user segment) |
| Calibration plots | Are predicted probabilities reliable? |
| SHAP values | Which features drive individual predictions? |
| Learning curves | More data, more params, or better features? |
| Ablation studies | Remove components one at a time to measure their contribution |

**Exercise:** Take your best model from the build project (Days 23-25). Perform: error analysis (categorize 50 errors), slice analysis (3 subgroups), SHAP feature importance, and calibration plot. Write a 1-page diagnosis with 3 concrete improvement recommendations.

---

#### Day 28: Responsible AI & ML Ethics

**Core question:** How do you build ML systems that are fair, transparent, and safe?

| Topic | Details |
|-------|---------|
| Bias in data | Historical bias, representation bias, measurement bias |
| Fairness metrics | Demographic parity, equalized odds, individual fairness |
| Model interpretability | SHAP, LIME, attention visualization |
| Data privacy | Differential privacy, federated learning, GDPR/CCPA |
| AI safety considerations | Alignment, robustness, adversarial attacks |

**Exercise:** Audit your build project model for fairness. Define 2 protected attributes. Measure demographic parity and equalized odds. If bias exists, implement one mitigation strategy (resampling, threshold adjustment, or adversarial debiasing). Document findings.

---

#### Day 29: ML System Design Interview Prep

**Core question:** How do you ace an ML system design interview?

| Question Type | Example |
|--------------|---------|
| Recommendation system | "Design YouTube's video recommendation system" |
| Search ranking | "Design Google Search ranking for a new market" |
| Fraud detection | "Design a real-time fraud detection system for payments" |
| Content moderation | "Design an automated content moderation system for a social platform" |
| Ads ranking | "Design the ad ranking system for an e-commerce platform" |

**Framework:** Clarify requirements -> Define ML problem -> Data & features -> Model choice -> Evaluation -> Serving & scaling -> Monitoring

**Exercise:** Practice 2 ML system design questions with Claude as interviewer. 30 minutes each. Draw architecture diagrams. Defend your choices.

---

#### Day 30: Synthesis - ML System Design Document

**Exercise:** Write a complete ML system design document for one of:
- Real-time content recommendation for a news app
- Automated customer support ticket routing
- Dynamic pricing for a ride-sharing platform

Include: problem framing, data pipeline, feature engineering, model architecture, training infrastructure, serving design, monitoring plan, and cost estimate. 4-6 pages with diagrams. This is your Phase 3 portfolio artifact.

---

## Phase 4: Portfolio (Weeks 7-8, Days 31-40)

**Objective:** Build portfolio-worthy projects, practice interviews, and prepare to demonstrate your skills.

### Week 7: Portfolio Projects

#### Day 31-33: Kaggle Competition or Paper Reproduction

**Option A: Kaggle competition.** Enter an active competition. Spend 3 days iterating. Goal: top 20% finish.

**Option B: Paper reproduction.** Pick a recent ML paper and reproduce the key results:
- Suggested: LoRA (Hu et al., 2021), ColBERT (Khattab & Zaharia, 2020), or Flash Attention (Dao et al., 2022)
- Implement the core algorithm, train on a smaller dataset, verify the claimed improvements

---

#### Day 34-35: Portfolio Polish

- Clean up all notebooks and code from the curriculum
- Write README files for each project
- Create a portfolio page (GitHub profile README or personal site)
- Ensure each project has: problem statement, approach, results, what you learned

---

### Week 8: Interview Prep

#### Day 36-37: ML Coding Interview Prep

| Topic | Practice |
|-------|---------|
| Implement algorithms from scratch | Linear regression, logistic regression, k-means, decision tree |
| NumPy/pandas fluency | Data manipulation under time pressure |
| PyTorch fluency | Build a training loop, custom dataset, custom loss |
| SQL for ML | Feature engineering queries, window functions, joins |

**Exercise:** Timed coding challenges (30 min each). Claude provides the problem, you implement, Claude reviews.

---

#### Day 38: ML Theory & Math Interview Prep

| Topic | Common Questions |
|-------|-----------------|
| Bias-variance tradeoff | "Explain overfitting. How do you detect it? How do you fix it?" |
| Regularization | "What's the difference between L1 and L2? When use each?" |
| Gradient descent | "What happens when learning rate is too high? Too low?" |
| Transformers | "Explain self-attention. What's the computational complexity?" |
| Evaluation | "When would you use AUC-ROC vs precision-recall curve?" |

**Exercise:** Rapid-fire Q&A with Claude. 20 questions, 2 minutes each. Then deep-dive on your 3 weakest areas.

---

#### Day 39: Mock Interviews (Full Loop)

Full mock interview with Claude:
1. Round 1 (45 min): ML coding -- implement an algorithm + data pipeline
2. Round 2 (45 min): ML system design -- end-to-end system
3. Round 3 (30 min): ML theory & math -- concepts and tradeoffs
4. Debrief: Detailed feedback with hire/no-hire and improvement areas

---

#### Day 40: Final Portfolio Review & Next Steps

- Review all portfolio projects with Claude
- Identify 3 areas for continued learning
- Set up a learning plan for the next 3 months
- Final progress.md update

---

## Appendix: Key Resources

### Textbooks
1. Goodfellow et al., *Deep Learning* (free at deeplearningbook.org)
2. James et al., *Introduction to Statistical Learning* (ISLR, free)
3. Chip Huyen, *Designing Machine Learning Systems* (O'Reilly, 2022)
4. Bishop, *Pattern Recognition and Machine Learning*

### Courses
1. Stanford CS229: Machine Learning (Andrew Ng, free on YouTube)
2. Stanford CS231n: CNNs for Visual Recognition (free on YouTube)
3. Stanford CS224n: NLP with Deep Learning (free on YouTube)
4. Fast.ai: Practical Deep Learning for Coders (free, fast.ai)

### Tools & Platforms
1. Kaggle (kaggle.com) -- datasets, competitions, notebooks
2. HuggingFace (huggingface.co) -- models, datasets, Transformers library
3. Weights & Biases (wandb.ai) -- experiment tracking
4. Papers With Code (paperswithcode.com) -- papers + implementations

---

*Last updated: 2026-03-19*
