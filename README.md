# ☁️ Cloud Type Classification

*or: "I taught a computer to look up and guess"*

You know that thing where you lie in the grass, point at the sky, and confidently declare "that one's a dragon"? Yeah, a CNN does that now, except instead of dragons it says "Cumulonimbus" and instead of being charmingly wrong it's usually right. Progress, I guess.

Somewhere between a meteorologist's PhD and a toddler's finger-painting confidence, there's a model that stares at 2,543 photos of the sky and sorts them into 11 flavors of "yep, that's a cloud." This is that model. Two of them, actually, because one model felt too easy.

---

## 🌤️ The Two Clouds You Can Summon

**`Baseline CNN`** — *"I built this from scratch and I'm emotionally attached to it."*
A lightweight 3-block CNN, trained from zero, no pre-trained shortcuts, no cheating. Just you, some convolutions, and the quiet dignity of doing it the hard way first.

**`EfficientNetB0 (Transfer Learning)`** — *"Someone else already learned to see, so I borrowed their eyes."*
Pre-trained on ImageNet, fine-tuned on clouds. This one shows up already knowing what an edge is, which feels a little unfair to Baseline CNN, but here we are.

---

## 🗂️ What It's Actually Sorting

The **CCSN (Cirrus Cumulus Stratus Nimbus) Database** — 2,543 ground-based sky photos, each one quietly judged and filed into one of 11 WMO-defined cloud genera:

| Code | Genus | Code | Genus | Code | Genus |
|------|-------------|------|---------------|------|--------------|
| `Ac` | Altocumulus | `Cs` | Cirrostratus | `Sc` | Stratocumulus |
| `As` | Altostratus | `Ct` | Contrail | `St` | Stratus |
| `Cb` | Cumulonimbus | `Cu` | Cumulus | | |
| `Cc` | Cirrocumulus | `Ns` | Nimbostratus | | |
| `Ci` | Cirrus | | | | |

Yes, `Ct` (Contrail) is in there. Turns out humans have been quietly polluting the training data of the sky for decades, so we might as well classify it.

📦 [Grab the dataset here](https://drive.google.com/file/d/1OY6ljltOdKAeTIQowI8fARxOB7pzHt_I/view?usp=drive_link)

---

## 🚀 Getting This Running On Your Machine

### Prerequisites
Python 3.8+. That's it. That's the bar.

### 1. Clone it
```bash
git clone https://github.com/your-username/cloud-type-classification.git
cd cloud-type-classification
```

### 2. Give it its own room (virtual environment, recommended)
```bash
python -m venv venv
```

**Windows:**
```powershell
cd venv/Scripts
./Activate.ps1
```

**macOS / Linux:**
```bash
cd venv/bin
source ./activate
```

### 3. Feed it its dependencies
```bash
pip install -r requirements.txt
```

### 4. Get the sky into the folder
Download the dataset from the Drive link above and extract it into a folder named `dataset/` in the project root. The model can't classify clouds it's never seen — shocking, I know.

### 5. Open the notebook and press go
```bash
jupyter notebook
```
Open `cloud_type_classification.ipynb`, run it top to bottom, and watch a machine develop stronger opinions about cumulus clouds than you have.

---

## 🧰 What's Under the Hood

- **TensorFlow / Keras** — building, augmenting, and training the models
- **OpenCV** — getting the images in and making them presentable
- **Scikit-Learn** — stratified splits, class weights, and telling you honestly how well it actually did
- **Matplotlib / Seaborn** — the graphs and confusion matrices that make the results look official

---

*No clouds were harmed in the making of this project. Several were, however, deeply misunderstood by an early checkpoint of the model, and we've chosen not to talk about that.*
