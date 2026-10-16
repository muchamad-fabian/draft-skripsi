# PENYUSUNAN SKRIPSI: BAB I PENDAHULUAN

**Judul Penelitian:** Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning  
**Penulis:** Muchamad Budi Fabiantoro (NIM: 22314050111003)  
**Program Studi:** Informatika, Fakultas Teknologi dan Industri, Universitas Internasional Semen Indonesia (UISI)  
**Dosen Pembimbing:** Pak Zain  
**Tanggal Penyusunan:** Oktober 2026  

---

## A. Ringkasan Analisis Draf

1. **Topik dan Fokus Penelitian**  
   Penelitian ini berfokus pada pengenalan tulisan tangan huruf Hijaiyah bersambung (terdiri atas 2 hingga 3 karakter per citra) menggunakan pendekatan nirsegmentasi (*segmentation-free sequence recognition*) berbasis arsitektur gabungan *Convolutional Neural Network* dan *Long Short-Term Memory* (CNN-LSTM) dengan *Transfer Learning* (*backbone* MobileNetV4). Masukan sistem berupa citra digital tunggal hasil ekspor *canvas digital* interaktif dengan batas kosakata mengacu pada materi buku **Iqro 3**.

2. **Landasan Acuan dan Konteks Perkembangan Zaman**  
   Penelitian ini berpijak pada studi acuan utama oleh Rahmatulloh dkk. (2022) berjudul *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"*. Di era transformasi digital saat ini, teknologi kecerdasan buatan (*Artificial Intelligence*) memegang peranan krusial sebagai teknologi pembantu (*assisting technology*) yang memfasilitasi pembelajaran mandiri. Rahmatulloh dkk. (2022) menekankan perlunya sistem otomatis berbasis *Optical Character Recognition* (OCR) dan *Deep Learning* untuk mengenali tulisan tangan Hijaiyah serta mendampingi santri secara mandiri ketika bimbingan tatap muka oleh guru terbatas. Studi tersebut sukses mengoptimalkan CNN dengan pengoptimal ADAM pada dataset huruf tunggal (Hijja2 dan AHCD) serta merekomendasikan pengembangan model ke dalam aplikasi berbasis *mobile*. Penelitian skripsi ini mengambil tongkat estafet tersebut dengan memperluas domain pengenalan dari karakter tunggal (*isolated*) ke karakter bersambung (*connected characters*) pada kurikulum Iqro 3.

3. **Masalah Utama dan Celah Penelitian (Research Gap)**  
   - **Keterbatasan studi acuan pada huruf tunggal:** Penelitian terdahulu (seperti Rahmatulloh dkk., 2022) berfokus pada huruf Hijaiyah terisolasi (*isolated characters*), sementara proses belajar membaca dan menulis Al-Qur'an pada tahap Iqro 3 menuntut penguasaan huruf bersambung.
   - **Morfologi aksara Hijaiyah bersambung:** Setiap huruf mengalami perubahan bentuk visual drastis bergantung pada posisinya (*isolated*, *initial*, *medial*, *final*), serta banyak karakter berbagi kerangka bentuk serupa yang hanya dibedakan oleh letak dan jumlah titik diakritik.
   - **Kelemahan segmentasi konvensional:** Huruf bersambung membentuk ligatur tanpa spasi tegas. Pemotongan karakter bersambung secara eksplisit rentan mengalami *over-segmentation* atau pemotongan salah pada ligatur, sehingga kegagalan segmentasi merambat langsung menjadi kesalahan pengenalan (*cascading error*).
   - **Karakteristik tulisan tangan pemula/anak:** Tulisan tangan pada tahap belajar menulis memiliki variabilitas tinggi dan deformasi goresan yang besar dibandingkan tulisan cetak maupun tulisan orang dewasa.
   - **Kebutuhan model efisien dan transfer learning:** Melatih jaringan konvolusi dari awal (*from scratch*) pada dataset citra canvas mandiri berukuran terbatas rentan terhadap *overfitting*. Dibutuhkan arsitektur *transfer learning* yang ringan dan efisien (MobileNetV4) agar siap diintegrasikan ke perangkat interaktif/mobile di era komputasi modern.

