# PROPOSAL SKRIPSI

## KLASIFIKASI MULTI-LABEL UNTUK PENGENALAN HURUF HIJAIYAH SAMBUNG MENGGUNAKAN TRANSFER LEARNING

**Identitas Peneliti:**  
- **Nama Mahasiswa:** Muchamad Budi Fabiantoro  
- **NIM:** 22314050111003  
- **Program Studi:** S-1 Informatika  
- **Departemen:** Informatika  
- **Fakultas:** Fakultas Teknologi dan Industri (FTI)  
- **Institusi:** Universitas Internasional Semen Indonesia (UISI)  
- **Dosen Pembimbing:** Moch. Zain Hasan, S.Kom., M.Kom. (Pak Zain)  
- **Tahun Akademik:** 2026/2027  

*(Catatan Judul: Judul diselaraskan dengan arahan resmi Dosen Pembimbing. Secara teknis komputasi, implementasi menerapkan formulasi pengenalan sekuensial nirsegmentasi / sequence recognition berbasis Convolutional Recurrent Neural Network dengan arsitektur CNN-LSTM dan transfer learning backbone MobileNetV3).*

---

# BAB 1 PENDAHULUAN

## 1.1 Latar Belakang

Di era transformasi digital dan perkembangan kecerdasan buatan (*Artificial Intelligence*) saat ini, teknologi informasi berkembang sangat pesat menjadi instrumen pembantu (*assisting technology*) yang mempermudah berbagai aktivitas manusia, termasuk dalam bidang pendidikan keagamaan. Integrasi teknologi cerdas kini diarahkan untuk menghadirkan media pembelajaran yang adaptif, interaktif, dan dapat diakses secara mandiri oleh peserta didik kapan pun dan di mana pun. Di Indonesia, pembelajaran membaca dan menulis aksara Al-Qur'an pada tingkat dasar umumnya diselenggarakan menggunakan metode Iqro. Pada tahap awal (buku Iqro 1 dan Iqro 2), peserta didik mempelajari huruf-huruf Hijaiyah dalam bentuk tunggal yang terisolasi (*isolated characters*). Ketika melangkah ke buku **Iqro 3**, peserta didik mulai diperkenalkan pada kata-kata pendek yang tersusun atas dua hingga tiga huruf Hijaiyah yang ditulis secara bersambung. Penguasaan penulisan huruf Hijaiyah bersambung memegang peranan yang sangat fundamental karena seluruh teks Al-Qur'an dan literatur berbahasa Arab disajikan dalam bentuk rangkaian huruf kursif bersambung.

Meskipun memegang peranan krusial, proses evaluasi kemampuan menulis huruf Hijaiyah sejauh ini masih sangat bergantung pada koreksi visual manual oleh guru atau ustaz secara tatap muka langsung di kelas. Sebagaimana digarisbawahi oleh Rahmatulloh dkk. (2022), proses pembelajaran huruf Hijaiyah konvensional menuntut kehadiran pembimbing khusus secara langsung untuk memverifikasi kebenaran setiap goresan huruf. Ketergantungan mutlak pada evaluasi manual ini menimbulkan kendala nyata, terutama ketika kegiatan pembelajaran berlangsung secara jarak jauh (*remote learning*), membatasi frekuensi latihan mandiri peserta didik di luar jam pertemuan kelas, serta menghadirkan keterbatasan objektivitas dan konsistensi penilaian pada skala kelas yang berukuran besar. Mengingat laju perkembangan zaman yang serba cepat dan menuntut solusi praktis, Rahmatulloh dkk. (2022) menegaskan urgensi kehadiran teknologi cerdas berupa sistem pengenalan tulisan tangan (*Optical Character Recognition* / OCR) luring berbasis *deep learning* yang mampu mengidentifikasi tulisan dan memandu proses pembelajaran secara otomatis dengan memberikan umpan balik koreksi seketika (*instant warning and feedback*) apabila terjadi kesalahan penulisan.

