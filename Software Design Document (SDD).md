# SOFTWARE DESIGN DOCUMENT (SDD)

## 1. PENDAHULUAN

### 1.1 Tujuan Penulisan Dokumen
Dokumen Software Design Description (SDD) ini bertujuan untuk memberikan penjelasan lengkap mengenai langkah-langkah desain dan proses pengembangan website MnM Thrifting. Memastikan elemen desain mendukung pencapaian tujuan projek. Selain itu, dokumen ini berfungsi sebagai panduan utama bagi seluruh anggota dalam memahami arsitektur dan desain aplikasi. Dengan adanya dokumen ini, diharapkan pengembangan
website dapat berjalan terstruktur, efisien, dan sesuai dengan kebutuhan pengguna.

### 1.2 Lingkup Masalah
Website MnM Thrifting dirancang untuk menjadi platform publik yang
mempermudah konsumen dalam mencari, memilih, dan membeli pakaian
bekas berkualitas. Sistem ini menyediakan informasi produk secara lengkap,
termasuk harga, dan kondisi barang, serta memberikan akses mudah ke katalog
produk melalui fitur pencarian dan brand. Selain itu, website ini
menghubungkan konsumen langsung dengan admin melalui kontak yang
tersedia di platform yang langsung terhubung ke Whatsapp.

### 1.3 Definisi dan Istilah
- **SPMP**: Software Project Management Plan  
- **SRS**: Software Requirements Specification  
- **SDD**: Software Design Description  