4. **Arah dan Solusi Penelitian**  
   Penelitian diarahkan pada perancangan dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis materi Iqro 3 dan pengembangan model pengenalan sekuensial CNN-LSTM. Lapisan konvolusi (CNN) memanfaatkan bobot terlatih (*pre-trained*) MobileNetV4 sebagai pengekstraksi ciri visual spasial yang hemat komputasi, sedangkan lapisan LSTM bertindak sebagai pemodel dependensi urutan temporal huruf dari kanan ke kiri secara nirsegmentasi. Pengujian dievaluasi menggunakan metrik akurasi urutan penuh (*exact sequence match*), akurasi per karakter, dan *Character Error Rate* (CER).

---

## B. Naskah Bab 1: Pendahuluan

# BAB 1 PENDAHULUAN

## 1.1 Latar Belakang

Di era transformasi digital saat ini, perkembangan teknologi informasi dan kecerdasan buatan (*Artificial Intelligence*) berkembang sangat pesat menjadi instrumen pembantu (*assisting technology*) yang mempermudah berbagai aktivitas manusia. Dalam bidang pendidikan keagamaan, integrasi teknologi cerdas kini diarahkan untuk menghadirkan media pembelajaran yang adaptif, interaktif, dan dapat diakses secara mandiri. Di Indonesia, pembelajaran membaca dan menulis aksara Al-Qur'an pada tingkat dasar umumnya bertumpu pada metode Iqro. Pada tahap awal (Iqro 1 dan 2), peserta didik mempelajari huruf Hijaiyah dalam bentuk tunggal (*isolated*). Ketika melangkah ke buku Iqro 3, peserta didik mulai diperkenalkan pada kata-kata pendek yang tersusun atas dua hingga tiga huruf Hijaiyah yang ditulis secara bersambung. Penguasaan penulisan huruf Hijaiyah bersambung menjadi fondasi krusial bagi kelancaran literasi membaca dan menulis Al-Qur'an pada jenjang selanjutnya.

Meskipun memegang peranan fundamental, proses evaluasi latihan menulis huruf Hijaiyah sejauh ini masih sangat bergantung pada koreksi visual manual oleh guru atau ustaz secara tatap muka. Sebagaimana digarisbawahi oleh Rahmatulloh dkk. (2022), proses pembelajaran huruf Hijaiyah konvensional menuntut kehadiran ahli atau pembimbing khusus secara langsung untuk memandu setiap goresan. Ketergantungan mutlak pada evaluasi manual ini membatasi intensitas latihan mandiri peserta didik di luar jam pertemuan kelas, menimbulkan ketimpangan akses bimbingan bagi mereka yang belajar tanpa pendamping, serta menghadirkan kendala objektivitas dan konsistensi penilaian pada skala kelas yang besar. Mengingat laju perkembangan zaman yang serba cepat dan menuntut strategi adaptif, Rahmatulloh dkk. (2022) menegaskan urgensi kehadiran mekanisme teknologi cerdas berupa sistem pengenalan tulisan tangan (*Optical Character Recognition* / OCR luring) yang mampu mengidentifikasi tulisan dan memandu proses pembelajaran secara otomatis dengan memberikan umpan balik koreksi seketika (*instant warning/feedback*) jika terjadi kesalahan.

Peluang penerapan teknologi pembantu ini makin terbuka seiring meluasnya pemanfaatan perangkat layar sentuh dan media *canvas digital* interaktif. Peserta didik kini dapat berlatih menulis langsung di atas layar gawai dengan panduan garis titik-titik (*tracing dots*), di mana hasil goresan tersebut dapat diekspor menjadi berkas citra digital. Pemanfaatan perangkat digital untuk latihan menulis karakter Arab telah terbukti diterima secara antusias dan efektif oleh anak-anak usia sekolah dasar maupun kalangan pendidik, sebagaimana ditunjukkan pada evaluasi aplikasi tablet *Mutqin* (Durayhim dkk., 2023). Citra hasil goresan pada *canvas digital* tersebut memiliki potensi besar untuk menjadi masukan bagi sistem kecerdasan buatan guna menyediakan evaluasi otomatis yang cepat dan objektif.

