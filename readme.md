# UTS Data Aqcuisition & Management

## Profil Mahasiswa
| **Name**   | **Value**                            |
| ------- | --------------------------------- |
| Nama    | I Made Dio Kartiana Putra         |
| NIM     | 2501010142                        |
| Kelas   | F                                 |
| Jurusan | Informatika Manajemen Data Analis |


## Sumber Data
| Sumber | Judul | URL| Waktu Akses |
| :---: | --- | --- | :---: | 
| Kaggle | Bali Tourist Destinations (1000+ Places) - 2026 | https://www.kaggle.com/datasets/bertnardomariouskono/bali-tourist-destinations | 26 November 2026 |
| Portal Data KKP | Jumlah Kawasan Wisata Bahari yang dikelola oleh Kementerian Kelautan dan Perikanan | https://portaldata.kkp.go.id/api/portal/list_kawasan_bahari | 26 November 2026 |
| Satu Data Indonesia | Pencarian Dataset dengan Keyword "Budaya" | https://data.go.id/dataset?q=budaya | 26 November 2026 |

## Data Ethics Checklist
| Aspek | Status (Ya/Tidak/NA) |
| :--- | :---: |
| Sumber data dan URL dicantumkan | YA |
| Lisensi data diperiksa dan dicatat | YA |
| robots.txt / Terms of Service diperiksa | YA |
| Kolom PII diidentifikasi | TIDAK |
| PII dihapus, di-mask, atau di-pseudonimisasi | NA |
| Prinsip minimalisasi data diterapkan | YA |
| Potensi bias sampel dianalisis | NA |
| Tujuan penggunaan data dinyatakan eksplisit | NA |
| Rencana retensi dan penghapusan data ada | NA |

## Data Provenance Notes
### Berkas
#### A. Informasi Sumber Data
| Komponen           | Keterangan                                                              |
| :----------------- | :---------------------------------------------------------------------- |
| Nama sumber        | Kaggel                                                                  |
| Website            | https://www.kaggle.com                                                  |
| Halaman Target     | https://www.kaggle.com/datasets/martinsambulare/indonesia-tourism-and-financial-economic                         |
| Format Data | CSV                                                             |
| Bahasa pemrograman | Python 3.11                                                             |
| Library            | `Pandas`, `OS`, `Datetime` |
| Format output      | CSV                                                                     |
| Jenis Data      | `Terstruktur`                                                                     |

#### B. Informasi yang dikumpulkan
| Nama kolom | Keterangan |
| :--- | :--- |
| `id_tempat` | ID unik tempat wisata |
| `nama_tempat_wisata` | Nama tempat wisata |
| `kategori` | Kategori atau jenis tempat wisata |
| `kecamatan` | Nama kecamatan lokasi tempat wisata |
| `kabupaten_kota` | Nama kabupaten atau kota lokasi tempat wisata |
| `rating` | Skor rating rata-rata tempat wisata |
| `jumlah_rating` | Total jumlah pengguna yang memberikan rating |
| `latitude` | Koordinat garis lintang lokasi tempat wisata |
| `longitude` | Koordinat garis bujur lokasi tempat wisata |
| `link_google_maps` | Tautan menuju lokasi tempat wisata di Google Maps |
| `link_gambar` | Tautan gambar tempat wisata |

#### C. Tahapan pengumpulan data
| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Impor library | Mengimpor library `pandas`, `os`, dan `datetime` untuk kebutuhan pengolahan data serta pengelolaan file. |
| 2 | Pembacaan dataset | Memuat dataset mentah dari file `bali_tourist_destination.csv` pada direktori `../data/raw/` ke dalam DataFrame menggunakan Pandas. |
| 3 | Pemeriksaan struktur data | Memeriksa daftar nama kolom dan dimensi awal dataset yang terdiri dari 1.452 baris dan 11 kolom. |
| 4 | Seleksi kolom | Menghapus kolom `id_tempat` dan `link_gambar` yang tidak digunakan sehingga menyisakan 9 kolom utama. |
| 5 | Penyimpanan dataset | Menyimpan hasil akhir pengolahan data ke dalam format CSV dengan penamaan file berbasis waktu (*timestamp*) di direktori `../data/process/`. |



### REST API
#### A. Informasi Sumber Data

| Komponen | Keterangan |
| :--- | :--- |
| Nama sumber | REST API Wisata Bahari Indonesia |
| Website | Mengacu pada variabel lingkungan `URL_API` |
| Halaman Target | Endpoint REST API (`URL_API`) dengan parameter `limit=200` |
| Format Data | JSON (respons REST API) |
| Bahasa pemrograman | Python 3.11 (3.11.4) |
| Library | `Requests`, `Pandas`, `JSON`, `OS`, `Datetime` |
| Format output | CSV |
| Jenis Data | `Semi Terstruktur` |

#### B. Informasi yang dikumpulkan

