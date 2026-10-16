# Product Requirements Document

> **Status:** Draft untuk persetujuan pengguna  
> **Tahap:** Analisis dan perencanaan saja  
> **Tanggal analisis:** 25 September 2026  
> **Gate:** Implementasi, perubahan kode, perubahan notebook, perubahan dataset, instalasi dependency, dan pembuatan README final **tidak dimulai** dan tidak boleh dimulai sebelum pengguna menyatakan: **“PRD disetujui, lanjut implementasi.”**

## 1. Project Overview

Proyek adalah penelitian machine learning untuk mengenali urutan huruf Hijaiyah tulisan tangan yang salingambung pada citra hasil ekspor canvas digital. Satu citra berisi satu kata/kombinasi sambung, umumnya 2–3 huruf, dan keluaran harus mempertahankan urutan logis kanan-ke-kiri. Materi acuan kosakata adalah buku Iqro 3.

Arah metode yang tercatat dalam draft dan catatan terbaru adalah CNN-LSTM dengan transfer learning pada komponen CNN. Backbone yang diarahkan adalah MobileNetV4, dengan tahap awal melatih/fine-tuning backbone dan tahap berikutnya melatih CNN-LSTM secara end-to-end. Fokus mahasiswa adalah pipeline dataset dan model; gamifikasi serta integrasi aplikasi ditangani kolaborator.

PRD ini tidak menetapkan bahwa proyek sudah memiliki implementasi final. Pemeriksaan langsung terakhir menunjukkan `code/Pengerjaan/` ada tetapi kosong dan tidak memiliki path yang terlacak di Git. Inventory awal sempat menampilkan README, konfigurasi, source Python, tests, notebook, dataset demo, output, dan checkpoint; evidence tersebut dicatat sebagai snapshot tidak terverifikasi dan harus dikonfirmasi sebelum development.

### 1.1 Sifat proyek

- **Jenis:** penelitian akademik/processing data dan machine learning, bukan produk web utuh.
- **Tugas teknis utama:** sequence recognition pada citra tulisan tangan.
- **Media input:** citra PNG/JPEG hasil ekspor canvas, bukan trajectory/stroke waktu-nyata.
- **Output utama:** urutan karakter Hijaiyah, dengan evaluasi recognition sekuensial.
- **Sistem aplikasi/gamifikasi:** di luar scope penelitian mahasiswa.
- **Status data:** dataset Iqro 3 produksi dan bobot model final belum tersedia di filesystem yang dapat diverifikasi.

## 2. Background

Pembelajaran membaca Al-Qur'an pada tahap dasar menggunakan materi Iqro, termasuk Iqro 3, yang memperkenalkan huruf Hijaiyah dalam bentuk sambung. Pada tahap ini peserta didik tidak lagi menulis atau membaca satu huruf isolated, melainkan beberapa huruf yang membentuk kata. Penilaian manual oleh guru menjadi sulit ketika latihan dilakukan jarak jauh atau membutuhkan umpan balik yang konsisten.

Huruf Arab/Hijaiyah memiliki variasi bentuk initial, medial, final, dan isolated. Titik dapat membedakan huruf yang memiliki kerangka mirip dan dapat mengubah makna kata. Huruf yang bersambung juga sulit dipisahkan karena batas visual antarhuruf tidak selalu jelas. Segmentasi manual berpotensi menghasilkan over-segmentation dan error yang merambat ke karakter berikutnya.

Literatur yang tersedia menunjukkan dua kecenderungan yang berbeda:

1. accurasi tinggi pada klasifikasi huruf isolated, tetapi task tersebut tidak mengevaluasi urutan dan sambungan;
2. CRNN/CNN-RNN-CTC, segmentation-free, dan transfer learning digunakan pada word/line recognition, tetapi kombinasi dataset canvas Iqro 3, urutan 2–3 huruf, dan protokol writer-held-out belum tersedia dalam korpus yang diaudit.

Klaim bahwa transfer learning selalu meningkatkan akurasi tidak dapat diterima sebagai fakta. Beberapa penelitian menunjukkan hasil positif, sedangkan penelitian lain menemukan custom CNN atau model yang dilatih dari awal dapat lebih baik pada domain tertentu. Karena itu, transfer learning harus diuji melalui baseline/ablation.

## 3. Problem Statement

Permasalahan utama adalah membangun model yang dapat membaca satu citra tulisan tangan Hijaiyah sambung dan mengembalikan urutan huruf secara tepat, bukan sekadar himpunan label. Model harus dapat bekerja pada data yang dikumpulkan melalui canvas digital dengan kosakata terbatas pada materi Iqro 3.

Masalah teknis yang harus ditangani:

1. Bentuk huruf berubah menurut posisi dalam kata.
2. Titik, sambungan, dan goresan membuat segmentasi manual tidak stabil.
3. Jumlah data canvas yang dikumpulkan sendiri kemungkinan terbatas.
4. Split citra acak dapat menyebabkan gaya penulis yang sama muncul di train dan test.
5. Istilah “multi-label” pada judul tidak sama dengan task sequence recognition yang membutuhkan urutan dan duplikasi karakter.
6. Metrik accuracy klasifikasi tidak cukup untuk menilai output urutan; diperlukan exact match, character/positional accuracy, dan CER.
7. Literature lama tidak konsisten dalam dataset, split, task, dan metrik sehingga hasil antar-paper tidak dapat dibandingkan langsung.

### 3.1 Rumusan masalah dari draft

- Bagaimana membangun dataset citra tulisan tangan Hijaiyah sambung berbasis canvas digital yang sesuai dengan Iqro 3?
- Bagaimana menerapkan CNN-LSTM dengan transfer learning untuk mengenali urutan huruf tanpa segmentasi manual?
- Bagaimana mengukur kinerja prediksi urutan huruf pada data yang tidak terlihat saat training?

### 3.2 Hipotesis

Hipotesis pada arsip bersifat opsional dan belum dikonfirmasi:

> CNN-LSTM dengan transfer learning pada CNN menghasilkan akurasi urutan lebih baik dibandingkan model CNN tanpa komponen sekuensial dan tanpa transfer learning.

`Conflict detected — requires confirmation.` regarding whether the hypothesis is mandatory, and the exact baseline matrix has not been approved.

## 4. Project Objectives

### 4.1 Objective utama

1. Menyusun dataset citra tulisan tangan Hijaiyah sambung yang berasal dari canvas digital dan mengikuti kosakata Iqro 3.
2. Membangun pipeline preprocessing yang konsisten dan dapat diaudit.
3. Melatih backbone CNN transfer learning terlebih dahulu.
4. Melatih model CNN-LSTM untuk memodelkan urutan huruf.
5. Mengevaluasi prediksi urutan dengan metrik sequence recognition yang sesuai.
6. Menyimpan konfigurasi, checkpoint, history, laporan evaluasi, dan contoh prediksi agar hasil dapat ditelusuri.

### 4.2 Outcome yang diharapkan

- Manifest dataset yang tervalidasi.
- Statistik dataset dan EDA.
- Model stage-1 dan stage-2 yang dapat dilatih ulang.
- Prediksi urutan huruf pada split test.
- Exact match, positional character accuracy, dan CER.
- Analisis error dan perbandingan baseline/ablation.
- Notebook atau Colab yang dapat dijalankan berurutan dari atas ke bawah.
- Dokumentasi yang mencerminkan implementasi aktual.

### 4.3 Objective yang belum ditetapkan

- Target accurasi/CER numerik.
- Jumlah minimum writer dan sampel.
- ~~Varians MobileNetV4 final~~ (resolved: MobileNetV4-Conv-Small)
- ~~Sumber bobot pretrained final~~ (resolved: ImageNet)
- ~~Variabel label untuk panjang 2 dan 3 huruf~~ (resolved: fixed slots maks 3)
- Jumlah layer/arah LSTM dan (loss) final.
- Venue publikasi dan authorship final.

## 5. Scope

### In Scope

- Inventarisasi dan transkripsi kata sambung Iqro 3 maksimal 3 huruf (Section 10.5); 4+ huruf sebagai conditional expansion.
- Perancangan protokol pengumpulan data canvas.
- Definisi metadata, label, QC, dan split participant-wise.
- Import dan validasi dataset citra.
- EDA dan statistik dataset.
- Preprocessing citra offline.
- Eksperimen transfer learning dan baseline yang disetujui.
- Model CNN-LSTM untuk urutan karakter.
- Training, checkpoint, prediksi, evaluasi, dan analisis error.
- Visualisasi loss, metrik, distribusi label, dan contoh error.
- Notebook Jupyter/Google Colab yang reproducible.
- Dokumentasi metodologi, dataset, environment, hasil, dan batasan.
- Pemetaan requirement terhadap sumber dan validasi.

### Out of Scope

- Gamifikasi dan pengembangan antarmuka aplikasi utama.
- Integrasi aplikasi kolaborator.
- Penilaian tajwid, hukum bacaan, atau kualitas estetika tulisan.
- Pengenalan tulisan yang bukan Hijaiyah sambung.
- Pengenalan trajectory/online stroke time-series.
- Pemrosesan dokumen pindaian umum di luar dataset yang menjadi benchmark yang disetujui.
- Microservices, backend produksi, deployment cloud, dan arsitektur aplikasi kompleks.
- Menyelesaikan aplikasi kolaborator tanpa kontrak model dan data yang disetujui.

`Optional / Future Improvement` bukan requirement utama. Contohnya dapat dicantumkan pada Section 25 tanpa mengubah scope.

## 6. Source Documents

### 6.1 Prioritas sumber

1. **Panduan resmi UISI/Departemen Informatika:** `code/file pdf/ketentuan penulisan skripsi uisi.pdf`.
2. **Draft proposal utama terbaru:** `code/DRAFT_PROPOSAL_SKRIPSI.md`.
3. **Catatan teknis terbaru:** `code/skripsi_hijaiyah_canvas_research_notes.md`.
4. **Audit literatur korektif:** `code/ANALISIS_LITERATUR_LENGKAP.md`.
5. **Arsip proposal:** `code/ARSIP_DRAFT_BAB1_PROPOSAL.md`.
6. **Matriks gap lama:** `code/literatur_gap_skripsi.md`; digunakan untuk histori, bukan angka final.
7. **Snapshot notebook/code/config:** tidak dianggap current until file exists again and is re-audited.
8. **Template/old README:** `code/FORMAT_TUGAS_AKHIR.md`, `Skripsi.docx`, dan dokumentasi lama.

