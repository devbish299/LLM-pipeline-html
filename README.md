# LLM Pipeline Explorer 🌌

An interactive, single-file web application demonstrating how human text is converted into tokens and projected into 3D semantic vector space.

Built with vanilla JavaScript, modern dark-mode glassmorphism styling, and Plotly.js for interactive 3D scientific visualization.

![LLM Pipeline Explorer](https://img.shields.io/badge/Status-Complete-00f5d4?style=for-the-badge)
![Plotly.js](https://img.shields.io/badge/Plotly.js-3D_WebGL-8b5cf6?style=for-the-badge)
![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-Zero_Dependencies-f43f5e?style=for-the-badge)

---

## 🌟 Key Features

### 1. Interactive Tokenizer & Subword Fallback
- **Vocabulary Learner:** Learns tokens and morphological units from training text, assigning deterministic integer Token IDs (`<PAD>`: 0, `<UNK>`: 1).
- **Subword Fallback (BPE / WordPiece style):** Demonstrates greedy morphological subword decomposition:
  - `dogs` $\rightarrow$ `dog` (Stem) + `+s` (Subword)
  - `liked` $\rightarrow$ `like` (Stem) + `+d` (Subword)
  - `sunny` $\rightarrow$ `sun` (Stem) + `+ny` (Subword)
  - Unseen words (e.g. `zebra`) fall back cleanly to `<UNK>`.
- **Vector Array View:** Renders the resulting numeric token array `[ 2, 8, 28, 20, 29, 2, 27, 31, 1, 7 ]` with one-click copy.

### 2. Embeddings in 3D Semantic Space
- **High-Dimensional Latent Vectors:** Computes 20-dimensional semantic latent vectors based on weighted word associations and syntactic roles.
- **Pure JavaScript PCA / SVD:** Uses the Jacobi Eigenvalue algorithm on the sample covariance matrix to project high-dimensional embeddings into 3D coordinates $(X, Y, Z)$ with zero server dependencies.
- **Natural Semantic Clustering:**
  - 🟢 **Domestic Animals & Lounging** (*cat, kitten, dog, rug, mat*)
  - 🟣 **Software & Programming** (*coding, python, passion, developer*)
  - 🔴 **Polysemy Bridge:** *"Pythons are large snakes"* sits between animal biology and programming!
  - 🔵 **Finance & Markets** (*stocks, share prices, crashed, fell sharply*)
- **Interactive 3D Scatter Plot (Plotly.js):** Rotate, zoom, inspect coordinates, or snap to perspective presets (`3D View`, `Top (XY)`, `Side (XZ)`).
- **Cosine Similarity Inspector:** Computes exact cosine similarity scores ($\cos \theta \in [-1, 1]$) with color-coded gradient progress bars. Clicking any item centers the 3D camera on its coordinates.

### 3. Live Query Projection
- Type any word or sentence (or click preset tags like `puppy`, `python developer`, `stock selloff`).
- Watch it tokenize live, compute its dense semantic vector, project onto the PCA basis, and render as a glowing gold diamond marker in the 3D space.

---

## 🚀 Deployment to Vercel

This repository is structured for zero-configuration static deployment on Vercel:

1. Go to [Vercel](https://vercel.com) and click **"Add New" > "Project"**.
2. Import `devbish299/LLM-pipeline-html`.
3. Keep default settings:
   - **Framework Preset:** `Other`
   - **Root Directory:** `./`
4. Click **Deploy**. Vercel will immediately serve `index.html` on a global CDN.

---

## 💻 Local Usage

Simply clone and open `index.html` in any browser:

```bash
git clone https://github.com/devbish299/LLM-pipeline-html.git
cd LLM-pipeline-html
open index.html
```

Or serve locally with Python:

```bash
python3 -m http.server 8000
# Open http://localhost:8000
```