Peluang penerapan teknologi pembantu evaluasi mandiri ini semakin terbuka luas seiring meluasnya adopsi perangkat layar sentuh (*touchscreen*) seperti tablet dan ponsel pintar yang dilengkapi fasilitas media *canvas digital* interaktif. Melalui media tersebut, peserta didik dapat berlatih menuliskan aksara Hijaiyah langsung di atas layar gawai dengan panduan garis titik-titik (*tracing dots*), di mana hasil goresan tersebut dapat diekspor menjadi berkas citra digital 2 dimensi (2D). Pemanfaatan perangkat layar sentuh untuk latihan menulis karakter Arab telah terbukti diterima secara antusias dan efektif diterapkan pada anak-anak usia sekolah dasar maupun kalangan pendidik, sebagaimana ditunjukkan pada evaluasi aplikasi tablet *Mutqin* oleh Durayhim dkk. (2023). Citra hasil goresan pada *canvas digital* tersebut memiliki potensi yang sangat besar untuk dijadikan masukan (*input*) bagi sistem kecerdasan buatan guna menyediakan evaluasi otomatis yang cepat, konsisten, dan terukur.

Sebagai upaya mewujudkan sistem pengenalan tulisan tangan otomatis, penelitian acuan utama oleh Rahmatulloh dkk. (2022) yang berjudul *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"* telah membuktikan efektivitas pendekatan *Deep Learning*, khususnya arsitektur *Convolutional Neural Network* (CNN) yang dioptimalkan dengan algoritma ADAM, dalam mengenali dan mengklasifikasikan tulisan tangan huruf Hijaiyah. Penelitian tersebut sukses mencatatkan tingkat akurasi klasifikasi yang tinggi, yakni sebesar 91,24% pada dataset tulisan tangan anak-anak usia 7–12 tahun (Hijja2) dan 98,42% pada dataset tulisan dewasa (AHCD). Di akhir penelitiannya, Rahmatulloh dkk. (2022) memberikan arahan dan rekomendasi penting bagi penelitian selanjutnya (*future work*), yaitu mengembangkan dan mengimplementasikan model pengenalan tulisan tangan Hijaiyah tersebut ke dalam aplikasi berbasis perangkat bergerak (*mobile*) agar dapat digunakan secara praktis untuk membantu proses pembelajaran secara interaktif.

Kendati demikian, model yang dibangun oleh Rahmatulloh dkk. (2022)—serta sebagian besar penelitian pengenalan aksara Arab di Indonesia (Masruroh dkk., 2023)—masih terbatas pada pengenalan huruf tunggal yang berdiri sendiri (*isolated characters*). Di sisi lain, pada jenjang pembelajaran nyata kurikulum Iqro 3, peserta didik diwajibkan menuliskan rangkaian huruf yang saling bersambung membentuk kata. Pengenalan tulisan tangan huruf Hijaiyah bersambung menghadirkan tantangan komputasi yang jauh lebih rumit dibandingkan pengenalan huruf tunggal. Pertama, morfologi huruf Arab bersifat dinamis dan fleksibel; setiap karakter dapat berubah menjadi hingga empat bentuk glif visual yang berbeda bergantung pada posisinya di dalam kata, yaitu pada posisi awal (*initial*), tengah (*medial*), akhir (*final*), atau berdiri sendiri (*isolated*) (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023). Kedua, sebagaimana diidentifikasi oleh Rahmatulloh dkk. (2022), banyak huruf Hijaiyah berbagi kerangka dasar yang identik dan hanya dibedakan oleh jumlah serta letak titik diakritik (misalnya kelompok ب، ت، ث dan ج، ح، خ), di mana pada penulisan bersambung titik-titik ini rentan terdistorsi, bergeser, atau bertumpang tindih dengan goresan huruf di sekitarnya, padahal keberadaan titik sangat krusial karena dapat mengubah total identitas huruf dan makna kata (Albattah & Albahli, 2022). Ketiga, penulisan huruf yang saling bertaut membentuk sambungan alami (*ligature*) tanpa batas pemisah yang jelas. Karakteristik ligatur ini menyebabkan pendekatan konvensional berbasis segmentasi karakter (*segmentation-based*) kerap mengalami kegagalan fatal akibat pemotongan berlebih (*over-segmentation*) atau kesalahan potong pada persilangan garis ligatur, di mana galat segmentasi tersebut merambat langsung menjadi kesalahan fatal dalam pengenalan karakter (*cascading error*) (Peng, 2024; Mosbah dkk., 2024). Kompleksitas ini semakin tinggi pada tulisan tangan anak-anak atau pemula yang memiliki variabilitas goresan tinggi, ketidakstabilan tekanan garis, dan deformasi proporsi bentuk yang signifikan, terbukti dari akurasi pengenalan dataset anak yang secara empiris konsisten lebih rendah (82,5%–91%) dibandingkan dataset tulisan orang dewasa (97%–98%) (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023; Alwagdani & Jaha, 2023; Masruroh dkk., 2023).

