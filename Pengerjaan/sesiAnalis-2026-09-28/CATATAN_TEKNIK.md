# Catatan Teknis Akhir Sesi

## Kontrak data

- Input: satu citra PNG/JPEG hasil canvas digital.
- Label: 2–3 huruf.
- Urutan string: logis kanan ke kiri.
- Split: `train`, `validation`, `test`.
- Penulis yang sama tidak boleh muncul pada split berbeda.
- Bekas garis titik-titik canvas diperbolehkan.

## Kontrak output

Whitelist tunggal:

```text
ابتثجحخدذرزسشصضطظعغفقكلمنهوي
```

- Jumlah kelas huruf: 28.
- CTC blank hanya indeks internal.
- Harakat, tanda baca, huruf Latin, transliterasi, dan hamza terpisah tidak boleh keluar.
- Prediksi JSON hanya memuat `prediction` berisi urutan huruf Hijaiyah.

## Arsitektur

```text
canvas → grayscale/crop/resize/normalize
      → MobileNetV4
      → auxiliary multi-label BCE
      → feature map
      → reverse spatial order
      → LSTM searah
      → CTC
      → greedy decode
```

- Backbone produksi: `mobilenetv4_conv_small.e3600_r256_in1k`.
- Bobot baseline: ImageNet.
- Ukuran input: grayscale 256×64.
-CTC label length: 2–3.
- Metrik: exact sequence match, character accuracy, CER.
- Transfer learning harus dilatih dua tahap: backbone dahulu, lalu CNN-LSTM end-to-end.

## Keputusan sementara

-CTC dipilih agar tidak perlu bounding box per huruf.
- LSTM searah menjadi default agar arah lebih mudah diaudit.
- BiLSTM, bobot Hijja2, dan ablation learning rate adalah eksperimen lanjutan.
- Data sintetis hanya untuk validasi software.
- Gamifikasi, integrasi aplikasi, hukum bacaan, dan estetika tulisan di luar lingkup.
