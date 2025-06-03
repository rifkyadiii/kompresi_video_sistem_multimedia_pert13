# Skrip Kompresi Video H.264

**Kelompok 6 Sistem Multimedia**

**Anggota:**
1. Gevira Zahra Shofa (1227050050)
2. Moch Rifky Aulia Adikusumah (1227050072)
3. Muhammad Zidan (1227050079)
4. Muhammad Ahsani Taqwim (1227050083)

Skrip Python ini dirancang untuk mengkompresi sekumpulan video menggunakan codec H.264 (libx264) melalui FFmpeg. Skrip ini tidak hanya melakukan kompresi tetapi juga mengumpulkan statistik detail tentang proses tersebut dan memvisualisasikan perbandingan ukuran file serta rasio kompresi menggunakan Matplotlib.

## Fitur Utama

* **Kompresi Video H.264**: Menggunakan `ffmpeg-python` untuk mengkompresi video dengan codec H.264.
* **Parameter Kustom**: Memungkinkan pengaturan `CRF` (Constant Rate Factor) dan `preset` untuk setiap video.
* **Manajemen Direktori Otomatis**: Membuat folder `video_asli` (untuk input) dan `video_kompresi` (untuk output) jika belum ada.
* **Pengumpulan Statistik**: Mencatat ukuran file asli, ukuran file terkompresi, dan rasio kompresi untuk setiap video.
* **Visualisasi Data**:
    * Grafik batang untuk membandingkan ukuran file sebelum dan sesudah kompresi.
    * Grafik batang untuk menunjukkan rasio kompresi yang dicapai, dengan indikasi visual untuk kompresi positif (pengurangan ukuran) dan negatif (penambahan ukuran).
* **Penanganan Error**: Memberikan pesan error jika FFmpeg gagal melakukan kompresi.
* **Dukungan Berbagai Format Kontainer**: Mencoba mempertahankan format kontainer asli video setelah kompresi (misalnya, `.mp4` tetap `.mp4`, `.mov` tetap `.mov`).

## Kebutuhan Sistem

* Python 3.x
* **FFmpeg**: Harus terinstal di sistem Anda dan dapat diakses melalui `PATH` environment variable.
* Library Python:
    * `ffmpeg-python`
    * `matplotlib`
    * `numpy`

## Konfigurasi