Guna mengatasi kelemahan mendasar dari segmentasi fisik tersebut, paradigma pengenalan sekuensial nirsegmentasi (*segmentation-free sequence recognition*) menjadi solusi yang paling mutakhir dan menjanjikan. Pendekatan ini memperlakukan citra kata sebagai barisan representasi visual utuh yang dipetakan secara langsung menjadi urutan teks (*sequence of characters*). Integrasi arsitektur hibrida antara *Convolutional Neural Network* (CNN) dan *Long Short-Term Memory* (LSTM) terbukti sangat tangguh dalam mengenali barisan teks tulisan tangan bersambung (Saini dkk., 2024; Peng, 2024). Pada skema hibrida ini, lapisan CNN bertindak mengekstraksi representasi peta ciri visual spasial dari citra masukan, sedangkan lapisan rekuren LSTM membaca dependensi kontekstual urutan karakter secara temporal dari arah kanan ke kiri sesuai arah alami penulisan aksara Arab, sehingga mampu menyelesaikan persoalan ligatur yang rumit tanpa memerlukan pemotongan karakter secara fisik (Mosbah dkk., 2024).

Selain tantangan morfologi sambung, kendala teknis penting dalam merealisasikan rekomendasi Rahmatulloh dkk. (2022) menuju aplikasi interaktif adalah keterbatasan jumlah data latih citra *canvas digital* mandiri dan tuntutan efisiensi komputasi pada perangkat bergerak. Melatih jaringan konvolusi dalam (*deep CNN*) dari awal (*from scratch*) dengan data berskala terbatas sangat rentan menimbulkan *overfitting* serta memperlambat konvergensi model. Dalam konteks ini, penerapan *transfer learning* menjadi strategi krusial untuk memanfaatkan bobot yang telah dipelajari oleh model terlatih sebelumnya sebagai pengekstraksi ciri visual yang kaya dan tergeneralisasi (Lamtougui dkk., 2024; Masruroh dkk., 2023). Sejalan dengan tren teknologi masa kini yang menekankan komputasi cerdas pada perangkat berdaya rendah (*mobile and edge computing*), pemilihan arsitektur *backbone* modern yang sangat efisien seperti **MobileNetV3** (*Large*) menawarkan keunggulan latensi sangat rendah, bobot parameter yang ringkas (sekitar 5,4 juta parameter), dan akurasi tinggi berkat pemanfaatan blok *inverted residual* dengan modul *Squeeze-and-Excitation* (SE) serta aktivasi *hard-swish* (Howard dkk., 2019; El Khayati dkk., 2025). Karakteristik ini sangat ideal untuk mendukung inferensi cepat secara luring pada perangkat pembelajaran berbasis *canvas digital*.

Kajian literatur menunjukkan bahwa penelitian yang mengkaji tulisan tangan Arab bersambung sejauh ini umumnya masih berfokus pada naskah dokumen pindaian kertas statis tulisan orang dewasa seperti dataset IFN/ENIT dengan pendekatan klasifikasi kata utuh (*whole-word classification*) (Lamtougui dkk., 2024; Ahmed dkk., 2021). Berdasarkan telaah terhadap penelitian terdahulu, terdapat tiga kesenjangan penelitian (*research gap*) utama yang belum terjawab:
1. **Kesenjangan media masukan dan kurikulum:** Belum ada penelitian yang membangun dan mengevaluasi model pada citra hasil ekspor *canvas digital* interaktif yang secara terstruktur dirancang berdasarkan kosakata kurikulum pembelajaran Al-Qur'an tingkat dasar (**Iqro 3**).
2. **Kesenjangan dekomposisi sekuensial:** Penelitian tulisan tangan Arab bersambung sebelumnya (Lamtougui dkk., 2024; Ahmed dkk., 2021) memperlakukan kata sebagai satu label kelas utuh statis (*whole-word*), bukan memetakan citra menjadi urutan label karakter individual $[H_1, H_2, H_3]$ secara sekuensial nirsegmentasi sehingga model dapat mengenali kombinasi huruf baru secara fleksibel.
3. **Kesenjangan integrasi metode:** Penelitian yang memanfaatkan *transfer learning* (Masruroh dkk., 2023; Durayhim dkk., 2023; Lamtougui dkk., 2024) terbatas pada CNN murni tanpa pemodel urutan LSTM, sedangkan penelitian CNN-LSTM (Saini dkk., 2024; Ge Peng, 2024) hanya menguji aksara Latin atau pindaian dokumen cetak. Belum ada penelitian yang menggabungkan *transfer learning* MobileNetV3 sebagai pengekstraksi ciri spasial ringan dengan LSTM dan dekoder CTC (*Connectionist Temporal Classification*) untuk pengenalan kata sambung pendek huruf Hijaiyah.

