# PROJECT UAS PENGOLAHAN CITRA 2024

## Deteksi Tepi Pola Objek dengan OpenCV

## Teori Pendukung

Deteksi tepi adalah teknik mendasar dalam pengolahan citra yang digunakan untuk mengidentifikasi tepi atau batas suatu objek dalam gambar. Metode ini sering digunakan dalam berbagai aplikasi seperti pengenalan objek, analisis citra, dan visi komputer. Algoritma Canny Edge Detection adalah salah satu teknik deteksi tepi yang paling populer dan efektif. Algoritma ini bekerja dengan langkah-langkah berikut:

1. **Pengaburan (Gaussian Blurring)**: Mengurangi noise dalam gambar.
2. **Deteksi Gradien**: Menggunakan operator Sobel untuk mendeteksi perubahan intensitas yang signifikan.
3. **Non-maximum Suppression**: Menghilangkan piksel yang bukan merupakan bagian dari tepi.
4. **Hysteresis Thresholding**: Menggunakan dua ambang batas untuk mendeteksi tepi yang kuat dan lemah, serta menghubungkan tepi yang lemah ke tepi yang kuat jika mereka berdekatan.

Setelah deteksi tepi, langkah selanjutnya adalah deteksi kontur. Kontur adalah kurva yang menghubungkan semua titik kontinu (berdekatan) yang memiliki intensitas warna yang sama. Dalam OpenCV, deteksi kontur dilakukan dengan menggunakan fungsi `findContours`.

## Cara Menyelesaikan Proyek

1. **Mengimpor Pustaka yang Diperlukan**
   ```python
   import cv2
   import numpy as np
   import matplotlib.pyplot as plt
   ```

2. **Membaca dan Mengonversi Gambar**
- Membaca gambar menggunakan cv2.imread().
- Mengonversi gambar dari format BGR (Blue, Green, Red) ke RGB (Red, Green,Blue)menggunakan cv2.cvtColor().
    ```python
    image = cv2.imread("image/FotoHilmy.jpg")
    image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
    ```
  ![App Screenshot](./Screenshots/FotoHilmy.jpg)

3. **Mengonversi Gambar ke Grayscale**
- Mengubah gambar RGB ke grayscale untuk mempermudah proses deteksi tepi.
    ```python
    gray_image = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
    ```

4. **Deteksi Tepi Menggunakan Algoritma Canny**
- Menggunakan fungsi cv2.Canny() dengan dua ambang batas untuk mendeteksi tepi dalam gambar grayscale.Menggunakan fungsi cv2.Canny() dengan dua ambang batas untuk mendeteksi tepi dalam gambar grayscale.
    ```python
    edges = cv2.Canny(gray_image, 100, 200)
    ```

5. **Deteksi Kontur**
- Menggunakan fungsi cv2.findContours() untuk menemukan kontur dalam gambar hasil deteksi tepi.
- Menggambar kontur yang ditemukan pada gambar asli.
    ```python
    contours, _ = cv2.findContours(edges, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
    contour_image = image.copy()
    cv2.drawContours(contour_image, contours, -1, (0, 255, 0), 2)
    ```

6. **Menampilkan Gambar Hasil**
- Menggunakan matplotlib untuk menampilkan gambar asli, hasil deteksi tepi, dan hasil deteksi kontur dalam satu plot.
    ```python
    plt.figure(figsize=(15, 5))

    plt.subplot(1, 3, 1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis('off')

    plt.subplot(1, 3, 2)
    plt.title("Canny Edge Detection")
    plt.imshow(edges, cmap='gray')
    plt.axis('off')

    plt.subplot(1, 3, 3)
    plt.title("Contours Detection")
    plt.imshow(contour_image)
    plt.axis('off')

    plt.show()
    ```
![App Screenshot](./Screenshots/hasil.png)

7**Jurnal Terkait**
- Putu Teguh Krisna Putra, Ni Kadek Ayu Wirdiani (2014). Pengolahan Citra Digital Deteksi Tepi Untuk Membandingkan Metode Sobel, Robert dan Canny. MERPATI VOL. 2, NO. 2, AGUSTUS 2014 ISSN: 2252-3006. Jurusan Teknologi Informasi, Fakultas Teknik, Universitas Udayana, Bukit Jimbaran, Bali, Indonesia, telp. +62361703315. Email: teguhkrisna91@yahoo.com, ayu_wirdi@yahoo.com.

- Kornelis Letelay (2019). Perbandingan Kinerja Metode Deteksi Tepi Pada Citra. J-ICON, Vol. 7 No. 1, Maret 2019, pp. 1~8. Jurusan Ilmu Komputer, Fakultas Sains dan Teknik, Universitas Nusa Cendana. Email: kletelay@gmail.com.

# Selesai :)