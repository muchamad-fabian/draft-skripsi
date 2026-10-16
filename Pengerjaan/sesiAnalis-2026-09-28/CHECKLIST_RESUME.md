# Checklist Resume

## Sebelum mulai

- [ ] Baca `README.md` arsip.
- [ ] Baca `STATUS_SESI.md`.
- [ ] Pastikan `Pengerjaan` tidak dihapus.
- [ ] Jangan menjalankan perintah penghapusan massal.
- [ ] Periksa `git status` sebelum membuat perubahan.

## Setelah rekonstruksi

- [ ] `.venv` tersedia.
- [ ] `pyproject.toml` dan dependency terpasang.
- [ ] `constants.py` memiliki whitelist 28 huruf.
- [ ] Validator menolak harakat, Latin, dan hamza terpisah.
- [ ] Manifest memiliki validasi writer split.
- [ ] MobileNetV4 tersedia di `timm`.
- [ ] Notebook dapat menemukan `src`.

## Validasi wajib

- [ ] `pytest` lulus.
- [ ] `ruff check .` lulus.
- [ ] `mypy src` lulus.
- [ ] Notebook dieksekusi tanpa error.
- [ ] Checkpoint stage 1 dan stage 2 ada.
- [ ] Prediksi hanya huruf Hijaiyah whitelist.

## Data nyata

- [ ] Daftar kata Iqro 3 tersedia.
- [ ] Citra canvas tersedia.
- [ ] QC dua penverifikasi selesai.
- [ ] Split participant-wise selesai.
- [ ] Metrik demo tidak dipakai sebagai klaim skripsi.