Berdasarkan latar belakang permasalahan, arah perkembangan teknologi pembantu (*assisting technology*), serta pijakan riset acuan Rahmatulloh dkk. (2022), penelitian skripsi ini mengusulkan pengembangan model pengenalan sekuensial berbasis arsitektur gabungan **CNN-LSTM dengan *transfer learning* MobileNetV3** untuk mengenali tulisan tangan huruf Hijaiyah bersambung pada materi Iqro 3. Model ini dirancang untuk memproses citra digital hasil ekspor *canvas digital* secara *segmentation-free* dan memprediksi urutan karakter dari kanan ke kiri secara tepat. Penelitian ini difokuskan pada perancangan dataset citra dan rekayasa model *machine learning*, dengan harapan dapat menghadirkan sistem kecerdasan buatan yang andal, akurat, dan efisien dalam mendukung evaluasi mandiri literasi Al-Qur'an tingkat dasar.

---

## 1.2 Rumusan Masalah

Berdasarkan latar belakang permasalahan yang telah diuraikan, rumusan masalah dalam penelitian proposal skripsi ini dirumuskan sebagai berikut:
1. Bagaimana merancang dan membangun dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang merepresentasikan seluruh kosakata kata sambung pada buku Iqro 3?
2. Bagaimana mengimplementasikan arsitektur CNN-LSTM dengan memanfaatkan *transfer learning* MobileNetV3 untuk mengenali urutan huruf Hijaiyah yang ditulis bersambung pada citra tanpa melalui tahapan segmentasi manual (*segmentation-free*)?
3. Bagaimana kinerja model CNN-LSTM dengan *transfer learning* MobileNetV3 dalam memprediksi urutan karakter huruf Hijaiyah bersambung berdasarkan metrik evaluasi pengenalan sekuensial (*exact sequence match accuracy*, akurasi per karakter, dan *Character Error Rate*)?

---

## 1.3 Tujuan Penelitian

Sesuai dengan rumusan masalah yang diajukan, tujuan yang ingin dicapai dalam pelaksanaan penelitian ini adalah:
1. Merancang dan membangun dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang terstruktur dan representatif mengacu pada daftar kosakata buku Iqro 3.
2. Mengembangkan dan mengimplementasikan model pengenalan tulisan tangan bersambung berbasis arsitektur gabungan CNN-LSTM dengan *transfer learning* MobileNetV3 yang mampu memetakan citra masukan secara langsung menjadi urutan karakter dari arah kanan ke kiri secara nirsegmentasi (*segmentation-free*).
3. Menguji, menganalisis, dan mengevaluasi performa model CNN-LSTM dengan *transfer learning* MobileNetV3 dalam mengenali urutan karakter huruf Hijaiyah bersambung menggunakan metrik *exact sequence match accuracy*, akurasi per karakter, dan *Character Error Rate* (CER).

---

## 1.4 Manfaat Penelitian

Hasil penelitian ini diharapkan dapat memberikan kontribusi nyata yang terbagi ke dalam manfaat teoretis, praktis, dan akademis sebagai berikut:

### 1.4.1 Manfaat Teoretis
1. **Pengembangan Teori Visi Komputer:** Memberikan kontribusi ilmiah dalam pengembangan metode pengenalan teks sekuensial nirsegmentasi (*segmentation-free sequence recognition*) berbasis hibrida CNN-LSTM dengan strategi *transfer learning* pada domain aksara kursif non-Latin.
2. **Pengayaan Literatur Morfologi Aksara:** Memperkaya khazanah penelitian pemrosesan citra digital terkait penanganan ligatur alami dan variasi morfologi posisional (*initial, medial, final*) pada kata-kata pendek (dua hingga tiga karakter) tanpa segmentasi fisik.