### 6.2 Daftar sumber utama

| Source | Peran | Status evidence |
|---|---|---|
| `code/file pdf/ketentuan penulisan skripsi uisi.pdf` | Panduan administratif dan penulisan Departemen Informatika UISI versi 2026 | Sumber normative; agent audit membaca 25 halaman |
| `code/DRAFT_PROPOSAL_SKRIPSI.md` | Working draft penjelasan judul | Latest working source; 91 baris |
| `code/skripsi_hijaiyah_canvas_research_notes.md` | Catatan arahan dosen/kolaborator dan method notes | Dibuat 8 Sep, diperbarui 22 Sep 2026; 435 baris |
| `code/ARSIP_DRAFT_BAB1_PROPOSAL.md` | Draft Bab 1, rumusan masalah, metodologi, dan daftar pustaka | Draf versi 1; 119 baris |
| `code/ANALISIS_LITERATUR_LENGKAP.md` | Audit korektif atas paper dan gap | 584 baris; angka lama dinyatakan perlu dikoreksi |
| `code/literatur_gap_skripsi.md` | Matriks 15 paper lama | Tidak dapat dipercaya untuk angka; 86 baris |
| `code/DAFTAR_JURNAL_REFERENSI.md` | Register judul dan DOI | 20 baris; metadata belum lengkap |
| `code/FORMAT_TUGAS_AKHIR.md` | Template penulisan | 311 baris; contains unrelated examples and placeholder identity |
| `Skripsi.docx` | Template Word lama | Binary audit menunjukkan 21 halaman, 511 body paragraphs, unrelated content and identity contamination |
| `code/file pdf/Iqra-3-Belajar-Baca-Quran.pdf` | Source material for vocabulary | 32-page scan without reliable text layer; manual inventory required |
| `code/image.png` | Possible visual example of connected handwriting | One image only; not a dataset; dimensions are reported inconsistently across audit snapshots |
| `code/file GAP/*.pdf` | Main scholarly and architecture references | 4 PDF files, including MobileNetV4 reference |
| `code/file GAP/Jurnal Pendukung/*.pdf` | Supporting scholarly references | 13 PDF files |
| `code/file GAP/Jurnal Pendukung/Sementara/*` | Temporary drafts, reviews, and 7 PDF files | Includes Word lock file and near-duplicate title documents |
| `code/.opencode/`, `code/.qoder/`, `undefined/.cache/` | Tool configuration/cache | Generated/tooling files; excluded from project requirements |

### 6.3 Inventaris PDF yang diaudit

**`file GAP` langsung:**

- `Optimization_of_Hijaiyah_Letter_Handwriting_Recognition_Model_Based_on_Deep_Learning.pdf`
- `jait.2024.0473.pdf`
- `applsci-13-01692 (1).pdf`
- `MobileNetV4.pdf`

**`Jurnal Pendukung` langsung:**

- `sensors-23-06774-v2.pdf`
- `paper_ff78f31c69aa5719bd0bf18a6927da4a.pdf`
- `JOSSE-vol-2-no1-p3-2022.pdf`
- `Improving Arabic handwritten text recognition through transfer learning with convolutional neural network-based models _ Lamtougui _ Bulletin of Electrical Engineering and Informatics.pdf`
- `Handwritten-English-Script-Recognition-System-Using-CNN-and-LSTM.pdf`
- `entropy-23-00340-v2.pdf`
- `balaha2020.pdf`
- `Arabic handwriting recognition system using convolutional neural.pdf`
- `applsci-12-10155 (1).pdf`
- `ADOCRNet_A_Deep_Learning_OCR_for_Arabic_Documents_Recognition.pdf`
- `2509.05019v1.pdf`
- `2401.16549v3.pdf`
- `1904.03582v1.pdf`

**`Jurnal Pendukung/Sementara`:**

- `icics52457.2021.9464596.pdf`
- `Liberated Arabic Handwritten Text Recognition using Convolutional.pdf`
- `peerj-cs-995.pdf`
- `view.pdf`
- `s11063-024-11544-w.pdf`
- `s11263-026-02773-8.pdf`
- `Penjelasan_Judul_Skripsi.pdf`
- `Penjelasan_Judul_Skripsi.docx`
- `skripsi_hijaiyah_canvas_research_notes.docx`
- `~$njelasan_Judul_Skripsi.docx` (Word lock/temp file)

Current filesystem shows 24 PDF files in these reference folders, while project notes claim 17 PDFs. This is an inventory inconsistency, documented below.

### 6.4 Sumber yang tidak boleh diperlakukan sebagai requirement aktif

- `FORMAT_TUGAS_AKHIR.md` dan `Skripsi.docx` adalah template dengan contoh/topik/identitas lain.
- `literatur_gap_skripsi.md` adalah histori dan memiliki angka yang dikoreksi oleh `ANALISIS_LITERATUR_LENGKAP.md`.
- `.opencode`, `.qoder`, cache, `__pycache__`, `.venv`, and model/tool caches are not project research requirements.
- Historical code snapshot is not current implementation until restored and confirmed.

## 7. Existing Project Analysis

### 7.1 Keputusan yang relatif stabil

Berdasarkan draft terbaru dan research notes:

- Objek: tulisan tangan huruf Hijaiyah sambung.
- Input: satu citra PNG/JPEG hasil ekspor canvas digital.
- Task: outputs an ordered sequence of letters, not only a set of letters.
- Vocabulary: connected words in Iqro 3, limited to a maximum of three letters in the initial scope; 4+ words are added only if the 3-letter stage proves feasible.
- Reading order: right-to-left logical order.
- Model family: CNN-LSTM.
- CNN backbone direction: MobileNetV4.
- Training order: backbone first, then CNN-LSTM end-to-end.
- Manual character segmentation: not part of the intended method.
- Main evaluation: exact match, character/positional accuracy, CER.
- Student scope: dataset pipeline and ML model; gamification is collaborator scope.

### 7.2 Status dokumen

| Area | Status | Evidence |
|---|---|---|
| Research direction | Mostly defined | Latest draft and research notes |
| Formal proposal | Not complete | Latest draft explicitly says proposal/Bab 1 is not yet being written |
| Literature audit | Substantially done, with corrections | `ANALISIS_LITERATUR_LENGKAP.md` |
| Literature target from advisor | Not met | Approximately 4–6 genuinely connected-script papers identified, versus target about 15 |
| Iqro 3 vocabulary inventory | Missing | Checklist remains unchecked |
| Primary dataset | Missing | No current raw/processed production dataset |
| Model specification | Partial | CNN-LSTM and MobileNetV4 direction known; many details missing |
| Code implementation | Current filesystem unavailable/empty | Direct recheck of `code/Pengerjaan`; no Git-tracked paths |
| Notebook execution | Unproven | Initial snapshot had no saved execution output; current notebook path unavailable |
| Production results | Missing | No valid research metrics or final model evidence |

### 7.3 Audit literatur utama

- **P1 Durayhim et al. (2023):** custom CNN dan VGG-16 pada huruf Arab anak; task isolated, split tidak konsisten; useful as child-domain baseline.
- **P2 Ge Peng (2024):** segmentation-free CNN-BDLSTM-CTC pada line recognition; Arabic KHATT remains difficult; does not use transfer learning.
- **P3 Rahmatulloh et al. (2022):** isolated Hijaiyah CNN on Hijja2/AHCD; no sequence model; useful local baseline, not a direct benchmark.
- **P4 Albattah & Albahli (2022):** isolated Arabic character/digit classification; dataset and split inconsistencies; not connected-word recognition.
- **P5 Chen et al. (2019):** general multi-label image recognition with GCN; not handwriting and not ordered; theoretical reference only.
- **P6 Tarekegn et al. (2024):** multi-label learning survey; not an OCR experiment.
- **P7 El Khayati et al. (2025):** lightweight CNN transfer-learning study; mostly isolated characters; preprint and internal inconsistencies.
- **P8 Mosbah et al. (2024):** ADOCRNet CNN-BLSTM-CTC for Arabic documents; useful CRNN reference, not Hijaiyah canvas data.
- **P9 Altwaijry & Al-Turaiki (2021):** source/baseline for Hijja children's isolated character dataset.
- **P10 Balaha et al. (2021):** isolated character dataset/augmentation study; not sequence recognition.
- **P11 Ahmed et al. (2021):** Arabic digit/character/word classification; words are holistic classes, not character sequences.
- **P12 Saini et al. (2024):** English CNN-BiLSTM-CTC; method reference, language mismatch.
- **P13 Lamtougui et al. (2024):** Arabic whole-word transfer learning on IFN/ENIT; not character sequence output.
- **P14 Jbrail & Tenekeci (2022):** dataset/count inconsistencies make reported result unreliable.
- **P15 Masruroh et al. (2023):** isolated character transfer-learning comparison; VGG16, not MobileNetV2, is reported best in the audited source.
- **P16 Alwagdani & Jaha (2023):** child/adult handwriting and isolated character recognition; does not evaluate connected words.

Additional temporary references include Arabic handwriting reviews, isolated-character baselines, and a CRNN/BLSTM-CTC paper. They are useful for context but do not replace missing canonical CRNN/CTC sources or direct Indonesian connected-Hijaiyah studies.

### 7.4 Historical implementation snapshot—not current state

The initial inventory reported the following paths under `code/Pengerjaan`:

- `README.md`
- `pyproject.toml`
- `configs/demo.yaml`
- `configs/production.yaml`
- `src/hijaiyah_ocr/*.py`
- `tests/test_pipeline.py`
- `notebooks/training_hijaiyah_colab.ipynb`
- `data/demo/manifest.jsonl` and 12 demo images
- `outputs/demo/*.json` and `outputs/pretrained_smoke/*.json`
- `checkpoints/demo/*.pt` and `checkpoints/pretrained_smoke/*.pt`

A subsequent direct filesystem check found `code/Pengerjaan/` empty. `git ls-files Pengerjaan/**` returned no paths. Therefore all implementation details in this subsection are **snapshot evidence requiring restoration and re-audit**, not accepted current facts.

The snapshot suggested the following historical design:

- JSONL manifest with `image_path`, `text`, `writer_id`, and `split`.
- Writer-disjoint split validation.
- Grayscale, background estimation, thresholding, crop, aspect-preserving resize, and tensor normalization.
- MobileNetV4 feature extractor.
- Auxiliary 28-class BCE stage and CNN-LSTM CTC stage.
- Greedy CTC decoding.
- Exact match, positional accuracy, and CER.
- CLI commands and a Colab notebook.
- Historical smoke-test outputs and checkpoints.

