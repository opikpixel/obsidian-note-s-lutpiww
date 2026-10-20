# Panduan Layanan Penyimpanan dan Database AWS

## Glosarium Istilah Data

* **DataFrame**: Struktur data tabel dua dimensi (baris dan kolom) untuk memuat, memanipulasi, dan menganalisis data.


* **Data Distribution**: Pola sebaran nilai dalam himpunan data yang memperlihatkan frekuensi kemunculan nilai.


* **Data Engineering**: Disiplin ilmu perancangan dan pembangunan sistem pengumpulan, penyimpanan, serta transformasi data mentah.


* **Data Factory**: Layanan orkestrasi, ekstraksi, dan transformasi pergerakan data.


* **Data Ingestion & Integration**: Proses transfer data dari sumber ke penyimpanan, serta penyatuan berbagai sumber data ke satu tampilan kohesif.


* **Data Mesh**: Paradigma arsitektur data terdistribusi yang memperlakukan data sebagai produk berbasis domain bisnis.


* **Data Science & Visualization**: Ekstraksi wawasan melalui metode ilmiah dan algoritma, serta penyajian data secara visual melalui diagram grafik.


* **Data Warehousing**: Sistem pengelolaan dan penyimpanan data historis lintas sumber untuk analitik bisnis.


* **Delta Table & delta-parquet**: Format penyimpanan data tabel default di OneLake berbasis Parquet dengan kapabilitas transaksi ACID dan fleksibilitas skema.


* **Deployment**: Peletakan model machine learning ke lingkungan produksi untuk melayani prediksi.



---

## Layanan Penyimpanan AWS (Storage)

### 1. Block Storage: Instance Store vs Amazon EBS

* **Instance Store**:
* Penyimpanan tingkat blok yang bersifat sementara (*ephemeral*) dan terpasang secara fisik pada mesin *host* EC2.


* Data terhapus otomatis saat EC2 dihentikan (*stopped*) atau diakhiri (*terminated*).


* Cocok untuk *cache*, *buffer*, data *scratch*, atau data temporer yang mudah direproduksi.




* **Amazon Elastic Block Store (Amazon EBS)**:
* Layanan *block-level storage* virtual yang persisten dan terpisah dari siklus hidup *host* EC2.


* Beroperasi pada tingkat Availability Zone (AZ) sehingga EC2 dan volume EBS harus berada di AZ yang sama.


* Mendukung pencadangan bertahap (*incremental backup*) menggunakan EBS Snapshot, di mana hanya blok data yang berubah (*delta*) yang disimpan.





### 2. Object Storage: Amazon S3 (Simple Storage Service)

Menyimpan data sebagai objek di dalam *bucket* tanpa batasan kapasitas total. Setiap objek dapat berukuran hingga 5 TB dan memiliki URL unik, metadata, serta kunci identitas.

* **S3 Standard**: Ketahanan data 99,999999999% (11 nines), replikasi minimal di 3 Availability Zone, cocok untuk web hosting statis dan akses rutin.


* **S3 Standard-Infrequent Access (Standard-IA)**: Biaya penyimpanan lebih hemat untuk data yang jarang diakses namun memerlukan latensi pengambilan cepat.


* **S3 One Zone-Infrequent Access (One Zone-IA)**: Menyimpan data hanya pada satu AZ untuk efisiensi biaya; berisiko jika AZ mengalami gangguan.


* **S3 Intelligent-Tiering**: Pemindahan kelas otomatis antara Standard dan Standard-IA jika data tidak disentuh selama 30 hari berturut-turut.


* **S3 Glacier Flexible Archive**: Pengarsipan jangka panjang dengan waktu akses hitungan menit hingga jam; mendukung *Vault Lock Policy* (*Write Once, Read Many*).


* **S3 Glacier Deep Archive**: Opsi pengarsipan dengan biaya terendah dengan waktu pengambilan 12 hingga 48 jam.


* **S3 Lifecycle Policies**: Pengaturan otomatisasi siklus hidup data untuk transisi antar-kelas penyimpanan secara terjadwal.



### 3. File Storage: Amazon EFS (Elastic File System)

* Sistem file terkelola berbasis Linux yang dapat diakses secara bersamaan oleh ribuan instans EC2.


* Merupakan sumber daya tingkat Regional (*Regional resource*) yang tersimpan redundan di beberapa AZ.


* Melakukan penyesuaian kapasitas (*auto-scaling*) elastis otomatis hingga skala petabyte tanpa interupsi performa.



### Komparasi Amazon EBS vs Amazon S3

| Parameter | Amazon EBS | Amazon S3 |
| --- | --- | --- |
| **Model Penyimpanan** | *Block-level storage*<br> | *Object-level storage*<br> |
| **Batas Ukuran** | Volume hingga 16 TB

 | Tanpa batas total; objek maks 5 TB

 |
| **Perilaku Modifikasi** | Memperbarui blok data yang berubah saja

 | Menimpa keseluruhan file objek

 |