Sebagai upaya mewujudkan sistem pengenalan tulisan tangan otomatis, penelitian acuan oleh Rahmatulloh dkk. (2022) yang berjudul *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"* telah membuktikan efektivitas pendekatan *Deep Learning*, khususnya arsitektur *Convolutional Neural Network* (CNN) yang dioptimalkan dengan algoritma ADAM, dalam mengenali dan mengklasifikasikan tulisan tangan huruf Hijaiyah. Penelitian tersebut berhasil mencapai tingkat akurasi klasifikasi yang tinggi, yaitu 91% pada dataset tulisan tangan anak-anak usia 7–12 tahun (Hijja2) dan 98% pada dataset tulisan dewasa (AHCD). Di akhir penelitiannya, Rahmatulloh dkk. (2022) memberikan arahan rekomendasi penting bagi penelitian selanjutnya (*future work*), yakni mengembangkan model pengenalan tulisan tangan Hijaiyah tersebut ke dalam aplikasi berbasis *mobile* agar dapat digunakan secara praktis untuk mengidentifikasi tulisan tangan Hijaiyah secara interaktif.

Kendati demikian, model yang dibangun oleh Rahmatulloh dkk. (2022)—serta sebagian besar penelitian pengenalan aksara Arab di Indonesia (Masruroh dkk., 2023)—masih terbatas pada pengenalan huruf tunggal yang berdiri sendiri (*isolated characters*). Di sisi lain, pada jenjang pembelajaran nyata kurikulum Iqro 3, peserta didik diwajibkan menuliskan rangkaian huruf bersambung. Pengenalan tulisan tangan huruf Hijaiyah bersambung menghadirkan tantangan komputasi yang jauh lebih kompleks dibandingkan pengenalan huruf tunggal. Pertama, morfologi huruf Arab bersifat sangat dinamis; satu huruf dapat berubah menjadi hingga empat bentuk visual yang berbeda bergantung pada posisinya dalam kata, yaitu di awal (*initial*), tengah (*medial*), akhir (*final*), atau berdiri sendiri (*isolated*) (Altwaijry & Al-Turaiki, 2021; Durayhim dkk., 2023). Kedua, sebagaimana diidentifikasi dalam studi Rahmatulloh dkk. (2022), banyak huruf Hijaiyah berbagi kerangka bentuk dasar yang identik dan hanya dibedakan oleh jumlah serta posisi titik diakritik (seperti kelompok ب، ت، ث dan ج، ح، خ), di mana pada penulisan bersambung titik-titik ini kerap terdistorsi atau bertumpang tindih dengan goresan huruf sekitarnya (Albattah & Albahli, 2022). Ketiga, penulisan huruf yang saling bertaut membentuk sambungan (*ligature*) tanpa batas pemisah yang jelas. Karakteristik ligatur ini membuat pendekatan konvensional berbasis segmentasi karakter (*segmentation-based*) kerap mengalami kegagalan akibat pemotongan berlebih (*over-segmentation*) atau kesalahan potong pada persilangan garis, di mana galat segmentasi tersebut merambat langsung menjadi kesalahan fatal dalam pengenalan karakter (*cascading error*) (Peng, 2024; Mosbah dkk., 2024). Kompleksitas ini semakin tinggi pada tulisan tangan anak-anak atau pemula yang memiliki variabilitas dan ketidakteraturan goresan yang besar (Alwagdani & Jaha, 2023).

Guna mengatasi kelemahan mendasar dari segmentasi fisik tersebut, paradigma pengenalan nirsegmentasi (*segmentation-free sequence recognition*) menjadi solusi yang paling menjanjikan. Pendekatan ini memperlakukan citra kata sebagai barisan representasi visual utuh yang dipetakan secara langsung menjadi urutan teks (*sequence of characters*). Integrasi arsitektur hibrida antara *Convolutional Neural Network* (CNN) dan *Long Short-Term Memory* (LSTM) terbukti sangat tangguh dalam mengenali barisan teks tulisan tangan bersambung (Saini dkk., 2024; Peng, 2024). Pada skema ini, lapisan CNN bertindak mengekstraksi representasi peta ciri visual spasial dari citra masukan, sedangkan lapisan rekuren LSTM membaca dependensi kontekstual urutan karakter secara temporal dari arah kanan ke kiri sesuai arah alami penulisan aksara Arab, sehingga mampu menyelesaikan persoalan ligatur yang rumit tanpa memerlukan pemotongan karakter secara fisik (Mosbah dkk., 2024).

