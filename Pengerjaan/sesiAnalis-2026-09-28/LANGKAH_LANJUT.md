# Langkah Lanjut Aman

## Sesi berikutnya

### 1. Pastikan folder project tersedia

Periksa tanpa menghapus apa pun:

```powershell
Get-ChildItem -LiteralPath "C:\Users\fabia\Documents\Kuliah\Skripsi\code\Pengerjaan" -Force
```

Jika hanya folder `sesiAnalis-2026-09-28` yang ada, gunakan langkah rekonstruksi. Jangan menghapus arsip ini.

### 2. Rekonstruksi struktur minimum

Buat folder berikut jika belum ada:

```text
Pengerjaan/
├── notebooks/
├── configs/
├── data/raw/
├── data/demo/
├── checkpoints/
├── outputs/
├── artifacts/
├── src/hijaiyah_ocr/
├── tests/
└── dokumentasi/
```

### 3. Pulihkan implementasi

Gunakan `RENCANA_NOTEBOOK_COLAB.md` dan riwayat di `STATUS_SESI.md` untuk membangun ulang package. Prioritaskan modul berikut:

- `constants.py` — whitelist 28 huruf dan validator.
- `manifest.py` — JSONL dan validasi participant-wise.
- `preprocess.py` — grayscale, crop, resize, augmentasi.
- `model.py` — MobileNetV4, auxiliary head, LSTM.
- `metrics.py` — CTC decode, exact match, CER.
- `training.py` — stage 1, stage 2, evaluasi, prediksi.
- `demo.py` — generator data sintetis.
- `cli.py` — perintah bantu.

### 4. Buat environment

```powershell
cd "C:\Users\fabia\Documents\Kuliah\Skripsi\code\Pengerjaan"
uv venv --python 3.12 .venv
uv pip install --python ".venv\Scripts\python.exe" -e ".[dev]"
```

### 5. Jalankan validasi lebih dahulu

```powershell
.\.venv\Scripts\python.exe -m pytest
.\.venv\Scripts\ruff.exe check .
.\.venv\Scripts\mypy.exe src
```

Jangan lanjut ke training bila salah satu perintah gagal.

### 6. Jalankan notebook

```powershell
.\.venv\Scripts\jupyter.exe nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=1200 notebooks\training_hijaiyah_colab.ipynb
```

Awalnya gunakan `USE_DEMO_DATA = True`, `USE_PRETRAINED = False` untuk memeriksa pipeline. Setelah itu gunakan `USE_PRETRAINED = True` untuk transfer learning.

### 7. Beralih ke data nyata

- Siapkan `data/raw/manifest.jsonl` dan citra.
- Pastikan satu writer hanya satu split.
- Pastikan label hanya 2–3 huruf whitelist.
- Ubah `USE_DEMO_DATA = False` dan `REAL_MANIFEST_PATH`.
- Jalankan notebook ulang dan simpan hasilnya sebagai eksperimen baru.

### 8. Update arsip

Tambahkan tanggal, command, hasil, dan kendala baru ke `STATUS_SESI.md` atau buat folder `sesiAnalis-YYYY-MM-DD` berikutnya. Jangan menimpa arsip lama.
