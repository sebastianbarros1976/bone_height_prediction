# 🧠 Bone Age and Final Height Predictor

**Predict bone age from X-ray images and estimate final adult height using biological maturity and genetic target!**

This project uses a deep learning model based on **ConvNeXt-Tiny** combined with **tabular features** to predict a child's **bone age** from hand X-ray images.  
It then calculates the **expected final height** using **chronological age**, **bone age**, **current height**, and **parental heights**.

---

## 📋 Project Structure

- `bone_age_prediction.ipynb`: Main notebook for model training, evaluation, and app creation.
- `requirements.txt`: Python dependencies for reproducing the environment.
- `README.md`: This file – explaining how everything works.
- (Optional) `models/`: Folder to store your trained models (`.pth` files).

---

## 🚀 How to Run the Project

1. **Clone this repository:**

```bash
git clone https://github.com/your-username/bone-age-final-height-prediction.git
cd bone-age-final-height-prediction
```

2. **Install dependencies:**

```bash
pip install -r requirements.txt
```

3. **Launch the Gradio app (if using a script):**

```bash
python app.py
```

*Or run the notebook directly in Google Colab!*

---

## 🛠️ Requirements

This project requires Python 3.8+ and the following libraries:

- torch
- torchvision
- gradio
- scikit-learn
- pandas
- numpy
- matplotlib
- tqdm
- Pillow

Install them easily with:

```bash
pip install -r requirements.txt
```

---

## 📊 Model Overview

- **Image Backbone:** ConvNeXt-Tiny (pretrained on ImageNet, fine-tuned on X-rays).
- **Tabular Input:** Sex (encoded as binary).
- **Final Layers:** Combined CNN + tabular MLP, ending in a single regression output (bone age in months).
- **Loss Function:** Mean Squared Error (MSE).
- **Optimizer:** Adam.
- **Evaluation:** MAE, MSE, R² Score, Classification Report (by bone age ranges).

---

## 📈 Final Height Prediction Logic

After predicting **bone age**:

1. Calculate **maturity status** (Normal, Advanced, Delayed).
2. Estimate **residual growth** based on bone age (custom growth table).
3. Predict final height = **current height + expected growth**.
4. Clip prediction within **genetic target bands** based on parental heights.

---

## ⚠️ Dataset Disclaimer

Due to licensing restrictions, **the RSNA Bone Age Challenge dataset is not included** in this repository.

You must **download it manually** from the official RSNA page:

➡️ [RSNA Pediatric Bone Age Challenge](https://www.rsna.org/rsnai/ai-image-challenge/rsna-pediatric-bone-age-challenge-2017)

Once downloaded:
- Place the images and annotation CSVs accordingly.
- Update paths if necessary in the notebook.

---

## 📸 App Demo

The Gradio app allows users to:

- Upload a **hand X-ray**.
- Enter **chronological age**, **current height**, **father's height**, **mother's height**, and **sex**.
- Instantly get:
  - Predicted Bone Age
  - Expected Growth Remaining
  - Predicted Final Height
  - Genetic Target Height
  - Allowed Height Range

---

## 🤝 Contributions

Pull requests are welcome!  
For major changes, please open an issue first to discuss what you would like to change.

---

## 📜 License

This project is licensed under the MIT License.
