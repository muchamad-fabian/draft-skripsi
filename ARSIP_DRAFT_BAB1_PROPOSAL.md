# DRAFT PROPOSAL SKRIPSI

> **Status:** Draf awal (versi 1) — bagian pendahuluan & rencana metode.
> **Catatan:** Referensi jurnal BELUM dimasukkan. Sitasi penelitian terdahulu akan ditambahkan pada penyisipan berikutnya ke Latar Belakang dan Tinjauan Pustaka.

---

## JUDUL

**Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning**

*(Judul sesuai arahan Dosen Pembimbing. Secara teknis, implementasi menggunakan arsitektur CNN-LSTM dengan pemodelan urutan karakter.)*

---

## BAB 1 — PENDAHULUAN

### 1.1 Latar Belakang

Proses pembelajaran membaca Al-Qur'an pada tingkat dasar umumnya menggunakan metode Iqro, salah satunya buku **Iqro 3**, yang memperkenalkan pembacaan huruf-huruf Hijaiyah dalam bentuk bersambung. Pada tahap ini, peserta didik tidak lagi mengenali huruf secara tunggal (isolated), melainkan dalam bentuk sambungan antarhuruf yang menyusun sebuah kata. Kemampuan mengenali dan menulis huruf Hijaiyah sambung merupakan kompetensi dasar yang menentukan kelancaran tahap pembelajaran berikutnya. Selama ini pembelajaran huruf Hijaiyah masih bergantung pada evaluasi guru secara langsung, yang menjadi kendala ketika pembelajaran berlangsung jarak jauh (Rahmatulloh dkk., 2022).

Evaluasi kemampuan menulis huruf Hijaiyah sejauh ini masih bergantung pada penilaian guru secara manual. Seiring berkembangnya teknologi pembelajaran digital, media berbasis **canvas digital** memungkinkan peserta didik menuliskan huruf Hijaiyah secara langsung pada layar, dan hasil tulisan tersebut dapat diekspor sebagai citra digital. Pemanfaatan perangkat tulis digital untuk latihan menulis huruf Arab telah terbukti layak diterapkan pada anak; Durayhim dkk. (2023) mengembangkan prototipe aplikasi tablet "Mutqin" dan mengujinya langsung kepada anak usia sekolah bersama para guru. Citra hasil tulisan pada media semacam itu dapat dimanfaatkan sebagai masukan bagi sistem pengenalan tulisan tangan otomatis, sehingga penilaian dapat diberikan secara cepat dan konsisten, serta dapat diintegrasikan ke dalam sistem pembelajaran yang lebih luas.

Pengenalan tulisan tangan huruf Hijaiyah memiliki tantangan yang khas dibandingkan tulisan Latin. Setiap huruf Hijaiyah dapat berubah bentuk tergantung pada kedudukannya di dalam kata, yaitu pada posisi awal (*initial*), tengah (*medial*), akhir (*final*), atau berdiri sendiri (*isolated*) — satu huruf dapat memiliki hingga empat bentuk visual (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023). Selain itu, huruf-huruf yang memiliki kerangka sama dan hanya dibedakan oleh jumlah serta posisi titik (misalnya ب، ت، ث dan ج، ح، خ) rentan terhadap kekeliruan pengenalan; titik bahkan dapat mengubah makna sebuah kata (Albattah & Albahli, 2022). Karakteristik penulisan yang menyambung juga menyulitkan proses pemotongan (segmentasi) antarhuruf secara terpisah, karena huruf saling bersambung tanpa batas yang tegas (Lamtougui dkk., 2024; Ahmed dkk., 2021). Kesulitan ini nyata secara empiris: pada dataset karakter Hijaiyah tulisan tangan anak, akurasi pengenalan berhenti di sekitar 88% (Altwaijry & Al-Turaiki, 2021), dan tulisan tangan anak secara konsisten lebih sulit dikenali dibandingkan tulisan orang dewasa (Alwagdani & Jaha, 2023; Masruroh dkk., 2023).

