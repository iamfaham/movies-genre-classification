# 🎬 Movies Genre Classification

A multimodal machine learning project to classify movie genres using both **plot descriptions (text)** and **poster images (vision)**. The model predicts one of 7 genres: **Action**, **Animation**, **Comedy**, **Documentary**, **Drama**, **Horror**, and **Others**.

This project was developed using data scraped from the TMDB API and includes an interactive [Gradio web app](https://huggingface.co/spaces/iamfaham/movie_genre_classifier_ui) hosted on Hugging Face Spaces.

---

## 🚀 Demo

👉 Try it live: [Movie Genre Classifier Gradio App](https://huggingface.co/spaces/iamfaham/movie_genre_classifier_ui)

---

## 🧠 Model Overview

- **Text Embedding Model:** [`mixedbread-ai/mxbai-embed-large-v1`](https://huggingface.co/mixedbread-ai/mxbai-embed-large-v1)
- **Image Feature Extractor:** ResNet-50 (pretrained on ImageNet)
- **Fusion Model:** A feedforward neural network combining both modalities into a single prediction.

The model was trained using **52000 movie entries**, processed from an initial ~60000 entries obtained via the TMDB API.

---

## 📊 Performance

| Model Type         | Accuracy |
| ------------------ | -------- |
| Text-only          | ~60%     |
| Image-only         | ~54%     |
| **Fusion (Final)** | **~66%** |

> 🔍 The relatively lower accuracy is due to the **"Others"** category being a catch-all genre that introduces ambiguity and class imbalance. We are working on fixing this issue.

---

## 🏗️ How It Works

1. **User Input:**

   - Movie description (text)
   - Movie poster (image)

2. **Processing:**

   - The text is embedded using `mixedbread-ai/mxbai-embed-large-v1`.
   - The image is encoded using ResNet-50 up to the penultimate layer.
   - Both embeddings are concatenated and passed into a 5-layer fully connected classifier.

3. **Output:**
   - A ranked list of genre probabilities (top-1 shown as predicted genre).

---

## 📁 Genres Used

```
['Action', 'Animation', 'Comedy', 'Documentary', 'Drama', 'Horror', 'Others']
```

---

## 🧪 Dataset Details

- **Source:** [TMDB API](https://developer.themoviedb.org/docs)
- **Raw Size:** ~60,000 movie records
- **Final Size (after filtering and cleaning):** ~52,000
- **Inputs Used:**
  - Cleaned plot descriptions
  - Resized movie posters
- **Dataset Link:** [👉 Click here to view/download dataset](https://drive.google.com/file/d/16u_AiP8-HWbHBNEh32apXSp4I9M-_Pht/view?usp=drive_link)

---

## 🔗 Deployment

The model and app are hosted on Hugging Face:

- [🔗 Live Gradio App](https://huggingface.co/spaces/iamfaham/movie_genre_classifier_ui)
- [🧠 Model Weights Repo](https://huggingface.co/iamfaham/movie-genre-classifier)

---

## 🙌 Authors

- **Syed Mohammed Faham** — [LinkedIn](https://linkedin.com/in/iamfaham)
- **Anjaneya Bharadwaj** — [LinkedIn](https://linkedin.com/in/anjaneya-bhardwaj)

---

## 📌 Notes

- This project started as an exploration using **text-only** and **image-only** pipelines.
- Results significantly improved when we **fused both modalities** into a single classifier — and we stuck with that.
- No fine-tuning was done on the embedding models; only the classifier was trained end-to-end.
- If the IMDB_Genre_Prediction_Final.ipynb file does not open on github, check it out on [Google Colab](https://colab.research.google.com/drive/17WX3s4wscZutTN7J5xtV2un8UTwfwRqz?usp=sharing) 

---

## 💬 Feedback

Feel free to open issues or suggestions for improvement. Contributions and ideas are always welcome!