These items may be useful for recovery planning, but the PRD does not treat them as implemented or validated until the files are restored and inspected again.

## 8. Requirements

### 8.1Functional Requirements

| ID | Requirement | Source | Planned implementation | Status |
|---|---|---|---|---|
| FR-01 | Accept one exported canvas image per sample | Draft, notes, archive | Image loader with documented path contract | Planned; current code unavailable |
| FR-02 | Recognize connected Hijaiyah letters in logical right-to-left order | Draft and notes | Ordered sequence decoder | Planned; encoding requires decision |
| FR-03 | Limit initial vocabulary to connected words in Iqro 3 | Draft, notes, user decision | Approved vocabulary inventory and whitelist limited to ≤3-letter words from Section 10.5 | Confirmed as selected list; 4+ words are conditional expansion |
| FR-04 | Limit initial sequence length to three letters | Notes, archive, user decision | Fixed slots dengan padding/maks 3 slot | **Resolved (user):** fixed slots, maks 3 huruf; 4+ kata hanya setelah scope 3 huruf terbukti feasible |
| FR-05 | Preserve repeated characters | Notes | Encoding fixed slots tidak collapse berulang (tidak seperti CTC blank-collapse) | **Resolved (user):** fixed slots mempertahankan huruf berulang |
| FR-06 | Support optional dotted guide lines in exported images | Latest notes | Preprocessing/data policy for guide presence | **Resolved (user):** guide hanya untuk panduan penulis; dibuang sebelum input model |
| FR-07 | Collect writer/session metadata | Archive and notes | Manifest metadata fields | Planned; exact schema needs approval |
| FR-08 | Perform independent QC of samples | Archive | Two-verifier workflow and rejection log | Planned; workflow not implemented |
| FR-09 | Prevent writer leakage across splits | Archive | Participant-wise split with invariant checks | Planned; ratio unspecified |
| FR-10 | Apply documented image preprocessing | Draft and notes | Grayscale/crop/resize/normalize policy | Planned; parameters unspecified |
| FR-11 | Train/fine-tune CNN backbone before sequence model | Latest notes | Stage-1 training and checkpoint | Planned |
| FR-12 | Train CNN-LSTM after backbone stage | Latest notes | Stage-2 end-to-end training | Planned |
| FR-13 | Use transfer learning on CNN | Draft and notes | Pretrained ImageNet | **Resolved (user):** pretrained ImageNet |
| FR-14 | Avoid manual character segmentation | Archive | Segmentation-free image-to-sequence pipeline | Planned |
| FR-15 | Produce exact ordered predictions | Draft and notes | Decoder and prediction JSON/table | Planned |
| FR-16 | Calculate exact match | Draft, notes, snapshot | Aggregate and per-length metrics | Planned; definition to freeze |
| FR-17 | Calculate positional character accuracy | Draft and notes | Definisi fixed-slot: persentase posisi huruf cocok | **Resolved (user):** sejajar/fixed slots; formal formula dikunci di implementasi |
| FR-18 | Calculate CER | Draft, notes, snapshot | Corpus-level edit distance metric | Planned; aggregation must be documented |
| FR-19 | Compare approved baselines/ablations | Archive | Scratch/transfer and sequence/no-sequence matrix | Decision required |
| FR-20 | Perform qualitative error analysis | Research objective | Error samples, confusion patterns, guide analysis | Planned |
| FR-21 | Save reproducible artifacts | Project engineering need | Config, history, checkpoints, evaluation, predictions | Planned |
| FR-22 | Provide a top-to-bottom notebook execution flow | User requirement and notes | Ordered Colab/Jupyter cells | Planned; current notebook unavailable |
| FR-23 | Keep gamification outside the model project scope | Draft and notes | Model/data handoff only | In scope boundary; collaborator owns UI |

### 8.2Technical Requirements

| ID | Requirement | Source/evidence | Status |
|---|---|---|---|
| TR-01 | Use a reproducible Python ML environment | Initial implementation snapshot and project needs | Candidate; exact versions not specified in current files |
| TR-02 | Support notebook execution in Jupyter/Google Colab | Notes and user requirement | Planned |
| TR-03 | Provide a CNN feature extractor and recurrent sequence model | Draft and notes | Planned; CNN-LSTM required |
| TR-04 | Use MobileNetV4 as the directed backbone | Latest notes and draft | **Resolved (user):** MobileNetV4-Conv-Small |
| TR-05 | Support a two-stage training lifecycle | Latest notes | Planned |
| TR-06 | Store model/config compatibility metadata | Reproducibility recommendation | Planned; snapshot implementation did not fully validate it |
| TR-07 | Use deterministic seeds, environment capture, and run identifiers | Reproducibility requirement | Planned; no current implementation evidence |
| TR-08 | Avoid hidden dependency on absolute Google Drive paths | Notebook portability requirement | Planned; historical snapshot used hardcoded Drive paths |
| TR-09 | Keep architecture simple and notebook-centered | Project complexity constraint | Recommended; no microservices |
| TR-10 | Document hardware/runtime assumptions for Colab | MobileNetV4/Colab execution need | Planned; GPU requirement not specified |

Candidate libraries from the historical snapshot were NumPy, Pillow, PyYAML, timm, PyTorch, torchvision, pytest, Ruff, Mypy, JupyterLab, and nbclient. These are **not re-confirmed current requirements** because the implementation files are currently absent.

### 8.3Data Requirements

| ID | Requirement | Details | Status |
|---|---|---|---|
| DR-01 | Create a primary Canvas Iqro 3 dataset | Source collection, target words, writer/session metadata | Missing |
| DR-02 | Provide a complete word inventory | Complete ≤3-letter inventory per Section 10.5; 4+ as conditional expansion | Provisional — generated from PDF scan and pending manual verification |
| DR-03 | Define label policy | Base letters, hamzah, harakat, punctuation, Latin, and repeated letters | Decision required |
| DR-04 | Store images in a documented format | PNG/JPEG is documented; dimensions, DPI, color profile, and naming need approval | Partial |
| DR-05 | Store machine-readable metadata | At minimum image path, label sequence, writer, and split; recommended additional session/QC fields | Partial; historical schema only |
| DR-06 | Preserve raw data immutability | Raw images must not be overwritten by preprocessing or augmentation | Recommended and necessary for reproducibility |
| DR-07 | Perform QC before training | Reject wrong target, unreadable stroke, and completely disconnected writing | Planned; no final protocol |
| DR-08 | Use participant-wise split | One writer must occur in only one split | Explicit in archive; ratio unspecified |
| DR-09 | Prevent image and writer leakage | Audit duplicate paths/content, writer IDs, and split assignment | Planned; historical implementation had gaps |
| DR-10 | Evaluate secondary datasets separately | Hijja2 is optional pretraining/reference; AHCD/IFN/ENIT/KHATT are literature benchmarks, not automatically project test data | Decision required |
| DR-11 | Define consent, privacy, retention, and data licensing | Required for participant handwriting and Iqro material | Missing |
| DR-12 | Document dataset version and checksum | Needed to identify the exact data used by each run | Missing |

A historical snapshot proposed this manifest minimum:

```text
image_path
text
writer_id
split
sample_id (optional)
```

This is a **technical recommendation based on a non-current snapshot**, not a final approved schema.

### 8.4Analysis Requirements

| ID | Requirement | Method/output | Status |
|---|---|---|---|
| AR-01 | Perform literature review | Verified references, research gap, direct competitors | Partially complete; target about 15 connected papers not met |
| AR-02 | Perform dataset EDA | Counts by writer, word, length, split, missing values, image quality | Missing on real data |
| AR-03 | Define and validate preprocessing | Grayscale, polarity, crop, resize, normalization, guide handling | Partially documented; exact parameters missing |
| AR-04 | Define label encoding | Fixed slots (maks 3) dengan padding/EOS; hasil keputusan user | **Resolved (user)** |
| AR-05 | Establish a CNN baseline | At minimum approved baseline with identical split | Decision required |
| AR-06 | Train stage-1 backbone | Auxiliary/pretext task and checkpoint | Direction decided; loss/head details incomplete |
| AR-07 | Train stage-2 CNN-LSTM | Feature sequence, recurrent layers, transcription head | Direction decided; architecture incomplete |
| AR-08 | Run ablation | Transfer vs scratch; sequence vs no-sequence; ImageNet source | Required by archive; matrix masih `Ambiguous requirement` (D-14) |
| AR-09 | Evaluate sequence output | Exact match, positional accuracy, CER | Planned |
| AR-10 | Perform error analysis | Per-writer, per-word, per-length, visual examples, guide/no-guide | Planned |
| AR-11 | Report uncertainty/limitations | Multiple seeds or confidence interval if feasible | Not specified; feasibility decision needed |
| AR-12 | Avoid unsupported performance claims | No direct comparison across incompatible protocols | Required by literature audit |

### 8.5Output Requirements

| ID | Required output | Format/location recommendation |
|---|---|---|
| OR-01 | Approved Iqro 3 vocabulary inventory | Versioned table/CSV or controlled Markdown |
| OR-02 | Raw image collection | Immutable `data/raw/` with naming convention |
| OR-03 | Validated manifest and QC log | JSONL/CSV plus rejection report |
| OR-04 | EDA report and figures | Markdown/notebook with tables and plots |
| OR-05 | Preprocessing specification | Versioned config and documented transformations |
| OR-06 | Split manifest | Separate assignment with writer-level audit |
| OR-07 | Stage-1 checkpoint and history | `checkpoints/`, `outputs/` with run ID |
| OR-08 | Stage-2 checkpoint and history | `checkpoints/`, `outputs/` with run ID |
| OR-09 | Test evaluation report | JSON plus human-readable table |
| OR-10 | Per-sample predictions | JSONL/CSV with sample ID, reference, prediction, error type |
| OR-11 | Qualitative error figures | PNG/SVG or notebook-generated figures |
| OR-12 | Reproducibility manifest | Environment, config, seed, source revision, data checksum |
| OR-13 | Final thesis/proposal chapters | Academic deliverables defined by UISI |
| OR-14 | README final | Only after implementation, reflecting actual commands and results |

### 8.6Documentation Requirements

