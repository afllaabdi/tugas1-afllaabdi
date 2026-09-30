# Data Tugas 1

## Dataset yang Dipilih

| Item | Isi |
|---|---|
| Nama dataset | Corpus-Indonesia |
| Sumber dataset | Lyon28 (Hugging Face Datasets) |
| URL dataset | https://huggingface.co/datasets/Lyon28/Corpus-Indonesia |
| Format | Parquet |
| Lisensi/ketentuan pakai | Apache-2.0 |
| Jumlah file | 7 file Parquet (split `train`) |
| Ukuran total | 1.900.362.972 byte (sekitar 1,9 GB / 1,77 GiB) |
| Jumlah baris | 19.483.721 baris |
| Jumlah kolom | 1 kolom (`text`, tipe `String`) |
| Periode data | Tidak dinyatakan pada sumber |
| Unit analisis | Satu baris = satu dokumen/teks berbahasa Indonesia |

## Deskripsi Singkat

Corpus-Indonesia adalah kumpulan dokumen teks berbahasa Indonesia. Setiap baris berisi satu kolom `text`
berisi teks berbahasa Indonesia. Pada halaman Hugging Face dataset ini ditandai dengan task
`text-generation`, bahasa `Indonesian` (`id`), format `parquet`, kategori ukuran `10M - 100M` baris,
dan lisensi `apache-2.0`.

Dataset card (README) pada sumber tidak memuat deskripsi lebih lanjut; periode pengumpulan, sumber asli
teks, dan metode pengumpulan tidak dinyatakan pada sumber. Profiling terhadap file aktual di folder ini
dapat dilihat pada `notebooks/01_data_profiling.ipynb`.

## Struktur File

File diletakkan pada folder `data/raw/data/`:

```text
data/raw/data/
├── train-00000-of-00007.parquet
├── train-00001-of-00007.parquet
├── train-00002-of-00007.parquet
├── train-00003-of-00007.parquet
├── train-00004-of-00007.parquet
├── train-00005-of-00007.parquet
└── train-00006-of-00007.parquet
```

| File | Ukuran (byte) | Ukuran (MB) |
|---|---:|---:|
| train-00000-of-00007.parquet | 272.361.891 | 272,36 |
| train-00001-of-00007.parquet | 268.977.483 | 268,98 |
| train-00002-of-00007.parquet | 271.235.387 | 271,24 |
| train-00003-of-00007.parquet | 270.602.383 | 270,60 |
| train-00004-of-00007.parquet | 272.342.018 | 272,34 |
| train-00005-of-00007.parquet | 272.175.219 | 272,18 |
| train-00006-of-00007.parquet | 272.668.591 | 272,67 |
| **Total** | **1.900.362.972** | **1.900,36** |

## Cara Mendapatkan Dataset

### Opsi 1: huggingface-cli (disarankan)

Pastikan `huggingface_hub` terbaru terpasang, lalu jalankan dari root repository:

```bash
pip install -U "huggingface_hub[cli]"

huggingface-cli download Lyon28/Corpus-Indonesia \
  --repo-type dataset \
  --include "data/*.parquet" \
  --local-dir data/raw
```

Perintah tersebut menghasilkan folder `data/raw/data/` berisi 7 file Parquet sesuai struktur di atas.

### Opsi 2: Unduh manual per file

Buka https://huggingface.co/datasets/Lyon28/Corpus-Indonesia/tree/main/data
lalu unduh setiap file ke `data/raw/data/`. URL langsung per file berformat:

```text
https://huggingface.co/datasets/Lyon28/Corpus-Indonesia/resolve/main/data/train-0000X-of-00007.parquet
```

### Setelah data unduh

1. Jangan mengubah isi file mentah di `data/raw/`.
2. `DATA_PATH` pada `notebooks/01_data_profiling.ipynb` sudah menunjuk ke `data/raw/data/*.parquet`.

## Aturan Penyimpanan

- Jangan commit dataset mentah atau hasil olahan berukuran besar ke Git.
- Folder `data/raw/` sudah masuk `.gitignore` (`data/raw/*`); file Parquet tidak akan ter-commit.
- File pada `data/raw/` adalah data asli dan tidak boleh diubah, dipindah, atau dihapus.
- Simpan hasil transformasi yang dapat direproduksi pada `data/processed/`.
- Instruksi unduh dan informasi dataset tetap didokumentasikan di file ini.

## Tempat Mencari Dataset (referensi umum)

| Situs | Kegunaan |
|---|---|
| [Satu Data Indonesia](https://data.go.id/) | Portal data terbuka lintas instansi pemerintah Indonesia. |
| [Badan Pusat Statistik](https://www.bps.go.id/) | Statistik sosial, ekonomi, kependudukan, dan data wilayah. |
| [BMKG Data Online](https://dataonline.bmkg.go.id/) | Data cuaca, iklim, gempa bumi, dan observasi meteorologi. |
| [Hugging Face Datasets](https://huggingface.co/datasets) | Dataset publik yang dapat dicari berdasarkan topik, bahasa, atau ukuran. |
| [Kaggle Datasets](https://www.kaggle.com/datasets) | Katalog dataset publik; periksa lisensi dan dokumentasi pembuatnya. |
| [Google Dataset Search](https://datasetsearch.research.google.com/) | Mesin pencari untuk menemukan dataset dari berbagai portal. |
