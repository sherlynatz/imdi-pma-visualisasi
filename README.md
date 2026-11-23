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

- IMDI: Badan Pengembangan Sumber Daya Manusia Komunikasi dan Digital, Kementerian Komunikasi dan Digital. <https://imdi.sdmdigital.id/>
- Realisasi PMA dan PMDN: BKPM, <https://data.bkpm.go.id/visualisasi-detail/perkembangan-realisasi-investasi-oLSgf7G>
- Rata-rata lama sekolah: BPS, <https://sulsel.bps.go.id/id/statistics-table/2/Mjk5IzI%3D/rata-rata-lama-sekolah-rls-.html>
- - PDRB per kapita atas dasar harga berlaku (ribu rupiah): tabel BPS tiap provinsi (34 provinsi). Ubah angka pada `?year=` untuk memilih tahun 2022–2025.
  - Aceh: <https://aceh.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-aceh-province--thousand-rupiahs---2016.html?year=2022>
  - Sumatera Utara: <https://sumut.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sumatera-utara--ribu-rupiah---2018.html?year=2022>
  - Sumatera Barat: <https://sumbar.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sumatera-barat--ribu-rupiah---2017.html?year=2022>
  - Riau: <https://riau.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-riau--ribu-rupiah---2019.html?year=2022>
  - Kepulauan Riau: <https://kepri.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-kepulauan-riau--ribu-rupiah---2019.html?year=2022>
  - Jambi: <https://jambi.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-jambi--ribu-rupiah---2018.html?year=2022>
  - Sumatera Selatan: <https://sumsel.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sumatera-selatan--ribu-rupiah---2017.html?year=2022>
  - Bengkulu: <https://bengkulu.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-bengkulu-province--thousands-rupiahs---2023.html?year=2022>
  - Lampung: <https://lampung.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-lampung--ribu-rupiah---2018.html?year=2022>
  - Kepulauan Bangka Belitung: <https://babel.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-kepulauan-bangka-belitung--ribu-rupiah---2021.html?year=2022>
  - DKI Jakarta: <https://jakarta.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-dki-jakarta--ribu-rupiah---2017.html?year=2022>
  - Jawa Barat: <https://jabar.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-jawa-barat--ribu-rupiah---2017.html?year=2022>
  - Banten: <https://banten.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-banten-province--thousands-rupiahs---2023.html?year=2022>
  - Jawa Tengah: <https://jateng.bps.go.id/id/statistics-table/2/MTc0NiMy/-seri-2010--pdrb-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-jawa-tengah--ribu-rupiah-.html>
  - DI Yogyakarta: <https://yogyakarta.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-di-yogyakarta--ribu-rupiah---2020.html?year=2022>
  - Jawa Timur: <https://jatim.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-jawa-timur--ribu-rupiah---2019.html?year=2022>
  - Bali: <https://bali.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-bali-province--thousand-rupiahs---2017.html?year=2022>
  - Nusa Tenggara Barat: <https://ntb.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-nusa-tenggara-barat--ribu-rupiah---2019.html?year=2022>
  - Nusa Tenggara Timur: <https://ntt.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-nusa-tenggara-timur--ribu-rupiah---2018.html?year=2022>
  - Kalimantan Barat: <https://kalbar.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-kalimantan-barat-province--thousands-rupiahs---2016.html?year=2022>
  - Kalimantan Tengah: <https://kalteng.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-kalimantan-tengah--ribu-rupiah---2020.html?year=2022>
  - Kalimantan Selatan: <https://kalsel.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-kalimantan-selatan--ribu-rupiah---2018.html?year=2022>
  - Kalimantan Timur: <https://kaltim.bps.go.id/en/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-kalimantan-timur--ribu-rupiah---2023.html?year=2022>
  - Kalimantan Utara: <https://kaltara.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-kalimantan-utara-province--thousand-rupiahs---2019.html?year=2022>
  - Sulawesi Utara: <https://sulut.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-sulawesi-utara-province--thousands-rupiahs---2016.html?year=2022>
  - Gorontalo: <https://gorontalo.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-gorontalo--ribu-rupiah---2018.html?year=2022>
  - Sulawesi Tengah: <https://sulteng.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sulawesi-tengah--ribu-rupiah---2018.html?year=2022>
  - Sulawesi Selatan: <https://sulsel.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sulawesi-selatan--ribu-rupiah---2017.html?year=2022>
  - Sulawesi Barat: <https://sulbar.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-sulawesi-barat-province--thousand-rupiahs---2024.html?year=2022>
  - Sulawesi Tenggara: <https://sultra.bps.go.id/en/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-sulawesi-tenggara--ribu-rupiah---2021.html?year=2022>
  - Maluku: <https://maluku.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-maluku--ribu-rupiah---2019.html?year=2022>
  - Maluku Utara: <https://malut.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/per-capita-gross-regional-domestic-product-at-current-market-prices-by-regency-municipality-in-maluku-utara-province--thousand-rupiahs---2020.html?year=2022>
  - Papua: <https://papua.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-papua--ribu-rupiah---2017.html?year=2022>
  - Papua Barat: <https://papuabarat.bps.go.id/id/statistics-table/3/YWtoQlRVZzNiMU5qU1VOSlRFeFZiRTR4VDJOTVVUMDkjMw==/produk-domestik-regional-bruto-per-kapita-atas-dasar-harga-berlaku-menurut-kabupaten-kota-di-provinsi-papua-barat--ribu-rupiah---2023.html?year=2022>
- Kurs: Kurs Transaksi BI (USD), bi.go.id. <https://www.bi.go.id/id/statistik/informasi-kurs/transaksi-bi/Default.aspx>

Catatan pembersihan data lengkap ada di sheet `Catatan_Cleaning` pada file Excel.