### 1.4 Referensi
- IEEE Draft Standard for Software Design Descriptions. IEEE P1016/D5.0  
- Eka Ismantohadi & Moh. Yani, SDD (2018)  
- [GitHub firstiaulyaa](https://github.com/firstiaulyaa/RPL-D-5/blob/master/SDD.md)  
- [GitHub oksar3110-0110](https://github.com/oksar3110-0110/RPL-D-7/blob/master/SDD.md)

### 1.5 Ikhtisar Dokumen
| BAB                                 	| ISI                                                                                                                                                                                                                                                                                                    	|
|-------------------------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Bab I                               	| 1.1 Tujuan Penulisan Dokumen 1.2 Lingkup Masalah 1.3 Definisi dan Istilah 1.4 Referensi 1.5 Ikhtisar Dokumen                                                                                                                                                                                           	|
| Bab II Deskripsi Perancangan Global 	| 2.1 Rancangan Lingkungan Implementasi 2.2.2 Conceptual Data Model 2.2.3 Physical Data Model 2.2.4 Daftar Tabel Aplikasi 2.3 Deskripsi Modul                                                                                                                                                            	|
| Bab III Deskripsi Perancangan Rinci 	| 2.3 Deskripsi Modul Bab III Deskripsi Perancangan Rinci 3.1 Diagram Konteks 3.1.1 DFD Level 0 3.1.2 DFD Level 1 Proses M 3.1.3 DFD Level 1 Proses N 3.2 Deskripsi Rinci Tabel 3.2.1 Table A 3.2.2 Table B 3.3 Deskripsi Rinci Modul 3.3.1 D Modul 3.3.1.1 Fungsi Modul 3.3.1.2 Spesifikasi Layar Utama 	|

## 2. DESKRIPSI RANCANGAN GLOBAL
### 2.1 Rancangan Lingkungan Implementasi
#### 2.1.1 Rancangan Kebutuhan
| No. 	| Rancangan Kebutuhan 	| Keterangan                                                                                                                                                                                                            	|
|-----	|---------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| 1.  	| Sistem Operasi      	| • UML dibuat Menggunakan Draw.io dan Visual  Paradigm CE • Design Aplikasi dibuat Menggunakan Canva • Prototyping Aplikasi dibuat Menggunakan Figma • Pembuatan laporan dibuat menggunakan Microsoft Word 2013 & 2024 	|
| 2.  	| DBMS                	| MySQL                                                                                                                                                                                                                 	|
| 3.  	| Filling System      	| Dokumen-dokumen dan program disimpan dalam harddisk internal pada laptop masing- masing anggota                                                                                                                       	|
| 4.  	| Bahasa Pemrograman  	| Menggunakan PHP sebagai bahasa pemrograman utama untuk pengembangan website.                                                                                                                                          	|

#### 2.1.2 Tools yang digunakan
Laptop sebanya 4 unit

### 2.2 Deskripsi Data
Tabel Admin
| **Data Item** | **Type**  | **Volume** | **Laju**       | **Primary Key** | **Constrain Integrity** | **Deskripsi**                                                  |
|---------------|-----------|------------|----------------|------------------|--------------------------|----------------------------------------------------------------|
| id_admin      | integer   | 10         | Primary Key    | Ya               | Auto Increment           | Nomor auto increment id_admin                                  |
| username      | varchar   | 30         | Tidak          | Tidak            | -                        | Berisi username admin untuk dapat mengakses dashboard          |
| password      | varchar   | 8          | Tidak          | Tidak            | -                        | Berisi password admin untuk dapat mengakses dashboard          |
| nama          | varchar   | 30         | Tidak          | Tidak            | -                        | Berisi nama admin                                              |
| email         | varchar   | 50         | Tidak          | Tidak            | -                        | Berisi Alamat email admin                                      |
| gambar        | blob      | -          | Tidak          | Tidak            | -                        | URL atau path untuk foto profil admin                          |

Tabel Pelanggan
| **Data Item**    | **Type**  | **Volume** | **Laju**       | **Primary Key** | **Constrain Integrity** | **Deskripsi**                                                  |
|------------------|-----------|------------|----------------|------------------|--------------------------|----------------------------------------------------------------|
| id_pelanggan     | integer   | 10         | Primary Key    | Ya               | Auto Increment           | Nomor auto increment id_pelanggan                              |
| username         | varchar   | 10         | Tidak          | Tidak            | -                        | Berisi Nama pelanggan                                           |
| password         | varchar   | 8          | Tidak          | Tidak            | -                        | Kata sandi pelanggan                                            |
| nama             | varchar   | 30         | Tidak          | Tidak            | -                        | Berisi nama admin (mungkin maksudnya pelanggan)                |
| no_telpon        | integer   | 15         | Tidak          | Tidak            | -                        | Berisi Nomor telpon pelanggan                                   |
| gambar           | blob      | -          | Tidak          | Tidak            | -                        | URL atau path untuk gambar produk                               |
| alamat           | varchar   | 100        | Tidak          | Tidak            | -                        | Berisi Alamat pelanggan                                         |

Tabel Produk
| **Data Item** | **Type**  | **Volume** | **Laju**       | **Primary Key** | **Constrain Integrity** | **Deskripsi**                                                 |
|---------------|-----------|------------|----------------|------------------|--------------------------|---------------------------------------------------------------|
| id_produk     | Integer   | 10         | Primary Key    | Ya               | Auto Increment           | Nomor auto increment id_produk                                |
| nama          | Varchar   | 50         | Tidak          | Tidak            | -                        | Berisi Nama produk                                             |
| harga         | decimal   | 10,2       | Tidak          | Tidak            | -                        | Berisi Harga produk                                            |
| stok          | integer   | 5          | Tidak          | Tidak            | -                        | Berisi Jumlah stok Produk                                      |
| kategori      | varchar   | 20         | Tidak          | Tidak            | -                        | Berisi Kategori produk                                         |
| brand         | varchar   | 20         | Tidak          | Tidak            | -                        | Berisi Brand produk                                            |
| gambar        | blob      | -          | Tidak          | Tidak            | -                        | URL atau path untuk gambar produk                             |
| status        | varchar   | 10         | Tidak          | Tidak            | -                        | Berisi Status dari Produk (Ready / Tidak)                      |