| **Skema Infrastruktur** | Perlu dipasangkan ke instans EC2

 | *Serverless*, berbasis web/API mandiri

 |
| **Kasus Penggunaan** | Sistem operasi, database aktif, pengeditan file besar

 | Hosting web statis, media penyimpanan file, backup arsip

 |

---

## Layanan Database AWS

### 1. Database Relasional: Amazon RDS & Aurora

Mendukung model relasional (RDBMS) berbasis skema terstruktur dengan kueri SQL. Layanan terkelola ini menyediakan pencadangan otomatis, penambalan sistem, replika baca, dan pemulihan bencana.

* **Dukungan Mesin Database Amazon RDS**: Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, dan Microsoft SQL Server.


* **Amazon Aurora**:
* Database relasional performa tinggi kelas *enterprise* yang kompatibel penuh dengan MySQL (hingga 5x lebih cepat) dan PostgreSQL (hingga 3x lebih cepat).


* Menghadirkan performa setara database komersial dengan 1/10 biaya.


* Mendukung pencadangan kontinu ke Amazon S3 dan replikasi hingga 15 *read replicas*.





### 2. Database Non-Relasional: Amazon DynamoDB

* Database NoSQL *serverless* terkelola penuh dengan format *key-value* dan dokumen.


* Skema data fleksibel di mana setiap baris data (*item*) tidak diwajibkan memiliki atribut yang seragam.


* Menawarkan waktu respons konsisten dalam satuan milidetik pada skala transaksi masif di lintas Availability Zone.



### Komparasi Amazon RDS vs Amazon DynamoDB

| Parameter | Amazon RDS | Amazon DynamoDB |
| --- | --- | --- |
| **Paradigma Data** | Relasional (SQL)

 | Non-relasional / NoSQL (*key-value*)

 |
| **Struktur Skema** | Tetap (*rigid*), relasi antartabel kompleks

 | Fleksibel, tanpa skema kaku

 |
| **Skalabilitas** | Terbatas pada kapasitas komputasi instans

 | Skalabilitas horisontal otomatis hingga petabyte

 |
| **Kasus Penggunaan** | Sistem inventaris, ERP, kueri relasi transaksional

 | Data profil, katalog produk, sesi web latensi rendah

 |

### 3. Analitik & Data Warehousing: Amazon Redshift

* Layanan *data warehouse* berbasis SQL yang dioptimalkan untuk analitik *Big Data* dan *Business Intelligence* (BI) historis.


* Memiliki arsitektur node terdistribusi yang mampu memproses kueri hingga 10 kali lebih cepat dibanding database tradisional pada beban kerja analitik.


* Fitur **Amazon Redshift Spectrum** memungkinkan eksekusi kueri langsung terhadap data tidak terstruktur skala *exabyte* di Amazon S3 *data lake*.



---

## Migrasi Database: AWS Database Migration Service (AWS DMS)

AWS DMS memindahkan database ke AWS secara aman dengan mempertahankan operasional database sumber guna meminimalkan *downtime*.

* **Migrasi Homogen**: Sumber dan target database menggunakan mesin yang identik (misal: MySQL lokal ke Amazon RDS MySQL), skema dan kode dapat berpindah langsung.


* **Migrasi Heterogen**: Sumber dan target database menggunakan mesin yang berbeda (misal: Oracle ke Aurora PostgreSQL). Memerlukan **AWS Schema Conversion Tool (AWS SCT)** untuk mengonversi skema dan tipe data sebelum migrasi dijalankan melalui DMS.


* **Fungsi Tambahan**: Replikasi data berkelanjutan untuk *disaster recovery*, sinkronisasi lingkungan pengujian, dan konsolidasi beberapa database.



---

## Layanan Database Khusus & Akselerator

### 1. Database Sesuai Kebutuhan Khusus

* **Amazon DocumentDB**: Database dokumen terkelola yang kompatibel dengan API MongoDB untuk beban kerja katalog dan manajemen konten.


* **Amazon Neptune**: *Graph database engine* performa tinggi untuk mengelola grafik hubungan yang rumit, seperti mesin rekomendasi, deteksi penipuan, dan media sosial.


* **Amazon Managed Blockchain**: Pembuatan dan pengelolaan jaringan buku besar terdesentralisasi (*decentralized ownership*) menggunakan kerangka kerja sumber terbuka.


* **Amazon QLDB (Quantum Ledger Database)**: Buku besar terpusat (*centralized ownership*) yang bersifat *immutable*, transparan, dan dapat diverifikasi secara kriptografis untuk riwayat audit perbankan/finansial.



### 2. Akselerator Caching

* **Amazon ElastiCache**: *In-memory cache* terkelola untuk mempercepat pembacaan data aplikasi melalui mesin **Redis** atau **Memcached**.


* **Amazon DynamoDB Accelerator (DAX)**: Lapisan *in-memory cache* bawaan (*native*) yang menurunkan waktu respons baca Amazon DynamoDB dari milidetik menjadi mikrodetik.