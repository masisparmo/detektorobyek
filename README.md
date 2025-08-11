# Dokumentasi: Aplikasi Detektor Objek Jalan Raya
## 1. Deskripsi Aplikasi
**Detektor Objek Jalan Raya** adalah sebuah aplikasi web interaktif yang dirancang sebagai alat pembelajaran dan analisis di bidang Computer Vision. Aplikasi ini memungkinkan pengguna untuk mendeteksi berbagai objek umum (seperti orang, mobil, sepeda) secara *real-time* melalui webcam atau dari file gambar yang diunggah.

Free akses aplikasi ini di: [https://detektorobyek.isparmo.com/](https://detektorobyek.isparmo.com/)

Keunikan utama aplikasi ini adalah kemampuannya untuk menjadi **laboratorium perbandingan AI**. Pengguna dapat secara langsung membandingkan performa dan akurasi dari berbagai model AI yang berjalan di perangkat (*on-device*) dengan "kunci jawaban" yang diberikan oleh model AI generatif canggih (Google Gemini) yang berjalan di *cloud*. Hal ini memberikan wawasan praktis mengenai konsep-konsep inti Machine Learning seperti *speed vs. accuracy trade-off* dan *confidence threshold*.

## 2. Teknologi yang Digunakan
Aplikasi ini dibangun sepenuhnya menggunakan teknologi web modern yang berjalan langsung di browser pengguna, tanpa memerlukan instalasi atau *backend server* (kecuali untuk fitur analisis Gemini).
- **Frontend**: HTML5, Tailwind CSS
- **Logika Aplikasi**: JavaScript (ES6+)
- **AI On-Device**: TensorFlow.js
  * **Model Deteksi**: COCO-SSD (varian Lite & Full)
- **AI Cloud (Acuan)**: Google Gemini API (model gemini-2.5-flash-preview-05-20)
- **Interaksi Pengguna**: DOM Manipulation, Event Listeners

## 3. Target Pengguna
Aplikasi ini dirancang untuk:
- **Pelajar & Mahasiswa**: Mereka yang sedang belajar tentang Kecerdasan Buatan dan Computer Vision dan ingin melihat langsung bagaimana model AI bekerja dalam praktik.
- **Developer & Hobiis**: Para pengembang yang ingin bereksperimen dengan TensorFlow.js dan integrasi API AI di dalam aplikasi web.
- **Pengajar & Dosen**: Sebagai alat bantu demo di kelas untuk menjelaskan konsep-konsep seperti deteksi objek, ambang batas kepercayaan, dan perbandingan model.
- **Siapa Saja yang Ingin Tahu**: Orang awam yang penasaran dengan kemampuan AI dalam "melihat" dan memahami dunia visual.

## 4. Cara Menggunakan
Aplikasi memiliki dua mode utama: Deteksi via Webcam dan Deteksi via Upload.

### A. Mode Upload (Untuk Analisis & Perbandingan)
Ini adalah mode utama untuk melakukan analisis mendalam pada sebuah gambar.
1. **Masukkan API Key (Opsional tapi Direkomendasikan)**: Untuk menggunakan fitur perbandingan dengan AI canggih, dapatkan API Key gratis dari Google AI Studio dan masukkan ke kolom yang tersedia. Klik ikon (?) untuk panduan.
2. **Pilih Model & Threshold**:
  * Pilih model COCO-SSD (Lite atau Full) yang ingin Anda uji.
  * Atur nilai "Ambang Batas Kepercayaan" (misalnya, 0.4). Nilai yang lebih rendah akan mendeteksi lebih banyak objek, tetapi mungkin kurang akurat.
3. **Unggah Gambar**: Klik tombol "Choose File" dan pilih gambar dari komputer Anda.
4. **Jalankan Deteksi COCO-SSD**: Klik tombol **"1. Deteksi"**. Aplikasi akan menggambar kotak di sekitar objek yang terdeteksi dan menambahkan hasilnya sebagai kolom baru di tabel perbandingan.
5. **Jalankan Analisis AI (Gemini)**: Klik tombol **"2. Analisis dengan AI"**. Aplikasi akan mengirim gambar ke Google Gemini dan menambahkan hasilnya sebagai kolom "Acuan AI" di tabel.
6. **Bandingkan Hasil**: Ulangi langkah 2 & 4 dengan pengaturan model atau *threshold* yang berbeda untuk mengisi tabel perbandingan dan melihat skor akurasinya.
7. **Reset**: Klik tombol "Reset" untuk membersihkan tabel dan memulai analisis baru.

### B. Mode Webcam (Untuk Deteksi Real-Time)
Mode ini dirancang untuk melihat bagaimana AI bekerja secara langsung.
1. **Pilih Tab "Deteksi via Webcam"**.
2. **Pilih Model & Threshold**: Atur model dan ambang batas kepercayaan yang ingin Anda gunakan.
3. **Mulai Deteksi**: Klik tombol "Mulai Deteksi". Izinkan browser untuk mengakses kamera Anda jika diminta.
4. **Amati Hasil**: Arahkan kamera ke sekitar Anda. Aplikasi akan menggambar kotak di sekitar objek yang terdeteksi secara *real-time*. Teks di atas video akan menampilkan ringkasan objek yang terlihat.
5. **Ganti Kamera**: Di perangkat seluler, gunakan tombol "Ganti Kamera" untuk beralih antara kamera depan dan belakang.

## 5. Ide Pengembangan Fitur
Aplikasi ini memiliki potensi besar untuk dikembangkan lebih lanjut. Berikut 5 ide fitur:
1. **Deteksi dari Video**: Menambahkan kemampuan untuk mengunggah file video pendek. Aplikasi akan memproses video *frame-by-frame* dan menghasilkan laporan analisis rata-rata atau grafik jumlah objek dari waktu ke waktu.
2. **Visualisasi Data**: Selain tabel, tambahkan grafik batang atau diagram lingkaran untuk memvisualisasikan perbandingan jumlah objek yang terdeteksi oleh setiap model, membuatnya lebih mudah dibaca.
3. **Mode Pelacakan Objek (Object Tracking)**: Setelah sebuah objek terdeteksi, berikan ID unik dan lacak pergerakannya di seluruh frame video. Ini akan mengubahnya dari sekadar "detektor" menjadi "pelacak".
4. **Simpan & Ekspor Laporan**: Menambahkan tombol untuk mengunduh hasil tabel perbandingan sebagai file CSV atau PDF, sehingga pengguna dapat menyimpan dan membagikan hasil analisis mereka.
5. **Integrasi Model MoveNet**: Menambahkan MoveNet sebagai pilihan model ketiga. Saat dipilih, aplikasi tidak hanya akan mendeteksi orang, tetapi juga menggambar kerangka tubuh (pose estimation) di atasnya, membuka kemungkinan analisis yang lebih canggih.
