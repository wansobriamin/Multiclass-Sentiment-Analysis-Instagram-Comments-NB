# Analisis Sentimen Multikelas pada Komentar Instagram Menggunakan Naive Bayes dan LIME

Proyek ini mengimplementasikan sistem klasifikasi sentimen multikelas (**Positif, Negatif, Netral**) pada data komentar Instagram berbahasa Indonesia. Proyek ini dibangun berdasarkan metodologi penelitian yang dipublikasikan dalam [Jurnal Riset Informatika](https://ejournal.kresnamediapublisher.com/index.php/jri/article/view/500), dengan pengembangan pada tahap preprocessing, perbandingan varian model Naive Bayes, dan interpretabilitas model menggunakan LIME.

## Deskripsi Proyek
Tujuan utama dari proyek ini adalah untuk menganalisis opini publik (khususnya terkait isu politik dan ekonomi Indonesia) dari kolom komentar Instagram. Sistem ini memproses data teks mentah, melakukan serangkaian tahap preprocessing bahasa Indonesia, mengekstraksi fitur menggunakan TF-IDF, dan melatih model klasifikasi menggunakan **Multinomial Naive Bayes (MNB)** serta **Complement Naive Bayes (CNB)**.

## Fitur Utama
- **Preprocessing Teks Bahasa Indonesia:** Cleaning (URL, mention, hashtag), Case Folding, Normalisasi slang, Stopword Removal (dengan penanganan kata negasi), dan Stemming menggunakan library `Sastrawi`.
- **Ekstraksi Fitur:** Term Frequency-Inverse Document Frequency (TF-IDF).
- **Pemodelan:** Perbandingan performa antara Multinomial Naive Bayes dan Complement Naive Bayes.
- **Evaluasi Model:** Accuracy, F1-Macro, Classification Report, Confusion Matrix, dan ROC-AUC (One-vs-Rest).
- **Interpretabilitas Model:** Penggunaan library `LIME` (Local Interpretable Model-agnostic Explanations) untuk menjelaskan alasan di balik prediksi model pada tingkat instance (lokal).

## Dataset
- **Sumber:** Komentar Instagram (di-scrape dan dilabeli manual).
- **Jumlah Data:** 1.326 baris data mentah, dibersihkan menjadi 1.178 baris data valid.
- **Distribusi Kelas:** Positif (~704), Netral (~309), Negatif (~296). *(Data tidak seimbang/imbalanced, sehingga Complement NB diuji untuk mengatasi bias ini)*.
- **Format:** `.xlsx`.

## Multinomial Naive Bayes (MNB)
MNB adalah algoritma standar untuk klasifikasi teks. 
- **Konsep:** MNB mengasumsikan bahwa frekuensi kemunculan kata dalam sebuah dokumen mengikuti distribusi multinomial. 
- **Cara Kerja:** Algoritma ini menghitung probabilitas sebuah kata muncul dalam kelas tertentu (misal: probabilitas kata "bagus" muncul di kelas Positif). Prediksi akhir didasarkan pada perkalian probabilitas semua kata dalam teks untuk setiap kelas.

## Complement Naive Bayes (CNB)
CNB adalah adaptasi dari MNB yang secara spesifik dirancang untuk menangani **dataset yang tidak seimbang (*imbalanced datasets*)**.
- **Konsep:** Alih-alih menghitung probabilitas kata di dalam sebuah kelas, CNB menghitung probabilitas kata di dalam **komplemen kelas** (yaitu, semua kelas *kecuali* kelas target).
- **Cara Kerja:** Untuk memprediksi kelas "Negatif", CNB akan melihat seberapa sering kata tersebut muncul di kelas "Positif" dan "Netral". Jika sebuah kata jarang muncul di komplemen kelas Negatif, maka kata tersebut memiliki bobot tinggi untuk mengindikasikan kelas Negatif.

## Ablation Study

Untuk menemukan representasi fitur terbaik, dilakukan studi ablasi dengan memvariasikan konfigurasi TF-IDF dan model

## Kesimpulan

Berdasarkan eksperimen dan evaluasi yang telah dilakukan, dapat ditarik beberapa kesimpulan utama:

1. **Preprocessing adalah Kunci:** Tahap normalisasi *slang* dan *stemming* menggunakan Sastrawi sangat krusial untuk mereduksi dimensi fitur dan meningkatkan akurasi model pada teks bahasa Indonesia non-formal.
2. **MNB vs CNB:** Multinomial Naive Bayes (MNB) dengan konfigurasi TF-IDF unigram (1,1) memberikan performa prediksi terbaik secara umum. Namun, Complement Naive Bayes (CNB) terbukti lebih unggul dalam menangani ketidakseimbangan kelas.
3. **Interpretabilitas dengan LIME:** Implementasi LIME berhasil memvalidasi bahwa model tidak "menghafal" data, tetapi benar-benar mempelajari pola linguistik. LIME mampu menyoroti kata kunci (seperti *"moji"*, *"ngk"*, *"ang"*) yang secara logis berkontribusi terhadap keputusan klasifikasi, menjadikan model ini transparan dan dapat dipercaya untuk penelitian lebih lanjut.

---

## Lisensi

Project ini dapat digunakan untuk keperluan edukasi saja.

Copyright (c) 2026 wansobriamin