Pendekatan pengenalan tulisan tangan konvensional umumnya memisahkan setiap huruf terlebih dahulu sebelum dikenali satu per satu. Pendekatan ini rentan kesalahan pada tulisan sambung, karena karakter yang saling bersentuhan atau bersilangan menyebabkan *over-segmentation*, dan kegagalan segmentasi pada satu titik merambat pada hasil pengenalan (Peng, 2024). Sebagai alternatif, pengenalan tanpa segmentasi (*segmentation-free*) yang memperlakukan citra tulisan sebagai satu barisan yang dibaca langsung telah menunjukkan hasil lebih baik pada berbagai aksara (Peng, 2024; Mosbah dkk., 2024; Saini dkk., 2024).

Penelitian ini mengusulkan sistem pengenalan tulisan tangan huruf Hijaiyah sambung berbasis **CNN-LSTM**. Jaringan *Convolutional Neural Network* (CNN) digunakan untuk mengekstraksi ciri visual citra tulisan, sedangkan *Long Short-Term Memory* (LSTM) digunakan untuk memodelkan urutan huruf dari kanan ke kiri sesuai kaidah penulisan Arab. Kombinasi CNN dan LSTM dengan *Connectionist Temporal Classification* (CTC) telah berhasil mengenali kata tulisan tangan bersambung tanpa segmentasi manual (Saini dkk., 2024), dan arsitektur sejenis (CRNN) telah diterapkan pada dokumen berbahasa Arab (Mosbah dkk., 2024; Peng, 2024). Untuk mengatasi keterbatasan jumlah data latih yang dikumpulkan melalui canvas, komponen CNN memanfaatkan **transfer learning**, yaitu pemanfaatan bobot model yang telah terlatih sebelumnya sebagai pengekstraksi ciri; strategi ini terbukti meningkatkan akurasi pengenalan tulisan tangan Arab bersambung pada dataset terbatas (Lamtougui dkk., 2024; Masruroh dkk., 2023).

Dengan pendekatan tersebut, sistem diharapkan mampu mengenali kata sambung yang terdiri atas hingga tiga huruf sesuai materi Iqro 3, dan menghasilkan urutan huruf secara tepat, termasuk pada kata yang memuat huruf berulang.

Beberapa penelitian terdahulu telah menyentuh pengenalan tulisan tangan Hijaiyah, namun seluruhnya berhenti pada huruf tunggal. Rahmatulloh dkk. (2022) mengklasifikasikan huruf Hijaiyah isolated dengan CNN dan mencapai akurasi 91% pada dataset Hijja2 dan 98% pada AHCD. Studi transfer learning untuk karakter Arab/Hijaiyah juga telah dilakukan dengan berbagai backbone CNN (Masruroh dkk., 2023; El Khayati dkk., 2025; Durayhim dkk., 2023), namun tetap pada objek huruf tunggal atau kata sebagai satu label utuh (Lamtougui dkk., 2024). Sebaliknya, model sekuensial CNN-LSTM/CTC yang mampu membaca urutan huruf telah dibuktikan pada aksara Latin dan dokumen Arab cetak (Saini dkk., 2024; Mosbah dkk., 2024; Peng, 2024), tanpa dipadukan dengan transfer learning dan tanpa objek huruf Hijaiyah sambung pendek. Pengenalan tulisan tangan Arab bersambung pun masih diakui sebagai persoalan yang belum terselesaikan — model sekuensial sekalipun masih menghasilkan akurasi rendah pada naskah tulisan tangan Arab (Peng, 2024), dan pengenalan huruf Hijaiyah/Arab tersambung secara eksplisit dinyatakan sebagai pekerjaan lanjutan oleh sejumlah peneliti (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023; Alwagdani & Jaha, 2023; El Khayati dkk., 2025).

Berdasarkan telaah tersebut, terdapat celah penelitian yang belum terisi: belum ada studi yang menggabungkan ekstraksi ciri CNN dengan transfer learning dan pemodelan urutan LSTM untuk mengenali **urutan huruf Hijaiyah yang ditulis bersambung (2–3 huruf) pada citra hasil ekspor canvas digital**, dengan kosakata terukur berdasarkan materi buku Iqro 3. Penelitian ini mengisi celah tersebut.