### 1.4.2 Manfaat Praktis
1. **Bagi Peserta Didik:** Menyediakan fondasi teknologi kecerdasan buatan sebagai asisten pembantu (*assisting technology*) yang mampu memberikan umpan balik evaluasi penulisan kata Hijaiyah secara mandiri, objektif, dan seketika di luar ruang kelas.
2. **Bagi Tenaga Pendidik (Guru/Ustaz):** Membantu proses asesmen kemampuan menulis huruf Hijaiyah secara konsisten serta meringankan beban pemeriksaan visual manual pada skala bimbingan kelas yang besar.
3. **Bagi Pengembang Aplikasi Pembelajaran:** Menyediakan model *deep learning* yang ringan, akurat, dan berdaya komputasi efisien (*MobileNetV3 backbone*) sehingga siap diintegrasikan ke dalam modul evaluasi aplikasi pembelajaran membaca dan menulis Al-Qur'an interaktif berbasis perangkat bergerak (*mobile/tablet*).

### 1.4.3 Manfaat Akademis
1. Menjadi rujukan ilmiah dan komparasi empiris bagi sivitas akademika serta peneliti lanjutan yang mengembangkan riset *Optical Character Recognition* (OCR) aksara Arab/Hijaiyah di Indonesia, khususnya sebagai jembatan pengembangan dari model huruf tunggal (*isolated*) menuju teks bersambung (*connected script*).

---

## 1.5 Batasan Penelitian

Agar ruang lingkup penelitian tetap terarah, terukur, dan dapat diselesaikan secara mendalam sesuai dengan sumber daya yang tersedia, batasan penelitian ditetapkan berdasarkan aspek-aspek berikut:

1. **Objek Penelitian:**  
   Objek penelitian dibatasi pada tulisan tangan huruf Hijaiyah bersambung yang diekspor dari media *canvas digital* ke dalam format berkas citra digital 2 dimensi (2D) dengan format PNG/JPEG (pengenalan tulisan tangan luring / *offline handwriting recognition*). Penelitian tidak menggunakan data runtun waktu koordinat goresan pena secara waktu-nyata (*stroke trajectory time-series*).

2. **Data Penelitian:**  
   - Sumber data diperoleh dari pengumpulan mandiri melalui media *canvas digital* interaktif dengan skema penulisan terpandu *prompt* (sistem menampilkan kata target, responden menuliskan kata tersebut pada canvas).
   - Penggunaan pola garis titik-titik panduan (*tracing dots*) pada area *canvas* diperbolehkan sebagai alat bantu penulisan responden.
   - Kosakata tulisan dibatasi secara ketat pada seluruh variasi kata sambung yang terdapat di dalam buku **Iqro 3**, dengan panjang kata berkisar antara dua hingga tiga huruf per citra.
   - Ruang karakter (*whitelist*) dibatasi pada 28 huruf Hijaiyah dasar (alif hingga ya); data tidak memproses tanda baca, harakat (*fathah, kasrah, dhammah*), transliterasi Latin, maupun karakter hamzah terpisah.
   - Pembagian data dilakukan dengan skema *participant-wise split* (pembagian berdasarkan identitas penulis), di mana seorang partisipan hanya dialokasikan ke dalam salah satu himpunan (data latih, validasi, atau uji) guna mencegah kebocoran informasi gaya penulisan (*data leakage*).

3. **Metode dan Pendekatan:**  
   - Model yang dikembangkan menerapkan pendekatan nirsegmentasi (*segmentation-free*) berbasis arsitektur gabungan CNN-LSTM.
   - Komponen CNN menggunakan arsitektur *lightweight* **MobileNetV3** (*Large*) dengan bobot pra-pelatihan (*pre-trained*) ImageNet melalui mekanisme *transfer learning* sebagai pengekstraksi ciri visual spasial.
   - Komponen rekuren menggunakan *Long Short-Term Memory* (LSTM) searah untuk memodelkan ketergantungan urutan karakter dari arah kanan ke kiri sesuai kaidah penulisan aksara Arab.
   - Fungsi dekoder menggunakan *Connectionist Temporal Classification* (CTC) atau klasifikasi multi-output terurut untuk memetakan representasi fitur menjadi label urutan huruf.

