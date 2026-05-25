# Issue: Merge and Clean Scraped Google Maps Reviews

## 1. Title & Description
**Title:** Data Consolidation and Cleaning for Google Maps Reviews.
**Description:** Proses ini bertujuan untuk menggabungkan banyak file CSV hasil scraping ke dalam satu file utama dan melakukan pembersihan data dasar agar siap digunakan untuk tahap analisis atau pemodelan selanjutnya.

## 2. Requirements
Gunakan library berikut:
- `pandas`
- `os`
- `glob`

## 3. Step-by-step Implementation (Per Cell)

### Cell 1: Import Libraries
- Import `pandas`, `os`, dan `glob`.

### Cell 2: Setup Path & File Discovery
- Tentukan path folder input: `/data-scrap/`.
- Gunakan `glob.glob()` untuk mengambil semua file dengan ekstensi `.csv` di dalam folder tersebut.
- Cetak jumlah file yang ditemukan untuk verifikasi.

### Cell 3: Data Merging
- Buat list kosong untuk menampung DataFrame.
- Lakukan loop pada list file CSV, baca setiap file dengan `pd.read_csv()`, dan tambahkan ke dalam list.
- Gabungkan semua DataFrame menjadi satu menggunakan `pd.concat(..., ignore_index=True)`.
- Tampilkan ukuran (shape) DataFrame gabungan.

### Cell 4: Initial Data Inspection
- Tampilkan 5 baris pertama (`head()`).
- Tampilkan informasi ringkas DataFrame (`info()`).
- Cek jumlah *missing values* di setiap kolom.

### Cell 5: Column Renaming & Normalization
- Ubah semua nama kolom menjadi **lowercase**.
- Ganti spasi pada nama kolom dengan **underscore** (misal: `Nama Pengulas` -> `nama_pengulas`).
- Tampilkan nama kolom yang baru.

### Cell 6: Data Deduplication
- Identifikasi dan hapus data duplikat menggunakan `drop_duplicates()`.
- Fokus pada kombinasi kolom `nama_pengulas` dan `ulasan`.
- Tampilkan jumlah baris yang dihapus.

### Cell 7: Handling Missing Values
- Hapus baris yang memiliki nilai kosong pada kolom `ulasan` atau `rating` menggunakan `dropna()`.
- Pastikan tidak ada data yang "rusak" atau kosong secara signifikan.

### Cell 8: Final Data Validation
- Tampilkan ringkasan statistik atau distribusi `rating`.
- Tampilkan `unique values` jika diperlukan untuk memastikan konsistensi data.

### Cell 9: Data Export
- Buat folder `/data/processed/` jika belum ada (gunakan `os.makedirs`).
- Simpan DataFrame akhir ke `/data/processed/cleaned_data.csv` dengan parameter `index=False`.

## 4. Output
- File Jupyter Notebook: `process_data.ipynb`.
- File Output: `data/processed/cleaned_data.csv`.

## 5. Acceptance Criteria
- Kode dapat dieksekusi dari awal (Restart & Run All) tanpa error.
- Semua file CSV di folder `data-scrap` berhasil digabungkan.
- Nama kolom sesuai instruksi (lowercase & snake_case).
- Tidak ada data duplikat di hasil akhir.
- Data tersimpan dengan benar di folder output yang ditentukan.