### 1.2 Rumusan Masalah

1. Bagaimana membangun dataset citra tulisan tangan huruf Hijaiyah sambung berbasis canvas digital yang sesuai dengan materi buku Iqro 3?
2. Bagaimana menerapkan arsitektur CNN-LSTM dengan transfer learning untuk mengenali urutan huruf Hijaiyah yang ditulis secara bersambung pada satu citra tanpa segmentasi manual?
3. Bagaimana kinerja model yang dibangun dalam memprediksi urutan huruf (hingga tiga huruf per citra) berdasarkan metrik pengenalan sekuensial?

### 1.3 Batasan Masalah

1. Objek pengenalan adalah tulisan tangan **huruf Hijaiyah bersambung** yang diekspor dari canvas digital dalam bentuk **satu citra (gambar)** per kata; bukan data goresan (*stroke*) waktu-nyata.
2. Kosakata yang digunakan **dibatasi pada seluruh kata sambung yang terdapat dalam buku Iqro 3**, dengan jumlah huruf maksimal tiga huruf per citra.
3. Metode yang digunakan adalah arsitektur **CNN-LSTM** dengan **transfer learning** pada komponen pengekstrak ciri CNN.
4. Pengumpulan data dilakukan secara mandiri melalui media canvas digital dengan **skema penulisan terpandu prompt**: sistem menampilkan satu kata target yang diambil dari daftar kata sambung buku Iqro 3 (dalam bentuk cetakan dan/atau audio), kemudian responden menuliskan kata tersebut pada area canvas kosong **tanpa panduan garis putus-putus (tracing)**.
5. Pembatasan kosakata pada materi Iqro 3 dijamin oleh mekanisme sistem penentu kata target (prompt), bukan oleh pembatasan visual pada canvas; input yang menyimpang dari kata target disaring melalui tahapan kontrol kualitas data.
6. Penelitian berfokus pada **pengembangan dan evaluasi model pengenalan**; pengembangan aplikasi gamifikasi dan integrasi sistem bukan merupakan bagian dari lingkup penelitian ini.
7. Evaluasi difokuskan pada kinerja pengenalan urutan karakter, tidak mencakup penilaian hukum bacaan (tajwid) maupun kualitas estetika tulisan.

### 1.4 Tujuan Penelitian

1. Menghasilkan dataset citra tulisan tangan huruf Hijaiyah sambung berbasis canvas digital yang disusun berdasarkan materi buku Iqro 3.
2. Menghasilkan model pengenalan berbasis CNN-LSTM dengan transfer learning yang mampu mengenali urutan huruf Hijaiyah bersambung secara langsung dari citra tanpa segmentasi manual.
3. Mengukur kinerja model dalam memprediksi urutan huruf menggunakan metrik evaluasi pengenalan sekuensial.

### 1.5 Manfaat Penelitian

**Manfaat Teoretis**
- Memberikan kontribusi kajian penerapan arsitektur CNN-LSTM dengan transfer learning pada pengenalan tulisan tangan huruf Hijaiyah bersambung, yang masih jarang dikaji dibandingkan pengenalan huruf tunggal.
- Menambah khazanah penelitian pengolahan citra digital khususnya pada domain aksara Arab/Hijaiyah di Indonesia.

**Manfaat Praktis**
- Bagi peserta didik: menyediakan umpan balik otomatis dalam latihan menulis huruf Hijaiyah sambung.
- Bagi guru/instruktur: meringankan evaluasi tulisan tangan peserta didik secara konsisten.
- Bagi pengembangan sistem pembelajaran: hasil model dapat diintegrasikan ke dalam sistem pembelajaran berbasis gamifikasi sebagai komponen pengenalan tulisan.

### 1.6 Hipotesis Penelitian *(opsional — konfirmasi kebutuhan ke dosen)*

Model CNN-LSTM dengan transfer learning pada komponen CNN mampu mengenali urutan huruf Hijaiyah sambung pada citra hasil ekspor canvas dengan akurasi urutan yang lebih tinggi dibandingkan model CNN tanpa komponen sekuensial dan tanpa transfer learning.