- Proposal/Bab 1 containing background, problem, objectives, scope, and method.
- Related works with verified citations and direct competitor search.
- Dataset methodology and data dictionary.
- Notebook execution instructions for local Jupyter and Google Colab.
- Model card or technical description of input, output, preprocessing, and limitations.
- Experiment log containing configuration and result provenance.
- README final with the 16 items in Section 26.
- Thesis chapters, bibliography, appendices, and required administrative forms.
- No README final is created during this planning stage.

### 8.7Validation Requirements

| ID | Validation |
|---|---|
| VR-01 | Every active requirement has a source and implementation step |
| VR-02 | Vocabulary inventory is manually checked against Iqro 3 |
| VR-03 | Every image has an existing file, valid label, writer ID, and split |
| VR-04 | No writer appears in more than one split |
| VR-05 | No duplicate image or undocumented augmentation crosses splits |
| VR-06 | Preprocessing output dimensions, range, polarity, and label alignment are tested |
| VR-07 | Model forward pass produces valid time steps and output classes |
| VR-08 | CTC or other decoder handles repeated letters correctly |
| VR-09 | Checkpoint/config/alphabet compatibility is checked before inference |
| VR-10 | Evaluation uses a held-out test split and reports all primary metrics |
| VR-11 | Ablation results use the same data split and comparable protocol |
| VR-12 | Notebook can be restarted and run top-to-bottom from a clean kernel |
| VR-13 | Saved artifacts can be loaded in a fresh runtime |
| VR-14 | Documentation distinguishes demo results from real-data results |
| VR-15 | Official UISI formatting and submission requirements are checked before final submission |

### 8.8Traceability matrix

| Requirement | Source | Planned implementation step | Expected output | Validation | Status |
|---|---|---|---|---|---|
| Canvas image input | Draft/notes | Step 3–5 | Raw image + manifest | File/schema checks | Planned |
| Iqro 3 vocabulary | Draft/archive | Step 2 | Approved word list | Manual transcription review | Missing |
| 2–3 letter target | Notes, archive, user decision | Step 2 and 6 | Length policy ≤3; 4+ only if 3-letter stage feasible | Config and label tests | Confirmed; 4+ conditional |
| Right-to-left order | Notes | Step 6 and 10 | Ordered sequence | Order-specific fixtures | Planned |
| Dotted guide handling | Latest notes | Step 5 | Guide dibuang sebelum input (user D-04) | Visual/data QC | Resolved: guide panduan penulis, bukan input |
| Participant-wise split | Archive | Step 4 and 7 | Split manifest | Leakage audit | Planned |
| CNN-LSTM | Draft/notes | Step 9–10 | Two-stage model | Forward/training tests | Planned |
| MobileNetV4 | Latest notes | Step 9 | Backbone checkpoint | Model/config validation | Variant unresolved |
| Transfer learning | Draft/notes | Step 9 and 11 | Ablation results | Same-split comparison | Source unresolved |
| Exact match | Draft/notes | Step 12 | Metric report | Known fixtures | Planned |
| Positional accuracy | Draft/notes | Step 12 | Metric report | Definition review | Ambiguous |
| CER | Draft/notes | Step 12 | Metric report | Edit-distance fixtures | Planned |
| Error analysis | Archive/analysis | Step 13 | Figures and findings | Sample traceability | Planned |
| Reproducibility | User prompt | Step 1 and 14 | Environment/run manifest | Fresh-runtime rerun | Missing |
| Documentation | Official guide/user | Step 15 | Thesis/README | Checklist review | Pending approval |

## 9. Existing Notebook Analysis

### 9.1Status current

Current direct read: `code/Pengerjaan/notebooks/training_hijaiyah_colab.ipynb` is not available. Initial inventory and a prior audit snapshot reported one notebook at that path. The cell-level findings below are therefore **historical snapshot evidence, not current execution evidence**.

### 9.2Snapshot inventory

The snapshot contained 16 cells: 8 Markdown and 8 code cells, with no saved execution count or output.

| Cell | Type | Planned purpose in snapshot | Evidence/status |
|---:|---|---|---|
| 0 | Markdown | Title and two-stage model description | Present in snapshot; not current |
| 1 | Markdown | 28-letter output contract and rejection of harakat/Latin/hamza | Present in snapshot; policy needs confirmation |
| 2 | Code | Install NumPy, Pillow, PyYAML, timm, PyTorch, torchvision | No output saved |
| 3 | Code | Discover project root, add `src`, import package, print versions/device | Depends on package files |
| 4 | Markdown | Upload instructions and demo/production switch | Present in snapshot |
| 5 | Code | Mount Drive, load config, create artifact paths | Hardcoded `/content/drive/...`; no output |
| 6 | Markdown | Data and manifest instructions | Present in snapshot |
| 7 | Code | Generate demo or load real manifest, summarize and assert | No output |
| 8 | Markdown | Stage-1 MobileNetV4 description | Present in snapshot |
| 9 | Code | Call `train_backbone` | Depends on missing source |
| 10 | Markdown | Stage-2 CNN-LSTM + CTC description | Present in snapshot |
| 11 | Code | Call `train_crnn` | Depends on stage-1 checkpoint |
| 12 | Markdown | Evaluation description | Present in snapshot |
| 13 | Code | Evaluate, predict, save JSON, assert alphabet | Depends on test record/checkpoint |
| 14 | Markdown | Drive persistence description | Present in snapshot |
| 15 | Code | Copy checkpoints/JSON to Drive or print local paths | Depends on all prior artifacts |

### 9.3Notebook dependency chain

```text
install/import
    → project root and package
    → config and artifact paths
    → manifest/data
    → stage-1 backbone
    → stage-2 CNN-LSTM
    → evaluation/prediction
    → persistence
```

The chain is logically ordered, but hidden kernel state and missing files prevent a current clean run.

### 9.4Problems found in the snapshot

- All code cells had `execution_count: null` and empty outputs; there is no saved proof of successful execution.
- Default mode used demo data, three writers, four samples per writer, and one epoch; this is a smoke test, not a research experiment.
- Production path used an absolute Google Drive path and conflicted with the markdown instruction to upload a local `data/raw` folder.
- No EDA plots, loss curves, confusion matrix, per-sample output, or qualitative error analysis appeared in the notebook itself.
- Preprocessing, augmentation, label encoding, blank/padding, decoder, and CTC time-step validation were delegated to missing source modules.
- No fixed environment lock, run ID, config snapshot, manifest hash, or source revision was saved.
- Drive persistence was a final copy step, not a documented resume mechanism.
- The notebook did not assert that validation and test splits were nonempty or that output length was always 2–3.
- The notebook format declared `nbformat_minor=5` but the snapshot lacked cell IDs, which may reduce compatibility with strict validators.
- The notebook and source files are currently absent, so the snapshot must be re-audited after restoration.

### 9.5Notebook conclusion

The snapshot is a useful planning scaffold for a Colab demo, but it does not prove a reproducible research pipeline. It must not be treated as completed merely because its cell sequence looks logical.

## 10. Dataset Analysis

### 10.1Current filesystem state

- `code/Pengerjaan/data/raw/` and `code/Pengerjaan/data/processed/` were reported in initial inventory but are not present in the current direct filesystem check.
- The initial inventory reported `data/demo/manifest.jsonl` and 12 PNG files named by writer/sample pattern; these are not currently available for direct validation.
- Initial inventory reported demo outputs and checkpoints; these are not currently available for direct validation.
- `code/image.png` is the only currently visible project image. It is one small visual example, not a dataset. Audit snapshots disagree on its dimensions, so it cannot be used as a fixed preprocessing fixture without remeasurement.
- No CSV, parquet, tensor, or production manifest is currently available in the project tree.

### 10.2Primary dataset requirements still missing

- Complete list of connected ≤3-letter words from Iqro 3 (Section 10.5); 4+ words as conditional expansion.
- Number of target words and number of samples per word.
- Number and demographic profile of writers.
- Canvas device, browser, resolution, color mode, DPI, and export settings.
- Whether guide lines are present, how they are captured, and how they are handled.
- Consent, privacy, retention, and licensing documents.
- Two-verifier QC records and rejection reasons.
- Split ratios and writer allocation.
- Label normalization for Arabic Unicode variants.
- Minimum sample target and class/word balance policy.

### 10.3Secondary datasets in literature

| Dataset | Reported facts | Intended role | Constraint |
|---|---|---|---|
| Hijja/Hijja2 | Approximately 47,434 isolated character images; children aged 7–12; 28 letters plus hamzah in some descriptions; 108 positional forms | Optional backbone pretraining or isolated-character baseline | Not a connected-word dataset; local file not present; label mapping must be decided |
| AHCD | 16,800 isolated Arabic characters from adults | Literature baseline only | Not a direct benchmark for connected canvas words |
| IFN/ENIT | Arabic handwritten words, roughly 32k words and 400+ writers in cited studies | Optional external sequence benchmark | Different vocabulary/media; must be reported separately |
| KHATT | Arabic handwritten text lines | Optional external sequence benchmark | Task is line recognition, not short Iqro words |
| HMBD, IFHCDB, CMATERDB, and others | Reported in literature | Comparative context only | Do not mix into primary test set without approval |

### 10.4Label and sequence policy requiring decision

The documents and snapshot use different policies:

- 28 standard letters, excluding harakat, Latin, and a separately encoded hamzah in the historical notebook.
- Hijja2 descriptions include 28 letters plus hamzah and 108 positional forms.
- Some examples show harakat in the input image, while the notebook contract rejects them from the output.

`Conflict detected — requires confirmation.` The project must define whether labels represent base letters only, whether hamzah is excluded/mapped/abstained, and whether harakat are ignored, removed, or included. **Resolution (user):** hamzah dihitung sebagai huruf (termasuk kelas label); harakat/tanwin/sukun/tasydid/maddah/tanda baca tidak dihitung sebagai huruf; madda dinormalisasi ke hamzah+alif/أ.

For variable lengths 2–3, the following are possible designs but **fixed slots is now selected (D-07, user)**:

- ~~CTC with blank and greedy/beam decoding.~~
- **Fixed three slots with padding/EOS (selected).**
- ~~Multi-output dense head with a length head.~~
- ~~Auxiliary multi-label pretraining followed by a sequence head.~~

The choice affects metrics, architecture, label files, and integration. It must be approved before implementation.

### 10.5 Status data — daftar kosakata Iqro 3 maksimal 3 huruf (provisional)

**Sumber:** `code/file pdf/Iqra-3-Belajar-Baca-Quran.pdf`, halaman 3–30 (scan tanpa text layer yang andal).