| Nama kolom | Keterangan |
| :--- | :--- |
| `id` | ID unik data kelompok pengelola wisata bahari |
| `tahun` | Tahun pembentukan atau pencatatan data kelompok pengelola |
| `provinsi` | Nama provinsi lokasi wisata bahari |
| `id_prov` | Kode ID wilayah provinsi |
| `kabupaten` | Nama kabupaten atau kota lokasi wisata bahari |
| `id_kab` | Kode ID wilayah kabupaten atau kota |
| `kecamatan` | Nama kecamatan lokasi wisata bahari |
| `id_kec` | Kode ID wilayah kecamatan |
| `desa` | Nama desa atau kelurahan lokasi wisata bahari |
| `id_desa` | Kode ID wilayah desa atau kelurahan |
| `kelompok_pengelola` | Nama kelompok masyarakat atau lembaga pengelola wisata bahari |
| `lat` | Koordinat lokasi (tercatat nilai garis bujur pada respons API) |
| `long` | Koordinat lokasi (tercatat nilai garis lintang pada respons API) |
| `created_on` | Waktu (*timestamp*) pembuatan rekaman data pada sistem |
| `created_by` | Identitas pembuat rekaman data pada sistem |
| `updated_on` | Waktu (*timestamp*) pembaruan terakhir rekaman data |
| `updated_by` | Identitas pengguna yang terakhir memperbarui rekaman data |

#### C. Tahapan pengumpulan data

| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Impor library | Mengimpor library `requests`, `pandas`, `json`, `os`, dan `datetime` untuk kebutuhan pengambilan data API, pengolahan JSON/DataFrame, serta pengelolaan file. |
| 2 | Pengambilan data API | Mengambil URL endpoint dari environment variable `URL_API`, mengirim permintaan HTTP `GET` dengan parameter `limit=200` dan *timeout* 30 detik, memvalidasi status respons (`200 OK`), serta memetakannya ke format JSON. |
| 3 | Konversi & penyimpanan data mentah | Mengekstrak array `"data"` dari respons JSON menjadi DataFrame Pandas (`df`) dan menyimpannya ke direktori `../data/raw/` dengan penamaan `wisata_bahari_indonesia_<DD-MM-YYYY_HH-MM>.csv`. |
| 4 | Pemeriksaan struktur data | Memeriksa daftar nama kolom (17 kolom), dimensi dataset (`141` baris dan `17` kolom), serta membandingkan jumlah data dengan nilai `total_count` dari respons API (`141` data). |
| 5 | Seleksi kolom & pengurutan data | Menghapus 4 kolom metadata (`created_on`, `created_by`, `updated_on`, dan `updated_by`) sehingga menyisakan 13 kolom utama (`df_cropped`), serta membuat versi data yang diurutkan berdasarkan kolom `tahun` secara menaik/terlama (`df_order_by_year_old`). |
| 6 | Penyimpanan dataset hasil olahan | Menyimpan dua file hasil pengolahan ke format CSV berbasis waktu (*timestamp*) di direktori `../data/process/`, yaitu `wisata_bahari_indonesia_<DD-MM-YYYY_HH-MM>.csv` dan `wisata_bahari_indonesia_order-by-year_<DD-MM-YYYY_HH-MM>.csv`. |



### Web Scrapping
#### A. Informasi Sumber Data
| Komponen           | Keterangan                                                              |
| :----------------- | :---------------------------------------------------------------------- |
| Nama sumber        | Portal Satu Data Indonesia                                              |
| Website            | https://data.go.id/                                                     |
| Halaman Target     | https://data.go.id/dataset?q=budaya&perPage=100                         |
| Format Data | HTML                                                             |
| Bahasa pemrograman | Python 3.11                                                             |
| Library            | `Requests`, `BeautifulSoup`, `Pandas`, `OS`, `Datetime`, `RobotFileParser`, `URLJoin` |
| Format output      | CSV                                                                     |
| Jenis Data      | `Tidak Terstruktur`                                                                     |

#### B. Informasi yang dikumpulkan
| Nama kolom | Sumber HTML | Keterangan |
| :--- | :--- | :--- |
| `judul_dataset` | Tag `<h3>` | Judul dataset |
| `deskripsi` | `<div class="text-muted-foreground">` | Deskripsi dataset |
| `url_dataset` | Atribut `href` pada `<a>` | Tautan menuju halaman dataset |

#### C. Tahapan pengumpulan data
| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Pemeriksaan sumber | Membaca `robots.txt` dan memeriksa aturan crawling sebelum mengakses halaman target. |
| 2 | Pengambilan HTML | Menggunakan Requests untuk mengirim HTTP GET request ke halaman pencarian dataset budaya. |
| 3 | Parsing HTML | Menggunakan BeautifulSoup dengan parser `lxml` untuk membaca struktur HTML. |
| 4 | Ekstraksi informasi | Mengambil judul dari tag `<h3>`, deskripsi dari class `text-muted-foreground`, dan URL dari atribut `href`. |
| 5 | Pembentukan DataFrame | Menggabungkan hasil ekstraksi menjadi DataFrame menggunakan Pandas. |
| 6 | Pembersihan data | Menghapus duplikasi berdasarkan URL dataset dan memeriksa kelengkapan kolom. |
| 7 | Penyimpanan | Menyimpan hasil akhir dalam format CSV untuk proses pengolahan selanjutnya. |