### 1.7 Metodologi Penelitian (Ringkas)

1. **Studi literatur** — kajian teori CNN, LSTM, transfer learning, karakteristik huruf Hijaiyah sambung, dan penelitian terdahulu.
2. **Pengumpulan data** — dilakukan dengan protokol berikut:
   a. **Inventarisasi kosakata** — merekap seluruh kata sambung (2–3 huruf) dari buku Iqro 3 menjadi daftar kata target; daftar ini menjadi batas kosakata dataset.
   b. **Skenario penulisan (prompt-based free writing)** — pada setiap sampel, sistem menampilkan satu kata target dari daftar (cetakan dan/atau audio); responden menuliskannya pada canvas kosong tanpa garis putus-putus, lalu citra diekspor sebagai satu gambar. Label urutan huruf ditetapkan oleh kata target prompt (kanan → kiri).
   c. **Pencegahan input di luar kosakata** — kata target ditentukan sistem (responden tidak memilih kata); sebagai gerbang prosedural, responden mengonfirmasi kata target sebelum sesi penulisan; sampel menyimpang disaring pada tahap kontrol kualitas.
   d. **Kontrol kualitas (QC)** — setiap citra diverifikasi terhadap label oleh dua penverifikasi independen; kriteria penolakan: kata tidak sesuai target, goresan tidak terbaca, atau sambungan antarhuruf terputus total.
   e. **Metadata sampel** — setiap sampel dicap dengan identitas penulis, mode penulisan, dan urutan sesi, untuk mendukung pembagian data dan analisis lanjutan.
3. **Pembagian data** — dilakukan *participant-wise split* (satu penulis hanya muncul pada satu split) untuk mencegah kebocoran informasi antar latih/validasi/uji; proporsi split dilaporkan pada Bab 3.
4. **Pra-pemrosesan** — konversi grayscale, pemotongan area tulisan, penyesuaian ukuran dengan menjaga rasio aspek, dan normalisasi nilai piksel.
5. **Pemodelan** — ekstraksi ciri spasial menggunakan CNN (transfer learning), konversi peta ciri menjadi barisan (*map-to-sequence*), pemodelan urutan menggunakan LSTM, dan prediksi urutan karakter.
6. **Pelatihan & pengujian** — augmentasi data, penalaan hiperparameter, dan skenario pembanding (tanpa transfer learning / tanpa komponen sekuensial) sebagai ablation.
7. **Evaluasi** — akurasi urutan penuh (*exact match*), akurasi per posisi karakter, dan *Character Error Rate* (CER).

### 1.8 Sistematika Penulisan

- **BAB 1 Pendahuluan** — latar belakang, rumusan masalah, batasan, tujuan, manfaat, metodologi ringkas.
- **BAB 2 Landasan Teori** — teori pendukung dan penelitian terdahulu *(referensi jurnal akan disusun pada tahap ini)*.
- **BAB 3 Metodologi Penelitian** — alur penelitian, dataset, arsitektur model, skenario pelatihan dan evaluasi.
- **BAB 4 Hasil dan Pembahasan** — hasil pelatihan, perbandingan skenario, analisis kesalahan.
- **BAB 5 Penutup** — kesimpulan dan saran.

---

## DAFTAR PUSTAKA SEMENTARA (sitasi yang sudah dipakai di Bab 1 draf ini)

> Semua entri terverifikasi dari pembacaan penuh PDF (21/09/2026); angka & metadata dari isi dokumen, bukan dari matriks lama.