Selain tantangan morfologi sambung, kendala teknis penting dalam merealisasikan rekomendasi Rahmatulloh dkk. (2022) menuju aplikasi interaktif adalah keterbatasan jumlah data latih citra *canvas digital* mandiri dan tuntutan efisiensi komputasi. Melatih model konvolusi dari awal (*from scratch*) dengan data berskala terbatas sangat rentan menimbulkan *overfitting* serta memperlambat konvergensi pelatihan. Dalam hal ini, penerapan *transfer learning* menjadi strategi krusial untuk memanfaatkan bobot yang telah dipelajari oleh model terlatih sebelumnya sebagai pengekstraksi ciri visual yang kaya (Lamtougui dkk., 2024; Masruroh dkk., 2023). Sejalan dengan tren teknologi masa kini yang menekankan komputasi cerdas pada perangkat berdaya rendah (*edge and mobile computing*), pemilihan arsitektur *backbone* modern yang sangat efisien seperti MobileNetV4 menawarkan keunggulan latensi rendah, bobot parameter yang ringkas, dan akurasi tinggi (El Khayati dkk., 2025). Karakteristik ini sangat ideal untuk mendukung inferensi cepat pada aplikasi latihan menulis berbasis *canvas digital*.

Kajian literatur menunjukkan bahwa penelitian yang mengkaji tulisan tangan Arab bersambung sejauh ini umumnya masih berfokus pada naskah dokumen pindaian kertas statis tulisan orang dewasa seperti dataset IFN/ENIT dengan pendekatan klasifikasi kata utuh (*whole-word classification*) (Lamtougui dkk., 2024; Ahmed dkk., 2021). Belum ada penelitian yang secara spesifik menjembatani celah penelitian (*research gap*) antara model pengenalan huruf tunggal yang dirintis oleh Rahmatulloh dkk. (2022) dengan pengenalan rangkaian huruf bersambung pendek (dua hingga tiga huruf) berbasis ekspor *canvas digital* kurikulum Iqro 3 menggunakan kombinasi *transfer learning* MobileNetV4 dan LSTM secara nirsegmentasi.

Berdasarkan latar belakang, perkembangan teknologi pendamping belajar di era sekarang, serta acuan riset dan rekomendasi Rahmatulloh dkk. (2022), penelitian ini mengusulkan pengembangan model klasifikasi multi-output sekuensial berbasis arsitektur gabungan CNN-LSTM dengan *transfer learning* MobileNetV4 untuk mengenali tulisan tangan huruf Hijaiyah bersambung pada materi Iqro 3. Model ini dirancang untuk membaca citra hasil ekspor *canvas digital* secara *segmentation-free* dan memprediksi urutan label karakter yang terkandung di dalamnya secara teratur dari kanan ke kiri. Dengan demikian, penelitian ini diharapkan dapat mewujudkan sistem kecerdasan buatan yang andal dan efisien, sehingga mampu berperan nyata sebagai teknologi pembantu dalam mendukung proses evaluasi latihan mandiri serta memperkaya ekosistem digital pembelajaran literasi Al-Qur'an tingkat dasar.

## 1.2 Rumusan Masalah

Berdasarkan latar belakang yang telah diuraikan, rumusan masalah dalam penelitian ini adalah sebagai berikut:
1. Bagaimana merancang dan membangun dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang mencakup kosakata kata sambung pada buku Iqro 3?
2. Bagaimana mengimplementasikan arsitektur CNN-LSTM dengan memanfaatkan *transfer learning* MobileNetV4 untuk mengenali urutan huruf Hijaiyah yang ditulis bersambung pada citra tanpa melalui proses segmentasi manual?
3. Bagaimana kinerja model CNN-LSTM dengan *transfer learning* dalam memprediksi urutan karakter huruf Hijaiyah bersambung berdasarkan metrik evaluasi pengenalan sekuensial (*exact sequence match*, akurasi per karakter, dan *Character Error Rate*)?

## 1.3 Tujuan Penelitian

Sesuai dengan rumusan masalah yang ditetapkan, tujuan dari penelitian ini adalah:
1. Menghasilkan dataset citra tulisan tangan huruf Hijaiyah bersambung berbasis ekspor *canvas digital* yang tersusun secara representatif berdasarkan kosakata buku Iqro 3.
2. Mengembangkan model pengenalan tulisan tangan bersambung berbasis arsitektur gabungan CNN-LSTM dengan *transfer learning* MobileNetV4 yang mampu memetakan citra langsung menjadi urutan karakter secara nirsegmentasi (*segmentation-free*).
3. Mengevaluasi dan menganalisis performa model dalam memprediksi urutan huruf Hijaiyah bersambung menggunakan metrik *exact sequence match*, akurasi per karakter, dan *Character Error Rate* (CER).

