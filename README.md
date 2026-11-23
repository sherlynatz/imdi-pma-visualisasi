# Visualisasi IMDI dan PMA Kabupaten/Kota 2022–2025

Kode pendukung jurnal **"Indeks Masyarakat Digital dan Penanaman Modal Asing: Visualisasi dan Analisis Data Panel Kabupaten/Kota"**
(Tugas Akhir Komunikasi dan Visualisasi Data Ekonomi, Universitas Brawijaya).

Skrip menghasilkan **6 gambar** dan **2 tabel (CSV)** yang sama persis dengan yang dimuat di jurnal.

| Berkas | Isi |
|---|---|
| `generate_figures.py` | Skrip lengkap (bisa dijalankan dari terminal, VS Code, atau Spyder) |
| `generate_figures.ipynb` | Versi notebook (Jupyter / Google Colab), grafik tampil langsung di bawah tiap sel |
| `data/` | Taruh file Excel data bersih (`SherlyNatasyaZahwa_245020101111033.xlsx`, sheet `Sheet 2`) |
| `figures/` | Hasil: `gambar1_tren.png` … `gambar6_koefisien.png`, `tabel1_statistik_deskriptif.csv`, `tabel2_koefisien_IMDI.csv` |
| `requirements.txt` | Pustaka Python yang dibutuhkan |

## Cara menjalankan

**Lokal (Python 3.9+)**
```bash
pip install -r requirements.txt
python generate_figures.py
# tanpa jendela grafik (hanya simpan file):
#   Windows (PowerShell):  $env:SHOW="0"; python generate_figures.py
#   macOS/Linux:           SHOW=0 python generate_figures.py
```

**Google Colab**
1. Unggah repositori ini ke GitHub, lalu buka `generate_figures.ipynb` di <https://colab.research.google.com> (menu *GitHub*), atau unggah notebook langsung.
2. Jalankan semua sel (*Runtime → Run all*). Bila file data belum ada, Colab akan meminta unggah file `.xlsx`.

**Jupyter / VS Code**: buka `generate_figures.ipynb` atau `generate_figures.py` (sel ditandai `# %%`) lalu *Run All*.

## Isi gambar

| Gambar | Jenis | Dibuat dari |
|---|---|---|
| 1 | Tren (time-series) rata-rata IMDI + empat pilar, dan total PMA | Data bersih langsung |
| 2 | Perbandingan (bar) PMA menurut kuartil IMDI | Data bersih langsung |
| 3 | Perbandingan (bar horizontal) 10 kab/kota dengan PMA terbesar | Data bersih langsung |
| 4 | Korelasi (scatter) IMDI vs ln PMA: gabungan dan dalam wilayah | Data bersih langsung |
| 5 | Korelasi (heatmap) | Data bersih langsung |
| 6 | Koefisien IMDI (selang kepercayaan 95%) pada 5 spesifikasi | Regresi OLS/FE yang dihitung ulang |

Bagian akhir skrip mencocokkan koefisien dan galat baku regresi di Python dengan output Stata pada laporan ekonometrika.

## Sumber data

- IMDI: Badan Pengembangan Sumber Daya Manusia Komunikasi dan Digital, Kementerian Komunikasi dan Digital. (isi tautan)
- Realisasi PMA dan PMDN: BKPM, <https://data.bkpm.go.id/visualisasi-detail/perkembangan-realisasi-investasi-oLSgf7G>
- Rata-rata lama sekolah: BPS, <https://sulsel.bps.go.id/id/statistics-table/2/Mjk5IzI%3D/rata-rata-lama-sekolah-rls-.html>
- PDRB per kapita: BPS. (isi tautan)
- Kurs: Kurs Transaksi BI (USD), bi.go.id. (isi tautan)

Catatan pembersihan data lengkap ada di sheet `Catatan_Cleaning` pada file Excel.
