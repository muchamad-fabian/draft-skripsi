# PROPOSAL SKRIPSI
## UNIVERSITAS INTERNASIONAL SEMEN INDONESIA

---

> ### PETUNJUK FORMAT DAN TATA LETAK NASKAH (SESUAI PEDOMAN UISI)
> 1. **Kertas & Huruf:** Kertas A4 (80 gram). Huruf *Times New Roman* 12 pt normal, spasi 1,5 (kecuali abstrak, kutipan langsung > 1 kalimat, tabel/gambar, dan daftar pustaka yang berspasi 1).
> 2. **Batas Margin:** 
>    - Atas: 3,5 cm | Bawah: 3,0 cm.
>    - Halaman Ganjil: Kiri 4,0 cm, Kanan 3,0 cm.
>    - Halaman Genap: Kiri 3,0 cm, Kanan 4,0 cm.
> 3. **Format Judul & Bab:** BAB 1, BAB 2, dst. berukuran 14 pt kapital tebal (*bold*), rata tengah. Sub-bab ditulis dengan *Title Case* (hanya huruf awal kata yang kapital), rata kiri.
> 4. **Penomoran Halaman:**
>    - Halaman judul tidak diberi nomor halaman.
>    - Bagian awal (sebelum Bab 1) diberi nomor Romawi kecil (*i, ii, iii, ...*) di bagian bawah tengah.
>    - Bagian tubuh teks (Bab 1 sampai selesai, daftar pustaka, lampiran) diberi nomor angka Arab (*1, 2, 3, ...*) di bagian bawah tengah.

---

<!-- HALAMAN JUDUL / SAMPUL DEPAN (Tanpa Nomor Halaman) -->

<div align="center">

# PROPOSAL SKRIPSI

<br><br>

### **KLASIFIKASI MULTI-LABEL UNTUK PENGENALAN HURUF HIJAIYAH SAMBUNG MENGGUNAKAN TRANSFER LEARNING**

<br><br>

Proposal Skripsi Ini Disusun untuk Memenuhi Salah Satu Syarat<br>
Memperoleh Gelar Sarjana Komputer (S.Kom.) / Sarjana Teknik (S.T.)<br>
pada Program Studi S-1 Informatika

<br><br>

*(Logo Universitas Internasional Semen Indonesia dicetak berwarna merah)*

<br><br>

**Oleh:**<br>
**MUCHAMAD BUDI FABIANTORO**<br>
**NIM: 22314050111003**

<br><br><br>

**PROGRAM STUDI S-1 INFORMATIKA**<br>
**DEPARTEMEN INFORMATIKA**<br>
**FAKULTAS TEKNOLOGI DAN INDUSTRI**<br>
**UNIVERSITAS INTERNASIONAL SEMEN INDONESIA**<br>
**GRESIK**<br>
**2026**

</div>

<div style="page-break-after: always;"></div>

---

<!-- HALAMAN LEMBAR PENGESAHAN (Halaman ii) -->

<div align="center">

### **LEMBAR PENGESAHAN**
### **PROPOSAL SKRIPSI**

</div>

<br>

| | |
|:---|:---|
| **Judul** | : **Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning** |
| **Nama Mahasiswa** | : Muchamad Budi Fabiantoro |
| **NIM** | : 22314050111003 |
| **Program Studi** | : S-1 Informatika |
| **Departemen** | : Informatika |
| **Fakultas** | : Fakultas Teknologi dan Industri |

<br>

Telah diseminarkan pada Seminar Proposal Skripsi:
- **Hari** : ..............................................................
- **Tanggal** : ..............................................................
- **Tempat** : Universitas Internasional Semen Indonesia

<br>

<div align="center">
<b>DEWAN PENGUJI</b>
</div>

<br>

| No | Nama Dewan Penguji | Kedudukan | Tanda Tangan |
|:---|:---|:---|:---|
| 1. | ............................................................................<br>NIP/NUPTK: | Dosen Penguji I | ...................................... |
| 2. | ............................................................................<br>NIP/NUPTK: | Dosen Penguji II | ...................................... |
| 3. | ............................................................................<br>NIP/NUPTK: | Dosen Penguji III | ...................................... |

<br>

<div align="center">
<b>Disetujui oleh Tim Pembimbing Skripsi</b>
</div>

<br>

| No | Nama Pembimbing | Kedudukan | Tanda Tangan |
|:---|:---|:---|:---|
| 1. | **Ahmad Zainuddin, S.T., M.T.**<br>NIP/NUPTK: | Dosen Pembimbing | ...................................... |
| 2. | ............................................................................<br>NIP/NUPTK: | Dosen Co-Pembimbing *(jika ada)* | ...................................... |

<br>

<div align="right">
Gresik, &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Oktober 2026
</div>

<div style="page-break-after: always;"></div>

---

<!-- ABSTRAK BAHASA INDONESIA (Halaman iii) -->

<div align="center">

### **KLASIFIKASI MULTI-LABEL UNTUK PENGENALAN HURUF HIJAIYAH SAMBUNG MENGGUNAKAN TRANSFER LEARNING**

<br>

**Nama mahasiswa : Muchamad Budi Fabiantoro**<br>
**NIM : 22314050111003**<br>
**Dosen Pembimbing : Ahmad Zainuddin, S.T., M.T.**

<br>

### **ABSTRAK**

</div>

Pembelajaran literasi membaca dan menulis aksara Al-Qur'an pada tingkat dasar di Indonesia umumnya bertumpu pada metode Iqro. Pada tahap buku Iqro 3, peserta didik mulai mempelajari huruf-huruf Hijaiyah yang dirangkai bersambung membentuk kata pendek (2 hingga 3 karakter per citra). Proses evaluasi menulis selama ini masih bergantung pada koreksi visual manual oleh guru secara tatap muka, yang menghadapi kendala keterbatasan waktu, inkonsistensi penilaian, serta keterbatasan latihan mandiri di luar kelas. Seiring meluasnya media *canvas digital* pada perangkat layar sentuh, citra hasil goresan digital berpotensi besar dianalisis secara otomatis oleh sistem kecerdasan buatan sebagai teknologi pembantu (*assisting technology*). Penelitian acuan terdahulu oleh Rahmatulloh dkk. (2022) berhasil mengoptimalkan Convolutional Neural Network (CNN) untuk mengenali tulisan tangan huruf Hijaiyah tunggal (*isolated*) dengan akurasi 91% pada dataset anak-anak (Hijja2) dan merekomendasikan pengembangan model pengenalan tulisan tangan ke dalam aplikasi *mobile*. Namun, model tersebut belum mampu mengenali huruf bersambung yang memiliki dinamika perubahan bentuk posisional (*initial*, *medial*, *final*), ambiguitas titik diakritik, serta ketiadaan batas pemisah antarhuruf (ligatur). 

Untuk menyelesaikan permasalahan tersebut, penelitian ini mengusulkan pengembangan model pengenalan sekuensial nirsegmentasi (*segmentation-free sequence recognition*) berbasis arsitektur gabungan CNN dan *Long Short-Term Memory* (CNN-LSTM) dengan *Transfer Learning*. Lapisan CNN memanfaatkan *backbone* modern hemat daya MobileNetV4 terbobot *pre-trained* sebagai pengekstraksi ciri visual spasial dari citra masukan *canvas digital*, sedangkan lapisan Recurrent/LSTM memodelkan dependensi urutan temporal huruf dari kanan ke kiri sesuai arah alami penulisan Arab. Data penelitian dikumpulkan secara mandiri melalui *canvas digital* interaktif dengan batas kosakata mencakup seluruh kata sambung pada buku Iqro 3, dibagi menggunakan skema *participant-wise split* guna menjamin keandalan generalisasi, serta diperkaya melalui teknik augmentasi morfologis. Kinerja model dievaluasi menggunakan metrik *exact sequence match accuracy*, *character-level accuracy*, dan *Character Error Rate* (CER). Penelitian ini diharapkan menghasilkan model pengenalan tulisan tangan bersambung yang akurat, ringan, dan siap diintegrasikan pada aplikasi evaluasi belajar mandiri.

<br><br>

**Kata kunci:** *canvas digital*, CNN-LSTM, huruf Hijaiyah bersambung, Iqro 3, MobileNetV4, *transfer learning*.

<div style="page-break-after: always;"></div>

---

<!-- ABSTRACT BAHASA INGGRIS (Halaman iv) -->

<div align="center">

### **MULTI-LABEL CLASSIFICATION FOR CONNECTED HIJAIYAH LETTER RECOGNITION USING TRANSFER LEARNING**

<br>

**By : Muchamad Budi Fabiantoro**<br>
**Student Identity Number : 22314050111003**<br>
**Supervisor : Ahmad Zainuddin, S.T., M.T.**

<br>

### **ABSTRACT**

</div>

*Learning to read and write the Quranic script at the elementary level in Indonesia predominantly relies on the Iqro method. In the third book (Iqro 3), learners are introduced to cursive connected Hijaiyah letters forming short words consisting of two to three characters per image. To date, the handwriting evaluation process has depended on manual face-to-face feedback from teachers, which suffers from time constraints, subjective inconsistency, and limited independent practice opportunities outside the classroom. With the increasing adoption of interactive digital canvas interfaces on touchscreen devices, exported handwriting images hold great potential to be evaluated automatically by artificial intelligence as an assisting technology. A baseline study by Rahmatulloh et al. (2022) successfully optimized Convolutional Neural Networks (CNN) for isolated Hijaiyah character recognition, achieving 91% accuracy on a children's dataset (Hijja2), and recommended deploying handwriting recognition models into mobile applications. However, existing models remain limited to isolated characters and cannot handle connected cursive script characterized by dynamic positional shape variations (initial, medial, final), diacritical dot ambiguities, and ligature connections lacking clear character boundaries.*

*To address these challenges, this study proposes a segmentation-free sequence recognition model based on a hybrid CNN and Long Short-Term Memory (CNN-LSTM) architecture empowered by Transfer Learning. The CNN feature extractor employs a pre-trained, computation-efficient MobileNetV4 backbone to capture spatial visual features from exported digital canvas images, while the recurrent LSTM layers model the temporal character sequence from right to left in accordance with natural Arabic script flow. The experimental dataset is collected independently via a digital canvas interface bounded by the vocabulary of Iqro 3, partitioned using a participant-wise split protocol to prevent data leakage, and augmented with morphological distortions. Model performance is comprehensively evaluated using exact sequence match accuracy, character-level accuracy, and Character Error Rate (CER). This research aims to deliver an accurate, lightweight handwriting recognition model ready for integration into interactive self-learning mobile applications.*

<br><br>

**Keywords:** *connected Hijaiyah letters, CNN-LSTM, digital canvas, Iqro 3, MobileNetV4, transfer learning.*

<div style="page-break-after: always;"></div>

---

<!-- DAFTAR ISI (Halaman v) -->

# DAFTAR ISI

<br>

| | Halaman |
|:---|---:|
| **HALAMAN JUDUL** | i |
| **LEMBAR PENGESAHAN PROPOSAL SKRIPSI** | ii |
| **ABSTRAK** | iii |
| **ABSTRACT** | iv |
| **DAFTAR ISI** | v |
| **DAFTAR GAMBAR** | vii |
| **DAFTAR TABEL** | viii |
| **DAFTAR NOTASI DAN SINGKATAN** | ix |
| | |
| **BAB 1 PENDAHULUAN** | **1** |
| &nbsp;&nbsp;&nbsp;&nbsp;1.1 Latar Belakang | 1 |
| &nbsp;&nbsp;&nbsp;&nbsp;1.2 Rumusan Masalah | 6 |
| &nbsp;&nbsp;&nbsp;&nbsp;1.3 Tujuan Penelitian | 6 |
| &nbsp;&nbsp;&nbsp;&nbsp;1.4 Manfaat Penelitian | 7 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.4.1 Manfaat Teoretis | 7 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.4.2 Manfaat Praktis | 7 |
| &nbsp;&nbsp;&nbsp;&nbsp;1.5 Ruang Lingkup Penelitian | 8 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.5.1 Batasan Masalah | 8 |
| &nbsp;&nbsp;&nbsp;&nbsp;1.6 Sistematika Penulisan Proposal | 9 |
| | |
| **BAB 2 KAJIAN PUSTAKA DAN DASAR TEORI** | **11** |
| &nbsp;&nbsp;&nbsp;&nbsp;2.1 Penelitian Terdahulu (*State of the Art*) | 11 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.2 Karakteristik Huruf Hijaiyah Sambung dan Kurikulum Iqro 3 | 16 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.3 Media *Canvas Digital* dan Akuisisi Citra Tulisan Tangan | 18 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.4 *Convolutional Neural Network* (CNN) sebagai Pengekstrak Ciri | 19 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.5 *Transfer Learning* dan Arsitektur *MobileNetV4* | 20 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.6 *Long Short-Term Memory* (LSTM) untuk Pemodelan Urutan Temporal | 22 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.7 Paradigma Pengenalan Nirsegmentasi (*Segmentation-Free*) | 23 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.8 Formulasi Masalah *Multi-Label* dan Pemodelan Urutan | 24 |
| &nbsp;&nbsp;&nbsp;&nbsp;2.9 Metrik Evaluasi Pengenalan Teks Sekuensial | 25 |
| | |
| **BAB 3 METODOLOGI PENELITIAN** | **27** |
| &nbsp;&nbsp;&nbsp;&nbsp;3.1 Alur dan Desain Penelitian | 27 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.2 Desain dan Protokol Pengumpulan Dataset *Canvas* Iqro 3 | 29 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2.1 Inventarisasi Kosakata Buku Iqro 3 | 29 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2.2 Protokol Pengumpulan Tulisan Tangan pada *Canvas Digital* | 30 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2.3 Verifikasi Kontrol Kualitas Data (*Quality Control*) | 31 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2.4 Skema Pembagian Data Berbasis Partisipan (*Participant-Wise Split*) | 32 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.3 Pra-pemrosesan Citra Tulisan Tangan | 32 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.4 Perancangan Arsitektur Model CNN-LSTM MobileNetV4 | 34 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.5 Skenario Pelatihan dan Penalaan Hiperparameter | 37 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.6 Skenario Pengujian dan Kajian Ablasi (*Ablation Study*) | 38 |
| &nbsp;&nbsp;&nbsp;&nbsp;3.7 Jadwal dan Rencana Pelaksanaan Penelitian | 40 |
| | |
| **DAFTAR PUSTAKA** | **42** |
| | |
| **LAMPIRAN** | **47** |
| &nbsp;&nbsp;&nbsp;&nbsp;Lampiran A: Rincian Distribusi Kosakata Kata Sambung Buku Iqro 3 | 47 |
| &nbsp;&nbsp;&nbsp;&nbsp;Lampiran B: Desain Antarmuka *Canvas Digital* dan Format Lembar Pengambilan Data | 49 |
| | |
| **BIODATA PENULIS** | **51** |

