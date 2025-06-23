# Sistem Case-Based Reasoning (CBR) – Putusan Pengadilan

## Deskripsi
Proyek ini merupakan implementasi sistem Case-Based Reasoning (CBR) sederhana untuk mendukung analisis putusan pengadilan berdasarkan data dari Direktori Putusan Mahkamah Agung Republik Indonesia.

## Install Dependensi

```bash
pip install -r requirements.txt
```

## Menjalankan Pipeline

1. Unduh file putusan dari Direktori Putusan MA.
2. Jalankan `Script_01_base.ipynb` untuk ekstraksi dan pembersihan (cleaning) dokumen.
3. Jalankan `Script_02_representation.ipynb` untuk ekstraksi metadata dari dokumen, termasuk:
   - Nomor perkara
   - Nama terdakwa
   - Pekerjaan terdakwa
   - Tindak pidana
   - Pasal
   - Penuntut umum
   - Tanggal putusan
   - Amar putusan
   - Ringkasan barang bukti
   - Teks lengkap
4. Jalankan `Script_03_retrieval.ipynb` untuk membuat embedding dokumen dan melakukan retrieval kasus mirip menggunakan IndoBERT.
5. Jalankan `Script_04_predict.ipynb` untuk memprediksi amar putusan berdasarkan solusi dari top-k kasus mirip.
6. Jalankan `Script_05_evaluation.ipynb` untuk menghitung metrik evaluasi berupa akurasi, presisi, recall, dan F1-score.

### Contoh perintah (jika menggunakan script Python)

```bash
python Script_03_retrieval.py
```

> Jika menggunakan Jupyter Notebook, cukup buka dan jalankan sel-sel notebook sesuai urutan.

## Struktur Folder

```
/data/pdf/           → Dokumen putusan asli dalam format PDF  
/data/convert/       → File hasil konversi PDF ke teks mentah (.txt)  
/data/raw/           → File teks hasil cleaning  
/data/processed/     → File JSON/CSV berisi hasil ekstraksi metadata dan representasi kasus  
/data/eval/          → File query uji dan hasil evaluasi (metrics)  
/data/results/       → File hasil prediksi (`predictions.csv`)  
/notebooks/          → Jupyter notebook per tahap CBR  
```
NB: Ekstrak cases.zip pada folder /data/processed terlebih dahulu sebelum menjalankan script