## 1.4 Manfaat Penelitian

Hasil penelitian ini diharapkan memberikan manfaat teoretis dan praktis sebagai berikut:

### 1.4.1 Manfaat Teoretis
1. Memberikan kontribusi ilmiah pada bidang visi komputer dan pengenalan pola (*pattern recognition*), khususnya dalam pengembangan metode nirsegmentasi berbasis CNN-LSTM dengan *transfer learning* untuk pengenalan karakter non-Latin bersambung.
2. Menjembatani kesenjangan riset antara model pengenalan karakter Hijaiyah tunggal (*isolated*) dan teks bersambung (*connected*), serta memperkaya literatur akademik terkait penanganan variasi morfologi dan ligatur pada kata pendek (dua hingga tiga huruf).

### 1.4.2 Manfaat Praktis
1. **Bagi peserta didik:** Menyediakan fondasi teknologi kecerdasan buatan sebagai asisten pembantu yang mampu memberikan umpan balik evaluasi penulisan kata Hijaiyah secara mandiri, cepat, dan objektif di luar jam kelas.
2. **Bagi pendidik (guru/ustaz):** Membantu proses asesmen latihan penulisan huruf Hijaiyah sambung secara konsisten serta meringankan beban evaluasi manual pada pembelajaran berskala besar.
3. **Bagi pengembang aplikasi pembelajaran:** Menyediakan arsitektur model *deep learning* yang ringan, akurat, dan efisien untuk diintegrasikan ke dalam aplikasi pembelajaran membaca dan menulis Al-Qur'an interaktif berbasis perangkat bergerak (*mobile*) atau tablet.

## 1.5 Ruang Lingkup Penelitian

