# ANALISIS LITERATUR LENGKAP — SKRIPSI HIJAIYAH SAMBUNG (CNN-LSTM)

**Mahasiswa:** Muchamad Budi Fabiantoro (22314050111003) — Informatika UISI
**Topik:** Pengenalan tulisan tangan huruf Hijaiyah sambung (2–3 huruf/gambar, ekspor canvas digital, materi Iqro 3) dengan CNN-LSTM + Transfer Learning
**Tanggal analisis:** 21 September 2026
**Cakupan:** SELURUH folder dan file dalam direktori kerja. 16 paper jurnal unik dibaca penuh (isi dokumen, bukan nama file); 6 file non-jurnal diinventarisasi.

> ⚠️ **PERINGATAN KORUPSI DATA — BACA DULU.** Hasil pembacaan penuh 16 PDF ini menemukan bahwa **banyak angka pada `literatur_gap_skripsi.md` lama TIDAK sesuai isi dokumen** (kemungkinan dihasilkan tanpa membaca teks penuh). Contoh koreksi besar (rincian di Tahap 2):
> - Lamtougui 2024: terbaik adalah **VGG16 94,73%**, bukan "ResNet-50 94,73%".
> - Masruroh 2023: terbaik **VGG16+Adam lr 1e-4 (AHCD 96%, Hijja 87%)**; **MobileNet justru terlemah (Hijja 75%)** — bukan "MobileNetV2 & DenseNet-121 terbaik 94,2%".
> - Albattah 2022: tidak ada angka "ResNet-50+SVM 98,15%"; aktual CNN+SVM **87,2%**.
> - Ge Peng 2024: tidak ada "CER 4,82% IAM / RIMES"; aktual **CCR 96,135% IAM**, RIMES tidak diuji; KHATT (Arab) hanya **58,02%**.
> - Saini 2024: tidak ada "akurasi 91,8%"; aktual **CER 8,6547%**.
> - Durayhim 2023: aktual CNN **99% Hijja (29 kelas)** dan VGG-16 **83%** — bukan "82,5% vs 66,8%".
> - Ahmed 2021: tidak menguji IFN/ENIT/KHATT; aktual 6 dataset digit/huruf/kata (99,72–99,95%).
> - Balaha 2021: tidak menguji Hijja; aktual HMBD 98,4%, AHCD (cross-val) 97,3%.
> - El Khayati 2025: tidak ada "MobileNetV2 97,8%"; aktual terbaik ShuffleNet TWI 0,97 (AHCD), Hijja 0,92.
> - Jbrail 2022: klaim "99,3% Hijja" tapi jumlah sampel yang diolah (13.440/3.360) identik AHCD — **diduga salah dataset**.
> - Satu paper **terlewat** dari matriks lama: **ADOCRNet (IEEE Access 2024)** — justru salah satu rujukan paling relevan.
> Seluruh angka dalam dokumen ini diambil langsung dari teks penuh PDF dan dapat ditelusuri ke halamannya.

---

## TAHAP 1 — INVENTARISASI SELURUH FILE

| No | Folder | Nama File | Jenis Dokumen | Tahun | Status Isi | Relevansi Awal |
|---|---|---|---|---|---|---|
| 1 | file GAP | applsci-13-01692 (1).pdf | Jurnal (MDPI Applied Sciences) | 2023 | Lengkap | Sangat relevan |
| 2 | file GAP | jait.2024.0473.pdf | Jurnal (JAIT) | 2024 | Lengkap | Sangat relevan |
| 3 | file GAP | Optimization_of_Hijaiyah_...pdf | Konferensi (IEEE ICADEIS) | 2022 | Lengkap | Pendukung |
| 4 | file GAP/Jurnal Pendukung | applsci-12-10155 (1).pdf | Jurnal (MDPI Applied Sciences) | 2022 | Lengkap | Sebagian |
| 5 | file GAP/Jurnal Pendukung | 1904.03582v1.pdf | Preprint arXiv (versi CVPR 2019) | 2019 | Lengkap | Pendukung (teori) |
| 6 | file GAP/Jurnal Pendukung | 2401.16549v3.pdf | Preprint arXiv (survey, gaya IEEE Access) | 2024 | Lengkap | Sangat relevan (teori) |
| 7 | file GAP/Jurnal Pendukung | 2509.05019v1.pdf | Preprint arXiv | 2025 | Lengkap | Sangat relevan |
| 8 | file GAP/Jurnal Pendukung | ADOCORNet_...pdf | Jurnal (IEEE Access) | 2024 | Sebagian (tabel bergambar tak berteks; body terbaca) | Sangat relevan |
| 9 | file GAP/Jurnal Pendukung | Arabic handwriting recognition system using convolutional neural.pdf | Jurnal (Springer NC&A) | 2020/2021 | Lengkap | Pendukung |
| 10 | file GAP/Jurnal Pendukung | balaha2020.pdf | Jurnal (Springer NC&A) | 2020/2021 | Lengkap | Pendukung |
| 11 | file GAP/Jurnal Pendukung | entropy-23-00340-v2.pdf | Jurnal (MDPI Entropy) | 2021 | Lengkap | Pendukung |
| 12 | file GAP/Jurnal Pendukung | Handwritten-English-Script-...pdf | Konferensi (IEEE InC4) | 2024 | Lengkap | Sangat relevan (metode) |
| 13 | file GAP/Jurnal Pendukung | Improving Arabic handwritten ... Lamtougui ...pdf | Jurnal (BEEI) | 2024 | Lengkap (scan, dibaca visual) | Sangat relevan |
| 14 | file GAP/Jurnal Pendukung | JOSSE-vol-2-no1-p3-2022.pdf | Jurnal (JOSSE) | 2022 | Lengkap | Sebagian (reliabilitas rendah) |
| 15 | file GAP/Jurnal Pendukung | paper_ff78f31c69aa5719bd0bf18a6927da4a.pdf | Jurnal (JOIV) — terverifikasi = Masruroh et al. 2023 | 2023 | Lengkap | Sangat relevan |
| 16 | file GAP/Jurnal Pendukung | sensors-23-06774-v2.pdf | Jurnal (MDPI Sensors) | 2023 | Lengkap | Pendukung |
| 17 | file pdf | Iqra-3-Belajar-Baca-Quran.pdf | **Bahan ajar** (bukan literatur) | — | Sebagian (32 hlm, hasil pindai tanpa lapisan teks) | Referensi materi dataset |
| 18 | file pdf | ketentuan penulisan skripsi uisi.pdf | Panduan penulisan (bukan literatur) | — | Lengkap (25 hlm) | Tidak relevan sebagai sitasi riset |
| 19 | (root) | skripsi_hijaiyah_canvas_research_notes.md | Catatan penelitian sendiri | 2026 | Lengkap | Konteks penelitian |
| 20 | (root) | skripsi_hijaiyah_canvas_research_notes.docx | **Duplikat** dari file 19 (douban judul/daftar isi terverifikasi) | 2026 | Duplikat | — |
| 21 | (root) | literatur_gap_skripsi.md | Analisis literatur draft sebelumnya | 2026 | Lengkap, tetapi **banyak angka tidak akurat** (lihat peringatan) | Dasar koreksi |
| 22 | (root) | RINGKASAN_SKRIPSI_POIN_PENTING.md | Ringkasan catatan sendiri | 2026 | Lengkap | Konteks |
| 23 | (root) | image.png | Citra contoh (60×17 px): tulisan sambung Arab putus-putus "محمد" | — | Lengkap (terbaca visual) | Kemungkinan contoh referensi gaya sambung |
| 24 | file GAP/Jurnal Pendukung/Sementara | (kosong) | — | — | — | 2 duplikat PDF (entropy, sensors) yang dicatat analisis lama **sudah dihapus** — tidak ada file hilang |
| 25 | .qoder | settings.local.json | Konfigurasi tool | — | Tidak relevan | — |

**Total: 16 paper jurnal unik + 9 file non-paper.** Tidak ada file rusak/kosong di antara PDF jurnal.

---

## TAHAP 2 — RINGKASAN SETIAP PAPER

### P1. Durayhim et al. 2023 — *Towards Accurate Children's Arabic Handwriting Recognition via Deep Learning*
- **Identitas:** Anfal Bin Durayhim, Amani Al-Ajlan, Isra Al-Turaiki, Najwa Altwaijry. *Applied Sciences* 13(3):1692. DOI: 10.3390/app13031692.
- **Masalah/objek:** tulisan tangan **huruf Arab tunggal anak** (7–12 th); eksperimen kedua memakai **108 kelas bentuk posisional** (isolated/initial/medial/final) — paling dekat ke aspek "sambung" di seluruh koleksi.
- **Dataset:** Hijja (47.434 citra, 591 anak, Riyadh; 29 huruf + Hamzah → 108 bentuk); AHCD (16.800, 60 dewasa, 28 kelas).
- **Metode:** CNN 7-layer custom (4 conv 3×3, BN, dropout 20%, Adam, categorical cross-entropy) vs **VGG-16 transfer learning** (4 grup bawah beku, RMSprop, input 32→224).
- **Hasil:** CNN custom **99% Hijja 29 kelas**, **95% Hijja 108 kelas**, **98% AHCD**; VGG-16 hanya **83% Hijja / 94% AHCD** (penyebab diduga resize 32→224). Model 5,12 jt parameter, inferensi 1,96 s. Prototipe aplikasi tablet **Mutqin** + UAT 11 anak & 8 guru (lulus).
- **Keterbatasan:** split tertulis 70/10/10 (=90%, tidak konsisten); perbandingan CNN vs VGG-16 tidak terkendali (split VGG beda); tanpa pemodelan sekuens; **huruf sambung/kata eksplisit dinyatakan sebagai future work**.
- **Ringkasan inti:**
  1. SOTA dataset Hijja saat terbit (99% kelas 29; 95% kelas 108).
  2. Peringatan empiris: **transfer learning VGG-16 bisa kalah dari CNN kecil pada citra tulisan resolusi rendah** — argumen penting saat memilih backbone untuk skripsi.
  3. Satu-satunya yang mengevaluasi 108 varian bentuk posisional (modal untuk pre-training domain-specific).
  4. Preseden aplikasi tablet tulis-angka + validasi anak = justifikasi konteks canvas Iqro.
  5. Future work literal: "recognize connected letters and words" → gap yang diisi skripsi.