1.  **Instal FFmpeg**:
    Unduh FFmpeg dari [situs resminya](https://ffmpeg.org/download.html) dan instal sesuai dengan sistem operasi Anda. Pastikan direktori `bin` dari FFmpeg ditambahkan ke `PATH` sistem Anda.

2.  **Instal Library Python**:
    Buka terminal atau command prompt dan jalankan perintah berikut:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Siapkan Video Asli**:
    * Skrip akan secara otomatis membuat folder bernama `video_asli` di direktori yang sama dengan skrip.
    * Tempatkan file-file video yang ingin Anda kompres ke dalam folder `video_asli` ini.
    * Secara default, skrip dikonfigurasi untuk mencari file berikut:
        * `sample_960x540.mp4`
        * `sample_960x540.mov`
        * `sample_960x540.mkv`
        * `sample_960x540.avi`
        * `sample_960x540.webm`
    * Anda dapat mengubah daftar video dan parameter kompresinya dengan mengedit variabel `daftar_video_input` dalam skrip.

## Cara Menggunakan

1.  **Pastikan semua kebutuhan sistem dan konfigurasi telah terpenuhi.**
    * Ini termasuk Python, FFmpeg yang terinstal dan ada di PATH, serta library Python yang dibutuhkan (`ffmpeg-python`, `matplotlib`, `numpy`).
    * Anda juga memerlukan lingkungan untuk menjalankan Jupyter Notebook, seperti Jupyter Lab, Jupyter Notebook klasik, atau VS Code dengan ekstensi Jupyter. Jika belum punya, Anda bisa menginstal Jupyter Lab dengan:
        ```bash
        pip install jupyterlab
        ```

2.  **Siapkan file video Anda.**
    * Letakkan file-file video yang ingin Anda kompres ke dalam folder `video_asli` (skrip akan membuat folder ini jika belum ada, di direktori tempat notebook dijalankan).

3.  **Jalankan Jupyter Notebook**:
    * Buka terminal atau command prompt.
    * Navigasi ke direktori tempat Anda menyimpan file `.ipynb` Anda.
    * Luncurkan Jupyter Lab (atau Jupyter Notebook):
        ```bash
        jupyter lab
        ```
        atau
        ```bash
        jupyter notebook
        ```
    * Perintah ini akan membuka antarmuka Jupyter di browser web Anda.

4.  **Buka dan Jalankan Notebook**:
    * Dari antarmuka Jupyter di browser, navigasikan dan buka file `.ipynb` Anda (misalnya, `nama_file_notebook_anda.ipynb`).
    * Setelah notebook terbuka, Anda dapat menjalankan sel-sel kode secara berurutan. Biasanya ini dilakukan dengan memilih sel dan menekan `Shift + Enter`, atau menggunakan opsi "Run" dari menu.
    * Pastikan untuk menjalankan sel impor library dan konfigurasi awal terlebih dahulu sebelum menjalankan sel kompresi video dan visualisasi.

## Struktur Proyek (Setelah Eksekusi Awal)

```
.
├── Kompresi_Video.ipynb
├── video_asli/
│   ├── sample_960x540.mp4
│   ├── sample_960x540.mov
│   └── ... (video lainnya)
└── video_kompresi/
    └── ... (video hasil kompresi akan muncul di sini)
```

## Output yang Dihasilkan

* **Folder `video_kompresi`**: Berisi video-video yang telah berhasil dikompresi. Nama file output akan mencakup informasi CRF dan preset yang digunakan.
* **Output di Konsol**:
    * Status pembuatan folder.
    * Log detail untuk setiap proses kompresi, termasuk nama file, codec, CRF, preset, ukuran asli, ukuran kompresi, dan rasio kompresi.
    * Pesan error jika terjadi kegagalan kompresi.
    * Ringkasan jumlah video yang berhasil dikompresi.
* **Dua Grafik Visualisasi** (ditampilkan dalam jendela terpisah jika dijalankan di lingkungan yang mendukung GUI):
    1.  **Perbandingan Ukuran File Video**: Menunjukkan ukuran file dalam MB sebelum dan sesudah kompresi H.264 untuk setiap video yang berhasil diproses.
    2.  **Rasio Kompresi Video**: Menampilkan persentase rasio kompresi. Bar hijau menandakan pengurangan ukuran file (kompresi berhasil), sedangkan bar merah (nilai negatif) menandakan penambahan ukuran file.

## Analisis Hasil

![image](https://github.com/user-attachments/assets/2ecd4f02-17d6-4453-afb2-7a34028b8957)
![image](https://github.com/user-attachments/assets/766fe75b-8a8a-4ad0-bb56-596fd0d2d8b9)

* **Kompresi H.264 pada berbagai format**:
    * **MP4 dan MOV**: Umumnya menunjukkan pengurangan ukuran yang baik. File `.mov` dengan CRF 25 dan preset `fast` mencapai efisiensi terbaik dalam contoh (rasio ~34.26%).
    * **MKV**: Mungkin menunjukkan sedikit atau hampir tidak ada perubahan ukuran, tergantung pada konten asli dan pengaturan (rasio ~2.23% dengan CRF 22, preset `medium`).
    * **AVI**: Dapat mengalami **peningkatan ukuran** setelah proses kompresi (rasio negatif, misal -52.34%). Ini bisa terjadi jika file AVI asli sudah sangat terkompresi dengan codec yang efisien atau jika kombinasi parameter H.264 tidak optimal untuk jenis stream di dalam AVI tersebut.
* **Masalah Kompatibilitas Kontainer**:
    * **WebM**: Dalam contoh yang diberikan, kompresi video kelima (`.webm`) gagal. Skrip ini mencoba mempertahankan format kontainer asli. Meskipun H.264 secara teknis dapat dimasukkan ke dalam kontainer WebM, ini bukan kombinasi standar (WebM biasanya menggunakan VP8/VP9/AV1). Kegagalan ini mungkin disebabkan oleh batasan FFmpeg dengan kombinasi tersebut atau cara `ffmpeg-python` menangani streamnya. Skrip akan melewati file ini jika terjadi error FFmpeg.

## Kustomisasi

* **Mengubah Daftar Video dan Parameter**: Modifikasi list `daftar_video_input` di dalam skrip untuk mengubah nama file, target CRF, dan preset kompresi.
    ```python
    daftar_video_input = [
        {"nama": "video_saya.mp4", "crf": 20, "preset": "slower"},
        {"nama": "klip_lain.mkv", "crf": 28, "preset": "ultrafast"},
        # ... tambahkan video Anda di sini
    ]
    ```
* **Mengubah Nama Folder**: Ubah variabel `folder_video_asli` dan `folder_video_kompresi` di awal skrip jika Anda ingin menggunakan nama folder yang berbeda.

## Catatan Tambahan

* Kualitas video hasil kompresi sangat bergantung pada nilai `CRF`. Nilai CRF yang lebih rendah (misalnya, 18) menghasilkan kualitas lebih baik dengan ukuran file lebih besar, sedangkan nilai yang lebih tinggi (misalnya, 28) menghasilkan ukuran file lebih kecil dengan potensi penurunan kualitas yang lebih terlihat.
* `Preset` memengaruhi kecepatan kompresi dan efisiensi ukuran. Preset yang lebih lambat (`slow`, `slower`, `veryslow`) membutuhkan waktu lebih lama tetapi dapat menghasilkan kompresi yang lebih baik untuk ukuran file tertentu. Preset yang lebih cepat (`fast`, `faster`, `ultrafast`) bekerja lebih cepat tetapi mungkin kurang efisien.
* Skrip menggunakan `acodec='aac'` dan `strict='experimental'` untuk audio. Ini adalah pilihan umum, tetapi mungkin perlu disesuaikan untuk kebutuhan khusus.
* Pastikan Anda memiliki ruang disk yang cukup untuk menyimpan video hasil kompresi.
