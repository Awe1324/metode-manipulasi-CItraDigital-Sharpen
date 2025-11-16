# Sharpening Gambar Menggunakan OpenCV dan Python

Dokumen ini menjelaskan cara melakukan **sharpening (penajaman)** pada gambar menggunakan Python, OpenCV, NumPy, dan Matplotlib. Metode ini umum digunakan untuk memperjelas detail gambar, terutama pada foto hitam putih atau foto lama.

---

## 1. Deskripsi Proyek

Proyek ini bertujuan untuk:

* Membaca gambar menggunakan OpenCV
* Mengonversi gambar menjadi grayscale
* Menerapkan teknik **sharpening** menggunakan kernel 3x3
* Menampilkan hasil penajaman menggunakan Matplotlib

Metode sharpening yang digunakan akan meningkatkan detail tepi (edge) pada gambar sehingga tampak lebih jelas ketika diperbesar atau dilihat dari dekat.

---

## 2. Library yang Digunakan

Pastikan telah menginstall library berikut:

```
pip install opencv-python
pip install numpy
pip install matplotlib
```

---

## 3. Penjelasan Kernel Sharpening

Kernel yang digunakan:

```
[ 0, -1,  0]
[-1,  5, -1]
[ 0, -1,  0]
```

* Angka **5** di tengah berfungsi memperkuat pixel utama.
* Angka **-1** di sekelilingnya mengurangi nilai pixel tetangga.
* Hasil akhirnya membuat garis dan detail tampak lebih tegas.

---

## 4. Source Code (Jupyter Notebook)

Berikut kode lengkap yang dapat digunakan di file `.ipynb`:

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Membaca gambar
ing = cv2.imread('foto.jpg')

# Mengubah ke grayscale
gray = cv2.cvtColor(ing, cv2.COLOR_BGR2GRAY)

# Kernel sharpening
kernel = np.array([[0, -1, 0],
                   [-1, 5, -1],
                   [0, -1, 0]])

# Proses sharpening
sharpened = cv2.filter2D(gray, -1, kernel)

# Tampilkan hasil
plt.figure(figsize=(12,5))
plt.subplot(1,2,1)
plt.imshow(gray, cmap='gray')
plt.title('Gambar Asli')
plt.axis('off')

plt.subplot(1,2,2)
plt.imshow(sharpened, cmap='gray')
plt.title('Hasil Sharpening')
plt.axis('off')
```

---

## 5. Cara Kerja Program

1. Gambar dibaca dalam format BGR.
2. Dikoversi ke grayscale agar sharpening lebih efektif.
3. Kernel sharpening diterapkan menggunakan operasi konvolusi.
4. Hasil sebelum dan sesudah ditampilkan untuk dibandingkan.

---

## 6. Hasil yang Diharapkan

* Gambar menjadi lebih tajam
* Detail wajah, pakaian, atau objek lebih terlihat
* Tepi objek lebih kuat

---

## 7. Catatan Tambahan

* Semakin besar nilai tengah kernel, semakin kuat efek sharpening.
* Jika gambar menjadi terlalu tajam atau noisy, turunkan nilai kernel.
* Metode ini aman dan sangat cocok untuk tugas manipulasi citra digital.

---

## 8. Lisensi

Proyek ini bebas digunakan untuk keperluan pembelajaran dan tugas akademik.