### P2. Ge Peng 2024 — *Segmentation-Free Recognition Algorithm Based on Deep Learning for Handwritten Text Image*
- **Identitas:** Ge Peng (Baoshan University, China). *Journal of Artificial Intelligence and Technology* 4(2):169–178. DOI: 10.37965/jait.2024.0473.
- **Masalah/objek:** segmentasi manual gagal pada karakter **bersentuhan/bersilangan**; pengenalan **baris teks tulisan tangan offline multi-bahasa** (Inggris, Mandarin, Rusia, Spanyol, **Arab**).
- **Dataset:** IAM (13.353 line), CASIA-HWDB 2.0/2.1/2.2, HIT-MW, DigitalPeter, Rodrigo, **KHATT Arab (13.435 line, 1.000 penulis, alfabet 94)**. Split 60:20:20.
- **Metode:** Preprocessing (tinggi dinormakan 64 px) → **CNN tanpa FC** (syarat: output H=1, W ≥ 5× panjang label) → **2-layer BDLSTM** → **CTC loss**; varian P1–P4; metode **"data filling"** (memanjangkan label dengan menyambung citra lain, bukan padding blank). Tanpa transfer learning.
- **Hasil:** rata-rata CCR 6 DB: P2 **91,13%** vs CRNN baseline 81,89%-setara; **KHATT tetap terburuk: 58,02%** (CRNN 50,34%; metode segmentasi-based rata-rata 43,18%). Waktu 11,43 ms/karakter; model 47,6–161 MB.
- **Keterbatasan:** CCR tidak didefinisikan formal (belum tentu = 1−CER); framework tidak dilaporkan; satu penulis; **Arab diakui belum terselesaikan**; data filling mengubah semantik label (tak cocok konteks pendek).
- **Ringkasan inti:**
  1. Cetak-biru **CNN→BiLSTM→CTC segmentation-free** + constraint teknis yang bisa dikutip (H=1, W≥5×label).
  2. **Bukti terkuat gap riset**: skrip Arab kursif adalah kasus tersulit (58,02% bahkan untuk model sekuensial).
  3. Teknik "data filling" dapat diadaptasi untuk menormalkan lebar gambar canvas 2–3 huruf.
  4. Tanpa TL → pelengkap alami bagi skripsi (TL + Arab).

