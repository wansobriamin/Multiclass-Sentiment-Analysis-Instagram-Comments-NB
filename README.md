# Analisis Sentimen Multikelas pada Komentar Instagram Menggunakan Naive Bayes dan LIME

Proyek ini mengimplementasikan sistem klasifikasi sentimen multikelas (**Positif, Negatif, Netral**) pada data komentar Instagram berbahasa Indonesia. Proyek ini dibangun berdasarkan metodologi penelitian yang dipublikasikan dalam [Jurnal Riset Informatika](https://ejournal.kresnamediapublisher.com/index.php/jri/article/view/500), dengan pengembangan pada tahap preprocessing, perbandingan varian model Naive Bayes, dan interpretabilitas model menggunakan LIME.

## 📌 Deskripsi Proyek
Tujuan utama dari proyek ini adalah untuk menganalisis opini publik (khususnya terkait isu politik dan ekonomi Indonesia) dari kolom komentar Instagram. Sistem ini memproses data teks mentah, melakukan serangkaian tahap preprocessing bahasa Indonesia, mengekstraksi fitur menggunakan TF-IDF, dan melatih model klasifikasi menggunakan **Multinomial Naive Bayes (MNB)** serta **Complement Naive Bayes (CNB)**.

## ✨ Fitur Utama
- **Preprocessing Teks Bahasa Indonesia:** Cleaning (URL, mention, hashtag), Case Folding, Normalisasi slang, Stopword Removal (dengan penanganan kata negasi), dan Stemming menggunakan library `Sastrawi`.
- **Ekstraksi Fitur:** Term Frequency-Inverse Document Frequency (TF-IDF).
- **Pemodelan:** Perbandingan performa antara Multinomial Naive Bayes dan Complement Naive Bayes.
- **Evaluasi Model:** Accuracy, F1-Macro, Classification Report, Confusion Matrix, dan ROC-AUC (One-vs-Rest).
- **Interpretabilitas Model:** Penggunaan library `LIME` (Local Interpretable Model-agnostic Explanations) untuk menjelaskan alasan di balik prediksi model pada tingkat instance (lokal).

## 📊 Dataset
- **Sumber:** Komentar Instagram (di-scrape dan dilabeli manual).
- **Jumlah Data:** 1.326 baris data mentah, dibersihkan menjadi 1.178 baris data valid.
- **Distribusi Kelas:** Positif (~704), Netral (~309), Negatif (~296). *(Data tidak seimbang/imbalanced, sehingga Complement NB diuji untuk mengatasi bias ini)*.
- **Format:** `.xlsx` (`data_Labeling_gabung.xlsx`).

## 🛠️ Teknologi yang Digunakan
- **Bahasa Pemrograman:** Python 3.x
- **Data Manipulation:** Pandas, NumPy
- **Natural Language Processing:** NLTK, Sastrawi (Stemmer & Stopwords Bahasa Indonesia), Re (Regular Expression)
- **Machine Learning:** Scikit-Learn (TF-IDF, MNB, CNB, Metrics)
- **Model Explainability:** LIME
- **Visualisasi:** Matplotlib, Seaborn

## 📂 Struktur Proyek
```text
├── NBC.ipynb                      # Notebook utama berisi seluruh alur kerja (EDA, Preprocessing, Modeling, Evaluation)
├── data_Labeling_gabung.xlsx      # Dataset komentar Instagram yang telah dilabeli
├── requirements.txt               # Daftar dependensi library Python
└── README.md                      # Dokumentasi proyek ini