**Aturan penghitungan (dikonfirmasi pengguna):**
- Hanya huruf Hijaiyah dasar yang dihitung; harakat, tanwin, sukun, tasydid, maddah, dan tanda baca tidak dihitung.
- `ال` dan hamzah dihitung karena termasuk huruf (keputusan user, D-06); madda dinormalisasi ke hamzah+alif/أ.
- Setiap sel kosakata dihitung sebagai satu item terpisah, termasuk variasi baca yang sama.
- Baris instruksi, nomor halaman, dan tabel persamaan huruf (mis. `ه = ة = ى = و`) dikecualikan.

`Status: PROVISIONAL — belum dapat dipercaya penuh.` Dua pemindaian visual independen menghasilkan daftar panjang yang saling bertentangan pada kata >3 huruf. Subset ≤3 huruf berikut relatif konsisten tetapi tetap **wajib diverifikasi manual terhadap buku fisik/salinan resolusi tinggi (VR-02)** sebelum dijadikan whitelist final.

| Kata (contoh bertanwin/bersukun) | Normalisasi (huruf dasar) | Jumlah huruf | Halaman |
|---|---|---|---|
| بَ | ب | 1 | 3 |
| جَ | ج | 1 | 8 |
| دَ | د | 1 | 10 |
| فَ | ف | 1 | 16 |
| بَا / بَاْ | با | 2 | 3 |
| بِي / بِيْ | بي | 2 | 3 |
| بُو / بُوْ | بو | 2 | 3 |
| تَبْ | تب | 2 | 3 |
| تِبْ | تب (perlu cek) | 2 (berpotensi 3) | 3 |
| نَبْ | نب | 2 | 3 |
| يَبْ | يب | 2 | 3 |
| رَبُّ / رَبٌّ | رب | 2 | 23 |
| آدَم | ادم | 3 | 4, 15 |
| ثَانٍ | ثان | 3 | 5, 15 |
| غَاثٍ | غاث | 3 | 5, 15 |
| هَادٍ | هاد | 3 | 5, 15 |
| مَائِة | مئة | 3 | 5, 15 |
| فَضْلًا | فضل | 3 | 5 |
| قَوْلًا | قول | 3 | 5 |
| وَهْبًا | وهب | 3 | 5 |
| شَكْرًا | شكر | 3 | 5 |
| لَيْلًا | ليل | 3 | 5 |
| قِصَّة | قصة | 3 | 6 |
| لَيِّن | لين | 3 | 7 |
| كَيْف | كيف | 3 | 7 |
| عَيْن | عين | 3 | 7 |
| بَيْت | بيت | 3 | 3, 7 |
| نَيْل | نيل | 3 | 7 |
| غَيْب | غيب | 3 | 7 |
| سَيِّد / سَيِّدٌ | سيد | 3 | 7, 23 |
| فَيْء | فيء | 3 | 7 |
| ذَات | ذات | 3 | 8 |
| نَار | نار | 3 | 8 |
| لَحْي | لحي | 3 | 9 |
| لَاخِ | لاخ | 3 (MEDIUM) | 9 |
| دَار | دار | 3 | 10 |
| دَهْر | دهر | 3 | 10 |
| دَوْر | دور | 3 | 10 |
| دَانٍ | دان | 3 | 10 |
| دَاعٍ | داع | 3 | 10 |
| أَنْس / أُنْسٌ | انس | 3 | 12, 21 |
| عَوْن | عون | 3 | 12 |
| حَفْظ | حفظ | 3 | 12 |
| وَلَد | ولد | 3 | 12 |
| بَنُو | بنو | 3 | 12 |
| سَفَر | سفر | 3 | 12 |
| صِدْق | صدق | 3 | 13 |
| ضِعْف | ضعف | 3 | 13 |
| فَتَح | فتح | 3 | 16 |
| كُرْز | كرز | 3 | 16 |
| رَزْق | رزق | 3 | 3, 16 |
| رَزْل | رزل | 3 (perlu cek) | 16 |
| تَانٍ | تان | 3 | 19 |
| قَارٍ | قار | 3 | 19 |
| بَيْنَ | بين | 3 | 19 |
| بَعْضُ | بعض | 3 | 19 |
| عَالٍ | عال | 3 | 19 |
| بَابُ | باب | 3 | 3, 19 |
| دَيْث | ديث | 3 | 21 |
| وَأْدٌ | وأد | 3 | 21 |
| فَهْمٌ | فهم | 3 | 21 |
| أَثَرٌ | أثر | 3 | 21 |
| ثَوْبٌ | ثوب | 3 | 21 |
| بِشْرٌ | بشر | 3 | 22 |
| طَيِّبٌ | طيب | 3 | 22 |
| فَضْلٌ | فضل | 3 | 22 |
| عِزَّةٌ | عزة | 3 | 22 |
| قَوِيٌّ | قوي | 3 | 23 |
| وَرِعٌ | ورع | 3 | 24 |
| فَتِيٌّ | فتي | 3 | 24 |
| وَتِدٌ | وتد | 3 | 24 |
| ضَيِّقٌ | ضيق | 3 | 18, 24 |

Catatan penting:
- **Upaya verifikasi otomatis belum dapat dipercaya.** Empat pemindaian visual terpisah (subagent) menghasilkan daftar yang saling bertentangan untuk halaman yang sama (mis. halaman 3, 10–11, 16–21), termasuk kata-kata yang tidak konsisten dengan struktur kosakata Iqro 3. Penyebab: PDF berupa hasil scan tanpa text layer, dan Arabic OCR tidak tersedia serta tidak boleh diinstal sebelum gate persetujuan. Daftar tetap **PROVISIONAL sampai pengecekan manusia** (reviewer) terhadap halaman sumber di PDF.
- **Keputusan scope (telah dikonfirmasi pengguna):** scope awal hanya kosakata maksimal 3 huruf. Kata 4+ huruf (mis. فَاتِح، كَاتِب، خَالِق، dan seluruh kalimat panjang halaman 25–30) **tidak** termasuk daftar awal dan **hanya** akan ditambahkan bila tahap 3 huruf terbukti tidak membebani (resource/data/mencapai acceptable accuracy).
- Tingkat confidence variatif; entri yang ditandai *perlu cek* atau *MEDIUM* membutuhkan verifikasi visual langsung.
- Jika aturan label kelak mengecualikan hamzah (mis. menormalisasi `فَيْء/آدَم`), penghitungan dapat berubah.

## 11. Proposed System / Analysis Architecture

This is a proposed minimal architecture, not an implementation.

```text
Iqro 3 source material
        ↓
Controlled vocabulary inventory and scope decision
        ↓
Canvas collection protocol
        ↓
Raw images + manifest + QC log
        ↓
Dataset validation and participant-wise split
        ↓
EDA and preprocessing specification
        ↓
Stage 1: MobileNetV4 backbone training/fine-tuning
        ↓
Backbone checkpoint + history
        ↓
Stage 2: CNN-LSTM sequence training
        ↓
CRNN checkpoint + history
        ↓
Held-out evaluation: exact match, positional accuracy, CER
        ↓
Ablation and qualitative error analysis
        ↓
Versioned artifacts, notebook, and documentation
```

### 11.1Minimal data contract

The final schema must be decided, but the minimum conceptual fields are:

| Field | Purpose |
|---|---|
| `sample_id` | Stable sample identity |
| `image_path` | Location of raw/exported image |
| `text` | Ordered reference sequence |
| `writer_id` | Participant identity for leakage control |
| `session_id` | Collection session, recommended |
| `split` | `train`, `validation`, or `test` |
| `target_word` | Prompt/ground-truth word, recommended |
| `guide_present` | Guide-line condition, recommended |
| `qc_status` | Accepted/rejected and reason |
| `qc_reviewer_1/2` | Independent QC metadata, recommended |
| `source` | Canvas/demo/secondary dataset provenance |

### 11.2Architecture boundaries

- Dataset layer handles ingestion, validation, QC, split, and manifests.
- Preprocessing layer handles image-to-tensor conversion.
- Model layer handles stage-1 backbone and stage-2 sequence model.
- Evaluation layer handles decoding, metrics, ablation, and error reports.
- Documentation layer handles notebook, run instructions, and final thesis/README.

No database server, message queue, or microservice is justified by the current project scope.

## 12. End-to-End Workflow

```text
Approval of PRD and unresolved decisions
        ↓
Environment and reproducibility setup
        ↓
Iqro 3 vocabulary inventory and scope freeze
        ↓
Canvas collection protocol and metadata/QC design
        ↓
Raw data collection and quality control
        ↓
Manifest validation and participant-wise split
        ↓
EDA and label/preprocessing decisions
        ↓
Baseline definition
        ↓
Stage-1 MobileNetV4 training/fine-tuning
        ↓
Stage-2 CNN-LSTM end-to-end training
        ↓
Held-out testing and decoding
        ↓
Metrics, ablation, and qualitative error analysis
        ↓
Artifact persistence and fresh-runtime validation
        ↓
Notebook, thesis documentation, and final checklist
```

## 13. Detailed Implementation Steps

The following steps are plans only. They are not instructions to execute during this stage.

### Step 1 — Approval and Decision Register

**Tujuan**  
Menetapkan batas kerja, urutan prioritas sumber, dan daftar keputusan yang harus disetujui.

**Input**  
This PRD, `DRAFT_PROPOSAL_SKRIPSI.md`, research notes, official guide, and audit findings.

**Proses**  
Record every confirmed requirement, conflict, decision owner, and acceptance condition. Separate “source fact” from “technical recommendation”.

**Output**  
Approved decision register and implementation-ready scope.

**Validasi**  
Every P0/P1 decision has an owner and status; unresolved title/task ambiguity is not silently converted into code.

**Dependency**  
None.

**Catatan**  
Implementation must not start before explicit PRD approval.

### Step 2 — Environment and Reproducibility Contract

**Tujuan**  
Membuat environment yang dapat direproduksi untuk notebook, local run, and Colab.

**Input**  
Approved implementation language/framework, runtime, hardware assumptions, and project source.

**Proses**  
Define Python version, dependency versions, device policy, seed policy, run ID, config capture, and artifact naming. Decide whether local run or Colab is the primary execution path.

**Output**  
Versioned environment specification and reproducibility checklist.

**Validasi**  
A fresh runtime can report the intended versions and locate the project without relying on hidden absolute paths.

**Dependency**  
Step 1.