<div style="page-break-after: always;"></div>

---

<!-- DAFTAR GAMBAR (Halaman vii) -->

# DAFTAR GAMBAR

<br>

| Nomor Gambar | Judul Gambar | Halaman |
|:---|:---|---:|
| Gambar 2.1 | Variasi Bentuk Glif Huruf Hijaiyah Berdasarkan Posisi dalam Kata | 17 |
| Gambar 2.2 | Arsitektur Blok *Universal Inverted Bottleneck* (UIB) pada MobileNetV4 | 21 |
| Gambar 2.3 | Struktur Sel Rekuren *Long Short-Term Memory* (LSTM) dengan Tiga *Gates* | 23 |
| Gambar 3.1 | Diagram Alir Tahapan Pelaksanaan Penelitian | 28 |
| Gambar 3.2 | Diagram Alur Protokol Akuisisi Data Tulisan Tangan Berbasis *Prompt Canvas* | 30 |
| Gambar 3.3 | Tahapan Pra-pemrosesan Citra Masukan Tulisan Tangan Bersambung | 33 |
| Gambar 3.4 | Diagram Arsitektur Lengkap Model CNN-LSTM dengan *Backbone* MobileNetV4 | 35 |

<div style="page-break-after: always;"></div>

---

<!-- DAFTAR TABEL (Halaman viii) -->

# DAFTAR TABEL

<br>

| Nomor Tabel | Judul Tabel | Halaman |
|:---|:---|---:|
| Tabel 2.1 | Matriks Sintesis Penelitian Terdahulu dan Identifikasi Celah Riset (*Research Gap*) | 14 |
| Tabel 2.2 | Perbandingan Karakteristik Klasifikasi Multi-Label Klasik vs Pengenalan Urutan Karakter | 25 |
| Tabel 3.1 | Rincian Konfigurasi Parameter Lapisan Arsitektur CNN-LSTM MobileNetV4 | 36 |
| Tabel 3.2 | Rencana Matriks Skenario Eksperimen dan Kajian Ablasi (*Ablation Study*) | 39 |
| Tabel 3.3 | Matriks Jadwal Rencana Pelaksanaan Kegiatan Penelitian Skripsi | 41 |

<div style="page-break-after: always;"></div>

---

<!-- DAFTAR NOTASI DAN SINGKATAN (Halaman ix) -->

# DAFTAR NOTASI DAN SINGKATAN

<br>

| Simbol / Singkatan | Keterangan |
|:---|:---|
| AHCD | *Arabic Handwritten Characters Dataset* |
| ADAM | *Adaptive Moment Estimation* (Algoritma Optimasi Pembelajaran Mesin) |
| BCE | *Binary Cross-Entropy* |
| BiLSTM | *Bidirectional Long Short-Term Memory* |
| CER | *Character Error Rate* |
| CNN | *Convolutional Neural Network* |
| CRNN | *Convolutional Recurrent Neural Network* |
| CTC | *Connectionist Temporal Classification* |
| FC | *Fully Connected Layer* (Lapisan Terhubung Penuh) |
| FTI | Fakultas Teknologi dan Industri |
| GAP | *Global Average Pooling* |
| LSTM | *Long Short-Term Memory* |
| OCR | *Optical Character Recognition* (Pengenalan Karakter Optis) |
| QC | *Quality Control* (Kendali Mutu Data) |
| ReLU | *Rectified Linear Unit* (Fungsi Aktivasi Non-Linear) |
| SOTA | *State of the Art* (Capaian Terbaik Terkini) |
| TL | *Transfer Learning* (Pembelajaran Transfer Bobot) |
| UIB | *Universal Inverted Bottleneck* (Blok Bangunan MobileNetV4) |
| UISI | Universitas Internasional Semen Indonesia |
| WER | *Word Error Rate* |

<div style="page-break-after: always;"></div>

---

<!-- BAGIAN TUBUH PROPOSAL: BAB 1 (Halaman 1) -->

# BAB 1
# PENDAHULUAN

<br>

### 1.1 Latar Belakang

Di era transformasi digital dan revolusi industri modern saat ini, perkembangan teknologi kecerdasan buatan (*Artificial Intelligence*) berkembang sangat pesat menjadi instrumen pembantu (*assisting technology*) yang mempermudah berbagai aspek kehidupan manusia. Dalam ranah pendidikan keagamaan dan literasi bahasa, integrasi teknologi cerdas kini diarahkan untuk menghadirkan media pembelajaran yang adaptif, interaktif, dan dapat diakses secara mandiri oleh peserta didik kapan pun dan di mana pun. Di Indonesia, pembelajaran membaca dan menulis aksara Al-Qur'an pada tingkat dasar umumnya diselenggarakan menggunakan metode Iqro. Pada tahap permulaan (buku Iqro 1 dan Iqro 2), peserta didik diperkenalkan pada huruf-huruf Hijaiyah dalam bentuk tunggal yang berdiri sendiri (*isolated characters*). Ketika melangkah ke buku **Iqro 3**, peserta didik mulai diperkenalkan pada kata-kata pendek yang tersusun atas dua hingga tiga huruf Hijaiyah yang ditulis secara bersambung. Penguasaan penulisan huruf Hijaiyah bersambung memegang peranan yang sangat fundamental karena seluruh teks Al-Qur'an dan literatur Arab disajikan dalam bentuk rangkaian huruf kursif bersambung.

Kendati memegang peranan krusial, proses evaluasi latihan menulis huruf Hijaiyah sejauh ini masih sangat bergantung pada koreksi visual manual oleh guru atau ustaz secara tatap muka langsung di dalam kelas. Sebagaimana digarisbawahi oleh Rahmatulloh dkk. (2022), proses pembelajaran huruf Hijaiyah konvensional menuntut kehadiran pembimbing khusus secara langsung untuk memverifikasi kebenaran setiap goresan. Ketergantungan mutlak pada evaluasi manual ini menimbulkan kendala serius, terutama ketika kegiatan pembelajaran berlangsung secara jarak jauh (*remote learning*), membatasi intensitas latihan mandiri santri di luar jam pertemuan kelas, menimbulkan ketimpangan akses bimbingan bagi mereka yang belajar tanpa pendamping, serta membebani objektivitas dan konsistensi penilaian pada skala kelas yang berukuran besar. Mengingat laju perkembangan zaman yang serba cepat dan menuntut solusi praktis, Rahmatulloh dkk. (2022) menegaskan urgensi kehadiran teknologi cerdas berupa sistem pengenalan tulisan tangan (*Optical Character Recognition* / OCR luring) yang mampu mengidentifikasi tulisan dan memandu proses pembelajaran secara otomatis dengan memberikan umpan balik evaluasi seketika (*instant warning and feedback*) jika terjadi kekeliruan goresan.

Peluang penerapan teknologi pembantu ini makin terbuka luas seiring masifnya pemanfaatan perangkat layar sentuh (*touchscreen*) seperti tablet dan ponsel pintar, yang dilengkapi fasilitas *canvas digital* interaktif. Melalui media tersebut, peserta didik dapat berlatih menuliskan aksara Hijaiyah langsung di atas layar menggunakan jari atau pena digital (*stylus*) dengan bantuan pola garis titik-titik panduan (*tracing dots*). Hasil goresan tulisan pada area kanvas kemudian diekspor menjadi berkas citra digital 2 dimensi (2D). Pemanfaatan perangkat layar sentuh untuk latihan menulis karakter Arab telah terbukti diterima secara antusias dan sangat efektif diterapkan pada anak-anak usia sekolah dasar maupun kalangan pendidik, sebagaimana ditunjukkan pada evaluasi komprehensif aplikasi tablet *Mutqin* oleh Durayhim dkk. (2023). Citra digital hasil ekspor kanvas tersebut memiliki potensi yang sangat besar untuk dijadikan masukan (*input*) bagi model kecerdasan buatan guna menyediakan evaluasi penulisan secara otomatis, cepat, dan objektif.

Sebagai upaya membangun sistem pengenalan otomatis, penelitian acuan utama oleh Rahmatulloh dkk. (2022) berjudul *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"* telah membuktikan efektivitas pendekatan *Deep Learning*, khususnya arsitektur *Convolutional Neural Network* (CNN) yang dioptimalkan dengan algoritma ADAM, dalam mengenali dan mengklasifikasikan tulisan tangan huruf Hijaiyah. Penelitian tersebut sukses mencatatkan tingkat akurasi klasifikasi yang tinggi, yakni sebesar 91% pada dataset tulisan tangan anak-anak usia 7–12 tahun (Hijja2) dan 98% pada dataset tulisan dewasa (AHCD). Di akhir publikasinya, Rahmatulloh dkk. (2022) memberikan arahan dan rekomendasi penting bagi penelitian selanjutnya (*future work*), yaitu memperluas dan mengimplementasikan model pengenalan tulisan tangan Hijaiyah tersebut ke dalam aplikasi berbasis *mobile* agar dapat digunakan secara praktis untuk membantu proses pembelajaran secara interaktif.

Meskipun demikian, model yang dibangun oleh Rahmatulloh dkk. (2022)—serta sebagian besar penelitian pengenalan aksara Arab di Indonesia (Masruroh dkk., 2023)—masih terbatas pada pengenalan huruf tunggal yang terisolasi (*isolated characters*). Di sisi lain, pada tahap pembelajaran nyata kurikulum buku Iqro 3, peserta didik diwajibkan menuliskan rangkaian huruf yang saling bersambung membentuk kata. Pengenalan tulisan tangan huruf Hijaiyah bersambung menghadirkan tingkat kompleksitas komputasi yang jauh lebih tinggi dibandingkan pengenalan huruf tunggal, yang disebabkan oleh tiga faktor utama:
1. **Dinamika perubahan morfologi posisional:** Aksara Arab/Hijaiyah bersifat sangat fleksibel dan dinamis, di mana satu karakter dapat bermutasi menjadi hingga empat bentuk glif visual yang berbeda bergantung pada posisinya di dalam kata, yaitu di awal (*initial*), tengah (*medial*), akhir (*final*), atau berdiri sendiri (*isolated*) (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023).
2. **Keserupaan kerangka dasar dan distorsi titik diakritik:** Banyak karakter Hijaiyah berbagi kerangka goresan dasar yang identik dan hanya dibedakan oleh jumlah serta posisi titik diakritik (misalnya kelompok ب، ت، ث dan ج، ح، خ). Pada penulisan tangan bersambung, titik-titik diakritik ini sangat rentan mengalami pergeseran posisi, saling bertumpukan, atau terdistorsi dengan garis huruf di sekitarnya, sehingga meningkatkan risiko ambiguitas klasifikasi (Albattah & Albahli, 2022).
3. **Ketiadaan batas tegas antarhuruf (*ligature problem*):** Rangkaian huruf bersambung membentuk sambungan alami (*ligature*) tanpa batas pemisah yang jelas. Pendekatan konvensional berbasis segmentasi eksplisit (*segmentation-based*) kerap mengalami kegagalan fatal berupa pemotongan berlebih (*over-segmentation*) atau kesalahan pemotongan pada persilangan garis ligatur. Kegagalan segmentasi pada satu karakter merambat langsung menjadi kesalahan pengenalan pada seluruh rangkaian kata (*cascading error*) (Peng, 2024; Mosbah dkk., 2024).