1. Ahmed, R., Gogate, M., Tahir, A., Dashtipour, K., Al-tamimi, B., Hawalah, A., El-Affendi, M. A., & Hussain, A. (2021). Novel deep convolutional neural network-based contextual recognition of Arabic handwritten scripts. *Entropy*, 23(3), 340. https://doi.org/10.3390/e23030340
2. Albattah, W., & Albahli, S. (2022). Intelligent Arabic handwriting recognition using different standalone and hybrid CNN architectures. *Applied Sciences*, 12(19), 10155. https://doi.org/10.3390/app121910155
3. Altwaijry, N., & Al-Turaiki, I. (2021). Arabic handwriting recognition system using convolutional neural network. *Neural Computing and Applications*, 33, 2249–2261. https://doi.org/10.1007/s00521-020-05070-8
4. Alwagdani, M. S., & Jaha, E. S. (2023). Deep learning-based child handwritten Arabic character recognition and handwriting discrimination. *Sensors*, 23(15), 6774. https://doi.org/10.3390/s23156774
5. Durayhim, A. B., Al-Ajlan, A., Al-Turaiki, I., & Altwaijry, N. (2023). Towards accurate children's Arabic handwriting recognition via deep learning. *Applied Sciences*, 13(3), 1692. https://doi.org/10.3390/app13031692
6. El Khayati, M., Maafiri, A., Himeur, Y., Alkhazaleh, H. A., Atalla, S., & Mansoor, W. (2025). Leveraging transfer learning and mobile-enabled convolutional neural networks for improved Arabic handwritten character recognition. *arXiv:2509.05019v1*. (preprint — cek apakah sudah terbit resmi sebelum dikumpulkan)
7. Lamtougui, H., El Moubtahij, H., Fouadi, H., & Satori, K. (2024). Improving Arabic handwritten text recognition through transfer learning with convolutional neural network-based models. *Bulletin of Electrical Engineering and Informatics*, 13(6), 4294–4305. https://doi.org/10.11591/eei.v13i6.8178
8. Masruroh, S. U., Syahid, M. F., Munthaha, F., Muharram, A. T., & Putri, R. A. (2023). Deep convolutional neural networks transfer learning comparison on Arabic handwriting recognition system. *International Journal on Informatics Visualization (JOIV)*, 7(2), 330–337. (DOI tidak tercantum pada dokumen — cari di situs JOIV sebelum dikumpulkan)
9. Mosbah, L., Moalla, I., Hamdani, T. M., Neji, B., Beyrouthy, T., & Alimi, A. M. (2024). ADOCRNet: A deep learning OCR for Arabic documents recognition. *IEEE Access*, 12, 55620–55629. https://doi.org/10.1109/ACCESS.2024.3379530
10. Peng, G. (2024). Segmentation-free recognition algorithm based on deep learning for handwritten text image. *Journal of Artificial Intelligence and Technology*, 4(2), 169–178. https://doi.org/10.37965/jait.2024.0473
11. Rahmatulloh, A., Rizal, R., Gunawan, R. I., Darmawan, I., & Rahmat, B. Z. (2022). Optimization of Hijaiyah letter handwriting recognition model based on deep learning. *2022 International Conference Advancement in Data Science, E-learning and Information Systems (ICADEIS)*. IEEE. https://doi.org/10.1109/ICADEIS56544.2022.10037496
12. Saini, M. L., Sati, D. C., Telikicharla, R. S., & Mahadev. (2024). Handwritten English script recognition system using CNN and LSTM. *2024 IEEE International Conference on Contemporary Computing and Communications (InC4)*. IEEE. https://doi.org/10.1109/InC460750.2024.10649099

**Masih perlu dicari untuk kelengkapan Bab 1–2** (lihat ANALISIS_LITERATUR_LENGKAP.md Tahap 10.E/F): Shi dkk. 2016 (CRNN), Graves dkk. 2006 (CTC), paper originasi dataset IFN/ENIT & KHATT, kompetitor CNN-BLSTM-CTC Arab (Noubigh; Eltay 2020; Lamtougui 2022), serta penelitian hijaiyah/Arab sambung konteks Indonesia untuk memenuhi target ≥15 paper sambung dari dosen pembimbing.

---

*Draft ini disusun dari catatan penelitian yang telah disinkronkan dengan arahan Dosen Pembimbing (Pak Zain): judul, metode CNN-LSTM, input canvas satu gambar, batasan kosakata Iqro 3 (maks. 3 huruf), dan lingkup (mahasiswa hanya mengembangkan model).*