**Catatan**  
Do not add complex infrastructure. A notebook and lightweight Python package are sufficient unless evidence requires more.

### Step 3 — Iqro 3 Inventory and Scope Freeze

**Tujuan**  
Menentukan kosakata target dan batas panjang sequence.

**Input**  
`Iqra-3-Belajar-Baca-Quran.pdf`, approved interpretation of the book, and scope decision.

**Proses**  
Manually transcribe connected words, normalize Arabic strings, record source page, confirm duplicates, define inclusion/exclusion rules, and freeze the initial scope to ≤3-letter words (Section 10.5); 4+ words are a conditional future expansion only if the 3-letter stage is feasible.

**Output**  
Versioned vocabulary table with source page and approved label sequence.

**Validasi**  
Two-person review or documented manual check; no untraceable label enters the manifest.

**Dependency**  
Step 1.

**Catatan**  
The Iqro PDF is scanned and has no reliable text layer; OCR alone is not sufficient evidence.

### Step 4 — Canvas Collection and Metadata Design

**Tujuan**  
Mendefinisikan cara yang konsisten untuk memperoleh citra canvas.

**Input**  
Approved vocabulary, target users/consent process, canvas/export settings, and collaborator contract.

**Proses**  
Define prompt display, blank or guided canvas, optional dotted guides, image export, naming, writer/session metadata, device information, and rejected-sample handling.

**Output**  
Collection protocol, metadata schema, and sample manifest template.

**Validasi**  
A sample can be traced from prompt to raw image to reference label; consent and privacy fields exist.

**Dependency**  
Steps 1 and 3.

**Catatan**  
The student owns the model/data pipeline. The exact ownership of a minimal canvas UI is not fully resolved.

### Step 5 — Data Quality Control and Manifest Validation

**Tujuan**  
Memastikan hanya citra valid dan berlabel benar yang masuk pipeline.

**Input**  
Raw images, manifest, reviewer records, and rejection criteria.

**Proses**  
Validate file existence, image readability, target match, connected-stroke criteria, label alphabet, duplicate IDs/paths/content, and writer metadata. Record rejected samples rather than deleting evidence.

**Output**  
Validated manifest and QC/rejection report.

**Validasi**  
No invalid record passes silently; all accepted records satisfy the approved contract.

**Dependency**  
Step 4.

**Catatan**  
The historical snapshot had fail-fast behavior and incomplete duplicate/content checks; current status is unavailable.

### Step 6 — EDA, Label Encoding, and Preprocessing Specification

**Tujuan**  
Memahami data dan mengunci kontrak preprocessing serta sequence encoding.

**Input**  
Validated manifest and raw images.

**Proses**  
Generate counts/distributions, inspect image quality, decide grayscale/polarity/background handling, crop, resize, normalization, guide handling, augmentation, sequence length, blank/padding/EOS, and RTL representation.

**Output**  
EDA report, figures, preprocessing specification, and label encoding specification.

**Validasi**  
Save representative before/after images and assert dimensions, value range, label length, and visual alignment.

**Dependency**  
Steps 3–5.

**Catatan**  
Label encoding sudah diputuskan: fixed slots (maks 3) dengan padding/EOS (D-07). Bagian lain preprocessing tetap harus dispesifikasi eksplisit; jangan memilih secara diam-diam.

### Step 7 — Dataset Split and Leakage Audit

**Tujuan**  
Membagi data sehingga generalisasi writer tidak diukur secara optimistis.

**Input**  
Validated manifest and approved split policy.

**Proses**  
Allocate writers to train/validation/test, check stratification and word coverage, detect leakage, freeze split assignment, and record the split version.

**Output**  
Immutable split manifest and audit report.

**Validasi**  
No writer, duplicate image, or unauthorized augmentation crosses splits; all splits meet minimum coverage requirements.

**Dependency**  
Steps 5–6.

**Catatan**  
Ratios such as 70:15:15 or 60:20:20 are examples only and are not approved requirements.

### Step 8 — Baseline and Ablation Plan

**Tujuan**  
Menentukan perbandingan yang menguji klaim transfer learning dan sequence modeling.

**Input**  
Approved task definition, split, metrics, and resource limits.

**Proses**  
Select a fair baseline matrix, such as scratch versus pretrained and sequence versus non-sequence, while keeping data and evaluation protocol identical. Decide whether auxiliary multi-label pretraining is a baseline or a required stage.

**Output**  
Experiment matrix and acceptance criteria for each run.

**Validasi**  
Every comparison changes only the intended factor or is explicitly labeled as a multi-factor exploratory run.

**Dependency**  
Steps 1, 6, and 7.

**Catatan**  
The exact ablation matrix is `Ambiguous requirement — requires clarification.`

### Step 9 — Stage-1 Backbone Training

**Tujuan**  
Menghasilkan representasi visual CNN sebelum model sequence dilatih.

**Input**  
Training/validation data, preprocessing contract, MobileNetV4 variant/checkpoint, and stage-1 config.

**Proses**  
Initialize or fine-tune the backbone, train the approved auxiliary objective, validate, select checkpoint, and record history.

**Output**  
Stage-1 checkpoint, history, config, and evaluation record.

**Validasi**  
Checkpoint loads in a fresh process; loss is finite; validation selection is documented; data split is unchanged.

**Dependency**  
Steps 2, 6–8.

**Catatan**  
MobileNetV4-Conv-Small pretrained ImageNet (D-09/D-10). Input channels, freeze policy, dan auxiliary objective stage-1 masih perlu dikunci.

### Step 10 — Stage-2 CNN-LSTM Training

**Tujuan**  
Mengubah feature map menjadi urutan huruf dan melatih model end-to-end.

**Input**  
Stage-1 checkpoint, sequence labels, preprocessing contract, and stage-2 config.

**Proses**  
Build map-to-sequence, recurrent layer, transcription head, chosen loss/decoder, train/validate, select best checkpoint, and preserve class/alphabet metadata.

**Output**  
Stage-2 checkpoint, history, and training log.

**Validasi**  
Forward output shape, time-step feasibility, finite loss, repeated-letter fixtures, and checkpoint compatibility pass.

**Dependency**  
Steps 6, 7, and 9.

**Catatan**  
Encoding fixed slots (D-07) dengan repetisi langsung (tanpa collapse); LSTM unidirectional (D-08). Snapshot lama menyebut CTC, tetapi itu bukti historis yang belum dipulihkan, bukan keputusan final.

### Step 11 — Ablation and Sensitivity Experiments

**Tujuan**  
Menguji dampak transfer learning, sequence component, and other approved factors.

**Input**  
Frozen split, baseline definitions, and stage-1/stage-2 implementations.

**Proses**  
Run comparable experiments, record seeds and resource usage, and avoid changing preprocessing or split between compared runs.

**Output**  
Experiment table and figures.

**Validasi**  
Results are traceable to run IDs and configs; differences are not attributed to uncontrolled data changes.

**Dependency**  
Steps 8–10.

**Catatan**  
Ablation breadth is limited by available data and confirmed research questions.

### Step 12 — Testing, Decoding, and Evaluation

**Tujuan**  
Mengukur prediksi pada data held-out.

**Input**  
Best approved checkpoint, test split, label contract, and metric definitions.

**Proses**  
Decode predictions, calculate exact match, positional accuracy, CER, per-length and per-writer breakdowns, and optional qualitative summaries.

**Output**  
Evaluation JSON/report, prediction table, and metric definitions.

**Validasi**  
Metric unit tests use known examples; test split is untouched during training; demo results cannot be presented as production results.

**Dependency**  
Steps 6–11.

**Catatan**  
No numeric performance threshold is specified in the available documents. Do not invent one.

### Step 13 — Error Analysis and Visualization

**Tujuan**  
Memahami sumber error dan substantiate research findings.

**Input**  
Predictions, reference labels, images, writer/session metadata, and experiment results.

**Proses**  
Plot loss curves, label distributions, confusion patterns, length-wise metrics, guide/no-guide comparisons, and representative correct/incorrect samples.

**Output**  
Figures and qualitative analysis linked to sample IDs.

**Validasi**  
Every highlighted error can be traced to a manifest record and model run.

**Dependency**  
Steps 6, 7, and 12.

**Catatan**  
Do not overgeneralize from a small or synthetic demo dataset.

### Step 14 — Notebook and Artifact Packaging

**Tujuan**  
Membuat pipeline dapat dijalankan ulang dari atas ke bawah.

**Input**  
Approved code, configs, data manifest, environment contract, and evaluation functions.

**Proses**  
Arrange ordered cells, add preflight assertions, save final config, checkpoints, histories, evaluation, predictions, and run metadata. Provide local and Colab instructions.

**Output**  
Reproducible notebook, artifact bundle, and run instructions.

**Validasi**  
Fresh kernel/runtime run completes without hidden state; artifacts reload successfully.

**Dependency**  
Steps 2, 9–13.

**Catatan**  
The current notebook is unavailable; this step is planned, not completed.

### Step 15 — Documentation and Final Validation

**Tujuan**  
Menyelaraskan proposal, thesis, README, and implementation aktual.

**Input**  
Final approved requirements, results, limitations, and official UISI rules.

**Proses**  
Update proposal/related works/method/results/conclusion, verify citations and formatting, write README based on actual commands, and execute the final checklist.

**Output**  
Approved thesis package, final README, reproducibility statement, and validation report.

**Validasi**  
Requirement traceability has no unexplained gaps; all acceptance criteria are marked pass or explicitly blocked.

**Dependency**  
Steps 1–14.

**Catatan**  
README final must not contain fictional commands, metrics, or results.

## 14. Notebook / Google Colab Execution Flow

The following is the proposed cell order for the future notebook, based on the project and the historical snapshot. It is not a modification of the current missing notebook.

