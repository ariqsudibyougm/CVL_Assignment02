# CVL_Assignment02
 # Analisis Hasil Deteksi Objek

 Dataset : https://www.kaggle.com/datasets/malder82fox/dataset-cans

## 1. Metode yang Digunakan
Pada eksperimen ini, sistem **deteksi objek** diimplementasikan **tanpa menggunakan library deteksi** seperti YOLO atau Faster R-CNN.  
Pendekatan yang digunakan adalah metode **klasik pengolahan citra**, yang terdiri dari beberapa tahapan utama:

- Konversi citra ke **grayscale** dan penerapan **Gaussian Blur** untuk mengurangi noise.  
- **Thresholding Otsu** serta operasi morfologi (**opening** dan **closing**) untuk memisahkan objek dari latar belakang.  
- **Deteksi kontur** menggunakan `cv2.findContours` untuk memperoleh bounding box setiap objek yang terdeteksi.  
- Perbandingan hasil deteksi dengan **ground truth** (label YOLO) menggunakan metrik **IoU (Intersection over Union)** dan **akurasi**.

---

## 2. Metrik Evaluasi

**Akurasi** mengukur seberapa banyak deteksi yang sesuai dengan objek sebenarnya:


**IoU (Intersection over Union)** mengukur tingkat tumpang tindih antara bounding box hasil deteksi dengan ground truth:


---

## 3. Ringkasan Hasil

| Frame       | GT  | Detected | Akurasi | Mean IoU |
|--------------|-----|-----------|----------|-----------|
| frame_0000   | 60  | 61        | 100%     | 0.437     |
| frame_0001   | 55  | 59        | 100%     | 0.437     |
| frame_0002   | 59  | 60        | 100%     | 0.436     |
| frame_0003   | 60  | 57        | 95%      | 0.427     |
| frame_0004   | 62  | 64        | 100%     | 0.444     |
| **Rata-rata** | —   | —         | **99%**  | **0.436** |

---

## 4. Analisis Performa

Nilai **akurasi rata-rata 99%** menunjukkan bahwa sebagian besar objek berhasil terdeteksi dengan baik menggunakan metode segmentasi sederhana.  
Jumlah objek hasil deteksi yang hampir sama dengan ground truth menandakan sistem cukup stabil dalam mengenali area objek.

Nilai **IoU rata-rata 0.436** menunjukkan bahwa meskipun posisi deteksi sudah cukup baik, bentuk dan ukuran bounding box belum sepenuhnya sejajar dengan ground truth.  
Hal ini wajar karena bounding box dihasilkan dari kontur hasil segmentasi, sehingga sedikit pergeseran pada tepi objek dapat menurunkan nilai IoU.  
Berbeda dengan metode deep learning yang dapat mempelajari bentuk objek secara presisi, pendekatan ini sepenuhnya bergantung pada **perbedaan intensitas piksel**.

Secara keseluruhan, sistem ini menunjukkan kinerja yang sangat baik dalam **mendeteksi dan menghitung jumlah objek**, meskipun **akurasi posisi bounding box** masih dapat ditingkatkan.

---

## 6. Kesimpulan

Metode deteksi objek berbasis segmentasi dan kontur sederhana ini memberikan hasil yang cukup baik pada dataset pengujian, dengan akurasi tinggi (99%) dan IoU rata-rata 0.436.  
Meskipun belum seakurat model deep learning, metode ini efektif untuk **deteksi cepat tanpa pelatihan model** dan dapat menjadi dasar bagi pengembangan sistem deteksi yang lebih kompleks di tahap selanjutnya.