Kompleksitas di atas menjadi kian menantang apabila diterapkan pada tulisan tangan anak-anak atau pemula yang memiliki variabilitas goresan tinggi, ketidakstabilan tekanan garis, dan deformasi proporsi bentuk yang signifikan dibandingkan tulisan orang dewasa (Alwagdani & Jaha, 2023).

Guna mengatasi kelemahan mendasar dari segmentasi fisik tersebut, paradigma pengenalan sekuensial nirsegmentasi (*segmentation-free sequence recognition*) menjadi solusi paling mutakhir dan menjanjikan. Pendekatan ini memperlakukan citra kata sebagai barisan representasi visual utuh yang dipetakan secara langsung menjadi urutan label karakter (*sequence of characters*). Integrasi arsitektur hibrida antara *Convolutional Neural Network* (CNN) dan *Long Short-Term Memory* (LSTM) terbukti sangat tangguh dalam mengenali barisan teks tulisan tangan bersambung (Saini dkk., 2024; Peng, 2024). Pada skema hibrida ini, lapisan konvolusi CNN bertindak sebagai pengekstraksi ciri spasial tingkat tinggi dari citra masukan, sedangkan lapisan rekuren LSTM membaca dependensi kontekstual urutan karakter secara temporal dari arah kanan ke kiri sesuai arah alami penulisan aksara Arab, sehingga mampu mengenali kata bersambung secara utuh tanpa memerlukan pemotongan karakter secara fisik (Mosbah dkk., 2024).

Selain tantangan morfologi sambung, kendala praktis krusial dalam merealisasikan rekomendasi Rahmatulloh dkk. (2022) menuju aplikasi interaktif adalah terbatasnya jumlah data latih citra *canvas digital* mandiri dan tuntutan efisiensi komputasi pada perangkat bergerak. Melatih jaringan konvolusi dalam (*deep CNN*) dari awal (*from scratch*) dengan data berskala terbatas sangat rentan memicu terjadinya *overfitting* serta memperlambat konvergensi model. Dalam konteks ini, penerapan *Transfer Learning* menjadi strategi kunci dengan memanfaatkan bobot yang telah dipelajari oleh model terlatih sebelumnya sebagai pengekstraksi representasi visual yang kaya dan tergeneralisasi (Lamtougui dkk., 2024; Masruroh dkk., 2023). Sejalan dengan perkembangan komputasi cerdas pada perangkat berdaya rendah (*mobile and edge computing*), pemilihan arsitektur *backbone* modern seperti **MobileNetV4** menawarkan keunggulan latensi sangat rendah, jumlah parameter yang ringkas, dan akurasi tinggi berkat penggunaan blok *Universal Inverted Bottleneck* (UIB) (El Khayati dkk., 2025). Karakteristik tersebut sangat ideal untuk mendukung inferensi cepat secara luring pada perangkat pembelajaran interaktif.

Kajian terhadap literatur terkini menunjukkan bahwa penelitian pengenalan tulisan tangan Arab bersambung sejauh ini masih terpusat pada dokumen pindaian kertas statis tulisan orang dewasa (seperti dataset IFN/ENIT) dengan pendekatan klasifikasi kata utuh secara holistik (*whole-word classification*) (Lamtougui dkk., 2024; Ahmed dkk., 2021). Hingga saat ini, belum ada penelitian yang menjembatani celah penelitian (*research gap*) antara model pengenalan huruf tunggal yang dirintis oleh Rahmatulloh dkk. (2022) dengan pengenalan rangkaian huruf bersambung pendek (dua hingga tiga karakter) berbasis ekspor *canvas digital* kurikulum Iqro 3 menggunakan kombinasi *transfer learning* MobileNetV4 dan LSTM secara nirsegmentasi.

Berdasarkan latar belakang permasalahan, arah perkembangan teknologi pembantu (*assisting technology*), serta pijakan riset acuan Rahmatulloh dkk. (2022), penelitian skripsi ini mengusulkan pengembangan model **Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning**. Model ini dirancang untuk memproses citra digital hasil ekspor *canvas digital* secara *segmentation-free* dan memprediksi urutan label karakter yang terkandung di dalamnya secara tepat dari kanan ke kiri. Dengan demikian, penelitian ini diharapkan dapat memberikan kontribusi nyata dalam menghadirkan sistem kecerdasan buatan yang akurat dan efisien untuk mendukung evaluasi mandiri dalam pembelajaran literasi Al-Qur'an tingkat dasar.

<br>

### 1.2 Rumusan Masalah

Berdasarkan uraian latar belakang di atas, rumusan masalah dalam penelitian proposal skripsi ini adalah:
1. Bagaimana merancang dan membangun dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang mencakup seluruh kosakata kata sambung pada buku Iqro 3?
2. Bagaimana mengimplementasikan arsitektur CNN-LSTM dengan memanfaatkan *transfer learning* MobileNetV4 untuk mengenali urutan huruf Hijaiyah bersambung pada citra tanpa melalui tahapan segmentasi manual?
3. Bagaimana kinerja model CNN-LSTM dengan *transfer learning* dalam mengenali urutan karakter huruf Hijaiyah bersambung berdasarkan metrik evaluasi pengenalan sekuensial (*exact sequence match accuracy*, *character accuracy*, dan *Character Error Rate*)?

<br>

### 1.3 Tujuan Penelitian

Sesuai dengan rumusan masalah yang diajukan, tujuan yang ingin dicapai dalam penelitian ini adalah:
1. Menghasilkan dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang terstruktur dan representatif mengacu pada materi kosakata buku Iqro 3.
2. Mengembangkan model pengenalan tulisan tangan bersambung berbasis arsitektur gabungan CNN-LSTM dengan *transfer learning* MobileNetV4 yang mampu memetakan citra secara langsung menjadi urutan karakter secara nirsegmentasi (*segmentation-free*).
3. Mengukur, menganalisis, dan mengevaluasi kinerja performa model dalam memprediksi urutan karakter huruf Hijaiyah bersambung menggunakan metrik *exact sequence match accuracy*, akurasi per karakter, dan *Character Error Rate* (CER).

<br>

### 1.4 Manfaat Penelitian

Hasil dari penelitian ini diharapkan dapat memberikan manfaat baik secara teoretis maupun praktis:

#### 1.4.1 Manfaat Teoretis
1. Memberikan kontribusi ilmiah pada bidang visi komputer (*computer vision*) dan pengenalan pola (*pattern recognition*), khususnya dalam pengembangan arsitektur hibrida nirsegmentasi CNN-LSTM dengan *transfer learning* untuk aksara kursif non-Latin.
2. Mengisi kesenjangan riset (*research gap*) antara pengenalan karakter Hijaiyah tunggal (*isolated*) dan teks bersambung (*connected text*), serta memperkaya literatur terkait pemodelan komputasi pada aksara yang memiliki variasi morfologi posisional dan ligatur kompleks pada kata pendek (2–3 huruf).

#### 1.4.2 Manfaat Praktis
1. **Bagi Peserta Didik:** Menyediakan landasan model kecerdasan buatan sebagai asisten pembantu yang mampu memberikan koreksi dan evaluasi penulisan kata Hijaiyah secara mandiri, objektif, dan instan di luar ruang kelas.
2. **Bagi Tenaga Pendidik (Guru/Ustaz):** Membantu memfasilitasi proses asesmen latihan menulis huruf Hijaiyah secara konsisten serta meringankan beban pemeriksaan manual dalam kegiatan belajar mengajar berskala besar.
3. **Bagi Pengembang Aplikasi Pembelajaran Digital:** Menyediakan rancangan model *deep learning* yang ringan, akurat, dan berdaya komputasi efisien untuk diintegrasikan ke dalam modul evaluasi aplikasi pembelajaran membaca dan menulis Al-Qur'an interaktif berbasis perangkat bergerak (*mobile/tablet*).

<br>

### 1.5 Ruang Lingkup Penelitian