| Cell | Section | Required behavior | Output/validation |
|---:|---|---|---|
| 1 | Project introduction | State task, scope, title terminology, and non-goals | Reader knows what is and is not being recognized |
| 2 | Reproducibility parameters | Define run ID, seed, device, data mode, and paths | Preflight values are visible |
| 3 | Environment | Install or verify pinned dependencies | Versions and runtime printed |
| 4 | Project discovery/import | Discover project root and import package deterministically | No ambiguous root; no hidden `sys.path` state |
| 5 | Data location | Select demo or real manifest; mount Drive only if selected | Explicit path and no accidental demo use |
| 6 | Load and validate manifest | Load records and check schema, labels, files, writers, and splits | Assertions and summary |
| 7 | EDA | Counts, label length, writer/session, split, and image quality | Tables and plots |
| 8 | Label/preprocessing contract | Show alphabet, sequence encoding, guide policy, and sample transforms | Clear before training |
| 9 | Reproducibility setup | Set seeds, device, dataloaders, and run metadata | Deterministic run context |
| 10 | Stage-1 training | Train/fine-tune MobileNetV4 backbone | Checkpoint, history, validation record |
| 11 | Stage-2 training | Load stage-1 checkpoint and train CNN-LSTM | Sequence checkpoint and history |
| 12 | Evaluation | Decode test predictions and calculate primary metrics | Evaluation JSON/report |
| 13 | Visualization/error analysis | Loss curves, label distribution, per-length results, examples | Figures and error IDs |
| 14 | Persistence | Save config, environment, checkpoints, outputs, and checksums | Reloadable artifact bundle |
| 15 | Final assertions | Validate no invalid characters, required splits, artifact existence, and run completion | Clear success/failure summary |

### 14.1 Notebook rules

- No cell may rely on an undeclared variable from a previous cell without an explicit assertion or documented state contract.
- Demo mode must be visibly labeled and must not be used as the final research result.
- The notebook must fail early on missing data, invalid labels, writer leakage, or incompatible config.
- The notebook must save the final config alongside checkpoints.
- A clean run means a fresh kernel and a documented data/artifact location.

## 15. Project Structure

The current repository has the broad shape below, but `code/Pengerjaan` is currently empty. The implementation structure below is a **proposed recovery/development structure**, not a request to create files now.

```text
Skripsi/
├── prd.md
├── Skripsi.docx                         # existing template; not active proposal
└── code/
    ├── .gitignore
    ├── DRAFT_PROPOSAL_SKRIPSI.md
    ├── ARSIP_DRAFT_BAB1_PROPOSAL.md
    ├── ANALISIS_LITERATUR_LENGKAP.md
    ├── literatur_gap_skripsi.md
    ├── skripsi_hijaiyah_canvas_research_notes.md
    ├── DAFTAR_JURNAL_REFERENSI.md
    ├── FORMAT_TUGAS_AKHIR.md
    ├── image.png
    ├── file GAP/                        # literature references
    ├── file pdf/                        # Iqra material and official guide
    ├── Pengerjaan/                       # current directory is empty
    │   ├── pyproject.toml               # proposed/recovery item
    │   ├── README.md                    # future, after implementation
    │   ├── configs/
    │   │   ├── demo.yaml
    │   │   └── production.yaml
    │   ├── data/
    │   │   ├── raw/
    │   │   ├── processed/
    │   │   └── demo/
    │   ├── notebooks/
    │   │   └── training_hijaiyah_colab.ipynb
    │   ├── src/
    │   │   └── hijaiyah_ocr/
    │   ├── tests/
    │   ├── checkpoints/
    │   ├── outputs/
    │   └── dokumentasi/
    ├── .opencode/                       # tool configuration
    ├── .qoder/                          # tool configuration
    └── undefined/                       # generated cache
```

The structure should remain lightweight. Do not introduce a service architecture unless a later approved requirement demonstrates a need.

## 16. Validation Strategy

### 16.1Requirement validation

- Build a source-to-requirement-to-step-to-output-to-validation matrix.
- Mark every unresolved conflict as blocked rather than selecting silently.
- Recheck final thesis claims against the verified literature audit.

### 16.2Data validation

- Validate manifest schema and file existence.
- Check label alphabet, length, Unicode normalization, and writer ID.
- Check duplicate IDs, paths, and content hashes.
- Check split coverage and writer leakage.
- Review a statistically useful sample manually, including guide/no-guide and failure cases.

### 16.3Preprocessing validation

- Test grayscale conversion, polarity, crop, aspect ratio, resize, and normalization.
- Save before/after examples.
- Assert output dimensions and value range.
- Verify guide-line policy on both accepted and rejected samples.

### 16.4Model validation

- Run unit tests for label encoding, sequence decoding, repeated letters, and metric formulas.
- Run a small forward-pass smoke test before full training.
- Verify CTC time-step constraints or fixed-slot padding/EOS behavior.
- Verify checkpoint/config/alphabet compatibility.
- Run one known-good prediction fixture through a fresh process.

### 16.5Training validation

- Log train/validation loss and learning metrics per epoch.
- Use a fixed, frozen split for comparisons.
- Record seed, config, data version, source revision, device, and duration.
- Do not select a run using the test set.
- If early stopping is used, implement and test it rather than leaving a dead config.

### 16.6Evaluation validation

- Evaluate on held-out data.
- Report exact match, positional accuracy, and CER with definitions and denominators.
- Break down by sequence length, writer, and word where sample size permits.
- Compare only experiments with compatible data and task definitions.
- Separate demo, pilot, validation, and final test results.

### 16.7Notebook validation

- Restart kernel.
- Run all cells from top to bottom.
- Test with a temporary artifact directory and a fresh runtime.
- Confirm no hidden variables, stale checkpoints, or absolute paths are required.
- Confirm final cells assert artifact existence and result status.

### 16.8Documentation validation

- Check official UISI formatting and submission requirements.
- Verify citations against source PDFs or official bibliographic records.
- Ensure README describes actual commands, dependencies, data location, and results.
- Ensure thesis claims do not overstate novelty or transfer-learning effectiveness.

## 17. Acceptance Criteria

### Data

- [ ] Approved Iqro 3 vocabulary inventory exists and is traceable to source pages.
- [ ] Primary canvas images and metadata are available.
- [ ] QC is completed and rejected samples have documented reasons.
- [ ] Labels follow the approved alphabet/length policy.
- [ ] Raw data is preserved separately from processed/augmented data.
- [ ] Participant-wise split is frozen and leakage-free.
- [ ] Dataset statistics and EDA are available.

### Analysis

- [ ] Literature claims are corrected against the audited sources.
- [ ] Research gap is phrased as supported by the available corpus, not as an unsupported global claim.
- [ ] Preprocessing and label encoding are documented.
- [ ] Baseline and ablation matrix is approved.
- [ ] Required visualizations and error analysis are available.

### Model

- [ ] Stage-1 backbone training is reproducible.
- [ ] Stage-2 CNN-LSTM training is reproducible.
- [ ] Predictions preserve approved order and label policy.
- [ ] Repeated-letter behavior is tested.
- [ ] Exact match, positional accuracy, and CER are calculated with documented definitions.
- [ ] Test results are not confused with demo/pilot results.

### Execution

- [ ] Notebook runs from a fresh kernel top-to-bottom.
- [ ] No hidden cell dependency or stale artifact is required.
- [ ] No critical error remains unresolved.
- [ ] Environment, seeds, config, data version, and run ID are captured.
- [ ] Checkpoints and outputs reload in a fresh process.

### Documentation

- [ ] Proposal and thesis chapters reflect the approved method.
- [ ] README final is written only after implementation.
- [ ] Dataset, dependencies, commands, and limitations are documented.
- [ ] Results and evaluation tables are reproducible.
- [ ] Official formatting, originality, publication, and submission requirements are checked.

No numeric performance threshold is imposed here because `Not specified in available project documents.`

## 18. Definition of Done

Proyek dianggap selesai hanya when:

### Data

- Dataset primer terkumpul, tervalidasi, dan QC selesai.
- Inventaris Iqro 3 dan schema metadata disetujui.
- Split participant-wise reproducible dan bebas leakage.
- Dataset serta lisensi/privasi terdokumentasi.

### Analysis

- Semua analysis wajib selesai.
- EDA, preprocessing, label policy, and error analysis tersedia.
- Metode sesuai dengan requirement yang disetujui.
- Klaim literatur dan novelty tidak berlebihan.

### Model

- Model stage-1 dan stage-2 berhasil dilatih pada data yang disetujui.
- Model dapat melakukan prediksi urutan.
- Evaluasi held-out dan ablation selesai.
- Failure cases dan limitations dibahas.

### Execution

- Notebook dapat dijalankan dari atas ke bawah.
- Tidak ada dependency cell tersembunyi.
- Tidak ada critical error.
- Artifact dapat dimuat ulang.
- Demo dan production result terpisah jelas.

### Documentation

- Proposal, thesis, related works, and references selesai.
- README final mencerminkan implementasi aktual.
- Dataset, environment, method, results, and limitations terdokumentasi.
- Final validation checklist disetujui.

## 19. Current State

### Current State

- Dokumen proposal, catatan advisor, audit literatur, dan panduan resmi tersedia.
- Arah penelitian relatif jelas, tetapi formal proposal masih dinyatakan belum lengkap.
- Dataset Iqro 3 belum memiliki inventory final.
- `code/Pengerjaan` current empty; implementation and notebook are not available for direct validation.
- Initial inventory reported historical code/notebook/demo artifacts, but these are not tracked in Git and cannot currently be accepted as implementation.
- No current production result, final model, or real-data evaluation is available.
- Literature collection is substantial, but direct connected-Hijaiyah competitors and the advisor’s approximately 15-paper target remain incomplete.

## 20. Missing Components

- Approved Iqro 3 word list.
- Primary canvas dataset.
- Real writer/session count and sample target.
- Consent/privacy/license documentation.
- QC records and rejection log.
- Final split ratios and frozen assignment.
- Final label/sequence encoding.
- Final MobileNetV4 variant and weight source.
- Final CNN-LSTM layer specification.
- Approved baseline/ablation matrix.
- Current code, tests, configs, and notebook.
- Current manifest, processed data, outputs, and checkpoints.
- Reproducibility lock/run manifest.
- Final results, figures, thesis chapters, and README.

## 21. Problems

1. **Task terminology mismatch:** title says multi-label, while the method requires ordered sequence recognition.
2. **Data gap:** the central dataset is absent.
3. **Model ambiguity:** stage-1 auxiliary objective and stage-2 loss/decoder are not fixed.
4. **Evidence gap:** notebook and source code cannot currently be rerun.
5. **Literature gap:** old matrix contains inaccurate numbers and overstates novelty.
6. **Template contamination:** Word/Markdown template contains unrelated topics, identities, and examples.
7. **Administrative ambiguity:** official guide and template disagree on citation style and proposal structure.
8. **Integration ambiguity:** ownership of the minimal canvas/data-collection interface is not fully clear.

## 22. Conflicts and Inconsistencies

