# 🔍 Fine-Tuned CLIP-Based Image Search Engine

An advanced **text-to-image semantic search engine** built on top of OpenAI’s [CLIP], fine-tuned on a custom dataset for higher accuracy and domain adaptability.

This project allows users to enter a text query (e.g., *“A golden retriever on a beach”*) and returns images that **semantically** match the query based on joint image-text embeddings.


## 📌 Table of Contents

- [📌 Table of Contents](#-table-of-contents)
- [🎯 Motivation](#-motivation)
- [🧠 How It Works](#-how-it-works)
- [✨ Features](#-features)
- [📸 Demo](#-demo)
- [🧰 Project Structure](#-project-structure)
- [⚙️ Installation](#️-installation)
- [🚀 Running the Project](#-running-the-project)
- [🧪 Fine-Tuning](#-fine-tuning)
- [📦 Model Weights](#-model-weights)
- [🗂 Dataset Format](#-dataset-format)


## 🎯 Motivation

OpenAI’s CLIP is a powerful model trained on a large variety of internet image-text pairs. However, **general-purpose CLIP sometimes underperforms** in specific domains (e.g., medical images, artworks, or custom products).  
To solve this, we **fine-tune CLIP** on a domain-specific dataset to enhance retrieval relevance and accuracy.


## 🧠 How It Works

### 🔁 Workflow

1. **Encoding**:
    - Images and text queries are encoded into vector embeddings using the CLIP model.
2. **Similarity Matching**:
    - Cosine similarity is calculated between the text query and each image embedding.
3. **Retrieval**:
    - The top `k` most similar images are returned.

### ⚙️ Architecture

                |───────────────┐
                │  Text Query   │
                └──────┬────────┘
                       │
         ┌─────────────▼──────────────┐
         │  CLIP Text Encoder (ViT)   │
         └─────────────┬──────────────┘
                       │
                Text Embedding
                       │
              ┌────────▼────────┐
              │ Image Embedding │◄── Image Dataset
              └────────┬────────┘
                       │
           Cosine Similarity Search
                       │
                ┌─────▼─────┐
                │  Top-K    │
                │  Results  │
                └───────────┘


## ✨ Features

- ✅ **Fine-tuned CLIP** for domain-specific performance
- 🔍 **Text-to-Image Retrieval** using cosine similarity
- 📦 **Embeddings caching** for speed optimization
- 🧪 **Jupyter notebook** with end-to-end fine-tuning and search pipeline
- 🖼️ Easily extendable for **custom datasets**


## 📸 Demo
### Query: `"A child running with a dog in the park"`
Top results: ✅ Precise image retrieved based on learned semantics.


## ⚙️ Installation

> 🔧 Python 3.8+ and PyTorch ≥ 1.8 are required.
# 1. Clone the repository
git clone https://github.com/your-username/clip-image-search.git
cd clip-image-search

# 2. Install dependencies
pip install -r requirements.txt

## 🚀 Running the Project
🧪 Use Jupyter Notebook
-jupyter notebook fine-tuned-clip-based-image-search-engine.ipynb.

## 🧪 Fine-Tuning
To fine-tune CLIP on your own dataset:

Format your dataset as:
-image_path,text_description
-data/img1.jpg,"A cat on a sofa"
-data/img2.jpg,"A sunset over the hills"
-Update the notebook's dataset loading path.
-Run all training cells.
-Save the fine-tuned model to model/.

## 📦 Model Weights
Model files:
model/
├── pytorch_model.bin       # Standard PyTorch checkpoint
└── model.safetensors       # Optional: optimized format

## 🗂 Dataset Format
Either as CSV:
-image_path            |text_description
-images/cat.jpg        |A cat on a sofa
-images/dog.jpg        |A dog running in the field