#### 1.5.1 Batasan Masalah
Agar penelitian ini tetap terfokus, mendalam, dan mencapai sasaran yang terukur, batasan masalah ditetapkan sebagai berikut:
1. Objek pengenalan dibatasi pada citra tulisan tangan huruf Hijaiyah bersambung yang diekspor dari media *canvas digital* ke dalam format berkas citra digital 2 dimensi (pengenalan luring/*offline handwriting recognition*), bukan berupa data runtun waktu koordinat goresan pena (*stroke time-series*).
2. Kosakata tulisan tangan dibatasi secara ketat pada seluruh kata sambung yang termuat di dalam buku **Iqro 3**, dengan panjang rangkaian karakter terdiri atas dua hingga tiga huruf per citra.
3. Citra masukan bersumber dari penulisan pada *canvas digital* dengan bantuan tampilan pola garis titik-titik panduan (*tracing dots*).
4. Arsitektur model yang dikembangkan dibatasi pada kombinasi jaringan konvolusional (*Convolutional Neural Network*) dengan *backbone* MobileNetV4 terbobot pra-pelatihan (*transfer learning*) dan jaringan *Long Short-Term Memory* (LSTM) untuk memodelkan urutan temporal karakter dari kanan ke kiri.
5. Penelitian berfokus penuh pada perancangan dataset citra, rekayasa arsitektur model, pelatihan, penalaan hiperparameter, serta evaluasi performa pengenalan; perancangan antarmuka gamifikasi dan integrasi aplikasi secara menyeluruh dikerjakan secara terpisah oleh pihak kolaborator.
6. Evaluasi model difokuskan pada ketepatan prediksi urutan karakter teks dan tidak mencakup penilaian kaidah hukum tajwid, panjang-pendek bacaan (*mad*), maupun aspek estetika kaligrafi (*khat*).

<br>

### 1.6 Sistematika Penulisan Proposal

Proposal skripsi ini disusun dengan sistematika penulisan yang terbagi menjadi tiga bab utama sebagai berikut:

- **BAB 1 PENDAHULUAN**  
  Bab ini memuat uraian latar belakang permasalahan yang mengaitkan konteks teknologi pembantu di era modern, penelitian acuan Rahmatulloh dkk. (2022), urgensi pengenalan huruf Hijaiyah bersambung pada kurikulum Iqro 3, rumusan masalah, tujuan penelitian, manfaat penelitian teoretis dan praktis, ruang lingkup batasan masalah, serta sistematika penulisan.
- **BAB 2 KAJIAN PUSTAKA DAN DASAR TEORI**  
  Bab ini memuat tinjauan pustaka mengenai penelitian terdahulu yang relevan (*state of the art*), analisis celah penelitian (*research gap*), serta landasan teori komprehensif mengenai morfologi aksara Hijaiyah sambung, materi Iqro 3, media *canvas digital*, ekstraksi ciri visual CNN, *transfer learning*, arsitektur MobileNetV4, jaringan LSTM, konsep pengenalan nirsegmentasi (*segmentation-free*), formulasi *multi-label* urutan, dan metrik evaluasi pengenalan teks sekuensial.
- **BAB 3 METODOLOGI PENELITIAN**  
  Bab ini menguraikan tahapan dan metodologi pelaksanaan penelitian secara sistematis, meliputi diagram alir penelitian, protokol inventarisasi kosakata dan akuisisi data tulisan tangan *canvas*, kontrol kualitas dan pembagian data berbasis partisipan (*participant-wise split*), tahapan pra-pemrosesan citra, perancangan arsitektur model CNN-LSTM MobileNetV4, skenario pelatihan dua fase (*two-stage training*), rencana eksperimen dan kajian ablasi, serta matriks jadwal pelaksanaan penelitian skripsi.

<div style="page-break-after: always;"></div>

---

<!-- BAGIAN TUBUH PROPOSAL: BAB 2 (Halaman 11) -->

# BAB 2
# KAJIAN PUSTAKA DAN DASAR TEORI

<br>

### 2.1 Penelitian Terdahulu (*State of the Art*)

Penelitian di bidang pengenalan tulisan tangan aksara Arab dan Hijaiyah (*Arabic/Hijaiyah Handwriting Recognition*) telah mengalami perkembangan yang signifikan seiring pesatnya kemajuan teknologi *Deep Learning*. Namun demikian, sebagian besar penelitian yang telah dipublikasikan masih memiliki batasan ruang lingkup pada karakter tunggal atau mengabaikan pemodelan urutan sekuensial nirsegmentasi.

Sebagai pijakan utama penelitian ini, Rahmatulloh dkk. (2022) melakukan penelitian berjudul *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"*. Penelitian tersebut menginvestigasi optimasi CNN menggunakan pengoptimal ADAM untuk mengklasifikasikan huruf Hijaiyah tunggal (*isolated*). Dengan menggunakan citra berukuran 32×32 piksel, model tersebut mencapai akurasi sebesar 91% pada dataset anak-anak (Hijja2) yang terdiri atas 47.434 citra dari 591 anak, serta akurasi 98% pada dataset dewasa (AHCD). Meskipun memberikan fondasi yang kuat, penelitian Rahmatulloh dkk. (2022) hanya mengenali karakter terisolasi dan belum menangani karakter bersambung. Dalam bagian kesimpulannya, Rahmatulloh dkk. (2022) secara eksplisit merekomendasikan pengembangan model pengenalan tulisan tangan Hijaiyah ke dalam aplikasi interaktif berbasis perangkat bergerak (*mobile*).

Durayhim dkk. (2023) meneliti pengenalan tulisan tangan huruf Arab pada anak-anak menggunakan dataset Hijja. Penelitian tersebut mengeksplorasi pengenalan 108 varian bentuk posisional huruf (*isolated*, *initial*, *medial*, *final*) dan mengembangkan prototipe aplikasi tablet bernama *Mutqin*. Hasil pengujian aplikasi menunjukkan penerimaan yang sangat positif dari 11 siswa dan 8 guru sekolah dasar. Model CNN kustom yang dibangun mencapai akurasi 95% pada klasifikasi 108 bentuk posisi. Namun demikian, Durayhim dkk. (2023) mencatat bahwa pengenalan kata bersambung seutuhnya belum dapat dilakukan dan secara spesifik menyatakan pengenalan huruf tersambung dan kata (*connected letters and words*) sebagai agenda riset lanjutan (*future work*).

Terkait strategi *transfer learning*, Masruroh dkk. (2023) menyajikan studi komparasi mendalam pada sistem pengenalan tulisan tangan Arab dengan membandingkan enam arsitektur *backbone* (ResNet50, DenseNet, VGG16, VGG19, InceptionV3, dan MobileNet) menggunakan dua pengoptimal (ADAM dan SGD) serta variasi *learning rate*. Hasil pengujian menunjukkan bahwa pengoptimal ADAM dengan *learning rate* 1e-4 menghasilkan performa terbaik (VGG16 mencapai akurasi 96% pada AHCD dan 87% pada Hijja). Masruroh dkk. (2023) menemukan bahwa proses pelatihan dua tahap (tahap pembekuan bobot dasar diikuti penalaan halus/fine-tuning) sangat krusial untuk mencegah rusaknya representasi visual awal pada dataset tulisan tangan yang terbatas.

Dalam hal efisiensi komputasi pada perangkat bergerak, El Khayati dkk. (2025) mengevaluasi efektivitas *transfer learning* pada jaringan konvolusional ringan (*mobile-enabled CNNs*). Penelitian tersebut membandingkan strategi *Training with Initialization* (TWI), *Training Feature Extractor* (TFE), dan *Training from Scratch* (TFS). Temuan mereka menegaskan bahwa pembekuan lapisan secara total tanpa *fine-tuning* (TFE) mengalami penurunan performa drastis akibat adanya pergeseran domain (*domain shift*) antara citra natural ImageNet dan citra goresan tulisan tangan, sehingga penalaan halus sebagian lapisan konvolusi atas (*partial fine-tuning*) menjadi sebuah keharusan metodologis.

Untuk mengatasi permasalahan segmentasi pada tulisan sambung kursif, Peng (2024) mempublikasikan algoritma pengenalan tulisan tangan nirsegmentasi (*segmentation-free*) berbasis gabungan CNN dan BiLSTM dengan *Connectionist Temporal Classification* (CTC) pada enam basis data multibahasa. Penelitian tersebut membuktikan bahwa pendekatan nirsegmentasi jauh lebih unggul dibandingkan metode segmentasi tradisional, karena tidak rentan terhadap pemotongan salah pada ligatur karakter yang saling bertumpuk. Namun, Peng (2024) menggarisbawahi bahwa aksara Arab kursif (dataset KHATT) merupakan kasus tersulit dengan akurasi pengenalan karakter hanya mencapai 58,02%, yang menandakan bahwa pengenalan teks Arab bersambung masih menjadi tantangan terbuka yang memerlukan arsitektur pengekstraksi ciri visual yang lebih tangguh.

Sejalan dengan hal tersebut, Mosbah dkk. (2024) mengembangkan *ADOCRNet* pada jurnal *IEEE Access*, yang memadukan lapisan konvolusional bertingkat dengan jaringan *Bidirectional LSTM* (BLSTM) dan fungsi kerugian CTC untuk mengenali dokumen teks Arab secara *end-to-end*. Mosbah dkk. (2024) membuktikan bahwa penambahan lapisan rekuren LSTM berhasil memodelkan konteks penulisan aksara Arab secara temporal dan menurunkan *Character Error Rate* (CER) secara signifikan tanpa memerlukan segmentasi glif secara individual.

Saini dkk. (2024) pada konferensi IEEE InC4 juga membuktikan ketangguhan arsitektur gabungan CNN dan LSTM dengan dekoder CTC pada dataset kata tulisan tangan IAM, menghasilkan *Character Error Rate* (CER) validasi sebesar 8,65%. Arsitektur gabungan ini menjadi bukti empiris bahwa ekstraksi ciri spasial oleh CNN yang dilanjutkan dengan pembacaan dependensi sekuensial oleh LSTM adalah konfigurasi standar yang sangat andal untuk mengenali barisan teks sambung.

Ringkasan perbandingan antara penelitian-penelitian terdahulu dan posisi kebaruan (*novelty*) dari penelitian yang diusulkan ini dirangkum pada Tabel 2.1.

<br>

**Tabel 2.1 Matriks Sintesis Penelitian Terdahulu dan Identifikasi Celah Riset (*Research Gap*)**

| No | Peneliti & Tahun | Objek & Dataset | Metode / Arsitektur | Capaian Utama | Celah Penelitian Teridentifikasi (*Research Gap*) |
|:---|:---|:---|:---|:---|:---|
| 1. | **Rahmatulloh dkk. (2022)** *(Baseline)* | Huruf Hijaiyah tunggal (*isolated*); dataset Hijja2 & AHCD | CNN custom + ADAM optimizer | Akurasi 91% (Hijja2) dan 98% (AHCD) | Hanya huruf tunggal; belum menangani huruf sambung; menyarankan implementasi ke aplikasi *mobile*. |
| 2. | **Durayhim dkk. (2023)** | Huruf Arab anak (108 varian posisi); dataset Hijja | CNN 7-layer vs VGG-16; aplikasi tablet *Mutqin* | Akurasi 95% (108 kelas posisi); UAT tablet berhasil | Masih klasifikasi huruf per huruf; kata sambung dinyatakan sebagai *future work*. |
| 3. | **Masruroh dkk. (2023)** | Karakter Arab/Hijaiyah isolated; dataset Hijja & AHCD | Grid 6 CNN backbone (VGG, ResNet, MobileNet) + ADAM | VGG16 + ADAM (lr 1e-4) terbaik: 87% Hijja, 96% AHCD | Klasifikasi statis huruf tunggal; belum memodelkan urutan huruf bersambung. |
| 4. | **El Khayati dkk. (2025)** | Karakter Arab tunggal & kata; AHCD, Hijja, IFN/ENIT | MobileNet, ShuffleNet; evaluasi TWI, TFE, TFS | ShuffleNet TWI 92% Hijja; TFE beku total gagal | Fokus pada huruf isolated; pengenalan kursif berbasis segmen manual memiliki CER tinggi. |
| 5. | **Peng (2024)** | Teks baris tulisan tangan multibahasa; KHATT Arab | CNN + BiLSTM + CTC (*segmentation-free*) | Akurasi rata-rata 91,13%; KHATT Arab tersulit (58,02%) | Tanpa *transfer learning*; akurasi aksara Arab kursif masih rendah; membutuhkan backbone visual modern. |
| 6. | **Mosbah dkk. (2024)** | Dokumen Arab teks cetak & tulis; IFN/ENIT | CRNN (CNN + BLSTM + CTC loss) | WER 1,09% pada IFN/ENIT kata tertutup | Kosakata tertutup nama kota dewasa pindaian kertas; belum menyentuh citra *canvas* anak/pemula. |
| 7. | **Saini dkk. (2024)** | Kata tulisan tangan sambung; dataset IAM | CNN 11-layer + BiLSTM 5-layer + CTC | CER validasi 8,65% tanpa segmentasi manual | Berorientasi aksara Latin (kiri ke kanan); tanpa variasi bentuk posisional dan titik diakritik Arab. |
| 8. | **Penelitian yang Diusulkan (2026)** | Kata sambung Hijaiyah (2–3 huruf); ekspor *canvas digital*; buku **Iqro 3** | **CNN-LSTM** (*backbone* **MobileNetV4** terbobot *transfer learning*) | Target: Pengenalan sekuensial nirsegmentasi akurat & efisien | **Mengisi celah riset:** Menggabungkan *transfer learning* MobileNetV4 hemat komputasi dan LSTM untuk mengenali urutan huruf Hijaiyah sambung Iqro 3 hasil *canvas digital*. |

<br>

Berdasarkan sintesis pada Tabel 2.1, terlihat jelas adanya celah penelitian yang belum terpecahkan: belum ada penelitian yang menggabungkan efisiensi *transfer learning* arsitektur modern MobileNetV4 dengan pemodelan urutan LSTM untuk mengenali **urutan huruf Hijaiyah bersambung (2 hingga 3 huruf) secara nirsegmentasi pada citra hasil ekspor *canvas digital* kurikulum Iqro 3**. Penelitian ini secara langsung mengisi ruang kosong tersebut sekaligus menjawab rekomendasi penelitian Rahmatulloh dkk. (2022).

<br>

### 2.2 Karakteristik Huruf Hijaiyah Sambung dan Kurikulum Iqro 3

Aksara Hijaiyah terdiri atas 28 hingga 29 karakter fonemik dasar yang ditulis dan dibaca secara horisontal dari arah kanan ke kiri (*Right-to-Left*). Berbeda dengan sistem alfabet Latin yang memiliki pemisah spasi tegas antarhuruf dalam satu kata, aksara Hijaiyah secara alami ditulis secara kursif bersambung (*cursive script*).

Dalam konteks pengenalan pola komputasi visual, penulisan huruf Hijaiyah bersambung menghadirkan kompleksitas unik yang meliputi:
1. **Perubahan Alomorf Posisi (*Positional Allomorphs*):** Sebagian besar huruf Hijaiyah mengalami modifikasi morfologis yang signifikan bergantung pada posisinya dalam kata. Sebagaimana divisualisasikan pada Gambar 2.1, satu karakter huruf dapat memiliki hingga empat glif visual yang berbeda: bentuk berdiri sendiri (*isolated*), bentuk awal (*initial*), bentuk tengah (*medial*), dan bentuk akhir (*final*). Terdapat pula kelompok huruf tertentu (seperti alif [ا], dal [د], dhal [ذ], ra [ر], zai [ز], dan waw [و]) yang hanya dapat menyambung dengan huruf di sebelah kanannya tetapi tidak dapat menyambung dengan huruf di sebelah kirinya, sehingga memutus kontinuitas garis dasar (*baseline*).

<br>

<div align="center">

```
Bentuk Mandiri (Isolated)  <--  Bentuk Akhir (Final)  <--  Bentuk Tengah (Medial)  <--  Bentuk Awal (Initial)
          ع                               ـع                              ـعـ                             عـ
          ب                               ـب                              ـبـ                             بـ
```

**Gambar 2.1 Variasi Bentuk Glif Huruf Hijaiyah Berdasarkan Posisi dalam Kata**

</div>

<br>

2. **Keserupaan Kerangka dan Peran Diakritik (*Skeleton Similarity and Dots*):** Banyak karakter Hijaiyah yang berbagi kerangka bentuk tubuh (*grapheme primary body*) yang persis sama. Sebagai contoh, karakter Ba (ب), Ta (ت), dan Tsa (ث) memiliki lengkungan dasar identik dan hanya dibedakan oleh penempatan dan jumlah titik diakritik (satu titik di bawah untuk Ba, dua titik di atas untuk Ta, dan tiga titik di atas untuk Tsa). Pada tulisan tangan, titik-titik ini kerap kali terdistorsi menjadi garis pendek, bergeser, atau menyatu dengan goresan ligatur, yang dapat mengakibatkan kesalahan identifikasi fatal (Albattah & Albahli, 2022).
3. **Pembentukan Ligatur Nir-ruang (*Ligature and Overlapping*):** Rangkaian huruf yang bersambung membentuk sambungan (*ligature*) yang mulus tanpa adanya spasi pemisah. Pada beberapa pasangan huruf tertentu (misalnya Jim yang disambung dengan Mim [جم]), terjadi penumpukan karakter secara vertikal di atas garis dasar. Karakteristik ini menyebabkan teknik segmentasi konvensional berbasis proyeksi profil vertikal atau analisis komponen terhubung (*connected component analysis*) mengalami kegagalan sistematis (Peng, 2024).

Buku **Iqro 3** merupakan kurikulum standardisasi pengenalan kata bersambung tingkat dasar di Indonesia. Pada buku ini, materi pembelajaran berfokus penuh pada kata-kata pendek yang tersusun atas dua hingga tiga huruf Hijaiyah bersambung dengan harakat fathah tunggal yang dibaca pendek (*qashr*). Pembatasan ruang lingkup pada kosakata buku Iqro 3 memberikan korpus linguistik yang terdefinisi dengan sangat baik (*bounded vocabulary*), memungkinkan evaluasi performa model berfokus pada variasi goresan tulisan tangan tanpa terdistorsi oleh variasi kosakata bahasa Arab yang tak terbatas.

<br>

### 2.3 Media *Canvas Digital* dan Akuisisi Citra Tulisan Tangan

Media *canvas digital* merupakan antarmuka grafis interaktif berbasis perangkat layar sentuh yang memungkinkan pengguna menggoreskan garis secara bebas menggunakan jari atau pena stilus. Dalam sistem pengenalan tulisan tangan (*Handwriting Recognition*), terdapat dua domain pengenalan:
1. **Pengenalan Daring (*Online Recognition*):** Sistem memproses urutan koordinat temporal spasial $(x_t, y_t)$, kecepatan goresan, dan tekanan pena seiring berjalannya waktu saat goresan dibuat.
2. **Pengenalan Luring (*Offline Recognition*):** Sistem memproses berkas citra digital 2 dimensi statis yang dihasilkan setelah seluruh proses penulisan selesai dilakukan.

Penelitian ini memfokuskan diri pada domain **pengenalan luring (*offline recognition*)**, di mana masukan model berupa satu citra hasil ekspor kanvas berformat grafis raster. Pendekatan luring dipilih karena memiliki kompatibilitas universal yang jauh lebih luas, tidak bergantung pada spesifikasi perangkat keras sensor sentuh tertentu, serta memungkinkan penyimpanan dan transmisi data yang lebih efisien dalam arsitektur sistem modular.

Untuk memandu peserta didik pemula dalam berlatih menulis kata bersambung, antarmuka *canvas digital* menampilkan pola garis titik-titik panduan (*tracing dots/guide lines*). Kehadiran garis panduan ini berfungsi menjaga proporsi goresan dan kelurusan garis dasar (*baseline*), sebagaimana diterapkan pada aplikasi *Mutqin* oleh Durayhim dkk. (2023). Citra hasil goresan kemudian diekspor dengan latar belakang transparan/putih dan goresan berwarna kontras.

<br>

### 2.4 *Convolutional Neural Network* (CNN) sebagai Pengekstrak Ciri

*Convolutional Neural Network* (CNN) merupakan arsitektur jaringan saraf tiruan yang dirancang secara khusus untuk memproses data berstruktur kisi spasial dua dimensi seperti citra digital. CNN memiliki kemampuan luar biasa dalam mengekstraksi hierarki representasi visual secara otomatis, mulai dari deteksi tepi (*edges*), sudut (*corners*), goresan melengkung, hingga struktur bentuk glif karakter yang kompleks melalui operasi konvolusi berbobot bersama (*weight sharing*) dan *spatial pooling*.

Operasi konvolusi 2D pada sebuah posisi piksel $(i, j)$ dalam peta fitur masukan $X$ dengan kernel filter $W$ berukuran $k \times k$ dan bias $b$ dirumuskan secara matematis sebagai berikut:

$$Y(i, j) = f\left( \sum_{m=-p}^{p} \sum_{n=-p}^{p} W(m, n) \cdot X(i+m, j+n) + b \right) \tag{2.1}$$

dengan:
- $Y(i, j)$ adalah nilai keluaran pada peta fitur baru pada koordinat $(i, j)$,
- $f(\cdot)$ adalah fungsi aktivasi non-linear (seperti ReLU atau Hard-Swish),
- $p = \frac{k-1}{2}$ merupakan radius ukuran kernel ganjil,
- $W(m, n)$ adalah bobot kernel konvolusi, dan
- $b$ adalah parameter bias.

Melalui penumpukan lapisan konvolusional dan reduksi dimensi spasial, CNN mampu menghasilkan representasi ciri visual yang invarian terhadap pergeseran posisi kecil (*translation invariant*) dan variasi ketebalan goresan tulisan tangan.

<br>

### 2.5 *Transfer Learning* dan Arsitektur MobileNetV4

*Transfer Learning* merupakan paradigma dalam pembelajaran mesin di mana pengetahuan berupa representasi bobot yang telah dipelajari oleh suatu model pada domain tugas sumber yang berskala masif (seperti klasifikasi 1,4 juta citra pada dataset ImageNet) ditransfer dan dimanfaatkan untuk menyelesaikan tugas pada domain sasaran baru yang memiliki keterbatasan jumlah data latih.

Dalam pengenalan tulisan tangan pada dataset kanvas mandiri berukuran terbatas, melatih arsitektur jaringan dalam dari nol (*from scratch*) sangat rentan menimbulkan fenomena *overfitting*, di mana model menghafal derau (*noise*) data latih dan gagal melakukan generalisasi pada tulisan pengguna baru (Lamtougui dkk., 2024). Dengan memanfaatkan bobot pra-pelatihan (*pre-trained weights*), lapisan konvolusi awal model telah memiliki kapabilitas mendeteksi fitur-fitur visual fundamental secara matang.

Penelitian ini mengadopsi arsitektur *backbone* modern **MobileNetV4** yang diperkenalkan oleh Google pada tahun 2024. MobileNetV4 dirancang khusus untuk memberikan efisiensi komputasi maksimal pada perangkat bergerak (*mobile devices*) melalui integrasi blok **Universal Inverted Bottleneck (UIB)**. Sebagaimana diilustrasikan pada Gambar 2.2, blok UIB menyatukan fleksibilitas antara *Inverted Bottleneck* (IB), *Conv-Forward*, dan *Depthwise Separable Convolution* ke dalam satu modul terpadu.

<br>

<div align="center">

```
Masukan (C kanal)
       │
       ▼
┌────────────────────────────────────────┐
│ Konvolusi 1×1 (Ekspansi Kanal Spasial) │
└────────────────────────────────────────┘
       │
       ▼
┌────────────────────────────────────────┐
│ Konvolusi Depthwise (DW) Spasial 3×3/5×5│
└────────────────────────────────────────┘
       │
       ▼
┌────────────────────────────────────────┐
│ Konvolusi 1×1 (Proyeksi Reduksi Kanal) │
└────────────────────────────────────────┘
       │
       ▼  (Ditambahkan Sambungan Residual jika dimensi sama)
Keluaran Blok
```

**Gambar 2.2 Arsitektur Blok *Universal Inverted Bottleneck* (UIB) pada MobileNetV4**

</div>

<br>

Keunggulan utama MobileNetV4 dibandingkan arsitektur CNN klasik (seperti VGG16 atau ResNet50) adalah rasio efisiensi parameter yang sangat superior. MobileNetV4 varian *Small/Medium* hanya memiliki parameter sekitar 3,8 hingga 11 juta (berbanding 138 juta pada VGG16), namun mampu menghasilkan akurasi yang setara atau lebih tinggi dengan konsumsi memori dan latensi inferensi yang jauh lebih rendah. Karakteristik ini sangat selaras dengan visi implementasi aplikasi *mobile* yang direkomendasikan oleh Rahmatulloh dkk. (2022).

Dalam implementasinya, strategi *transfer learning* dijalankan melalui skema penalaan halus bertahap (*two-stage fine-tuning*). Pada tahap awal, lapisan bawah *backbone* dibekukan (*frozen*) agar bobot visual dasar tidak rusak, sementara kepala model (*head*) dilatih untuk beradaptasi dengan domain aksara Arab. Pada tahap kedua, beberapa blok atas MobileNetV4 dibuka kuncinya (*unfrozen*) untuk dilatih bersamaan dengan laju pembelajaran (*learning rate*) rendah (misalnya $10^{-4}$ atau $10^{-5}$) guna memetakan detail visual spesifik huruf Hijaiyah (Masruroh dkk., 2023; Lamtougui dkk., 2024).

<br>

### 2.6 *Long Short-Term Memory* (LSTM) untuk Pemodelan Urutan Temporal

Jaringan saraf konvolusional standar (CNN) mengekstraksi fitur visual secara independen di setiap wilayah spasial tanpa memahami dependensi kontekstual urutan teks. Pada teks bersambung, kemunculan suatu karakter sangat dipengaruhi oleh karakter sebelum dan sesudahnya sesuai kaidah bahasa dan morfologi kata.

*Recurrent Neural Network* (RNN) dirancang khusus untuk memproses data sekuensial. Namun, RNN konvensional menderita masalah degradasi gradien yang hilang (*vanishing gradient*) pada deret yang panjang. Arsitektur *Long Short-Term Memory* (LSTM) mengatasi kendala ini dengan memperkenalkan *memory cell* dan tiga gerbang pengendali aliran informasi: *forget gate* ($f_t$), *input gate* ($i_t$), dan *output gate* ($o_t$).

<br>

<div align="center">

```
              ┌─────────────────────────┐
              │ State Sel c_{t-1} ──────┼───> [ + ] ────────────> c_t
              │                         │      ▲
              │   ┌───────────────┐     │      │ (*)
              │   │ Forget Gate   │────(*)     │
              │   │ f_t           │            │
Masukan x_t ──┼──>│ Input Gate    │───────────(*)
              │   │ i_t & \tilde{c}_t          ▲
              │   │                            │
              │   │ Output Gate   │───────────(*)
              │   │ o_t           │            │
              │   └───────────────┘            ▼
              │ State Tersembunyi h_{t-1} ────┼───────────────> h_t
              └─────────────────────────┘
```

**Gambar 2.3 Struktur Sel Rekuren *Long Short-Term Memory* (LSTM) dengan Tiga *Gates***

</div>

<br>

Persamaan matematis pembaruan sel LSTM pada langkah waktu temporal $t$ disajikan sebagai berikut:

$$f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f) \tag{2.2}$$

$$i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i) \tag{2.3}$$

$$\tilde{c}_t = \tanh(W_c \cdot [h_{t-1}, x_t] + b_c) \tag{2.4}$$

$$c_t = f_t \odot c_{t-1} + i_t \odot \tilde{c}_t \tag{2.5}$$

$$o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o) \tag{2.6}$$

$$h_t = o_t \odot \tanh(c_t) \tag{2.7}$$

dengan:
- $\sigma$ melambangkan fungsi aktivasi sigmoid logistic,
- $\odot$ melambangkan operasi perkalian elemen-demi-elemen (*Hadamard product*),
- $x_t$ adalah vektor ciri visual pada kolom spasial ke-$t$ dari keluaran CNN,
- $h_t$ adalah vektor keadaan tersembunyi (*hidden state*) pada langkah $t$, dan
- $c_t$ adalah nilai memori internal sel pada langkah $t$.

Dalam penelitian ini, arah urutan temporal diselaraskan dengan arah penulisan aksara Arab, yakni membaca fitur kolom dari arah kanan menuju kiri, sehingga lapisan LSTM secara kontekstual mempelajari urutan kemunculan karakter dari awal hingga akhir kata.

<br>

### 2.7 Paradigma Pengenalan Nirsegmentasi (*Segmentation-Free*)

Paradigma pengenalan tulisan tangan konvensional bertumpu pada tahapan segmentasi eksplisit: memotong citra kata menjadi segmen-segmen huruf tunggal, lalu mengklasifikasikan tiap segmen menggunakan model klasifikasi standar. Pada aksara Arab/Hijaiyah bersambung, pemotongan ini sangat tidak andal karena keberadaan ligatur dan tumpang tindih goresan vertikal yang mengakibatkan galat segmentasi merambat (*cascading error*) (Peng, 2024).

Paradigma **nirsegmentasi (*segmentation-free*)** menghilangkan kebutuhan pemotongan fisik karakter. Seluruh citra kata diproses sebagai satu kesatuan utuh oleh arsitektur *Convolutional Recurrent Neural Network* (CRNN). Citra berdimensi $(H, W, C)$ diekstraksi oleh CNN menjadi peta fitur visual terkompresi berdimensi $(1, W', D)$. Peta fitur ini kemudian ditransformasikan (*map-to-sequence*) menjadi barisan vektor kolom sebanyak $W'$ langkah waktu, di mana setiap vektor kolom merepresentasikan irisan fitur visual selebar resolusi tertentu. Barisan vektor tersebut selanjutnya dimasukkan ke dalam lapisan LSTM untuk memprediksi label urutan karakter secara simultan (Mosbah dkk., 2024; Saini dkk., 2024).

<br>

### 2.8 Formulasi Masalah *Multi-Label* dan Pemodelan Urutan

Judul penelitian ini menggunakan frasa **"Klasifikasi Multi-Label"**, yang dalam konteks arahan penelitian ini memiliki pengertian spesifik yang diselaraskan dengan kebutuhan praktis pembelajaran Iqro 3. Pada literatur pembelajaran mesin konvensional, klasifikasi *multi-label* didefinisikan sebagai penentuan keberadaan beberapa label kelas dari himpunan kandidat pada satu sampel citra tanpa memperhatikan urutan kemunculannya (*order-invariant*) (Chen dkk., 2019; Tarekegn dkk., 2024).

Namun demikian, pada pengenalan kata bersambung, urutan kemunculan huruf memegang peranan krusial (misalnya kata "بَتَ" [Ba-Ta] memiliki makna linguistik yang berbeda dengan "تَبَ" [Ta-Ba]), serta terdapat potensi kemunculan huruf yang sama secara berulang (misalnya kata "بَبَمَ" [Ba-Ba-Ma]). Klasifikasi *multi-label* biner standar (menggunakan fungsi kerugian *Binary Cross-Entropy*) tidak mampu menangani huruf berulang dan urutan baca. Oleh sebab itu, implementasi teknis pada penelitian ini menyelaraskan makna *multi-label* tersebut ke dalam arsitektur **pemodelan urutan karakter (*sequence recognition*)** berbasis CNN-LSTM, sebagaimana diperbandingkan pada Tabel 2.2.

<br>

**Tabel 2.2 Perbandingan Karakteristik Klasifikasi Multi-Label Klasik vs Pengenalan Urutan Karakter**

| Dimensi Karakteristik | Multi-Label Klasik (Standar) | Pengenalan Urutan Karakter (Penelitian Ini) |
|:---|:---|:---|
| **Definisi Luaran** | Himpunan label aktif biner $\{0, 1\}^K$ tanpa urutan | Barisan sekuensial label karakter $\mathbf{y} = (y_1, y_2, \dots, y_L)$ |
| **Urutan Karakter** | Diabaikan (*order-invariant*) | Wajib dipertahankan (kanan ke kiri) |
| **Karakter Berulang** | Tidak dapat menangani kemunculan ganda (hanya 0 atau 1) | Mampu memprediksi huruf berulang pada posisi berbeda |
| **Arsitektur Model** | CNN *standalone* + Sigmoid Output Layer | Gabungan CNN (MobileNetV4) + Sequence Layer (LSTM) |
| **Relevansi Kata Sambung** | Rendah (tidak dapat membedakan permutasi kata) | Sangat tinggi (mendeteksi kata Iqro 3 secara presisi) |

<br>

### 2.9 Metrik Evaluasi Pengenalan Teks Sekuensial

Evaluasi performa model pengenalan urutan karakter tidak cukup dinilai menggunakan metrik akurasi klasifikasi sederhana. Penelitian ini menggunakan tiga metrik evaluasi baku berstandar internasional dalam bidang *Handwriting Text Recognition*:

1. **Exact Sequence Match Accuracy (Word-Level Accuracy):**  
   Mengukur persentase citra di mana seluruh urutan karakter yang diprediksi oleh model cocok secara sempurna ($100\%$ identik) dengan urutan label acuan (*ground truth*). Metrik ini dihitung sebagai:

   $$\text{Exact Match (\%)} = \frac{\sum_{i=1}^{N} \mathbb{I}(\mathbf{\hat{y}}_i == \mathbf{y}_i)}{N} \times 100\% \tag{2.8}$$

   dengan $\mathbb{I}(\cdot)$ bernilai 1 jika seluruh deret karakter identik dan 0 jika terdapat setidaknya satu karakter yang salah, serta $N$ adalah total jumlah sampel uji.

2. **Character-Level Accuracy (Akurasi Karakter):**  
   Mengukur persentase karakter individu yang diprediksi dengan benar pada posisi urutan yang bersesuaian terhadap total panjang karakter target.

3. **Character Error Rate (CER):**  
   Metrik standar utama berbasis jarak Levenshtein (*Levenshtein distance*) yang menghitung jumlah minimum operasi penyuntingan yang diperlukan untuk mengubah barisan prediksi menjadi barisan acuan. CER didefinisikan sebagai:

   $$\text{CER} = \frac{S + D + I}{N_c} \times 100\% \tag{2.9}$$

   dengan:
   - $S$ adalah jumlah karakter yang disubstitusi (salah prediksi),
   - $D$ adalah jumlah karakter yang terhapus (*deletion* / tidak terprediksi),
   - $I$ adalah jumlah karakter yang tersisip berlebih (*insertion*), dan
   - $N_c$ adalah total jumlah karakter keseluruhan pada teks acuan (*ground truth*).

<div style="page-break-after: always;"></div>

---

<!-- BAGIAN TUBUH PROPOSAL: BAB 3 (Halaman 27) -->

# BAB 3
# METODOLOGI PENELITIAN

<br>

### 3.1 Alur dan Desain Penelitian

Penelitian ini dilaksanakan secara bertahap dan sistematis melalui enam tahapan utama yang saling berkesinambungan. Diagram alir tahapan pelaksanaan penelitian disajikan pada Gambar 3.1.

<br>

<div align="center">

```
                        ┌──────────────────────────────────────┐
                        │      1. Studi Literatur & Acuan      │
                        │    (Rahmatulloh 2022, IQRO 3, CNN)   │
                        └──────────────────┬───────────────────┘
                                           │
                                           ▼
                        ┌──────────────────────────────────────┐
                        │  2. Pengumpulan Dataset Canvas Iqro  │
                        │  (Kosakata Iqro 3, Prompting Canvas) │
                        └──────────────────┬───────────────────┘
                                           │
                                           ▼
                        ┌──────────────────────────────────────┐
                        │    3. Kontrol Kualitas & Split Data  │
                        │      (QC & Participant-Wise Split)   │
                        └──────────────────┬───────────────────┘
                                           │
                                           ▼
                        ┌──────────────────────────────────────┐
                        │       4. Pra-pemrosesan Citra        │
                        │ (Invert, Crop Bounding Box, Resize)  │
                        └──────────────────┬───────────────────┘
                                           │
                                           ▼
                        ┌──────────────────────────────────────┐
                        │  5. Pemodelan CNN-LSTM MobileNetV4   │
                        │  (Transfer Learning Two-Stage Train) │
                        └──────────────────┬───────────────────┘
                                           │
                                           ▼
                        ┌──────────────────────────────────────┐
                        │     6. Evaluasi & Analisis Performa  │
                        │      (Exact Match, CER, Ablasi)      │
                        └──────────────────────────────────────┘
```

**Gambar 3.1 Diagram Alir Tahapan Pelaksanaan Penelitian**

</div>

<br>

Rincian dari setiap tahapan penelitian pada Gambar 3.1 dijelaskan sebagai berikut:
1. **Studi Literatur:** Mempelajari landasan teoritis mengenai morfologi aksara Hijaiyah bersambung, menelaah penelitian acuan Rahmatulloh dkk. (2022), serta mengkaji metode mutakhir arsitektur CNN-LSTM, *transfer learning* MobileNetV4, dan paradigma nirsegmentasi.
2. **Pengumpulan Dataset Canvas Iqro 3:** Merancang antarmuka *canvas digital* interaktif, merekap seluruh perbendaharaan kata bersambung pada buku Iqro 3, dan menyelenggarakan kegiatan pengambilan data tulisan tangan terpandu *prompt*.
3. **Kontrol Kualitas dan Pembagian Data:** Memeriksa kesahihan citra goresan terhadap label target serta membagi dataset menjadi subset pelatihan, validasi, dan pengujian berbasis penulis (*participant-wise split*).
4. **Pra-pemrosesan Citra:** Melakukan normalisasi format citra, konversi aras keabuan (*grayscale*), inversi biner, pemotongan area goresan (*bounding box crop*), penyesuaian ukuran proporsional (*aspect ratio preserving resize*), dan augmentasi citra.
5. **Pemodelan CNN-LSTM dan Pelatihan:** Membangun arsitektur gabungan pengekstraksi ciri MobileNetV4 dan pembaca sekuensial LSTM, kemudian melatih model menggunakan skema *two-stage fine-tuning*.
6. **Evaluasi dan Analisis Performa:** Menguji kinerja model menggunakan metrik *exact match*, akurasi karakter, dan CER, serta melakukan kajian ablasi (*ablation study*) dan analisis matriks kekeliruan (*confusion matrix*).

<br>

### 3.2 Desain dan Protokol Pengumpulan Dataset *Canvas* Iqro 3

Ketiadaan dataset publik yang secara spesifik memuat citra tulisan tangan huruf Hijaiyah bersambung hasil *canvas digital* kurikulum Iqro menuntut pelaksanaan akuisisi data primer secara mandiri dan terstandarisasi.

#### 3.2.1 Inventarisasi Kosakata Buku Iqro 3
Langkah pertama dalam perancangan dataset adalah merekapitulasi seluruh kosakata kata sambung yang termuat di dalam buku **Iqro 3** (halaman 1 hingga 30). Setiap entri kata diinventarisasi ke dalam berkas manifest data yang memuat:
- Representasi teks Arab asli (misalnya: "بَتَ", "سَجَدَ", "خَلَقَ"),
- Panjang karakter (terdiri atas 2 hingga 3 huruf),
- Posisi glif morfologis tiap huruf (*initial*, *medial*, *final*), serta
- Nilai transkripsi fonetik Latin standar.

Daftar kosakata ini menjadi batas korpus (*vocabulary boundary*) tertutup bagi sistem.

#### 3.2.2 Protokol Pengumpulan Tulisan Tangan pada *Canvas Digital*
Pengambilan data dilakukan menggunakan aplikasi *canvas digital* berbasis web/tablet layar sentuh dengan skema penulisan terpandu *prompt* (*prompt-based guided writing*). Diagram alur protokol akuisisi disajikan pada Gambar 3.2.

<br>

<div align="center">

```
┌────────────────────────┐      ┌────────────────────────┐      ┌────────────────────────┐
│ 1. Sistem Menampilkan  │      │ 2. Responden Menulis   │      │ 3. Sistem Mengekspor   │
│    Kata Target & Audio │ ───> │    Goresan pada Canvas │ ───> │    Citra Tunggal (PNG) │
│    Panduan Tracing Dots│      │    Layar Sentuh/Stilus │      │    Disertai Metadata   │
└────────────────────────┘      └────────────────────────┘      └────────────────────────┘
```

**Gambar 3.2 Diagram Alur Protokol Akuisisi Data Tulisan Tangan Berbasis *Prompt Canvas***

</div>

<br>

Prosedur pelaksanaan akuisisi meliputi:
1. Responden diperlihatkan satu kata target secara acak dari korpus Iqro 3 pada layar. Layar kanvas menampilkan garis panduan titik-titik samar (*tracing dots*) untuk membantu responden menjaga proporsi goresan.
2. Responden menebalkan atau menuliskan kata target tersebut pada area kanvas aktif menggunakan jari atau pena stilus.
3. Setelah goresan selesai, sistem secara otomatis mengekspor area kanvas menjadi berkas citra berformat PNG dengan latar belakang putih dan goresan berwarna hitam.
4. Setiap sampel yang tersimpan secara otomatis diasosiasikan dengan metadata yang mencakup ID responden, indeks kata target, urutan penulisan, dan label urutan huruf dari kanan ke kiri.

Target pengumpulan data minimal adalah **1.500 hingga 2.500 sampel citra** yang dikumpulkan dari sedikitnya 20 hingga 30 responden sukarelawan (peserta didik usia anak/pemula serta mahasiswa).

#### 3.2.3 Verifikasi Kontrol Kualitas Data (*Quality Control*)
Untuk menjamin validitas dan reliabilitas data latih, seluruh citra yang terkumpul melalui tahapan kendali mutu (*Quality Control*) independen oleh dua verifikator. Sampel citra akan ditolak (*discarded*) apabila memenuhi kriteria berikut:
- Goresan terlalu kabur, terputus parah, atau tidak terbaca secara visual,
- Kata yang ditulis tidak bersesuaian dengan kata target yang diminta oleh sistem *prompt*, atau
- Goresan menyentuh tepi batas kanvas secara ekstrem (*clipping*).

Hanya citra yang lolos verifikasi kendali mutu yang dimasukkan ke dalam korpus data final.

#### 3.2.4 Skema Pembagian Data Berbasis Partisipan (*Participant-Wise Split*)
Pembagian dataset (*data partitioning*) dilakukan menggunakan skema **pembagian berbasis partisipan (*participant-wise split*)**, bukan pengacakan sampel secara bebas (*random sample split*). Pada skema ini, seluruh sampel tulisan dari seorang responden tertentu hanya akan dialokasikan ke dalam salah satu subset: pelatihan (*training*), validasi (*validation*), atau pengujian (*testing*). 

Proporsi pembagian data dialokasikan sebesar **70% untuk data latih, 15% untuk data validasi, dan 15% untuk data uji**. Skema *participant-wise split* ini menjamin tidak terjadinya kebocoran informasi gaya tulisan (*data leakage*) antar-subset, sehingga metrik evaluasi benar-benar merefleksikan kapabilitas model dalam mengenali gaya tulisan dari responden baru yang belum pernah dilihat sebelumnya (*unseen writers*).

<br>

### 3.3 Pra-pemrosesan Citra Tulisan Tangan

Citra hasil ekspor kanvas digital mentah memiliki dimensi resolusi yang bervariasi dan memuat area kosong (*whitespace*) yang tidak informatif. Oleh karena itu, tahapan pra-pemrosesan citra dirancang secara terstruktur sebagaimana diilustrasikan pada Gambar 3.3.

<br>

<div align="center">

```
Citra Mentah Canvas (RGB)
          │
          ▼
┌────────────────────────────────────────┐
│ Konversi Grayscale & Inversi Piksel    │  (Latar belakang 0 [hitam], Goresan 255 [putih])
└────────────────────────────────────────┘
          │
          ▼
┌────────────────────────────────────────┐
│ Pemotongan Kotak Pembatas (Bounding    │  (Memangkas margin kosong di sekeliling goresan)
│ Box Crop)                              │
└────────────────────────────────────────┘
          │
          ▼
┌────────────────────────────────────────┐
│ Penyesuaian Ukuran Menjaga Rasio Aspek │  (Tinggi dinormalkan ke 64/128 px, Lebar dipad)
│ (Aspect-Ratio Preserving Resize)       │
└────────────────────────────────────────┘
          │
          ▼
┌────────────────────────────────────────┐
│ Normalisasi Nilai Piksel [0, 1]        │  (Penskalaan nilai piksel untuk stabilitas gradien)
└────────────────────────────────────────┘
          │
          ▼
Citra Siap Masuk ke Jaringan CNN
```

**Gambar 3.3 Tahapan Pra-pemrosesan Citra Masukan Tulisan Tangan Bersambung**

</div>

<br>

Rincian teknis dari setiap tahapan pra-pemrosesan adalah sebagai berikut:
1. **Konversi Grayscale dan Inversi Warna:** Citra masukan RGB diubah menjadi citra aras keabuan satu kanal (*grayscale*). Selanjutnya, nilai piksel diinversikan sehingga piksel latar belakang bernilai 0 (hitam) dan piksel goresan tulisan bernilai tinggi mendekati 255 (putih), sesuai kaidah representasi komputasi konvolusi (Alwagdani & Jaha, 2023).
2. **Pemotongan Kotak Pembatas (*Bounding Box Crop*):** Sistem mendeteksi koordinat piksel aktif terluar $(x_{\min}, y_{\min}, x_{\max}, y_{\max})$ untuk memangkas margin kosong berlebih di sekeliling tulisan, sehingga representasi visual terfokus penuh pada morfologi karakter.
3. **Penyesuaian Ukuran Proporsional (*Aspect-Ratio Preserving Resize*):** Mengubah ukuran citra secara langsung tanpa menjaga rasio aspek dapat mendistorsi proporsi bentuk huruf Arab. Oleh sebab itu, tinggi citra dinormalkan secara tetap ke dimensi $H = 64$ piksel (atau $128$ piksel), sedangkan lebar citra disesuaikan secara proporsional. Sisa ruang kosong pada lebar maksimum diisi dengan nilai bantalan nol (*zero-padding*).
4. **Normalisasi Piksel:** Nilai intensitas piksel $[0, 255]$ diskalakan ke dalam rentang numerik $[0.0, 1.0]$ untuk mempercepat konvergensi optimasi gradien.
5. **Augmentasi Citra Daring (*Online Data Augmentation*):** Pada tahap pelatihan, citra diperkaya secara dinamis menggunakan augmentasi morfologis meliputi rotasi acak kecil ($\pm 5^\circ$ hingga $\pm 10^\circ$), pergeseran translasi ($\pm 5\%$), penskalaan *zoom* ($0.95 - 1.05$), dan distorsi peregangan (*shear*) guna mereplikasi variabilitas alami penulisan tangan (Balaha dkk., 2021).

<br>

### 3.4 Perancangan Arsitektur Model CNN-LSTM MobileNetV4

Arsitektur model yang diusulkan menggabungkan modul pengekstraksi ciri spasial berbasis CNN dan modul pemodel urutan temporal berbasis LSTM secara *end-to-end*. Diagram arsitektur lengkap disajikan pada Gambar 3.4.

<br>

<div align="center">

```
Citra Masukan Canvas (H=64, W=256, C=3)
                 │
                 ▼
┌────────────────────────────────────────────────────────┐
│             BACKBONE KONVOLUSI: MobileNetV4            │
│ (Universal Inverted Bottleneck / UIB Blocks)           │
│ *Bobot Awal Pra-Pelatihan ImageNet (Transfer Learning)*│
└────────────────────────────────────────────────────────┘
                 │  Peta Fitur Visual: (H'=1, W'=16, D=512)
                 ▼
┌────────────────────────────────────────────────────────┐
│            LAPISAN MAP-TO-SEQUENCE & DENSE             │
│ (Meratakan Fitur Spasial Menjadi Barisan Kolom W'=16)  │
└────────────────────────────────────────────────────────┘
                 │  Vektor Sekuensial: (Batch, W'=16, 256)
                 ▼
┌────────────────────────────────────────────────────────┐
│           LAPISAN PEMODEL URUTAN: BiLSTM               │
│ (2 Lapisan Bidirectional LSTM, 256 Unit Tersembunyi)   │
│ *Membaca Konteks Urutan Temporal Karakter Kanan->Kiri* │
└────────────────────────────────────────────────────────┘
                 │  Keadaan Tersembunyi: (Batch, W'=16, 512)
                 ▼
┌────────────────────────────────────────────────────────┐
│            LAPISAN PROYEKSI & OUTPUT DEKODER           │
│ (Dense Layer Proyeksi ke Jumlah Karakter Hijaiyah + 1) │
│ *Fungsi Kerugian CTC Loss / Sequence Cross-Entropy*    │
└────────────────────────────────────────────────────────┘
                 │
                 ▼
Prediksi Urutan Karakter Teks: [Char_1, Char_2, Char_3]
```

**Gambar 3.4 Diagram Arsitektur Lengkap Model CNN-LSTM dengan *Backbone* MobileNetV4**

</div>

<br>

Spesifikasi detail konfigurasi lapisan pada model CNN-LSTM MobileNetV4 dirinci pada Tabel 3.1.

<br>

**Tabel 3.1 Rincian Konfigurasi Parameter Lapisan Arsitektur CNN-LSTM MobileNetV4**

| Blok Lapisan | Tipe Lapisan / Operasi | Dimensi Keluaran (*Shape*) | Parameter & Konfigurasi |
|:---|:---|:---|:---|
| **Input Layer** | Image Input | $(64, 256, 3)$ | Citra kanvas ternormalisasi |
| **CNN Backbone** | MobileNetV4 (UIB Blocks) | $(2, 8, 512)$ | Bobot *pre-trained*; stride terpadu |
| **Pooling Spasial** | Max/Average Pooling (2×1) | $(1, 8, 512)$ | Menghilangkan dimensi vertikal ($H'=1$) |
| **Reshape Layer** | Map-to-Sequence Permute | $(8, 512)$ | Mentransformasikan ke runtun temporal |
| **Linear Projection**| Fully Connected Dense + ReLU | $(8, 256)$ | Dropout rate = $0.3$ |
| **Sequence Layer 1**| Bidirectional LSTM (BiLSTM) | $(8, 512)$ | 256 unit per arah; return sequences = True |
| **Sequence Layer 2**| Bidirectional LSTM (BiLSTM) | $(8, 512)$ | 256 unit per arah; return sequences = True |
| **Dense Classifier**| Time-Distributed Dense | $(8, K+1)$ | $K$ karakter Hijaiyah Iqro 3 + simbol kosong (*blank*) |
| **Loss Function** | CTC Loss / Sequence NLL | Skalar | Menghitung probabilitas penyejajaran sekuens |

<br>

Mekanisme decoding urutan karakter memanfaatkan algoritma *Connectionist Temporal Classification* (CTC) atau *Beam Search Decoder*. CTC memperkenalkan simbol penanda kosong (*blank token* $\epsilon$) untuk memungkinkan jaringan mengeluarkan prediksi karakter pada frame waktu tertentu dan menggabungkan karakter berulang yang dipisahkan oleh *blank*, sehingga mampu mengenali urutan huruf bersambung secara tepat tanpa memerlukan segmentasi posisi huruf secara manual (Mosbah dkk., 2024; Saini dkk., 2024).

<br>

### 3.5 Skenario Pelatihan dan Penalaan Hiperparameter

Pelatihan arsitektur hibrida CNN-LSTM dengan *transfer learning* dilakukan menggunakan protokol **pelatihan dua fase (*two-stage training protocol*)** untuk memastikan kestabilan konvergensi dan mencegah fenomena *catastrophic forgetting* (Masruroh dkk., 2023; Lamtougui dkk., 2024):

1. **Fase 1 — Pembekuan Bobot Dasar (*Feature Extraction / Warm-Up Phase*):**  
   Seluruh bobot parameter pada *backbone* konvolusi MobileNetV4 dibekukan (*frozen*). Pelatihan difokuskan secara eksklusif pada lapisan proyeksi, lapisan rekuren BiLSTM, dan lapisan klasifikasi luaran. Fase ini dijalankan selama **15 hingga 20 epoch** menggunakan pengoptimal **ADAM** dengan laju pembelajaran (*learning rate*) $\eta = 10^{-3}$, ukuran *batch* 32, dan fungsi pembatas gradien (*gradient clipping*) dengan nilai ambang 5.0.

2. **Fase 2 — Penalaan Halus Menyeluruh (*End-to-End Fine-Tuning Phase*):**  
   Kunci pembekuan pada beberapa blok konvolusi teratas (*top UIB blocks*) MobileNetV4 dibuka (*unfrozen*). Seluruh jaringan kemudian dilatih secara simultan secara *end-to-end* selama **40 hingga 60 epoch**. Pada fase ini, laju pembelajaran diturunkan secara signifikan menjadi $\eta = 10^{-4}$ (atau didukung mekanisme peluruhan *Cosine Annealing Schedule*) dengan *weight decay* $10^{-4}$ untuk mencegah rusaknya fitur visual awal. Pelatihan dipantau menggunakan mekanisme *early stopping* dengan batas kesabaran (*patience*) sebanyak 10 epoch berdasarkan metrik kerugian pada data validasi.

Lingkungan komputasi eksperimen direncanakan menggunakan bahasa pemrograman Python 3.10 dengan pustaka PyTorch / TensorFlow 2.x, OpenCV, Albumentations, dan Scikit-Learn pada lingkungan perangkat keras terakselerasi GPU (Google Colab / Workstation lokal).

<br>

### 3.6 Skenario Pengujian dan Kajian Ablasi (*Ablation Study*)

Untuk menguji hipotesis penelitian secara ilmiah dan membuktikan kontribusi masing-masing komponen yang diusulkan, serangkaian eksperimen terstruktur dan kajian ablasi (*ablation study*) dirancang sebagaimana dirinci pada Tabel 3.2.

<br>

**Tabel 3.2 Rencana Matriks Skenario Eksperimen dan Kajian Ablasi (*Ablation Study*)**

| Kode Skenario | Deskripsi Skenario Eksperimen | Backbone CNN | Komponen Sekuensial | Strategi Bobot / Training | Tujuan Pengujian & Justifikasi |
|:---|:---|:---|:---|:---|:---|
| **M-01 (Baseline 1)** | Model CNN Mandiri Klasik | CNN Kustom Sederhana | Tanpa LSTM (Dense Head) | *From Scratch* | Mengukur batas performa model CNN dasar tanpa komponen sekuensial (analog Rahmatulloh 2022). |
| **M-02 (Baseline 2)** | CNN-LSTM Tanpa Transfer Learning | MobileNetV4 | 2-Layer BiLSTM | *From Scratch* (Bobot Acak) | Mengukur dampak langsung dari penambahan lapisan LSTM tanpa bantuan bobot *pre-trained*. |
| **M-03 (Ablasi TL)** | CNN-LSTM + TL ImageNet (Frozen) | MobileNetV4 | 2-Layer BiLSTM | *Transfer Learning* (Hanya Fase 1 / Freeze) | Mengukur efektivitas representasi visual ImageNet tanpa penalaan halus domain tulisan tangan. |
| **M-04 (Proposed)** | **CNN-LSTM + TL MobileNetV4 (Fine-Tuning)** | **MobileNetV4** | **2-Layer BiLSTM** | **Two-Stage Fine-Tuning (Fase 1 + Fase 2)** | **Model Utama yang Diusulkan:** Mengukur performa puncak arsitektur usulan secara penuh. |
| **M-05 (Ablasi Data)**| Model M-04 Tanpa Augmentasi Citra | MobileNetV4 | 2-Layer BiLSTM | Two-Stage (Tanpa Augmentasi Morfologis) | Membuktikan seberapa besar kontribusi teknik augmentasi dalam mencegah *overfitting* data kecil. |

<br>

Evaluasi performa pada seluruh skenario diuji menggunakan data uji independen (*test set*) yang belum pernah dilihat sebelumnya, dengan mengukur:
1. *Exact Sequence Match Accuracy* (Akurasi kata utuh 100%),
2. *Character Accuracy* (Akurasi per posisi huruf),
3. *Character Error Rate* (CER), serta
4. Analisis matriks kekeliruan (*confusion matrix*) untuk mengidentifikasi kelompok karakter Hijaiyah yang paling sering mengalami misklasifikasi akibat keserupaan bentuk dasar atau pergeseran posisi titik diakritik.

<br>

### 3.7 Jadwal dan Rencana Pelaksanaan Penelitian

Penelitian skripsi ini direncanakan berlangsung selama satu semester akademik (kurun waktu 6 bulan). Matriks jadwal pelaksanaan kegiatan disajikan pada Tabel 3.3.

<br>

**Tabel 3.3 Matriks Jadwal Rencana Pelaksanaan Kegiatan Penelitian Skripsi**

| No | Rincian Kegiatan Penelitian | Bulan 1 | Bulan 2 | Bulan 3 | Bulan 4 | Bulan 5 | Bulan 6 |
|:---|:---|:---:|:---:|:---:|:---:|:---:|:---:|
| 1. | Studi pustaka komprehensif dan penyusunan proposal skripsi | [ X ] | | | | | |
| 2. | Seminar proposal skripsi dan revisi proposal | [ X ] | [ X ] | | | | |
| 3. | Inventarisasi kosakata Iqro 3 dan pengembangan antarmuka *canvas* | | [ X ] | | | | |
| 4. | Pengumpulan dataset tulisan tangan dan verifikasi kendali mutu (QC) | | [ X ] | [ X ] | | | |
| 5. | Pengembangan modul pra-pemrosesan citra dan pemipaan data (*pipeline*) | | | [ X ] | | | |
| 6. | Implementasi arsitektur CNN-LSTM MobileNetV4 dan pelatihan model | | | [ X ] | [ X ] | | |
| 7. | Pelaksanaan eksperimen kajian ablasi (*ablation study*) dan penalaan parameter | | | | [ X ] | [ X ] | |
| 8. | Evaluasi performa pengenalan, penghitungan CER, dan analisis hasil | | | | | [ X ] | |
| 9. | Penyusunan draf naskah laporan skripsi lengkap (Bab 1 s.d. Bab 5) | | | | | [ X ] | [ X ] |
| 10.| Sidang ujian skripsi dan revisi naskah akhir tugas akhir | | | | | | [ X ] |

<div style="page-break-after: always;"></div>

---

<!-- DAFTAR PUSTAKA (Format Harvard Sesuai Pedoman UISI) -->

# DAFTAR PUSTAKA

<br>

> **Catatan Format Penulisan Daftar Pustaka (Pedoman UISI Sub-Bab 3.2 no. 6):**
> Referensi disusun urut menurut abjad nama keluarga/belakang penulis pertama dan tahun penerbitan. Semua penulis dicantumkan lengkap. Judul artikel diapit tanda kutip biasa dengan *title case*, sedangkan nama jurnal/prosiding/buku dicetak miring (*italic*). Spasi 1 dengan baris kedua menjorok ke dalam 1 cm (*hanging indent*).

<br>

Ahmed, R., Gogate, M., Tahir, A., Dashtipour, K., Al-tamimi, B., Hawalah, A., El-Affendi, M. A., dan Hussain, A. (2021), “Novel Deep Convolutional Neural Network-Based Contextual Recognition of Arabic Handwritten Scripts”, *Entropy*, Vol. 23, No. 3, hal. 340.

Albattah, W. dan Albahli, S. (2022), “Intelligent Arabic Handwriting Recognition Using Different Standalone and Hybrid CNN Architectures”, *Applied Sciences*, Vol. 12, No. 19, hal. 10155.

Altwaijry, N. dan Al-Turaiki, I. (2021), “Arabic Handwriting Recognition System Using Convolutional Neural Network”, *Neural Computing and Applications*, Vol. 33, No. 7, hal. 2249–2261.

Alwagdani, M. S. dan Jaha, E. S. (2023), “Deep Learning-Based Child Handwritten Arabic Character Recognition and Handwriting Discrimination”, *Sensors*, Vol. 23, No. 15, hal. 6774.

Balaha, H. M., Ali, H. A., Saraya, M., dan Badawy, M. (2021), “A New Arabic Handwritten Character Recognition Deep Learning System (AHCR-DLS)”, *Neural Computing and Applications*, Vol. 33, No. 11, hal. 6325–6367.

Chen, Z.-M., Wei, X.-S., Wang, P., dan Guo, Y. (2019), “Multi-Label Image Recognition with Graph Convolutional Networks”, *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, Long Beach, hal. 5177–5186.

Durayhim, A. B., Al-Ajlan, A., Al-Turaiki, I., dan Altwaijry, N. (2023), “Towards Accurate Children’s Arabic Handwriting Recognition via Deep Learning”, *Applied Sciences*, Vol. 13, No. 3, hal. 1692.

El Khayati, M., Maafiri, A., Himeur, Y., Alkhazaleh, H. A., Atalla, S., dan Mansoor, W. (2025), “Leveraging Transfer Learning and Mobile-Enabled Convolutional Neural Networks for Improved Arabic Handwritten Character Recognition”, *arXiv preprint arXiv:2509.05019*, hal. 1–15.

Graves, A., Fernández, S., Gomez, F., dan Schmidhuber, J. (2006), “Connectionist Temporal Classification: Labelling Unsegmented Sequence Data with Recurrent Neural Networks”, *Proceedings of the 23rd International Conference on Machine Learning (ICML)*, Pittsburgh, hal. 369–376.

Lamtougui, H., El Moubtahij, H., Fouadi, H., dan Satori, K. (2024), “Improving Arabic Handwritten Text Recognition through Transfer Learning with Convolutional Neural Network-Based Models”, *Bulletin of Electrical Engineering and Informatics*, Vol. 13, No. 6, hal. 4294–4305.

Masruroh, S. U., Syahid, M. F., Munthaha, F., Muharram, A. T., dan Putri, R. A. (2023), “Deep Convolutional Neural Networks Transfer Learning Comparison on Arabic Handwriting Recognition System”, *International Journal on Informatics Visualization*, Vol. 7, No. 2, hal. 330–337.

Mosbah, L., Moalla, I., Hamdani, T. M., Neji, B., Beyrouthy, T., dan Alimi, A. M. (2024), “ADOCRNet: A Deep Learning OCR for Arabic Documents Recognition”, *IEEE Access*, Vol. 12, hal. 55620–55629.

Peng, G. (2024), “Segmentation-Free Recognition Algorithm Based on Deep Learning for Handwritten Text Image”, *Journal of Artificial Intelligence and Technology*, Vol. 4, No. 2, hal. 169–178.

Rahmatulloh, A., Rizal, R., Gunawan, R. I., Darmawan, I., dan Rahmat, B. Z. (2022), “Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning”, *Proceedings of 2022 International Conference Advancement in Data Science, E-learning and Information Systems (ICADEIS)*, Bandung, hal. 1–6.

Saini, M. L., Sati, D. C., Telikicharla, R. S., dan Mahadev. (2024), “Handwritten English Script Recognition System Using CNN and LSTM”, *Proceedings of 2024 IEEE International Conference on Contemporary Computing and Communications (InC4)*, Bangalore, hal. 1–6.

Shi, B., Bai, X., dan Yao, C. (2016), “An End-to-End Trainable Neural Network for Image-Based Sequence Recognition and Its Application to Scene Text Recognition”, *IEEE Transactions on Pattern Analysis and Machine Intelligence*, Vol. 39, No. 11, hal. 2298–2304.

Tarekegn, A. N., Ullah, M., dan Cheikh, F. A. (2024), “Deep Learning for Multi-Label Learning: A Comprehensive Survey”, *arXiv preprint arXiv:2401.16549*, hal. 1–28.

<div style="page-break-after: always;"></div>

---

<!-- LAMPIRAN-LAMPIRAN -->

# LAMPIRAN

<br>

### Lampiran A: Rincian Distribusi Kosakata Kata Sambung Buku Iqro 3

<br>

| No | Kata Target (Arab) | Transkripsi Latin | Panjang Karakter | Kombinasi Posisi Glif Huruf |
|:---:|:---:|:---:|:---:|:---:|
| 1. | بَتَ | Ba - Ta | 2 Huruf | Initial (بـ) + Final (ـت) |
| 2. | تَبَ | Ta - Ba | 2 Huruf | Initial (تـ) + Final (ـب) |
| 3. | نَثَ | Na - Tsa | 2 Huruf | Initial (نـ) + Final (ـث) |
| 4. | بَيَ | Ba - Ya | 2 Huruf | Initial (بـ) + Final (ـي) |
| 5. | سَجَدَ | Sa - Ja - Da | 3 Huruf | Initial (سـ) + Medial (ـجـ) + Final (ـد) |
| 6. | نَظَرَ | Na - Zho - Ra | 3 Huruf | Initial (نـ) + Medial (ـظـ) + Final (ـر) |
| 7. | خَلَقَ | Kha - La - Qa | 3 Huruf | Initial (خـ) + Medial (ـلـ) + Final (ـق) |
| 8. | فَعَلَ | Fa - 'A - La | 3 Huruf | Initial (فـ) + Medial (ـعـ) + Final (ـل) |
| 9. | كَتَبَ | Ka - Ta - Ba | 3 Huruf | Initial (كـ) + Medial (ـتـ) + Final (ـب) |
| 10.| صَدَقَ | Sha - Da - Qa | 3 Huruf | Initial (صـ) + Medial (ـد) + Isolated (ق) *(non-connecting)* |
| 11.| جَعَلَ | Ja - 'A - La | 3 Huruf | Initial (جـ) + Medial (ـعـ) + Final (ـل) |
| 12.| حَسَدَ | Ha - Sa - Da | 3 Huruf | Initial (حـ) + Medial (ـسـ) + Final (ـد) |
| ...| *(dst.)* | *(Mencakup seluruh kata sambung pada halaman 1–30 buku Iqro 3)* | 2–3 Huruf | Terinventarisasi dalam Manifest Data |

<br>

---

<br>

### Lampiran B: Desain Antarmuka *Canvas Digital* dan Format Lembar Pengambilan Data

<br>

<div align="center">

```
┌────────────────────────────────────────────────────────────────────────┐
│  APLIKASI PENGAMBILAN DATASET KANVAS HIJAIYAH SAMBUNG (IQRO 3)        │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│   Kata Target:       ب  ـتـ  ـب   ( كَتَبَ )       [ Dengarkan Audio ] │
│   ID Responden:      R-014                         Sesi: 2 dari 30    │
│                                                                        │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                                                                  │  │
│  │   - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -    │  │
│  │                                                                  │  │
│  │   · · · · كَـ · · · · · · · ـتَـ · · · · · · · ـبَ · · · · · ·   │  │
│  │   (Garis Panduan Titik-Titik / Tracing Dots untuk Responden)     │  │
│  │                                                                  │  │
│  │   - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -    │  │
│  │   ════════════════════════════════════════════════════════════   │  │
│  │   (Garis Dasar Penulisan / Baseline)                             │  │
│  │                                                                  │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│                                                                        │
│   [  HAPUS GORESAN (RESET)  ]              [  SIMPAN & LANJUT (NEXT) ] │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

**Gambar B.1 Rancangan Antarmuka Pengambilan Citra Tulisan Tangan pada Layar Sentuh**

</div>

<div style="page-break-after: always;"></div>

---

<!-- BIODATA PENULIS (Format Resmi UISI) -->

# BIODATA PENULIS

<br>

<div align="center">

*(Pasfoto Resmi Mahasiswa Ukuran 3×4)*

</div>

<br>

Penulis memiliki nama lengkap **Muchamad Budi Fabiantoro**, dilahirkan di Gresik pada tanggal ............................... Penulis merupakan anak ke-...... dari pasangan Bapak ............................... dan Ibu ................................ Penulis telah menempuh pendidikan formal sebagai berikut:
1. **Pendidikan Dasar:** SD .............................................................. (Lulus tahun ......)
2. **Pendidikan Menengah Pertama:** SMP .............................................................. (Lulus tahun ......)
3. **Pendidikan Menengah Atas:** SMA/SMK .............................................................. (Lulus tahun ......)
4. **Pendidikan Tinggi:** Pada tahun 2022, penulis resmi terdaftar sebagai mahasiswa Program Studi S-1 Informatika, Departemen Informatika, Fakultas Teknologi dan Industri (FTI), Universitas Internasional Semen Indonesia (UISI) dengan Nomor Induk Mahasiswa (NIM) 22314050111003.

Selama menempuh studi di Program Studi S-1 Informatika UISI, penulis aktif dalam kegiatan akademik dan memfokuskan peminatan keilmuan pada bidang Kecerdasan Buatan (*Artificial Intelligence*), Pembelajaran Mesin (*Machine Learning*), *Deep Learning*, dan Visi Komputer (*Computer Vision*). Proposal skripsi yang berjudul **"Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning"** ini disusun sebagai salah satu syarat akademis dalam menyelesaikan studi program Sarjana (S-1) untuk memperoleh gelar Sarjana Komputer (S.Kom.) / Sarjana Teknik (S.T.) di Universitas Internasional Semen Indonesia.

<br><br>

<div align="right">
Gresik, &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Oktober 2026<br><br><br><br>
<b>Muchamad Budi Fabiantoro</b><br>
NIM. 22314050111003
</div>