| ID | Inconsistency | Evidence | Required handling |
|---|---|---|---|
| CI-01 | Dotted guides allowed in latest notes vs prohibited in archive | Draft/notes vs archive lines 47 and 78 | Confirm latest policy |
| CI-02 | Max three letters is provisional in latest notes vs fixed in archive | Notes line 19/380 vs archive lines 34/45 | **Resolved:** initial scope ≤3 (Section 10.5); 4+ words conditional |
| CI-03 | “All Iqro 3 words” vs selected/closed vocabulary wording | Notes lines 111/202 vs draft line 25 | **Resolved:** selected ≤3-letter list for initial scope; 4+ conditional expansion |
| CI-04 | Multi-label title vs sequence/CTC implementation | Draft lines 52–60, notes lines 170–194 | Keep terminology only with explicit explanation |
| CI-05 | MobileNetV2/ResNet/VGG old notes vs MobileNetV4 latest direction | Old gap vs latest notes | **Resolved (user):** MobileNetV4-Conv-Small |
| CI-06 | ImageNet vs Hijja2 pretraining unresolved | Draft line 44 and notes line 402 | **Resolved (user):** pretrained ImageNet |
| CI-07 | CTC appears as precedent but is not fully specified as final algorithm | Archive lines 28/84–86 | **Resolved (user):** fixed slots (max 3 letters) |
| CI-08 | 28-letter output vs Hijja2 29-class description | Notebook snapshot vs notes lines 214–216 | **Resolved (user):** hamzah dihitung karena termasuk huruf |
| CI-09 | Guide lines may be present, but preprocessing policy is absent | Notes lines 124–126 | **Resolved (user):** dotted guide hanya panduan penulis; dibuang sebelum input model |
| CI-10 | Harvard in official guide vs APA 7 in template | Official PDF pages 18–25 vs `FORMAT_TUGAS_AKHIR.md:291–297` | Confirm department rule |
| CI-11 | Proposal structure differs between official guide and generic template | Official PDF pages 9/16 vs template | Confirm current proposal template |
| CI-12 | Historical notes count 17 PDFs vs current reference tree contains 24 PDFs | Notes/gap inventory vs current directory | Reconcile inventory and duplicates |
| CI-13 | Initial implementation inventory vs current empty `Pengerjaan` | Initial glob/read vs direct recheck and Git | Restore or confirm deletion |
| CI-14 | Literature target approximately 15 connected papers vs only about 4–6 verified | Research notes lines 281–285 vs literature audit lines 405–421 | Add verified direct studies |
| CI-15 | `image.png` dimensions differ across audit snapshots | Literature audit line 50 vs artifact audit | Remeasure before using as fixture |

## 23. Risks

| Risk | Likelihood | Impact | Mitigation for later stage |
|---|---|---|---|
| Dataset cannot be collected in sufficient quality | High | Critical | Freeze protocol, conduct pilot, monitor writer coverage |
| Writer leakage inflates results | High | Critical | Freeze participant-wise split and audit |
| Label/sequence policy changes late | High | Critical | Resolve Step 3 and Step 6 before code |
| MobileNetV4 variant/checkpoint unavailable or incompatible | Medium | High | Verify model name, input shape, license, and package version |
| ImageNet transfer underperforms domain-specific data | Medium | High | Include scratch and approved pretraining ablations |
| CTC time steps insufficient for repeated labels | Medium | High | Add shape/decoder tests before training |
| Overfitting on small canvas dataset | High | High | Use controlled augmentation, regularization, and held-out writers |
| Incorrect handling of guide lines harms generalization | Medium | High | Record guide condition and analyze separately |
| Notebook cannot reproduce because of hidden state | High | High | Fresh-kernel test, pinned environment, explicit paths |
| Code/notebook artifacts are lost or untracked | High | Critical | Confirm recovery and version-control policy before implementation |
| Literature novelty claim is challenged | Medium | High | Search direct competitors and phrase claims cautiously |
| Sensitive participant data is exposed | Medium | High | Consent, anonymization, access control, and data minimization |
| Official format requirements are missed | Medium | High | Validate against current department instructions |
| Demo results are mistaken for research results | Medium | High | Separate directories, labels, and reports |

## 24. Required Decisions

The following decisions are intentionally not resolved in this PRD:

1. **D-01:** Is the title wording “Klasifikasi Multi-Label” final despite the sequence task?
2. **D-02:** Is the final dataset all connected words in Iqro 3 or a controlled subset?
3. **D-03:** Is the maximum length fixed at three letters for the thesis, or only for initial experiments?
4. **D-04:** Are dotted guide lines allowed, required, optional, or removed during preprocessing? — **Resolved (user):** guide hanya untuk panduan penulis, tidak menjadi bagian input model (dibuang di preprocessing).
5. **D-05:** Are harakat included, ignored, removed, or rejected? — **Resolved (user):** harakat/tanda baca tidak dihitung sebagai huruf; label dasar (per Section 10.5).
6. **D-06:** Is hamzah excluded, mapped to a base letter, or treated as an abstention class? — **Resolved (user):** hamzah dihitung karena termasuk huruf (label letter; madda dinormalisasi ke hamzah+alif/أ).
7. **D-07:** Which sequence representation is final: CTC, fixed slots, or another design? — **Resolved (user):** fixed slots, karena jumlah huruf sudah ditentukan sejak awal (maksimal 3 huruf per sampel).
8. **D-08:** Is the recurrent layer unidirectional LSTM, bidirectional LSTM, or selected after ablation? — **Resolved (user):** unidirectional LSTM (pembangunan CNN-LSTM kanan-ke-kiri).
9. **D-09:** Which MobileNetV4 variant and pretrained checkpoint are valid for the chosen input? — **Resolved (user):** MobileNetV4-Conv-Small.
10. **D-10:** Should transfer learning use ImageNet, Hijja2, both, or a controlled comparison? — **Resolved (user):** ImageNet pretrained.
11. **D-11:** What is the minimum number of writers, words, and images per word?
12. **D-12:** What are the train/validation/test ratios and word coverage rules?
13. **D-13:** Who owns and implements the minimal canvas/data-collection interface?
14. **D-14:** What baseline and ablation matrix is required by the advisor?
15. **D-15:** What is the definition of "character accuracy": aligned positional accuracy or edit-aligned normalized accuracy? — **Resolved (user):** positional accuracy = persentase posisi huruf yang cocok sejajar (fixed slots); definisi akan dikunci di implementasi.
16. **D-16:** What performance threshold, if any, is required for acceptance?
17. **D-17:** What citation style and proposal template does the current department require?
18. **D-18:** Should the current historical code/notebook be restored, or should implementation start from a clean structure?
19. **D-19:** What publication venue, authorship order, and collaborator role are approved?
20. **D-20:** What consent, retention, and licensing policy applies to handwriting data and Iqro source material?

## 25. Future Improvements

These are `Optional / Future Improvement` and must not be added to the main scope without approval:

- Expand from short 2–3-letter words to longer words or lines.
- Add robust handling of arbitrary Arabic diacritics and Unicode glyph variants.
- Compare Transformer/ViT sequence recognizers against the selected CRNN baseline.
- Add domain-specific continual pretraining or writer-style adaptation.
- Validate synthetic word augmentation with human review before using it.
- Add active learning for QC and difficult samples.
- Add mobile inference benchmarking and model compression.
- Add user acceptance testing for the collaborator’s gamification module.
- Add cross-dataset evaluation on Hijja2, AHCD, IFN/ENIT, or KHATT.
- Add automated data-drift and model-quality monitoring after deployment.

## 26. README Requirements

README final shall be created only after implementation and shall contain actual information:

1. **Project overview** — purpose and current status.
2. **Problem statement** — connected Hijaiyah recognition problem.
3. **Objectives** — approved research objectives.
4. **Dataset** — Iqro 3 scope, collection protocol, labels, QC, split, and secondary data.
5. **Methodology** — preprocessing, stage-1, stage-2, decoder, and ablation.
6. **Technology/libraries** — exact versions and runtime.
7. **Project structure** — actual folders and artifact locations.
8. **Installation/environment** — local and Colab instructions.
9. **How to run** — exact commands for data validation, training, evaluation, and prediction.
10. **Google Colab/Jupyter instructions** — upload/mount/run order and limitations.
11. **Workflow** — end-to-end pipeline.
12. **Results** — actual metrics, figures, and run IDs.
13. **Evaluation** — metric definitions and test protocol.
14. **Limitations** — dataset size, writer coverage, label policy, and generalization limits.
15. **Conclusion** — findings tied to objectives.
16. **Reproducibility information** — seeds, environment, data/config hashes, checkpoints, and rerun instructions.

README must not contain fictional commands, fictional metrics, or claims that demo artifacts are production results.

## 27. Final Project Execution Checklist

### Gate A — Before implementation

- [ ] PRD reviewed by user.
- [ ] D-01 through D-20 resolved or explicitly deferred.
- [ ] Official source priority and citation/template rules confirmed.
- [ ] Current code/notebook state and recovery decision confirmed.
- [ ] No source, dataset, notebook, or dependency is changed before approval.

### Gate B — Data readiness

- [ ] Iqro 3 inventory completed.
- [ ] Collection protocol and consent approved.
- [ ] Manifest and QC fields finalized.
- [ ] Sufficient writers/samples collected.
- [ ] Label and sequence policy frozen.
- [ ] Split and leakage audit passed.

### Gate C — Modeling readiness

- [ ] MobileNetV4 variant/checkpoint verified.
- [ ] Transfer learning source decision recorded.
- [ ] Preprocessing implemented and visualized.
- [ ] Baseline/ablation matrix approved.
- [ ] Forward, decoder, and metric tests pass.

### Gate D — Results readiness

- [ ] Stage-1 and stage-2 runs complete.
- [ ] Held-out evaluation complete.
- [ ] Exact match, positional accuracy, and CER reported.
- [ ] Error analysis and visualizations complete.
- [ ] Demo/pilot/production results separated.

### Gate E — Delivery readiness

- [ ] Notebook runs top-to-bottom from a fresh runtime.
- [ ] Artifacts reload successfully.
- [ ] Proposal, thesis, references, and appendices are consistent.
- [ ] README final describes actual implementation.
- [ ] Official UISI submission/publication requirements checked.
- [ ] Traceability matrix has no unexplained critical gap.

### Approval gate

Implementation may begin only after the user explicitly states:

> **“PRD disetujui, lanjut implementasi.”**

Until then, the project remains at the planning and documentation stage. No source code, notebook, dataset, dependency, or final README has been implemented or modified in this stage.