4. **Variabel dan Parameter:**  
   - Variabel masukan adalah citra greyscale dengan dimensi seragam $256 \times 64$ piksel hasil prapemrosesan.
   - Variabel keluaran adalah barisan label huruf Hijaiyah berpanjang 2 hingga 3 karakter.
   - Parameter pelatihan utama mencakup optimasi dengan algoritma ADAM, pengaturan tingkat pembelajaran (*learning rate*), ukuran *batch* (*batch size*), fungsi aktivasi non-linear, dan mekanisme regularisasi *dropout* untuk mencegah *overfitting*.

5. **Proses dan Tahapan Penelitian:**  
   Tahapan penelitian dibatasi pada: (a) studi literatur, (b) inventarisasi kosakata buku Iqro 3 dan akuisisi data tulisan pada *canvas*, (c) verifikasi kendali mutu data (*quality control* / QC), (d) prapemrosesan citra (konversi *grayscale*, pemotongan area goresan /*bounding crop*, penyesuaian ukuran dengan preservasi rasio aspek, dan normalisasi piksel), (e) pelatihan model melalui skema dua fase (*two-stage training*: pelatihan bobot pengekstraksi ciri CNN terlebih dahulu, dilanjutkan pelatihan end-to-end CNN-LSTM), dan (f) evaluasi kinerja pengenalan sekuensial.

6. **Metrik Evaluasi:**  
   Evaluasi performa model diukur menggunakan tiga metrik pengenalan teks sekuensial standar:
   - *Exact Sequence Match Accuracy*: Mengukur persentase prediksi seluruh urutan huruf dalam satu citra yang tepat secara sempurna (100% cocok dari karakter awal hingga akhir).
   - *Character Accuracy* / Akurasi per Posisi Karakter: Mengukur persentase ketepatan prediksi pada masing-masing slot karakter (posisi 1, posisi 2, dan posisi 3).
   - *Character Error Rate* (CER): Mengukur rasio kesalahan karakter berdasarkan operasi substitusi, delesi, dan insersi (*Levenshtein distance*) terhadap total karakter referensi.

7. **Aspek yang Tidak Dibahas:**  
   - Penelitian berfokus penuh pada perancangan dataset citra dan rekayasa performa model *machine learning*; pengembangan sistem gamifikasi dan integrasi aplikasi secara menyeluruh dikerjakan secara terpisah oleh peneliti kolaborator.
   - Penelitian tidak mengevaluasi aspek hukum bacaan tajwid, kebenaran panjang-pendek bacaan (*mad*), maupun kaidah estetika kaligrafi (*khat*).

---

## 1.6 Sistematika Penulisan Proposal

Sistematika penulisan proposal skripsi ini disusun dalam tiga bab utama sesuai dengan pedoman buku skripsi sebagai berikut:

- **BAB 1 PENDAHULUAN**  
  Bab ini memuat uraian latar belakang permasalahan yang menguraikan konteks teknologi pembantu di era modern, penelitian acuan Rahmatulloh dkk. (2022), urgensi pengenalan huruf Hijaiyah bersambung pada kurikulum Iqro 3, rumusan masalah, tujuan penelitian, manfaat penelitian teoretis, praktis, dan akademis, ruang lingkup batasan penelitian, serta sistematika penulisan.
- **BAB 2 KAJIAN PUSTAKA DAN LANDASAN TEORI**  
  Bab ini memuat kajian penelitian terdahulu yang relevan (*state of the art*), sintesis celah penelitian (*research gap*), serta landasan teori komprehensif mengenai karakteristik morfologi aksara Hijaiyah sambung, materi kurikulum Iqro 3, media *canvas digital*, jaringan konvolusi CNN, *transfer learning*, arsitektur MobileNetV3, jaringan rekuren LSTM, paradigma pengenalan nirsegmentasi (*segmentation-free*), formulasi urutan sekuensial, dan metrik evaluasi pengenalan teks.
- **BAB 3 METODOLOGI PENELITIAN**  
  Bab ini menguraikan tahapan pelaksanaan penelitian secara terstruktur, meliputi diagram alir penelitian, protokol inventarisasi kosakata dan akuisisi data tulisan tangan *canvas*, verifikasi kontrol kualitas data, skema pembagian data berbasis partisipan (*participant-wise split*), tahapan prapemrosesan citra, perancangan arsitektur model CNN-LSTM MobileNetV3, skenario pelatihan dua tahap (*two-stage training*), rencana eksperimen ablasi, serta matriks jadwal rencana pelaksanaan penelitian.

---

## DAFTAR PUSTAKA

Ahmed, R., Gogate, M., Tahir, A., Dashtipour, K., Al-tamimi, B., Hawalah, A., El-Affendi, M. A., & Hussain, A. (2021). Novel deep convolutional neural network-based contextual recognition of Arabic handwritten scripts. *Entropy*, *23*(3), 340. https://doi.org/10.3390/e23030340

Albattah, W., & Albahli, S. (2022). Intelligent Arabic handwriting recognition using different standalone and hybrid CNN architectures. *Applied Sciences*, *12*(19), 10155. https://doi.org/10.3390/app121910155

Altwaijry, N., & Al-Turaiki, I. (2021). Arabic handwriting recognition system using convolutional neural network. *Neural Computing and Applications*, *33*(7), 2249–2261. https://doi.org/10.1007/s00521-020-05070-8

Alwagdani, M. S., & Jaha, E. S. (2023). Deep learning-based child handwritten Arabic character recognition and handwriting discrimination. *Sensors*, *23*(15), 6774. https://doi.org/10.3390/s23156774

Durayhim, A. B., Al-Ajlan, A., Al-Turaiki, I., & Altwaijry, N. (2023). Towards accurate children’s Arabic handwriting recognition via deep learning. *Applied Sciences*, *13*(3), 1692. https://doi.org/10.3390/app13031692

El Khayati, M., Maafiri, A., Himeur, Y., Alkhazaleh, H. A., Atalla, S., & Mansoor, W. (2025). Leveraging transfer learning and mobile-enabled convolutional neural networks for improved Arabic handwritten character recognition. *arXiv preprint arXiv:2509.05019*. https://doi.org/10.48550/arXiv.2509.05019

Howard, A., Sandler, M., Chu, G., Chen, L.-C., Chen, B., Tan, M., Wang, W., Zhu, Y., Pang, R., Vasudevan, V., Le, Q. V., & Adam, H. (2019). Searching for MobileNetV3. Dalam *Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)* (hlm. 1314–1324). IEEE. https://doi.org/10.1109/ICCV.2019.00140

Lamtougui, H., El Moubtahij, H., Fouadi, H., & Satori, K. (2024). Improving Arabic handwritten text recognition through transfer learning with convolutional neural network-based models. *Bulletin of Electrical Engineering and Informatics*, *13*(6), 4294–4305. https://doi.org/10.11591/eei.v13i6.8178

Masruroh, S. U., Syahid, M. F., Munthaha, F., Muharram, A. T., & Putri, R. A. (2023). Deep convolutional neural networks transfer learning comparison on Arabic handwriting recognition system. *International Journal on Informatics Visualization*, *7*(2), 330–337.

Mosbah, L., Moalla, I., Hamdani, T. M., Neji, B., Beyrouthy, T., & Alimi, A. M. (2024). ADOCRNet: A deep learning OCR for Arabic documents recognition. *IEEE Access*, *12*, 55620–55629. https://doi.org/10.1109/ACCESS.2024.3379530

Peng, G. (2024). Segmentation-free recognition algorithm based on deep learning for handwritten text image. *Journal of Artificial Intelligence and Technology*, *4*(2), 169–178. https://doi.org/10.37965/jait.2024.0473

Rahmatulloh, A., Rizal, R., Gunawan, R. I., Darmawan, I., & Rahmat, B. Z. (2022). Optimization of Hijaiyah letter handwriting recognition model based on deep learning. Dalam *2022 International Conference Advancement in Data Science, E-learning and Information Systems (ICADEIS)* (hlm. 1–6). IEEE. https://doi.org/10.1109/ICADEIS56544.2022.10037496

Saini, M. L., Sati, D. C., Telikicharla, R. S., & Mahadev. (2024). Handwritten English script recognition system using CNN and LSTM. Dalam *2024 IEEE International Conference on Contemporary Computing and Communications (InC4)* (hlm. 1–6). IEEE. https://doi.org/10.1109/InC460750.2024.10649099