### 1.5.1 Batasan Masalah
Untuk menjaga fokus penelitian agar tetap terarah, terukur, dan mendalam, batasan masalah ditetapkan sebagai berikut:
1. Objek pengenalan dibatasi pada citra tulisan tangan huruf Hijaiyah bersambung yang diekspor dari media *canvas digital* ke dalam format berkas citra digital 2 dimensi (pengenalan luring/*offline handwriting recognition*), bukan berupa data koordinat goresan waktu-nyata (*stroke time-series*).
2. Kosakata tulisan tangan dibatasi pada seluruh kata sambung yang terdapat di dalam buku Iqro 3, dengan panjang rangkaian karakter terdiri atas dua hingga tiga huruf per citra.
3. Citra masukan bersumber dari penulisan pada *canvas digital* dengan bantuan tampilan pola garis titik-titik panduan (*tracing dots*).
4. Arsitektur model yang dikembangkan dibatasi pada kombinasi jaringan konvolusional (*Convolutional Neural Network*) dengan *backbone* MobileNetV4 terbobot pra-pelatihan (*transfer learning*) dan jaringan *Long Short-Term Memory* (LSTM) untuk pemodelan urutan keluaran karakter dari arah kanan ke kiri.
5. Penelitian berfokus penuh pada perancangan dataset citra, pelatihan, penalaan hiperparameter, serta evaluasi performa model pengenalan; perancangan antarmuka gamifikasi dan integrasi aplikasi secara menyeluruh dikerjakan secara terpisah oleh pihak kolaborator.
6. Evaluasi model difokuskan pada ketepatan prediksi urutan karakter teks dan tidak mencakup penilaian kaidah hukum tajwid, panjang-pendek bacaan (*mad*), maupun aspek estetika kaligrafi (*khat*).

## 1.6 Sistematika Penulisan

Sistematika penulisan laporan skripsi ini disusun dalam lima bab dengan rincian sebagai berikut:

- **BAB 1 PENDAHULUAN**  
  Bab ini memuat latar belakang permasalahan yang menguraikan konteks teknologi pembantu di era sekarang, penelitian acuan Rahmatulloh dkk. (2022), urgensi pengenalan huruf Hijaiyah bersambung Iqro 3, rumusan masalah, tujuan penelitian, manfaat penelitian, ruang lingkup dan batasan masalah, serta sistematika penulisan laporan.
- **BAB 2 TINJAUAN PUSTAKA**  
  Bab ini memuat kajian penelitian terdahulu yang relevan mengenai pengenalan tulisan tangan huruf Hijaiyah dan Arab bersambung, serta landasan teori mengenai karakteristik morfologi aksara Hijaiyah, konsep pembelajaran Iqro 3, ekstraksi ciri CNN, *transfer learning*, arsitektur LSTM, konsep pemodelan urutan nirsegmentasi, dan metrik evaluasi pengenalan teks sekuensial.
- **BAB 3 METODOLOGI PENELITIAN**  
  Bab ini menguraikan tahapan pelaksanaan penelitian yang mencakup prosedur pengumpulan data tulisan tangan pada *canvas digital*, penyusunan manifest data berbasis partisipan (*participant-wise*), prapemrosesan citra, skema perancangan arsitektur CNN-LSTM dengan *backbone* MobileNetV4, tahapan pelatihan dua fase (*two-stage training*), serta skenario pengujian dan metrik evaluasi performa.
- **BAB 4 HASIL DAN PEMBAHASAN**  
  Bab ini menyajikan data hasil eksperimen pelatihan model, perbandingan performa skenario pelatihan (termasuk kajian ablasi pengaruh *transfer learning* dan komponen sekuensial), evaluasi metrik pengenalan urutan karakter, analisis matriks kekeliruan (*confusion matrix*), serta diskusi analitis terhadap temuan penelitian.
- **BAB 5 KESIMPULAN DAN SARAN**  
  Bab ini menyajikan kesimpulan menyeluruh yang menjawab rumusan masalah dan tujuan penelitian berdasarkan hasil pengujian empiris, serta saran-saran konstruktif untuk pengembangan penelitian selanjutnya.

---

## C. Catatan Evaluasi dan Penyelarasan Revisi

1. **Integrasi Konteks "Teknologi Membantu di Zaman Sekarang"**  
   Narasi latar belakang dibuka dan diperkuat dengan fakta bahwa di era transformasi digital dan kecerdasan buatan saat ini, teknologi modern berkembang menjadi instrumen pembantu (*assisting technology*) yang krusial di bidang pendidikan. Hal ini dikontekstualisasikan langsung dengan kebutuhan peserta didik untuk berlatih menulis aksara Hijaiyah secara mandiri di luar jam bimbingan guru tatap muka, didukung oleh maraknya gawai layar sentuh (*touchscreen/tablet*) dan *canvas digital*.

2. **Penetapan Paper Rahmatulloh dkk. (2022) sebagai Acuan Utama (*Baseline & Anchor*)**  
   - Makalah Rahmatulloh dkk. (2022) *"Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning"* dijadikan acuan fundamental yang dirujuk secara komprehensif pada Latar Belakang:
     1. **Konteks & urgensi masalah:** Bimbingan manual konvensional memerlukan komplementer sistem cerdas otomatis berbasis OCR/Deep Learning untuk memberikan evaluasi mandiri seketika jika terjadi kesalahan goresan.
     2. **Keberhasilan model acuan:** Model CNN dengan optimasi ADAM berhasil mencapai akurasi 91% pada dataset anak-anak (Hijja2) dan 98% pada dataset dewasa (AHCD) untuk huruf tunggal.
     3. **Arahan riset masa depan (*future work*):** Rahmatulloh dkk. merekomendasikan pengembangan model pengenalan tulisan tangan Hijaiyah ke dalam aplikasi interaktif berbasis *mobile*.
     4. **Kesenjangan penelitian (*research gap*):** Penelitian acuan masih terbatas pada huruf tunggal (*isolated*), sedangkan pembelajaran Al-Qur'an (khususnya materi Iqro 3) menuntut kemampuan menulis rangkaian huruf bersambung pendek (2-3 huruf) dengan ligatur yang kompleks.
   - Skripsi ini secara tegas memposisikan diri sebagai kelanjutan riset yang menjawab rekomendasi Rahmatulloh dkk. (2022) dengan memperluas domain ke pengenalan sekuensial nirsegmentasi (*segmentation-free* CNN-LSTM) menggunakan *transfer learning* MobileNetV4 yang ringan dan siap diimplementasikan pada perangkat interaktif modern.

3. **Kesesuaian Format dan Gaya Bahasa Akademik UISI**  
   - Format subbab konsisten dengan pedoman UISI (Subbab 1.1 hingga 1.6, termasuk Subbab 1.5.1 Batasan Masalah).
   - Penggunaan istilah teknis selaras antara bahasa Indonesia baku dan serapan ilmiah berhuruf miring (*italics*).

---

## D. Daftar Referensi yang Digunakan

Format sitasi mengacu pada kaidah *American Psychological Association* edisi ke-7 (APA 7th edition):

Ahmed, R., Gogate, M., Tahir, A., Dashtipour, K., Al-tamimi, B., Hawalah, A., El-Affendi, M. A., & Hussain, A. (2021). Novel deep convolutional neural network-based contextual recognition of Arabic handwritten scripts. *Entropy*, *23*(3), 340. https://doi.org/10.3390/e23030340

Albattah, W., & Albahli, S. (2022). Intelligent Arabic handwriting recognition using different standalone and hybrid CNN architectures. *Applied Sciences*, *12*(19), 10155. https://doi.org/10.3390/app121910155

Altwaijry, N., & Al-Turaiki, I. (2021). Arabic handwriting recognition system using convolutional neural network. *Neural Computing and Applications*, *33*(7), 2249–2261. https://doi.org/10.1007/s00521-020-05070-8

Alwagdani, M. S., & Jaha, E. S. (2023). Deep learning-based child handwritten Arabic character recognition and handwriting discrimination. *Sensors*, *23*(15), 6774. https://doi.org/10.3390/s23156774

Durayhim, A. B., Al-Ajlan, A., Al-Turaiki, I., & Altwaijry, N. (2023). Towards accurate children’s Arabic handwriting recognition via deep learning. *Applied Sciences*, *13*(3), 1692. https://doi.org/10.3390/app13031692

El Khayati, M., Maafiri, A., Himeur, Y., Alkhazaleh, H. A., Atalla, S., & Mansoor, W. (2025). Leveraging transfer learning and mobile-enabled convolutional neural networks for improved Arabic handwritten character recognition. *arXiv preprint arXiv:2509.05019*. https://doi.org/10.48550/arXiv.2509.05019

Lamtougui, H., El Moubtahij, H., Fouadi, H., & Satori, K. (2024). Improving Arabic handwritten text recognition through transfer learning with convolutional neural network-based models. *Bulletin of Electrical Engineering and Informatics*, *13*(6), 4294–4305. https://doi.org/10.11591/eei.v13i6.8178

Masruroh, S. U., Syahid, M. F., Munthaha, F., Muharram, A. T., & Putri, R. A. (2023). Deep convolutional neural networks transfer learning comparison on Arabic handwriting recognition system. *International Journal on Informatics Visualization*, *7*(2), 330–337.

Mosbah, L., Moalla, I., Hamdani, T. M., Neji, B., Beyrouthy, T., & Alimi, A. M. (2024). ADOCRNet: A deep learning OCR for Arabic documents recognition. *IEEE Access*, *12*, 55620–55629. https://doi.org/10.1109/ACCESS.2024.3379530

Peng, G. (2024). Segmentation-free recognition algorithm based on deep learning for handwritten text image. *Journal of Artificial Intelligence and Technology*, *4*(2), 169–178. https://doi.org/10.37965/jait.2024.0473

Rahmatulloh, A., Rizal, R., Gunawan, R. I., Darmawan, I., & Rahmat, B. Z. (2022). Optimization of Hijaiyah letter handwriting recognition model based on deep learning. Dalam *2022 International Conference Advancement in Data Science, E-learning and Information Systems (ICADEIS)* (hlm. 1–6). IEEE. https://doi.org/10.1109/ICADEIS56544.2022.10037496

Saini, M. L., Sati, D. C., Telikicharla, R. S., & Mahadev. (2024). Handwritten English script recognition system using CNN and LSTM. Dalam *2024 IEEE International Conference on Contemporary Computing and Communications (InC4)* (hlm. 1–6). IEEE. https://doi.org/10.1109/InC460750.2024.10649099

---

## E. Status Pengerjaan

Naskah Bab I telah berhasil direvisi dengan menyelaraskan konteks perkembangan teknologi pembantu di era sekarang serta mengintegrasikan secara komprehensif makalah acuan Rahmatulloh dkk. (2022) sebagai batu pijakan (*baseline*) dan justifikasi celah penelitian (*research gap*).