### P3. Rahmatulloh et al. 2022 — *Optimization of Hijaiyah Letter Handwriting Recognition Model Based on Deep Learning*
- **Identitas:** Alam Rahmatulloh, Randi Rizal, Ricky I. Gunawan (Univ. Siliwangi), Irfan Darmawan (Univ. Telkom), Biki Z. Rahmat. **ICADEIS 2022, IEEE**. DOI: 10.1109/ICADEIS56544.2022.10037496.
- **Masalah/objek:** klasifikasi **huruf Hijaiyah tunggal** tulisan tangan (isolated, 32×32×1); kesulitan: huruf mirip beda posisi titik.
- **Dataset:** **Hijja2** (47.434; 29 kelas; 591 anak) dan AHCD (16.800; 28 kelas); split 60:20:20.
- **Metode:** CNN Conv2D/MaxPool/Dropout/Flatten/Dense; **Adam** (klaim kebaruan), categorical cross-entropy; augmentasi rotation/zoom/shift; normalisasi 0–1; TensorFlow/Keras di Google Colab GPU.
- **Hasil:** **91% Hijja2, 98% AHCD** (P/R/F1 per kelas dilaporkan; terlemah dal F1 0,77 & thal 0,78).
- **Keterbatasan:** novelty tipis (ganti optimizer, tanpa ablation Adam vs SGD); epoch/batch/lr tidak dilaporkan; tanpa TL, tanpa LSTM, tanpa metrik sekuensial; beberapa galat ketik tabel.
- **Ringkasan inti:**
  1. **Baseline lokal wajib-cite** (satu-satunya paper berobjek eksplisit "Hijaiyah").
  2. Tabel kesulitan per huruf (dal/thal, 'ayn/ghain) menjelaskan mengapa pasangan mirip makin sulit saat disambung.
  3. Konfirmasi penggunaan Hijja2 sebagai dataset sekunder yang lazim.
  4. Tidak memberi dasar metodologis untuk CNN-LSTM/TL/multi-label.

### P4. Albattah & Albahli 2022 — *Intelligent Arabic Handwriting Recognition Using Different Standalone and Hybrid CNN Architectures*
- **Identitas:** Waleed Albattah, Saleh Albahli (Qassim University). *Applied Sciences* 12(19):10155. DOI: 10.3390/app121910155.
- **Masalah/objek:** **huruf (AHCD) dan digit (Arabic MNIST) terisolasi**; standalone ML/DL vs hybrid CNN-feature-extractor + klasifier tradisional.
- **Metode:** 10 ML standalone (XGBoost, RF, CatBoost, SVM, LR, FFNN), CNN 3-layer (129.162 parameter), TL (backbone **tidak dispesifikasi**), 6 hybrid (CNN+SVM/RF/AdaBoost/XGBoost/CatBoost/LR); Colab, Keras, Python 3.6.3, OpenCV.
- **Hasil:** digit: TL 0,99673; XGBoost 1,0. karakter Arab: **CNN standalone 0,8992; CNN+SVM 0,872; CNN+AdaBoost gagal (0,169)**.
- **Keterbatasan:** baseline di bawah SOTA yang dikutipnya sendiri; galat numerik split (13.400 vs 14.440); backbone TL tidak jelas → angka tak dapat direplikasi; **tanpa kursif sama sekali**.
- **Ringkasan inti:**
  1. Bagian *"Challenges and Open Problems"* bernilai kutipan langsung: **sifat kursif Arab, titik/harakat pengubah makna, kelangkaan dataset, ketidakseimbangan** — fondasi latar belakang.
  2. Bukti jurang kesulitan digit (99%+) vs huruf Arab (~87–90%).
  3. Peringatan: hybrid ensemble bisa gagal total; klasifikator non-sekuensial bukan solusi urutan.
  4. Kualitas eksperimen rendah → **jangan dijadikan pembanding angka utama**.

### P5. Chen et al. 2019 — *Multi-Label Image Recognition with Graph Convolutional Networks* (ML-GCN)
- **Identitas:** Zhao-Min Chen, Xiu-Shen Wei, Peng Wang, Yanwen Guo. arXiv:1904.03582v1 (terkenal sebagai CVPR 2019; DOI CVPR 10.1109/CVPR.2019.00532 dikutip paper lain — **di dalam PDF tidak tertulis**).
- **Masalah/objek:** klasifikasi multi-label citra natural; dependensi antar-label (ko-okurensi).
- **Dataset:** MS-COCO (82.081 latih, 80 kelas), PASCAL VOC 2007 (9.963, 20 kelas).
- **Metode:** ResNet-101 (ImageNet) + GCN 2-layer di atas word embedding GloVe; **loss BCE multi-label + threshold 0,5**; matriks korelasi kondisional P(Lj|Li), ambang τ=0,4, re-weighting p=0,2; SGD, PyTorch.
- **Hasil:** **mAP 83,0 (COCO), 94,0 (VOC)**; ablation: 2 layer GCN terbaik; τ=0/p=1 tidak konvergen.
- **Keterbatasan:** butuh embedding leksikal (tidak trivial untuk label huruf/glyph); citra natural, bukan teks; tanpa urutan baca.
- **Ringkasan inti:**
  1. Sumber formal **loss BCE + sigmoid** untuk multi-label (pembanding softmax/label power-set).
  2. Metode menghitung **matriks ko-okurensi label** — dapat dipakai menganalisis struktur kombinasi huruf Iqro 3.
  3. Metrik CP/CR/CF1/OP/OR/OF1/mAP sebagai kerangka evaluasi multi-label pelengkap.
  4. Bukan pembanding metode untuk tulisan sambung (objek berbeda total).

### P6. Tarekegn et al. 2024 — *Deep Learning for Multi-Label Learning: A Comprehensive Survey*
- **Identitas:** Adane Nega Tarekegn, Mohib Ullah, Faouzi Alaya Cheikh (Univ. Bergen/NTNU). arXiv 2401.16549v3 (terverifikasi via pencarian eksternal; **DOI tidak ditemukan dalam dokumen**); gaya IEEE Access.
- **Isi:** survey 212 paper (2006–2023) metode DL untuk multi-label classification/recognition.
- **Konten kunci:** taksonomi DNN/CNN/RNN-LSTM/autoencoder/Transformer/GCN untuk MLC; **perpustakaan loss**: BCE, cross-entropy, pairwise-ranking (BP-MLL), WARP, LogSumExp, ZLPR, asymmetric focal (Query2Label), triplet, target-replication; korelasi label orde-1/2/tinggi; strategi BR/LP/CC; karakteristik dataset (label cardinality/density/diversity, Eq. 15–17); metrik: Hamming loss, ranking loss, micro/macro-F1, mAP, subset accuracy.
- **Keterbatasan:** tanpa eksperimen sendiri; **tidak membahas CTC/CRNN/OCR Arab**; beberapa penomoran persamaan rancu.
- **Ringkasan inti:**
  1. Landasan teori Bab 2 paling kuat untuk framing "multi-label" (definisi formal + justifikasi memilih sigmoid-multi-label vs label power-set: 28 huruf → 2^28 kombinasi mustahil).
  2. Katalog loss function & metrik multi-label yang bisa diadopsi (Hamming loss, subset accuracy ≈ exact sequence match).
  3. Rumus cardinality/density/diversity untuk **mendeskripsikan dataset canvas Iqro 3 Anda sendiri** secara formal.
  4. Tidak menyentuh sisi sekuensial/Arab → harus dipasangkan dengan P2/P8/P12.

### P7. El Khayati et al. 2025 — *Leveraging Transfer Learning and Mobile-enabled CNNs for Improved Arabic Handwritten Character Recognition*
- **Identitas:** Mohsine El Khayati, Ayyad Maafiri, Yassine Himeur, Hamzah A. Alkhazaleh, Shadi Atalla, Wathiq Mansoor. arXiv:2509.05019v1 (5 Sep 2025); preprint, **jurnal tujuan & DOI tidak ditemukan dalam dokumen**.
- **Masalah/objek:** **huruf Arab isolated (28 kelas)** + efisiensi mobile; membandingkan 3 strategi TL: **TWI** (full fine-tuning), **TFE** (feature extractor beku), **TFS** (dari nol) × 4 backbone ringan (MobileNetV3-small, ShuffleNet_V2_X0_5, MnasNet0_5, SqueezeNet1_1).
- **Dataset:** AHCD (16.800), Hijja (47.434; 108 bentuk digabung ke 28), IFHCDB (70.120).
- **Metode:** CE loss, SGD/Adam per konfigurasi, Cosine Annealing LR, **Hyperband search, 5-fold CV, 50 epoch, batch 32–64, dropout optimal 0,3–0,4**; Colab 12,7 GB.
- **Hasil:** AHCD terbaik 0,97 (ShuffleNet); **Hijja terbaik 0,92** (rata-rata per dataset: Hijja 0,76 tersulit); IFHCDB 0,99. **Gain TL ImageNet hanya +0,4 s.d. +1,7%**; TFE kolaps (0,26–0,54). **Eksperimen word-level IFN/ENIT (segmentasi + bigram LM): word accuracy 87,2%, CER 7,8%** (MobileNet TWI).
- **Keterbatasan:** semua utama isolated; kursif = future work eksplisit; tanpa CTC/RNN; split IFHCDB tidak konsisten; framework tidak eksplisit.
- **Ringkasan inti:**
  1. Buktu kuantitatif **domain mismatch ImageNet→tulisan Arab**: TL membantu sedikit; beku-total gagal → justifikasi **pre-training domain-specific (Hijja2)** untuk backbone Anda.
  2. **Hijja (bentuk posisional, tulisan anak) dataset tersulit** — analog langsung kondisi canvas Iqro 3.
  3. Baseline word-level dengan CER (87,2% / 7,8%) — pembanding metode pipeline-segmentasi vs end-to-end Anda.
  4. Resep hiperparameter sangat rinci (Hyperband, 5-fold CV, dropout 0,3–0,4) untuk Bab 3.
  5. Klaim model ringan ≈ akurasi model besar → relevan integrasi ke aplikasi gamifikasi (Mas Nadhif).

### P8. Mosbah et al. 2024 — *ADOCRNet: A Deep Learning OCR for Arabic Documents Recognition*
- **Identitas:** Lamia Mosbah, Ikram Moalla, Tarek M. Hamdani, Bilel Neji, Taha Beyrouthy, Adel M. Alimi (ReGIM-Lab, Sfax). **IEEE Access** vol 12, hlm 55620–55629. DOI: 10.1109/ACCESS.2024.3379530.
- **Masalah/objek:** OCR Arab **end-to-end segmentation-free** untuk teks cetak + tulisan tangan; masalah spesifik: **segmentasi ligatur/sambungan** menyebabkan kesalahan transkripsi.
- **Dataset:** P-KHATT (9.310 baris, 8 font), APTI (45,3 jt kata cetak), **IFN/ENIT tulisan tangan (32.492 kata, 937 nama, 400+ penulis)**; split uji abc-d / abcd-e.
- **Metode:** **CRNN**: 3 blok CNN (conv 4×4 + ReLU + maxpool 2×2) → dense/reshape → **BLSTM (250 unit) + dropout 0,5 → CTC loss + CTC decoder (blank symbol)**; lr 0,001, batch 20, SGD; Keras/TensorFlow Colab K80; augmentasi morfologis (distorsi geometrik, contrast/stretch, perspektif; 12 varian/citra).
- **Hasil:** **CER 0,01% P-KHATT; CER 0,03% APTI; WER 1,09% IFN/ENIT** (vs pembanding teks: CNN-HMM 11,05%, CNN/BLSTM Maalej 7,79%, MDLSTM-CTC-Maxout 6,64%); augmentasi mempercepat konvergensi (epoch 150/200 → 60/90). Catatan: **angka rinci dalam tabel (Table 1–9) tidak dapat diekstrak (objek grafis)** — semua angka dari body text/abstrak.
- **Keterbatasan:** hasil tinggi didominasi teks cetak; IFN/ENIT = kosakata tertutup 937 entitas; tanpa transfer learning; deskripsi arsitektur tidak presisi ("250 layers of BLSTM").
- **Ringkasan inti:**
  1. **Template CRNN Arab paling lengkap**: CNN→BLSTM→CTC + mekanisme blank symbol & penggabungan karakter berulang — persis kebutuhan arsitektur skripsi.
  2. Argumen "ligatur Arab tak dapat disegmentasi andal" terdokumentasi → justifikasi segmentation-free.
  3. Definisi & pemakaian metrik **CER/WER/CRR/WRR** + protokol split IFN/ENIT untuk Bab 4.
  4. Bukti peran augmentasi morfologis untuk konvergensi data tulisan tangan terbatas.
  5. Single-label transkripsi (bukan multi-label) — sisi multi-label tetap butuh P5/P6.

### P9. Altwaijry & Al-Turaiki 2020/2021 — *Arabic handwriting recognition system using convolutional neural network*
- **Identitas:** Najwa Altwaijry, Isra Al-Turaiki (King Saud University). *Neural Computing and Applications* 33:2249–2261. DOI: 10.1007/s00521-020-05070-8.
- **Masalah/objek:** **perkenalan dataset Hijja** (huruf Arab tulisan tangan ANAK — belum ada sebelumnya) + model CNN baseline.
- **Dataset:** Hijja — **47.434 citra, 591 anak 7–12 th, Riyadh (Jan–Apr 2019), 300 dpi, 32×32 grayscale, 29 kelas, 108 bentuk posisi**, split 60:20:20; AHCD 16.800/28 kelas.
- **Metode:** CNN 3 blok conv (64/128/256, 3×3) + BN + LRN + maxpool; FC 4096-1024-512, **dropout 80% di FC**; Adam lr 0,001, 30 epoch, RTX 2080 Ti, 10× pengulangan.
- **Hasil:** **Hijja 88% (P 87,88/R 87,81/F1 87,8); AHCD 97%** — unggul atas baseline CNN-for-AHCD (80%/93,84%).
- **Keterbatasan:** isolated single letters; tanpa harakat; kelas tak seimbang; tanpa TL/RNN; **future work eksplisit: transfer learning + pipeline huruf tersambung**.
- **Ringkasan inti:**
  1. **Paper asal-usul dataset Hijja/Hijja2** — sitasi wajib saat memakai Hijja2 untuk pre-training.
  2. Analisis error huruf mirip (dal/ha, 'ayn/ghain, fa/qaf, mim) — dasar diskusi confusion class sambung.
  3. Angka 88% Hijja menjadi titik awal narasi peningkatan (88%→99% Durayhim) dan bukti tulisan anak lebih sulit.
  4. Rekomendasi TL + sambung oleh penulisnya sendiri = legitimasi gap skripsi.

### P10. Balaha et al. 2020/2021 — *A new Arabic handwritten character recognition deep learning system (AHCR-DLS)*
- **Identitas:** Hossam Magdy Balaha, Hesham Arafat Ali, Mohamed Saraya (Mansoura Univ.), Mahmoud Badawy. *Neural Computing and Applications*. DOI: 10.1007/s00521-020-05397-2. (Nama file `balaha2020.pdf`.)
- **Masalah/objek:** sistem AHCR lengkap + **dataset baru HMBD**; karakter Arab **isolated dalam 4 posisi + digit = 115 kelas**.
- **Dataset:** HMBD — 58.000→**54.115 citra bersih, 125 relawan usia 9–82**; + CMATERDB 3.3.1, AIA9k, AHCD; augmentasi hingga rasio 1:16 (865.840).
- **Metode:** 2 CNN manual (HMB1 14-conv, HMB2 6-conv); grid **optimizer × weight-initializer** (Adam/AdaDelta/AdaMax/AdaGrad/SGD × He/Glorot/LeCun); CE loss; augmentasi rotasi 15°, geser 0,1, shear 0,2, zoom 0,2; Keras/Colab.
- **Hasil:** HMBD 90,7% → **98,4% dengan augmentasi 1:16** (gap train–test turun 8,5%→1,5%); CMATER **100%**; AIA9k 99,0%; AHCD cross-validation 97,3% (vs kontrol 94,9%). Arsitektur SOTA lama (El-Sawy) **gagal generalisasi ke HMBD (maks 47,7%)**.
- **Keterbatasan:** isolated; tanpa sequence/CTC/TL; test split hanya 5%; inkonsistensi epoch internal (50 vs 64).
- **Ringkasan inti:**
  1. **Bukti kuantitatif terkuat efek augmentasi** (90,7→98,4%) — justifikasi pipeline augmentasi dataset canvas kecil.
  2. Panduan hyperparameter: **He Uniform + AdaDelta** konsisten baik.
  3. Gagalnya arsitektur lama di data baru (47,7%) = argumen pentingnya dataset representatif (analogi data canvas Anda).
  4. Cakupan 115 bentuk posisi mendukung desain label berbasis bentuk.

### P11. Ahmed et al. 2021 — *Novel Deep CNN-Based Contextual Recognition of Arabic Handwritten Scripts*
- **Identitas:** Rami Ahmed, Mandar Gogate, Ahsen Tahir, Kia Dashtipour, dkk. (Sudan Univ. of Science & Technology / Edinburgh Napier). *Entropy* 23(3):340. DOI: 10.3390/e23030340.
- **Masalah/objek:** satu model generalis untuk **digit, karakter, dan kata Arab** (unit terisolasi; kata = klasifikasi holistik 40 kelas nama); narasi tantangan kursivitas/ligatur/diakritik lengkap.
- **Dataset:** MADBase (70.000 digit), CMATERDB 3.3.1 (3.000), HACDB v2 (6.600, 66 bentuk), SUST-ALT Digits/Characters(34)/Names(40); resize 128×128; + MNIST.
- **Metode:** DCNN 5 blok (conv 3×3 + BN + maxpool 3×3 + dropout 10%; FC 1024 + dropout 0,5; Softmax; **RMSprop**, 200 epoch, batch 128, ReduceLROnPlateau); pembanding TL: VGGNet-19 & MobileNet beku.
- **Hasil:** akurasi uji **99,72–99,95%** di 6 dataset Arab + MNIST 99,94%; **DCNN custom > VGG-19 > MobileNet** (MobileNet presisi anjlok, mis. SUST-ALT Characters 0,1456).
- **Keterbatasan:** tanpa RNN/CTC — kata dikenali holistik (bukan transliterasi urutan); dataset kecil rawan overfit; TL justru kalah; beberapa inkonsistensi angka internal.
- **Ringkasan inti:**
  1. Narasi tantangan skrip Arab (kursif, ligatur, titik, diakritik) paling terstruktur — bahan latar belakang.
  2. Sekali lagi bukti **backbone ImageNet beku bisa kalah dari CNN custom** pada tulisan tangan — antisipasi pertanyaan penguji tentang klaim TL.
  3. Protokol augmentasi + ReduceLROnPlateau + grid jumlah blok layak direplikasi.
  4. Bukan pembanding metode sekuensial.

### P12. Saini et al. 2024 — *Handwritten English Script Recognition System Using CNN and LSTM*
- **Identitas:** Madan Lal Saini, Dayal Chandra Sati, Rahul Sai Telikicharla, Mahadev (Chandigarh Univ.). **IEEE InC4 2024**. DOI: 10.1109/InC460750.2024.10649099.
- **Masalah/objek:** pengenalan **kata tulisan tangan sambung bahasa Inggris** end-to-end tanpa segmentasi manual.
- **Dataset:** IAM via Kaggle — 97.412 record (87.671 train / 9.741 test).
- **Metode:** **CNN 11 conv + 4 maxpool + BN + dropout 0,2 → BiLSTM 5 layer → CTC loss + CTC decoder (word beam search)**; 26.907.008 parameter; 66 epoch × 1.258 batch; Flask web interface.
- **Hasil:** **CER validasi 8,6547%**; tanpa tabel perbandingan baseline.
- **Keterbatasan:** laporan hasil sangat tipis (tanpa confusion matrix/WER/benchmark); bahasa Latin tanpa varian bentuk posisional; tanpa transfer learning; inkonsistensi CPU/GPU.
- **Ringkasan inti:**
  1. **Blueprint arsitektur paling identik dengan skripsi** (CNN→BiLSTM→CTC) + bukti kelayakan training 26,9 jt parameter.
  2. Argumen pemakaian CTC karena kursif sukar disegmentasi — dapat dipindahkan utuh ke hijaiyah sambung.
  3. Format pelaporan CER sebagai metrik utama.
  4. Kelemahan pelaporannya (tanpa baseline) = contoh yang harus dihindari skripsi.

### P13. Lamtougui et al. 2024 — *Improving Arabic handwritten text recognition through transfer learning with CNN-based models*
- **Identitas:** Hicham Lamtougui, Hicham El Moubtahij, Hassan Fouadi, Khalid Satori (SMBU Fez / Ibn Zohr). *BEEI* 13(6):4294–4305. DOI: 10.11591/eei.v13i6.8178. (PDF hasil scan; dibaca visual penuh.)
- **Masalah/objek:** **kata tulisan tangan Arab kursif** (IFN/ENIT, nama kota Tunisia) dengan data terbatas; membandingkan 4 backbone ImageNet + **partial fine-tuning**.
- **Dataset:** IFN/ENIT — **32.492 kata / 257.336 karakter**, set A–E; split 60:20:20.
- **Metode:** VGG16/ResNet50/AlexNet/InceptionV3; freeze layer bawah, fine-tune 4–5 blok atas; head FC 1.024 ReLU dropout 0,4; **lr 0,0001, 20 epoch, batch 32, RMSprop, CategoricalCrossentropy**; augmentasi per model; input ±224×224 grayscale; TensorFlow.
- **Hasil:** **VGG16 94,73%** (P 94,83/R 94,15/F1 92,40) > ResNet50 93,88% > InceptionV3 92,87% > AlexNet 92,70%. Tabel 7 merangkum SOTA IFN/ENIT: BLSTM-CTC-WBS (Eltay 2020) 93,57%; CNN-BLSTM-CTC (Lamtougui 2022) 92,11%.
- **Keterbatasan:** klasifikasi **kata utuh sebagai satu label** (bukan urutan huruf) — tanpa LSTM/CTC/CER; generalisasi antar-dataset belum diuji; inkonsistensi optimizer/loss antar-bagian paper.
- **Ringkasan inti:**
  1. Bukti langsung **TL + partial fine-tuning efektif untuk Arab kursif ber-data terbatas** — justifikasi utama komponen TL skripsi.
  2. Resep hiperparameter fine-tuning siap pakai (lr 1e-4, 20 epoch, batch 32, freeze bawah).
  3. Tabel 7 = **peta pembanding metode sekuensial di IFN/ENIT** (BLSTM-CTC 93,57%) untuk Bab 2/4.
  4. Paper penulis yang sama versi 2022 memakai CNN-BLSTM-CTC (92,11%) — kandidat literatur wajib dicari berikutnya.

### P14. Jbrail & Tenekeci 2022 — *Character Recognition of Arabic Handwritten Characters Using Deep Learning*
- **Identitas:** Mohammed W. Jbrail, Mehmet Emin Tenekeci (Harran Univ.). *JOSSE* 2(1):32–40. DOI: 10.53898/josse2022213.
- **Masalah/objek:** karakter Arab isolated tulisan anak; eksplorasi kedalaman model (3/9/13 hidden layer).
- **Dataset:** **diklaim Hijja (47.434) tetapi data terolah = 13.440 train / 3.360 test (16.800) — identik AHCD** → indikasi kuat salah dataset; output layer tertulis 29 vs teks "28 kelas".
- **Metode:** CNN sederhana (Conv 30 filter → pool → Conv 15 → flatten → dropout 0,2 → dense 128-50-29 Softmax); Adam; 100 epoch; normalisasi 0–1.
- **Hasil:** Model C dilaporkan **99,3%** (A 81%, B 85%, D 13-layer 93%) — hanya metrik accuracy.
- **Keterbatasan:** **reliabilitas rendah** (kontradiksi dataset, tanpa P/R/F1/CM, sitasi banyak salah tempel, tanpa validasi terpisah).
- **Ringkasan inti:**
  1. Menunjukkan kedalaman tidak monoton (9 layer > 13 layer) — indikasi overfitting data kecil.
  2. Angka 99,3% **tidak aman dikutip tanpa catatan**; gunakan hanya jika perlu contoh "studi CNN klasik".
  3. Tidak ada TL/LSTM/multi-label/sambung.
  4. Pelajaran metodologis: pentingnya verifikasi dataset — relevan untuk audit internal Anda sendiri.

### P15. Masruroh et al. 2023 — *Deep CNN Transfer Learning Comparison on Arabic Handwriting Recognition System*
- **Identitas:** Siti Ummi Masruroh, M. Fikri Syahid, Firman Munthaha, Asep Taufik Muharram, Rizka Amalia Putri (UIN Syarif Hidayatullah Jakarta). **JOIV** 7(2):330–337. (File bernama acak `paper_ff78...pdf`; **DOI tidak ditemukan dalam dokumen**.)
- **Masalah/objek:** **huruf hijaiyah/Arab isolated** tulisan anak (Hijja) & dewasa (AHCD); grid komparasi 6 backbone TL × 2 optimizer × 3 lr.
- **Dataset:** Hijja 47.434 (28.460 train/9.488 val); AHCD 16.800 (10.080/3.360); split 60:20:20.
- **Metode:** ResNet50, DenseNet, VGG16, VGG19, InceptionV3, MobileNet (bobot ImageNet) + head FC kustom, dropout 50%; augmentasi shift/shear/zoom 0,2; **2 tahap: 20 epoch freeze + 80 epoch fine-tune**; Adam/SGD × lr {1e-3, 1e-4, 1e-5} = 36 konfigurasi.
- **Hasil:** terbaik **VGG16 + Adam lr 1e-4: AHCD test 96%, Hijja test 87%**. Adam > SGD semua backbone; lr 1e-3 menyebabkan divergensi (beberapa 0%); **MobileNet terlemah (Hijja 75%)**; InceptionV3/ResNet50 83% Hijja; DenseNet 77%.
- **Keterbatasan:** hanya accuracy (tanpa P/R/F1/CM); tanpa multi-run/CI; satu arsitektur head untuk semua backbone (diakui penulis berpotensi bias); isolated, tanpa LSTM/CTC.
- **Ringkasan inti:**
  1. **Grid 36 konfigurasi backbone×optimizer×lr pada huruf hijaiyah** — sumber justifikasi Bab 3 paling praktis di koleksi ini.
  2. Temuan kontras dengan asumsi umum: di sini **VGG16 menang, MobileNet kalah** (vs El Khayati yang model ringan menang) → perbedaan hasil antar-paper nyata dan layak didiskusikan.
  3. Konsisten dengan literatur: lr fine-tuning kecil (1e-4) wajib; lr besar merusak.
  4. Konteks Indonesia + istilah "hijaiyah letters" → mudah ditempatkan di related work lokal.

### P16. Alwagdani & Jaha 2023 — *Deep Learning-Based Child Handwritten Arabic Character Recognition and Handwriting Discrimination*
- **Identitas:** Maram Saleh Alwagdani, Emad Sami Jaha (KAU Jeddah). *Sensors* 23(15):6774. DOI: 10.3390/s23156774.
- **Masalah/objek:** pengenalan **huruf Arab isolated anak** + efek sumber data latih + diskriminasi penulis anak vs dewasa.
- **Dataset:** Hijja — **hanya subset disconnected 12.355/47.434 (≈26%)** dipakai; subset tersambung (initial/medial/final) **eksplisit tidak dipakai**; AHCD 16.800; gabungan 26.880 train/5.831 test.
- **Metode:** CNN custom 10 layer (conv 16/32/64/128; **Nadam, He Normal**, batch 80, 100 epoch, ReduceLROnPlateau); preprocessing: grayscale→**invert**→kontras→brightness +2%→**threshold <90**→crop/center 32×32; fusi fitur CNN+HOG(324-D)+12 fitur statistik; pembanding Softmax/SVM/KNN/RF grid search.
- **Hasil:** test Hijja: train Hijja-only rata-rata **91,78%** (terbaik SVM 91,95%); **AHCD-only saat diuji Hijja anjlok ke 79,31%**; **gabungan tertinggi 92,78%** (Softmax/SVM 92,96%). Writer discrimination dengan fusi fitur: Softmax 93,98%.
- **Keterbatasan:** isolated saja; subset Hijja tidak penuh; tanpa TL; perbedaan antar-classifier tipis tanpa uji signifikansi; galat kecil angka kesimpulan (89,28% vs 89,56%).
- **Ringkasan inti:**
  1. **Temuan paling aplikatif: mencampur data dewasa berkualitas ke data anak menaikkan pengenalan tulisan anak (79→93%)** → justifikasi strategi training gabungan AHCD/Hijja + data canvas Anda.
  2. Dokumentasi struktur Hijja (29 kelas/108 subkelas posisi) dasar argumen label posisional.
  3. Pipeline preprocessing lengkap (invert, threshold 90, crop-center) — referensi teknis langsung.
  4. **Future work eksplisit: huruf tersambung anak** → legitimasi gap.

### File non-jurnal
- **Iqra-3-Belajar-Baca-Quran.pdf** — bahan ajar (32 hlm, pindai tanpa lapisan teks; tidak dapat ditranskripsi otomatis). Bukan literatur ilmiah; **peran: sumber inventaris kata sambung dataset** — tetap perlu ditranskripsi manual (belum checklist selesai di catatan Anda).
- **ketentuan penulisan skripsi uisi.pdf** — panduan penulisan Informatika UISI (25 hlm, terbaca). Bukan literatur; peran: format Bab 1–5.
- **image.png** — contoh tulisan sambung Arab model putus-putus ("محمد"); kemungkinan referensi gaya goresan canvas.
- **Catatan sendiri (.md/.docx)** — docx terverifikasi duplikat md; `literatur_gap_skripsi.md` sudah usir/bermasalah akurasinya (lihat peringatan atas).

---

## TAHAP 3 — EKSTRAKSI INFORMASI KELOMPOK

**1. Teori**
- Multi-label formal (BCE+sigmoid, BR/LP/CC, korelasi label orde-1/2/tinggi, cardinality/density/diversity): P6; ko-okurensi via GCN: P5.
- Segmentasi vs segmentation-free; masalah touching/interleaving & ligatur Arab: P2, P8, P4 (challenges), P11.
- Morfologi Arab 4 bentuk posisi + titik/harakat: P1, P8, P9, P11, P13, P16.
- CTC (blank symbol, pelipatan karakter berulang): P2, P8, P12.

**2. Metode penelitian**
- Komparasi sistematis backbone TL: P13 (4 backbone), P15 (6 backbone × optimizer × lr), P7 (3 strategi TL × 4 backbone).
- Ablation arsitektur (4 varian): P2; grid optimizer×initializer: P10; kedalaman model: P14.
- Efek sumber data latih (anak/dewasa/gabungan): P16.
- UAT pengguna anak pada aplikasi tulis: P1 (Mutqin).

**3. Algoritma/model**
- **CRNN (CNN→BiLSTM→CTC): P2, P8, P12** — tiga-tiganya inti metode skripsi.
- CNN custom: P1, P3, P4, P9, P10, P11, P14, P15, P16. TL CNN: P1, P7, P13, P15. Hybrid CNN+ML: P4. GCN multi-label: P5.

**4. Dataset**
- **Hijja/Hijja2 (47.434; 29 kelas; 108 bentuk posisi; 591 anak 7–12)**: P1, P3, P7, P9 (asal), P14, P15, P16 — dataset publik utama yang cocok domain Anda.
- **AHCD (16.800; 28 kelas; 60 dewasa)**: P1, P3, P4, P7, P9, P10, P15, P16.
- **IFN/ENIT (32.492 kata kursif, 937 nama, 400+ penulis)**: P8, P13, P7 (word-level).
- **KHATT (13.435 baris Arab)**: P2 (juga P8 untuk P-KHATT cetak).
- HMBD (54.115; 115 kelas): P10. IFHCDB: P7. Lainnya (MADBase, CMATERDB, HACDB, SUST-ALT, APTI, P-KHATT, IAM, MNIST, MS-COCO/VOC).

**5. Preprocessing**
- Grayscale, resize 32×32/64-tinggi/128/224: beragam; invert + threshold + crop-center: P16; normalisasi 0–1: P3, P14; biner + tinggi 64 px: P2.
- **Data filling** menyamakan panjang label: P2.

**6. Ekstraksi fitur**
- CNN sebagai feature extractor: P4, P7 (TFE), P11 (VGG19/MobileNet beku); HOG + 12 statistik + fusi: P16; fitur manual statistik/kelengkungan untuk klasifier ML: P4.

**7. Training**
- Adam lr 1e-3 (scratch): P3, P9; Adam lr 1e-4 fine-tune: P13, P15; RMSprop: P1, P11, P13; Nadam: P16; SGD: P5, P7, P8, P15; **Cosine annealing + Hyperband + 5-fold CV: P7**; freeze-then-finetune 2 tahap: P15; partial fine-tuning: P13.
- **Augmentasi**: rotasi/zoom/shift P3; rotasi 15°/shear/geser/zoom 1:16 → +7,7% P10; shift/shear/zoom 0,2 P15; distorsi morfologis 12 varian/citra → konvergensi cepat P8.

**8. Evaluasi**
- Sequence: **CER** (P7 word-level 7,8%; P8 0,01–0,03% cetak, WER 1,09% IFN/ENIT; P12 8,6547%), **CCR** P2.
- Klasifikasi: acc/P/R/F1 per kelas (mayoritas); multi-label: mAP/OF1 (P5), Hamming/ranking loss (P6).
- Kalibrasi & robustness noise (ECE): P7 — jarang dilakukan, layak diadopsi.

**9. Tools/framework**
- TensorFlow/Keras + Google Colab: P3, P4, P8, P10, P13, P16; PyTorch: P5; Flask deploy: P12; OpenCV/MATLAB: P4, P10. (P1, P7, P15: tidak eksplisit.)

**10. Hasil** — lihat tabel Tahap 4.

**11. Keterbatasan berulang** (dengan pendukung)
- Objek isolated, bukan sambung: P1, P3, P4, P7, P9, P10, P11, P14, P15, P16.
- Kata utuh satu label (tanpa dekomposisi huruf): P13, P11 (holistik), P8 (walau CTC).
- Tanpa TL pada model sekuensial: P2, P8, P12. Tanpa sequence model pada TL: P1, P7, P13, P15.
- Laporan lemah/tanpa baseline: P12, P14; inkonsistensi internal: P1 (split), P4 (split & TL), P7 (IFHCDB), P10 (epoch), P13 (loss/optimizer), P14 (dataset), P16 (kesimpulan).
- Tanpa metrik sekuensial: 13 dari 16 paper.

**12. Permasalahan belum terselesaikan (eksplisit di paper)**
- Huruf/kata tersambung hijaiyah: future work P1, P9, P16, P7; Arab masih 58% pada model sekuensial (P2); generalisasi antar-dataset TL Arab belum terbukti (P13); zero-shot/domain adaptasi (P13); kaligrafi & dataset kombinasi (P1).

---

## TAHAP 4 — TABEL PERBANDINGAN

| # | Paper | Thn | Objek | Dataset | Metode/Model | Evaluasi | Hasil Utama | Keterbatasan Kunci | Relevansi |
|---|---|---|---|---|---|---|---|---|---|
| P1 | Durayhim | 2023 | Huruf anak, 108 bentuk posisi | Hijja, AHCD | CNN custom vs VGG16-TL | Acc/P/R/F1 | 99% (29kl), 95% (108kl), 98% AHCD; VGG16 83% | isolated; TL kalah; sambung=FW | ●●● |
| P2 | Ge Peng | 2024 | Baris teks 5 bhs (termasuk Arab) | IAM, CASIA, HIT-MW, DigitalPeter, Rodrigo, KHATT | CNN→BDLSTM→CTC segmentation-free + data filling | CCR, waktu, ukuran | 96,1% IAM; **KHATT 58,0%**; > CRNN | Arab belum tuntas; tanpa TL; CCR tak terdefinisi | ●●● |
| P3 | Rahmatulloh | 2022 | Huruf Hijaiyah tunggal | Hijja2, AHCD | CNN+Adam+augmentasi | Acc/P/R/F1 | 91% Hijja2; 98% AHCD | isolated; novelty tipis; tanpa TL/LSTM | ●● |
| P4 | Albattah | 2022 | Digit+huruf isolated | Arabic MNIST, AHCD | CNN standalone/hybrid+SVM dll | Acc/F1 | TL 99,7% digit; karakter 89,9%; CNN+SVM 87,2% | kualitas eksperimen rendah; tanpa kursif | ● |
| P5 | Chen ML-GCN | 2019 | Citra multi-label | COCO, VOC | ResNet101+GCN, BCE | mAP/OF1 | 83,0 COCO; 94,0 VOC | bukan teks; tanpa urutan | ●● |
| P6 | Tarekegn | 2024 | Survey MLC DL | 212 paper | Taksonomi+loss+metrik | — | Kerangka teori multi-label | tanpa CTC/OCR Arab | ●●● (teori) |
| P7 | El Khayati | 2025 | Huruf isolated + word-level | AHCD, Hijja, IFHCDB, IFN/ENIT | 4 mobile-CNN × TWI/TFE/TFS | Acc, ECE, CER | 97% AHCD; 92% Hijja; gain TL ≤1,7%; **word 87,2%/CER 7,8%** | isolated; kursif=FW; preprint | ●●● |
| P8 | ADOCRNet | 2024 | Kata/baris cetak+tulis Arab | P-KHATT, APTI, IFN/ENIT | **CRNN: CNN→BLSTM→CTC** + augmentasi | CER/WER | CER 0,01% cetak; **WER 1,09% IFN/ENIT** | kosakata tertutup; tanpa TL; tabel tak terbaca | ●●● |
| P9 | Altwaijry | 2021 | Huruf anak isolated (asal Hijja) | Hijja, AHCD | CNN 3-conv BN+LRN | Acc/P/R/F1 | 88% Hijja; 97% AHCD | isolated; FW: TL+sambung | ●● |
| P10 | Balaha | 2021 | Karakter 4 posisi+digit | HMBD, CMATER, AIA9k, AHCD | 2 CNN manual + grid hyperparam + augmentasi 1:16 | Acc | 98,4% HMBD; 100% CMATER; 97,3% AHCD | isolated; tanpa TL/sequence | ●● |
| P11 | Ahmed | 2021 | Digit/huruf/kata isolated | 6 DB Arab + MNIST | DCNN 5 blok; baseline VGG19/MobileNet | Acc/P/R/F1 | 99,72–99,95%; custom > TL | holistik kata; tanpa RNN/CTC | ●● |
| P12 | Saini | 2024 | Kata sambung Inggris | IAM (87.671/9.741) | **CNN 11-conv→BiLSTM-5→CTC+WBS**, Flask | **CER** | CER 8,6547% | Latin; tanpa TL; laporan tipis | ●●● (metode) |
| P13 | Lamtougui | 2024 | **Kata Arab kursif** | IFN/ENIT | 4 backbone TL + partial fine-tune | Acc/P/R/F1 | **VGG16 94,73%**; (Tabel 7: BLSTM-CTC 93,57%) | whole-word label; tanpa CTC sendiri | ●●● |
| P14 | Jbrail | 2022 | Huruf anak isolated | "Hijja" (aktual ≈AHCD) | CNN 9-hidden | Acc | 99,3% (dipertanyakan) | reliabilitas rendah | ● |
| P15 | Masruroh | 2023 | Huruf hijaiyah isolated | Hijja, AHCD | 6 backbone TL × Adam/SGD × 3 lr, 2-tahap | Acc | **VGG16+Adam 1e-4: 96% AHCD / 87% Hijja**; MobileNet 75% | isolated; tanpa sequence | ●●● (TL) |
| P16 | Alwagdani | 2023 | Huruf anak isolated (subset) | Hijja disconnected, AHCD | CNN 10-layer + fusi HOG/statistik; 4 klasifier | Acc/P/R/F1 | gabungan train 92,78%; dewasa-only 79,31% | 26% Hijja; FW: sambung | ●● |

**Pola yang terlihat:** (1) terjadi migrasi jelas isolated→kata→baris seiring kompleksitas metode (softmax → whole-word TL → CRNN+CTC); (2) **hanya paper keluarga CRNN (P2, P8, P12) yang memakai LSTM/CTC, dan tidak satu pun menggabungkannya dengan transfer learning**; (3) sebaliknya, semua paper TL (P1, P7, P13, P15) berhenti di klasifikasi tunggal/kata-utuh; (4) hasil Arab konsisten di bawah Latin/Mandarin pada model sekuensial (58% vs 96% di P2) → skrip Arab kursif adalah frontier yang belum tuntas; (5) kualitas pelaporan berbanding terbalik dengan relevansi: paper paling relevan (P12, P14) justru paling lemah pelaporannya → skripsi Anda harus mengisi ceruk "CRNN+TL pada hijaiyah sambung **dengan evaluasi sekuensial yang ketat**".

---

## TAHAP 5 — IDENTIFIKASI RESEARCH GAP

**Research Gap 1 — Belum ada model sekuensial untuk gambar huruf Hijaiyah sambung pendek (2–3 huruf) dengan pelabelan urutan**
- Temuan terdahulu: paper Arab berhenti di (a) huruf isolated (P1, P3, P4, P7, P9, P10, P11, P14, P15, P16), (b) kata utuh satu label (P13; P11 holistik), atau (c) baris teks multi-bahasa dengan Arab tetap buruk (P2: 58,02%).
- Paper pendukung: P1, P9, P16 (future work eksplisit "connected letters/words"); P7 (kursif = future work); P2; P4 (challenges section).
- Kekurangan: tidak ada yang memodelkan citra berisi 2–3 huruf sambung sebagai **urutan label per posisi** [H1,H2,H3].
- Peluang: dataset canvas Iqro 3 + CRNN multi-output; posisi sebagai slot terarah (kanan→kiri).
- Keyakinan: **Tinggi** (dalam koleksi ini). *Catatan: klaim "belum ada di dunia" perlu konfirmasi pencarian lanjutan sebelum ditulis di proposal.*

**Research Gap 2 — Tidak ada integrasi Transfer Learning + arsitektur sekuensial (CNN-LSTM/CTC) pada tulisan tangan Arab/Hijaiyah**
- Temuan: TL terbukti membantu Arab (P13: 94,73%; P15: 96%/87%) tapi tanpa LSTM/CTC; CRNN terbukti untuk sambung (P2, P8, P12) tapi semuanya from-scratch tanpa TL.
- Paper pendukung: P1, P7, P13, P15 vs P2, P8, P12 (matriks Tahap 4 kolom metode).
- Peluang: backbone pre-trained (ImageNet atau **pre-train domain Hijja2**) → BiLSTM → CTC; uji apakah TL menutupi defisit data canvas kecil.
- Keyakinan: **Tinggi**.

**Research Gap 3 — Transfer learning ImageNet lemah untuk tulisan tangan Arab → perlunya pre-training domain-specific pada model sekuensial**
- Temuan: gain TL ImageNet hanya +0,4–1,7% (P7); TFE beku kolaps 0,26–0,54 (P7); VGG-16 kalah dari CNN kecil pada 32×32 (P1); DCNN custom > VGG19/MobileNet (P11); tetapi P15 menemukan VGG16 fine-tune terbaik — **hasil antar-paper bertentangan**.
- Paper pendukung: P1, P7, P11, P15.
- Kekurangan: belum ada studi strategi pre-training (ImageNet vs Hijja2 vs gabungan) khusus untuk CRNN Arab.
- Peluang: eksperimen ablation tiga mode: scratch vs ImageNet-TL vs Hijja2-pretrain pada CNN-LSTM Anda — sekaligus menjawab inkonsistensi literatur.
- Keyakinan: **Sedang–Tinggi** (gap nyata; tetapi arah "TL selalu membantu" tidak boleh diklaim mentah-mentah karena P1/P11 membantahnya).

**Research Gap 4 — Media input canvas digital dan konteks kurikulum Iqro tidak ada di literatur**
- Temuan: seluruh dataset Arab berasal dari pindaian kertas 300 dpi (Hijja, AHCD, HMBD, IFN/ENIT, KHATT); satu-satunya preseden perangkat tulis digital adalah aplikasi tablet Mutqin (P1) — tetapi modelnya tetap dilatih pada Hijja hasil pindai, bukan data papan tulis.
- Paper pendukung: inventaris dataset semua paper; P1.
- Kekurangan: karakteristik goresan canvas (ketebalan konstan, anti-aliasing, resolusi layar) belum terwakili dataset publik.
- Peluang: kontribusi **dataset baru** citra canvas kata sambung Iqro 3 + analisis domain gap canvas-vs-pindai.
- Keyakinan: **Sedang** (benar untuk koleksi ini; perlu cek literatur ed-tech/Iqro terpisah — lihat Tahap 6).

**Research Gap 5 — Evaluasi sekuensial (sequence accuracy/CER) nyaris tidak dipakai pada ranah Hijaiyah**
- Temuan: CER hanya dilaporkan P12 (Inggris), P8 (Arab cetak + IFN/ENIT), P7 (word-level Arab 7,8–8,2%); 13/16 paper hanya accuracy klasifikasi.
- Paper pendukung: seluruhnya (kolom "Evaluasi" Tahap 4).
- Kekurangan: tidak ada angka pembanding sequence accuracy untuk kata pendek 2–3 huruf Arab — publikasi Anda justru menetapkan protokolnya.
- Peluang: definisikan exact-match + per-position accuracy + CER sebagai metrik standar tugas ini.
- Keyakinan: **Tinggi**.

**Research Gap 6 — Inkonsistensi hasil antar-paper pada dataset yang sama (masalah reproducible)**
- Temuan: Hijja dilaporkan 88% (P9), 99% (P1), 92% (P7), 91% (P3), 87% (P15), 99,3% (P14, diragukan), 92,96% (P16) — karena perbedaan kelas (29 vs 108 vs 28 gabungan), split, input size, dan validasi.
- Paper pendukung: P1, P3, P7, P9, P14, P15, P16.
- Peluang: protokol evaluasi terstandar (split per-penulis, laporan P/R/F1 per kelas + CI) untuk skripsi Anda; sekaligus argumen mengapa angka Anda tidak bisa langsung dibandingkan mentah dengan paper lama.
- Keyakinan: **Tinggi**.

**Perbaikan terhadap gap di `literatur_gap_skripsi.md` lama:** gap lama nomor 2 ("belum ada yang memecah kata menjadi urutan huruf; paper lain whole-word") **tidak akurat** — P2, P8, P12 sudah melakukan dekomposisi karakter via CTC. Gap yang benar adalah kombinasi *objek hijaiyah + panjang pendek 2–3 huruf + konteks Iqro/canvas + TL + sekuensial* (Gap 1–4 di atas), bukan "orang lain tidak mengeluarkan urutan huruf". Perbaikan ini penting agar klaim kebaruan tidak dipatahkan penguji yang membaca ADOCRNet/Ge Peng.

---

## TAHAP 6 — CEK KEKURANGAN LITERATUR

| Informasi/Literatur yang Masih Kurang | Mengapa Dibutuhkan | Paper yang Sudah Ada | Jenis Paper yang Perlu Dicari |
|---|---|---|---|
| Paper seminal **CRNN** (Shi et al. 2016, "An End-to-End Trainable Neural Network for Image-based Sequence Recognition") | Rujukan kanonik arsitektur metode utama; dikutip P2 tapi tidak dimiliki | P2, P8, P12 (pemakai, bukan pencipta) | Paper asli CRNN (IEEE TPAMI) |
| Paper seminal **CTC** (Graves et al. 2006) & **BiLSTM** (Graves & Schmidhuber 2005) | Landasan teori decoding sekuensial di Bab 2 | Hanya disebut di P2/P8 | Paper asli Neural Computation/ICML |
| **Kompetitor terdekat**: Noubigh et al. (CNN-BLSTM-CTC KHATT), Eltay et al. 2020 (BLSTM-CTC-WBS 93,57%), Lamtougui et al. 2022 (CNN-BLSTM-CTC 92,11%) | Mereka sudah menggabungkan komponen Anda di Arab kata; wajib dibedakan posisinya | Hanya angka sitasi di P13 Tabel 7 & P8 | Paper-paper tersebut (Arab word/line recognition sekuensial) |
| Dataset asli **IFN/ENIT** (Reboud & Keller 2004) dan **KHATT** (Mahmoud et al. 2012) | Sitasi dataset yang dipakai pembanding | P2, P7, P8, P13 memakainya | Paper originasi dataset |
| **Hijaiyah/Arab sambung khusus konteks Indonesia/Iqro** | Dosen minta ≥15 paper fokus sambung; saat ini paper Arab kursif murni hanya P2 (line), P8, P13 (kata), P7 (word pipeline) | 4 dari 16 | Studi OCR hijaiyah bersambung / recognition tulisan Iqro (prosiding Indonesia + jurnal) |
| **Penggunaan canvas digital** untuk pengumpulan data tulisan Arab/hijaiyah | Mendukung Gap 4; saat ini nol bukti pembanding → klaim rapuh | Nol (terdekat: P1 Mutqin) | Paper on-line/off-line handwriting dari tablet/stylus/e-learning |
| Paper **Transformer/ViT/PatchTST untuk Arabic HTR 2024–2026** | Dosen menyebut ViT sebagai alternatif; koleksi berhenti di CNN/RNN; perlu pembanding SOTA terbaru | Nol | Surveys + eksperimen ViT/ABXR-style AHT 2024+ |
| Paper **transfer learning untuk sequence model OCR** (mis. TL-CRNN) | Satu-satunya celah metode Anda (Gap 2) — harus tahu apakah sudah ada yang mencoba | Nol | "transfer learning CRNN handwriting/OCR" |
| Rujukan teori **Urdu/Arab children handwriting** (Alrobah & Albahli 2021; Alyahya; Boufenar) | Muncul berulang sebagai pembanding di tabel P1/P4/P7/P16 tapi tidak dimiliki | Angka sitasi sekunder saja | Paper-paper tersebut (untuk verifikasi angka, bukan kutip但从) |
| Paper **generasi data sintetis tulisan tangan** (menyusun kata dari karakter Hijja2) | Rencana augmentasi sintetis Anda belum punya dasar metodologi | Nol (konsep data filling P2 paling dekat) | Synthetic handwriting generation (mis. giaou et al. / GAN-based) |
| Paper **usability/UAT aplikasi belajar menulis anak** | P1 sudah punya (Mutqin UAT) tetapi 1 sumber saja lemah untuk justifikasi desain | P1 | Paper HCI/ed-tech evaluasi aplikasi literasi anak |

**Status target dosen (≥15 paper fokus hijaiyah/Arab SAMBUNG):** koleksi saat ini baru memenuhi **±5–6 paper sambung/kursif** (P2, P7 word-level, P8, P12 [bahasa lain], P13, P1 sebagian [108 bentuk posisi]). **Target belum tercapai** — perlu 9–10 paper sambung tambahan seperti di tabel atas.

---

## TAHAP 7 — KLASIFIKASI BERDASARKAN PERAN

**A. Sangat relevan**
| Paper | Alasan |
|---|---|
| P12 Saini 2024 | Satu-satunya yang mereplikasi persis pipeline Anda (CNN→BiLSTM→CTC) untuk sambung + CER; minus: Latin |
| P2 Ge Peng 2024 | Dasar segmentation-free + bukti Arab 58% (gap); constraint arsitektur & data filling |
| P8 ADOCRNet 2024 | CRNN Arab terlengkap (CTC blank/merge, CER/WER, augmentasi morfologis, protokol IFN/ENIT) |
| P13 Lamtougui 2024 | TL + partial fine-tuning pada Arab kursif; tabel SOTA sekuensial IFN/ENIT |
| P15 Masruroh 2023 | Grid pemilihan backbone/optimizer/lr pada huruf hijaiyah (Bab 3) |
| P7 El Khayati 2025 | Bukti batas TL ImageNet + baseline word-level CER + resep Hyperband/CV |
| P1 Durayhim 2023 | Hijja 108 bentuk posisi; peringatan TL; preseden aplikasi tulis anak |
| P6 Tarekegn 2024 | Fondasi teori multi-label Bab 2 (loss, korelasi label, metrik, deskriptor dataset) |

**B. Relevan sebagai pendukung**
| Paper | Alasan |
|---|---|
| P9 Altwaijry 2021 | Paper asal dataset Hijja; baseline 88%; rekomendasi TL+sambung |
| P16 Alwagdani 2023 | Strategi data latih anak+dewasa (79→93%); pipeline preprocessing konkret |
| P10 Balaha 2021 | Kuantifikasi augmentasi (90,7→98,4%) & panduan initializer/optimizer |
| P11 Ahmed 2021 | Narasi tantangan kursif Arab + bukti anti-tesis TL (custom > pretrained) |
| P3 Rahmatulloh 2022 | Baseline lokal hijaiyah + konteks edukasi Indonesia |
| P5 Chen 2019 | Teori ko-okurensi label & BCE; hanya untuk definisi/analisis label |

**C. Relevan sebagian**
| Paper | Alasan |
|---|---|
| P4 Albattah 2022 | Hanya subbab "Challenges and Open Problems" + peta dataset yang aman dikutip; angka eksperimen di bawah SOTA sendiri, berisiko |
| P14 Jbrail 2022 | Kontradiksi dataset (klaim Hijja, data ≈AHCD) + metrik tunggal; hanya layak sebagai contoh studi dasar dengan catatan |

**D. Kurang relevan (tetap dicatat per instruksi)**
- `ketentuan penulisan skripsi uisi.pdf` — panduan format, bukan literatur riset (peran administratif).
- `Iqra-3-Belajar-Baca-Quran.pdf` — bahan ajar; bukan sitasi ilmiah, tapi **objek wajib analisis manual** untuk inventaris kata.
- `image.png`, file catatan sendiri, `.qoder/settings.local.json` — artefak kerja.
- Di antara jurnal: tidak ada yang 100% tidak relevan; terlemah P14 dan P4 (masuk C).

---

## TAHAP 8 — SUMBER PALING BERGUNA PER KEBUTUHAN

| Kebutuhan | Sumber terbaik | Catatan |
|---|---|---|
| Dasar teori multi-label | P6 (taksonomi+loss+metrik), P5 (BCE, korelasi label) | Jelaskan posisi "multi-label" Anda = multi-output berurutan |
| Dasar teori kursivitas Arab | P4 §Challenges, P11 §intro, P13 §intro | Titik/harakat, 4 bentuk posisi, ligatur lam-alif |
| Arsitektur metode utama | **P8** (CRNN Arab), **P12** (CNN-BiLSTM-CTC + CER), **P2** (varian + constraint) | Butuh tambahan Shi 2016 (belum ada) |
| Transfer learning | P13 (partial fine-tune), P15 (grid 36 konfigurasi), P7 (strategi TWI/TFE/TFS) | Plus counter-evidence P1, P11 |
| Dataset | P9 (asal Hijja), P1 (108 bentuk), P3 (Hijja2+AHCD usage), P16 (subset disconnected) | HMBD (P10) alternatif bila butuh data dewasa+anak campuran |
| Preprocessing | P16 (invert/threshold/crop), P2 (normalisasi tinggi 64 px), P8 (augmentasi morfologis) | |
| Augmentasi | P10 (efek 1:16 terkuantifikasi), P8, P15 | Generasi kata sintetis: BELUM ada sumber (Tahap 6) |
| Training/hiperparameter | P7 (Hyperband, cosine LR, 5-fold, dropout 0,3–0,4), P15 (Adam 1e-4), P10 (He Uniform/AdaDelta) | |
| Evaluasi | CER: P7, P8, P12; multi-label: P5, P6; per-kelas P/R/F1: P1, P3, P16 | |
| Pembanding hasil | P13 Tabel 7 (SOTA IFN/ENIT), P15 Tabel VIII, P16 Tabel 13, P7 Tabel VIII | Hati-hati: kondisi uji tidak identik |
| Research gap | P1/P7/P9/P16 (future work eksplisit), P2 (KHATT 58%) | |
| Implementasi/deploy | P12 (Flask), P1 (aplikasi tablet + UAT), P7 (model <3 MB) | Untuk integrasi dengan gamifikasi Nadhif |

---

## TAHAP 9 — KESIMPULAN LITERATUR

**1. Apa yang sudah diketahui?**
Tulisan tangan Arab/Hijaiyah lebih sulit dari Latin karena 4 bentuk posisi, titik/harakat, dan ligatur wajib (P4, P11, P13). Huruf mirip (dal/ha, 'ayn/ghain, fa/qaf) adalah sumber error dominan bahkan pada isolated (P3, P9). Tulisan anak jauh lebih sulit dari dewasa (Hijja 88 vs AHCD 97; P9, P15, P16). Augmentasi menaikkan akurasi secara terukur (P10: +7,7%; P8: konvergensi 2× lebih cepat). Arsitektur CNN→BiLSTM→CTC segmentation-free adalah state of the practice untuk tulisan sambung (P2, P8, P12).

**2. Apa yang sudah dilakukan penelitian sebelumnya?**
Klasifikasi isolated huruf Arab hingga 98–99% (P1, P10, P15); komparasi backbone TL pada hijaiyah (P13, P15, P7); pengenalan kata kursif whole-word (P13) dan transkripsi baris multi-bahasa (P2, P8); pembangunan dataset anak (Hijja, P9) dan multi-posisi (HMBD, P10); aplikasi edukatif dengan validasi anak (P1); teori multi-label DL (P5, P6).

**3. Apa yang masih menjadi masalah?**
Skrip Arab kursif tetap kasus terburuk model sekuensial (KHATT 58,02% CCR vs 96% Latin di P2); TL ImageNet hampir tidak membantu tulisan Arab (gain ≤1,7%, P7; bahkan kalah dari custom, P1/P11); reproducible rendah — hasil Hijja berbeda 88–99% antar-paper karena protokol tidak seragam.

**4. Apa yang belum banyak diteliti?**
(a) Objek 2–3 huruf sambung per citra dengan output urutan; (b) integrasi TL + CRNN pada Arab; (c) pre-training domain-specific (Hijja2) untuk model sekuensial; (d) data canvas digital (bukan pindaian) dalam konteks kurikulum Iqro; (e) metrik sequence accuracy untuk hijaiyah; (f) generasi kata sambung sintetis.

**5. Apa kelemahan penelitian terdahulu?**
Laporan eksperimen lemah pada paper paling relevan (P12 tanpa baseline; P14 kontradiksi dataset; P4 backbone TL tak disebut); split sering bocor/tidak per-penulis (P13); subset dataset tidak diumumkan (P16 pakai 26% Hijja); metrik tidak sebanding antar-paper (accuracy vs CCR vs CER); banyak inkonsistensi internal (P1, P4, P7, P10, P13, P16).

**6. Apa peluang penelitian yang dapat dilakukan?**
Skripsi Anda berada tepat di irisan tiga gap sekaligus: objek (hijaiyah sambung pendek, belum ada), metode (TL+CRNN, belum ada pada Arab), dan sumber data (canvas Iqro 3, belum ada). Kontribusi terkecil yang tetap sah: dataset canvas + protokol evaluasi sekuensial + ablation strategi pre-training (scratch vs ImageNet vs Hijja2).

**7. Literatur apa yang masih perlu ditambahkan?**
Shi 2016 (CRNN), Graves 2006 (CTC), Graves & Schmidhuber 2005 (BiLSTM), originasi IFN/ENIT & KHATT, Noubigh/Eltay/Lamtougui-2022 (CNN-BLSTM-CTC Arab — kompetitor langsung), hijaiyah-sambung Indonesia (memenuhi target 15), canvas/tablet handwriting collection, ViT/Transformer AHT 2024+, synthetic handwriting generation. (Detail: Tahap 6.)

---

## TAHAP 10 — HASIL AKHIR

### A. Executive Summary (15 poin)
1. Koleksi berisi **16 paper jurnal unik**; semuanya terbaca penuh (kecuali tabel grafis ADOCORNet); tidak ada yang rusak; folder `Sementara` kini kosong (2 duplikat lama sudah dihapus).
2. Matriks lama `literatur_gap_skripsi.md` **tidak dapat dipercaya angkanya** — ≥9 dari 15 baris menyimpang dari isi dokumen; dokumen ini adalah koreksinya.
3. Satu paper terlewat matriks lama dan justru krusial: **ADOCRNet (IEEE Access 2024)** — CRNN Arab CNN→BLSTM→CTC dengan WER 1,09% IFN/ENIT.
4. Tidak ada satu pun paper yang menangani citra **2–3 huruf hijaiyah sambung dengan output urutan karakter** — kebaruan objek Anda aman dalam koleksi ini.
5. **TL dan arsitektur sekuensial tidak pernah digabung** pada tulisan tangan Arab: paper TL (P1, P7, P13, P15) tanpa LSTM/CTC; paper CRNN (P2, P8, P12) tanpa TL — inilah gap metode utama Anda.
6. Transfer learning ImageNet untuk tulisan Arab **terbukti lemah** (gain +0,4–1,7%, P7; VGG16 kalah dari CNN kecil, P1; custom > pretrained, P11) — klaim TL harus dibuktikan dengan baseline, jangan diasumsikan.
7. Arah solusi yang didukung literatur: **pre-training domain-specific pada Hijja2** (47.434 citra, 108 bentuk posisi, P9/P1) sebagai pengganti/pendamping bobot ImageNet.
8. Model sekuensial generik masih gagal di skrip Arab: **KHATT hanya 58,02% CCR** (P2) — argumen terkuat bahwa masalah Anda belum selesai.
9. Preseden arsitektur siap pakai: CNN (tanpa FC)→BiLSTM→CTC dengan constraint output H=1, W≥5×panjang label (P2); 3 blok conv→BLSTM 250→CTC (P8); CNN 11-conv→BiLSTM-5→CTC, CER 8,65% (P12).
10. Bukti empiris strategi data: **mencampur data dewasa (AHCD) ke data anak menaikkan akurasi 79→93%** (P16) dan **augmentasi 1:16 menaikkan 90,7→98,4%** (P10) — dua-duanya langsung relevan untuk dataset canvas kecil.
11. Metrik yang harus dipakai: exact sequence match + per-position accuracy + CER (dipakai P7/P8/P12); Hamming/micro-F1 sebagai pelengkap framing multi-label (P5/P6); laporkan P/R/F1 per kelas (kelemahan umum literatur).
12. Resep hiperparameter paling terdokumentasi: Adam lr 1e-4 untuk fine-tune (P13, P15), dropout 0,3–0,4 (P7), He Uniform/AdaDelta (P10), 2-tahap freeze→fine-tune (P15), Hyperband+5-fold CV bila mampu (P7).
13. Konteks edukasi anak/primer terwakili: Hijja dikumpulkan dari anak 7–12 tahun (P9) dan aplikasi Mutqin tervalidasi UAT anak (P1) — justifikasi pengguna target Iqro 3.
14. Target dosen "≥15 paper huruf sambung" **belum tercapai**: baru ±5–6 paper kursif sejati; sisanya isolated — perlu 9–10 paper tambahan (prioritas di poin F).
15. Risiko akademik terbesar: mengutip angka sekunder tanpa verifikasi (seperti yang terjadi pada matriks lama) dan mengklaim "belum ada yang melakukan X" tanpa penelusuran eksternal (kompetitor langsung: Noubigh, Eltay, Lamtougui 2022 — belum dibaca).

### B. Peta Literatur
```
MASALAH: morfologi posisi (4 bentuk) + ligatur + titik/harakat + variabilitas anak
   │        [P4 §challenges, P9, P11, P13]
TEORI:   multi-label (BCE, korelasi label) [P5,P6]  |  segmentation-free & CTC [P2,P8,P12]
METODE:  isolated-CNN [P1,P3,P9,P10,P14,P15,P16] → whole-word TL [P11,P13] → CRNN+CTC [P2,P8,P12]
   │      TL: ImageNet gain kecil [P7] / kalah dari custom [P1,P11] / menang bila fine-tune [P13,P15]
DATASET: Hijja/Hijja2 (anak,108 bentuk) [P9→P1,P3,P7,P15,P16] · AHCD · IFN/ENIT (kata kursif) [P8,P13]
   · KHATT (baris Arab) [P2] · HMBD [P10]
MODEL:   CNN custom / VGG16 / ResNet50 / MobileNet / (Bi)LSTM+CTC
EVALUASI: accuracy/P-R-F1 (dominan) ← CER/WER hanya [P7,P8,P12] ← sequence-exact-match: KOSONG
HASIL:   isolated ≈88–99% · kata kursif ≈87–95% · baris Arab ≈58% (buruk)
   ▼
GAP: [1] 2–3 huruf sambung berurutan tak ada · [2] TL+CRNN Arab tak ada · [3] pre-train domain
     untuk sekuensial tak diteliti · [4] canvas/kurikulum Iqro tak ada · [5] metrik sekuensial
     hijaiyah kosong · [6] protokol tidak terstandar (Hijja 88→99% antar-paper)
```

### C. Research Gap Utama (didukung dokumen)
1. **Gap 2 (TL + arsitektur sekuensial pada tulisan tangan Arab)** — gap metode paling kuat dan paling mudah dipertahankan (bukti: matriks kolom metode, P1/P7/P13/P15 vs P2/P8/P12).
2. **Gap 1 (objek 2–3 huruf hijaiyah sambung dengan output urutan)** — gap objek; future work eksplisit P1, P7, P9, P16.
3. **Gap 3 (strategi pre-training domain-specific untuk CRNN)** — menjawab inkonsistensi TL (P1 vs P15; P7 vs P13); jadikan ablation inti eksperimen.
4. **Gap 4+5 (dataset canvas Iqro + protokol evaluasi sekuensial)** — gap kontekstual/metodologis; klaimkan sebagai kontribusi dataset & benchmark, bukan klaim kebaruan metode tunggal.

### D. Kekurangan Literatur Saat Ini
- **Literatur Arab kursif sejati baru 4–6 paper** (P2, P7, P8, P13 + sebagian P1); target 15 belum tercapai.
- **Paper seminal metode (CRNN/CTC/BiLSTM) tidak dimiliki** — Bab 2 akan rapuh jika mengutip hanya dari paper sekunder.
- **Kompetitor langsung belum dibaca**: Noubigh (CNN-BLSTM-CTC KHATT), Eltay 2020 (BLSTM-CTC-WBS), Lamtougui 2022 (CNN-BLSTM-CTC) — ketiganya muncul di tabel P13/P8 dan berpotensi menggeser klaim kebaruan Anda bila tidak dibedah.
- **Nol literatur canvas/on-line handwriting Arab dan literatur teknologi Iqro** — Gap 4 saat ini hanya didukung argumen absensi, bukan survei.
- **Nol sumber untuk generasi kata sintetis** (rencana augmentasi dari karakter Hijja2).
- **Nol representasi Transformer/ViT** untuk pembanding SOTA 2024–2026.

### E. Literatur yang Perlu Ditambahkan (karakteristik + alasan)
1. **Shi et al. 2016 (CRNN, TPAMI)** — paper asal arsitektur yang Anda pakai; wajib untuk Bab 2 & 3.
2. **Graves et al. 2006 (CTC) & Graves & Schmidhuber 2005 (BiLSTM)** — dasar matematis decoding sekuensial.
3. **Noubigh et al. (CNN-BLSTM-CTC, KHATT)** dan **Eltay et al. 2020 (BLSTM-CTC-WBS)** dan **Lamtougui et al. 2022 (CNN-BLSTM-CTC, IFN/ENIT 92,11%)** — kompetitor langsung; skripsi harus membedakan diri (objek pendek multi-label + TL + canvas).
4. **Paper originasi IFN/ENIT (Reboud & Keller) & KHATT (Mahmoud et al. 2012)** — sitasi dataset pembanding.
5. **Studi hijaiyah/Arab bersambung konteks Indonesia** (prosiding ICADEIS/SNTI/IEEE Indonesia 2020–2026, objek sambung/kalimat) — memenuhi arahan dosen ≥15 paper sambung dan related work lokal.
6. **Pengumpulan data tulisan tangan lewat tablet/stylus/canvas (on-line→off-line conversion)** — penguat Gap 4; bila ditemukan yang sudah memakai canvas untuk Arab, geser klaim ke arah kurikulum Iqro + multi-label urutan.
7. **TL untuk sequence model OCR / pre-trained CRNN (2022–2026)** — memastikan Gap 2 belum terisi di ranah global.
8. **Synthetic handwriting generation / concatenation augmentation** — metodologi penyusunan kata sambung dari karakter Hijja2.
9. **ViT/Transformer Arabic handwriting recognition terbaru** — pembanding SOTA dan antisipasi pertanyaan penguji "kenapa bukan Transformer".
10. **Survei OCR Arab (mis. survey AHT 2023–2025)** — satu sumber payung untuk related work.

### F. Prioritas Pencarian Literatur
**Sangat diperlukan (sebelum seminar proposal):**
- Shi 2016 CRNN + Graves CTC (fondasi metode).
- Noubigh / Eltay 2020 / Lamtougui 2022 CNN-BLSTM-CTC (kompetitor langsung — menentukan rumusan kebaruan).
- 4–6 paper hijaiyah/Arab SAMBUNG tambahan konteks Indonesia (target dosen).

**Diperlukan (sebelum Bab 2 final):**
- Originasi IFN/ENIT & KHATT; survei AHT terbaru; ViT/Transformer AHT; TL-untuk-sekuensial.

**Pelengkap (sebelum Bab 4/5):**
- Synthetic handwriting generation; studi canvas/tablet handwriting; paper usability/UAT aplikasi literasi anak; paper Alrobah/Boufenar/Alyahya untuk verifikasi silang angka pembanding.

---

*Metode kerja: 16 PDF diekstraksi dan dibaca penuh oleh 4 agen analisis paralel (teks per halaman; Lamtougui via pembacaan visual karena scan; tabel grafis ADOCRNet tidak dapat diekstrak dan angka diambil dari body text). Seluruh angka dalam dokumen ini merujuk teks PDF, bukan matriks lama. Interpretasi penulis ditandai eksplisit; informasi yang tidak ada di dokumen ditandai "Tidak ditemukan dalam dokumen."*
