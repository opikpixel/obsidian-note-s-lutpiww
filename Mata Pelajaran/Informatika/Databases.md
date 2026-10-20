
> [!NOTE] Glosarium
**DataFrame**: Struktur data berbentuk tabel dua dimensi (baris dan kolom) yang digunakan untuk memuat, memanipulasi, dan menganalisis data di lingkungan notebook Fabric.
**Data Distribution**: Sebaran nilai-nilai dalam sebuah himpunan data yang menunjukkan seberapa sering setiap nilai muncul.
**Data Engineering**: Disiplin ilmu yang berfokus pada perancangan dan pembangunan sistem untuk mengumpulkan, menyimpan, dan mentransformasi data mentah.
**Data Factory**: Layanan dalam Fabric yang digunakan untuk mengambil, mentransformasi, dan mengorkestrasi pergerakan dan pemrosesan data.
**Data Ingestion**: Proses memuat atau mentransfer data dari satu atau lebih sumber ke sistem penyimpanan.
Data Integration: Proses menggabungkan data dari sumber yang berbeda menjadi satu tampilan yang seragam dan kohesif.
Data Mesh: Paradigma arsitektur data terdistribusi yang memperlakukan data sebagai produk, di mana kepemilikan dan penyediaan data dipegang oleh domain bisnis.
Data Science: Bidang interdisipliner yang menggunakan metode ilmiah, proses, algoritma, dan sistem untuk mengekstrak pengetahuan dan wawasan dari data.
Data Visualization: Representasi data secara grafis, seperti melalui bagan atau plot, untuk mempermudah pemahaman pola dan tren.
Data Warehousing: Sistem yang mengumpulkan, menyimpan, dan mengelola data historis dari berbagai sumber untuk mendukung analisis bisnis.
Data Wrangler: Alat bantu visual interaktif yang terintegrasi di notebook Microsoft Fabric untuk eksplorasi, pembersihan, dan transformasi data.
Delta Table: Tabel yang menggunakan format Delta Lake untuk penyimpanan data, menawarkan kemampuan transaksi ACID, versioning, dan skema yang fleksibel, dan merupakan dasar dari OneLake dan Lakehouse di Fabric.
delta-parquet: Format penyimpanan data default di OneLake untuk data tabular, yang menggabungkan format Parquet dengan kapabilitas transaksi Delta Lake.
Dependency: Modul, library, atau paket perangkat lunak lain yang dibutuhkan oleh sebuah program atau proyek agar dapat berfungsi dengan baik.
Deployment: Proses peletakan model machine learning yang telah dilatih ke dalam lingkungan produksi agar dapat digunakan untuk menghasilkan prediksi.
### Tujuan Pembelajaran

Pelajari modul ini sehingga Anda akan memahami bagaimana cara:

- Meringkas konsep dasar dari penyimpanan dan database.
- Menjelaskan manfaat Amazon Elastic Block Store (Amazon EBS).
- Menerangkan manfaat Amazon Simple Storage Service (Amazon S3).
- Menjelaskan manfaat Amazon Elastic File System (Amazon EFS).
- Merangkum berbagai solusi penyimpanan.
- Memaparkan manfaat Amazon Relational Database Service (Amazon RDS).
- Memaparkan manfaat Amazon DynamoDB.
- Menguraikan berbagai layanan database.

_Ready, Set, Go!_

  

### Pengenalan ke Penyimpanan dan Database

Oke, kembali ke skenario. Sekarang kedai kopi kita telah beroperasi dengan cukup baik. Kita punya banyak pelanggan yang puas.

Faktanya, kita juga telah mempunyai arsitektur yang elastis, dapat diskalakan, tahan akan bencana, dan secara biaya pun telah optimal. Bahkan, sekarang kita memiliki jaringan global yang sangat aman dan dapat diterapkan sepenuhnya secara terprogram.

Melihat semakin banyaknya pelanggan setia yang hadir ke kedai kopi, maka kita harus memberikan apresiasi kepada mereka. Tapi, berbentuk apa ya?

Hmm. Bagaimana dengan program loyalitas pelanggan? Kita bisa membagikan kartu stempel kepada mereka yang sering memesan kopi di tempat kita. Tetapi, jujur saja, kita tak akan dapat melacak kartu tersebut dan mengenal pelanggan kita dengan baik.

Jadi, sepertinya kita membutuhkan kartu digital yang dapat melacak riwayat pemesanan pelanggan (apa yang mereka pesan atau berapa banyak yang mereka beli). Dengan demikian, kartu ini akan membantu c_ustomer_ kita mendapat apresiasi terbaik atas loyalitas mereka. Kita pun jadi bisa mengenal basis pelanggan dengan lebih baik dan lebih mudah.

Nah, itu berarti kita akan membutuhkan penyimpanan dan database (basis data). Ingat, bukan sembarang database. Pilihlah penyimpanan dan database yang tepat sesuai dengan masing-masing kebutuhan Anda.

Mari kita pelajari tentang berbagai layanan AWS yang dapat membantu Anda membangun solusi data yang sempurna.
Instance Store dan Amazon Elastic Block Store (Amazon EBS)
Saat Anda menjalankan aplikasi di AWS, tentunya aplikasi tersebut memerlukan akses ke CPU, memori, jaringan, dan penyimpanan. Nah, untungnya, EC2 instance dapat memberikan akses ke semua komponennya. Untuk saat ini, mari kita fokus pada penyimpanan.

Ketika aplikasi berjalan di EC2 instance, mereka kerap kali membutuhkan akses ke block-level storage (penyimpanan tingkat blok).

Jika Anda kurang kenal dengan istilah block-level storage, maka anggaplah ia sebagai tempat menyimpan file. File adalah serangkaian byte (bita) yang disimpan di dalam blok pada disk.

Pada saat file pada disk tersebut diperbarui, ia tak akan menimpa seluruh rangkaian blok, melainkan memperbarui bagian yang berubah saja. Dengan sistem seperti ini, penyimpanan untuk aplikasi (database, perangkat lunak perusahaan, atau sistem file) jadi lebih efisien.

Hmm. Mungkin penjelasan di atas sangat teknis ya. Oke, mari kita sederhanakan. Apakah sekarang Anda sedang menggunakan laptop atau komputer pribadi?

Nah! Itu berarti Anda sedang mengakses block-level storage alias penyimpanan tingkat blok. Block-level storage dalam kasus ini adalah hard drive (cakram keras) di komputer Anda.

EC2 instance juga memiliki hard drive dengan beberapa tipe yang berbeda.



Instance Store
Instance store (tempat penyimpanan instance) adalah penyimpanan block-level storage sementara untuk Amazon EC2 instance. Saat Anda meluncurkan EC2 instance--tergantung tipe EC2 instance yang Anda pilih--biasanya sudah tersedia penyimpanan lokal alias instance store volume di dalamnya.

Volume ini secara fisik terpasang ke host (mesin fisik), yaitu tempat di mana EC2 instance Anda berjalan. Anda dapat melakukan proses write (menulis) data padanya seperti hard drive pada umumnya.

Namun masalahnya, jika Anda menghentikan atau mengakhiri EC2 instance tersebut, maka semua data di sana akan terhapus. Ini terjadi karena ketika Anda memulai instance dari status stop alias berhenti kemungkinan EC2 instance akan berjalan di host lain, yang mana instance store volume tersebut tidak berada di sana.



Ingat! EC2 instance adalah mesin virtual. Oleh karena itu, host yang mendasarinya dapat berubah pada saat instance berhenti dan memulai.

Karena sifatnya yang sementara inilah biasanya instance store volume digunakan untuk penyimpanan data yang sering berubah, seperti cache, temporary file (file sementara), data yang dapat dibuat ulang dengan mudah, dan konten sementara lainnya. Tapi, ingat! Jangan simpan data penting Anda ke dalam instance store volume.

Lantas, bagaimana solusinya jika kita ingin menyimpan data secara persisten dan berada di luar siklus hidup EC2 instance? Atau dengan kata lain, bagaimana kita ingin menyimpan data yang takkan terhapus walau EC2 instance berhenti? Nah, jangan khawatir, di sinilah Anda perlu mengenal layanan Amazon Elastic Block Store (Amazon EBS).



Amazon Elastic Block Store (Amazon EBS)
Amazon Elastic Block Store (Amazon EBS) adalah layanan yang menyediakan block-level storage (penyimpanan tingkat blok) yang dapat Anda gunakan bersama dengan Amazon EC2 instance.

Amazon EBS memungkinkan Anda untuk membuat hard drive virtual (EBS volume) yang kemudian bisa di-attach (dipasang) ke EC2 instance. EBS volume ini merupakan penyimpanan yang terpisah dari instance store volume. Ia pun tak terikat langsung ke host yang menjalankan EC2 instance Anda.

Lalu, bagaimana cara membuat EBS volume? Sebenarnya, mudah saja. Anda hanya perlu menentukan konfigurasinya (seperti ukuran dan tipe) sesuai dengan kebutuhan. Jika sudah, Anda bisa meluncurkannya dan memasangkannya ke Amazon EC2 instance.

Sekarang, jika Anda menghentikan lalu memulai EC2 instance, data yang Anda simpan di EBS volume akan tetap ada.



Karena EBS volume digunakan untuk kebutuhan data yang persisten, maka penting untuk Anda melakukan backup (pencadangan) data. Anda dapat menjalankan incremental backup (pencadangan secara inkremental) dari EBS volume dengan membuat Amazon EBS snapshot.

Amazon EBS snapshot disimpan secara bertahap/inkremental. Itu berarti pada saat pertama kali proses pencadangan dilakukan, ia akan menyalin semua data yang ada di EBS volume. Namun, untuk pencadangan berikutnya, ia hanya menyimpan blok data yang berubah dari snapshot terakhir.

Tentu, incremental backup ini sesungguhnya berbeda ya dengan full backup (pencadangan penuh). Full backup itu akan menyalin semua data yang ada di dalam volume setiap pencadangan dilakukan, sementara incremental backup hanya mencadangkan data yang berubah (delta) dari pencadangan sebelumnya.

Lakukanlah snapshot untuk EBS volume secara teratur. Dengan begitu, jika sebuah drive corrupted atau rusak, maka Anda tidak akan kehilangan data, melainkan Anda dapat memulihkannya dari snapshot.

Amazon Simple Storage Service (Amazon S3)
Sekarang kita masuk ke materi yang berkenaan tentang Amazon Simple Storage Service (Amazon S3). Dari namanya, mungkin Anda sudah menduga bahwa ini adalah layanan penyimpanan yang sederhana.

Tahukah Anda? Sebagian besar bisnis memiliki data yang perlu disimpan di suatu tempat. Misalnya untuk kedai kopi kita, ini bisa berupa struk, gambar, spreadsheet Excel, video pelatihan karyawan, bahkan file teks.

Nah, Anda dapat menyimpan file-file tersebut di Amazon S3 karena ia merupakan layanan yang dapat menyimpan dan mengambil data dalam jumlah tak terbatas pada skala apa pun.

Dengan Amazon S3, data disimpan sebagai objek. Objek tersebut akan disimpan di dalam bucket. Sederhananya, anggaplah file yang ada di hard drive Anda sebagai objek dan direktori file adalah bucket.

Amazon S3 juga merupakan object-level storage (penyimpanan tingkat objek). Setiap objek terdiri dari data, metadata, dan kunci.

Mari kita lihat lebih lanjut. Data yang dimaksud itu bisa bermacam-macam, seperti gambar, video, dokumen teks, atau jenis file lainnya. Lalu, metadata adalah informasi yang berisi tentang apa itu data, cara penggunaannya, ukuran objeknya, dan sebagainya. Nah, key (kunci) pada suatu objek adalah identifier/pengenal yang unik.

Ukuran maksimum dari setiap objek yang dapat Anda unggah adalah 5 terabyte. S3 juga memiliki fitur versioning dengan membuat object version (versi objek). Maksudnya, Anda akan tetap dapat memiliki versi sebelumnya dari objek tersebut walaupun secara tidak sengaja menimpa objek dengan isi yang berbeda.

Selain itu, Anda juga dapat membuat beberapa bucket lalu menentukan permission (izin) untuk membatasi siapa yang dapat melihat atau mengakses objek di dalamnya.

Hal lain yang perlu diingat adalah ketika Anda mengubah file di block-level storage (penyimpanan tingkat blok), hanya bagian yang diubah saja yang akan diperbarui. Sebaliknya, saat Anda mengubah file di object-level storage (penyimpanan tingkat objek), maka keseluruhan objek yang akan diperbarui.

Oke, sekarang mari kita membahas storage class atau kelas penyimpanan yang ada pada Amazon S3. Maksudnya, ia menawarkan mekanisme untuk kasus penggunaan penyimpanan yang berbeda-beda. Misalnya untuk data yang sering diakses atau bahkan data audit yang perlu disimpan selama beberapa tahun. Mari kita uraikan.

S3 Standard
S3 Standard hadir dengan daya tahan 11 sembilan. Artinya, objek yang disimpan akan memiliki 99,999999999% probabilitas tetap utuh setelah jangka waktu satu tahun. Waw, Itu cukup tinggi, bukan?

Selain itu, data disimpan setidaknya di tiga data center. Sehingga, ini membuatnya dapat menawarkan high availability (ketersediaan tinggi) bagi objek. S3 Standard menjadi pilihan yang ideal untuk berbagai kasus penggunaan, seperti website, distribusi konten, dan analitik data.

Anda juga dapat menggunakan Amazon S3 untuk meng-hosting website statis, yaitu jenis website yang paling dasar dan berisi halaman web dengan konten statis. Caranya cukup mudah, Anda hanya perlu:
Unggah semua file HTML, aset web statis, dan sebagainya ke dalam bucket.
Centang opsi untuk meng-hosting website statis.
Lalu buka website tersebut dengan memasukkan URL bucket dan ta-da! Website instan.
Cara yang cukup mengagumkan ya untuk memulai blog tentang kedai kopi kita.

S3 Standard-Infrequent Access (S3 Standard-IA)
Kelas penyimpanan jenis ini digunakan untuk data yang jarang diakses tetapi membutuhkan proses cepat saat dibutuhkan. Artinya, opsi ini adalah tempat yang ideal untuk menyimpan backup (cadangan), disaster recovery file (file pemulihan bencana), atau objek apa pun yang memerlukan penyimpanan jangka panjang.

S3 One Zone-Infrequent Access (S3 One Zone-IA)
Berbeda dengan S3 Standard dan S3 Standard-IA yang menyimpan data minimal di tiga Availability Zone, kelas penyimpanan S3 One Zone-IA menyimpan data hanya di satu Availability Zone.

Nah, ini menjadikannya kelas penyimpanan yang perlu Anda pertimbangkan jika memiliki kondisi seperti berikut:
Ingin menghemat biaya penyimpanan.
Data dapat diproduksi ulang dengan mudah jika terjadi kegagalan di Availability Zone.

S3 Intelligent-Tiering
Pada kelas penyimpanan S3 Intelligent-Tiering, Amazon S3 memantau pola akses objek. Jika Anda tidak pernah mengakses objek selama 30 hari berturut-turut, Amazon S3 akan memindahkannya secara otomatis dari S3 Standard ke S3 Standard-IA.

Kemudian, jika Anda mengakses kembali objek di S3 Standard-IA, Amazon S3 akan memindahkannya secara otomatis ke S3 Standard.

S3 Glacier
Opsi kelas penyimpanan ini ideal untuk data audit. Katakanlah Anda perlu menyimpan data selama beberapa tahun untuk tujuan audit. Sehingga, tidak memerlukan proses akses yang langsung pada saat itu juga. Maka dari itu, Anda dapat menggunakan Amazon S3 Glacier untuk mengarsipkan data tersebut.

Perlu diingat bahwa untuk mengakses objek yang disimpan di S3 Glacier, Anda memerlukan waktu beberapa menit hingga beberapa jam.

Lalu bagaimana cara menggunakan Glacier? Mudah saja, Anda hanya perlu memindahkan data ke sana atau dengan membuat vault (brankas) lalu mengisinya dengan arsip.

Jika Anda memiliki compliance requirement (persyaratan kepatuhan) tentang penyimpanan data untuk periode waktu tertentu, Anda dapat menerapkan S3 Glacier vault lock policy untuk mengunci vault Anda.

Kontrol yang dapat Anda tentukan pada vault lock policy adalah write once/read many (WORM) alias cukup menulis data sekali lalu membacanya berkali-kali. Selain itu, Anda juga dapat mengunci kebijakan dari pengeditan di masa mendatang sehingga setelah terkunci, kebijakan tersebut tidak dapat lagi diubah.

Anda juga memiliki tiga opsi untuk pengambilan data yang berkisar dari hitungan menit hingga jam. Bahkan, Anda memiliki pilihan untuk mengunggah langsung ke kelas Glacier atau menggunakan S3 Lifecycle policies.

S3 Lifecycle policies adalah kebijakan yang bisa Anda buat untuk memindahkan data secara otomatis antar storage class (kelas penyimpanan).

Misalnya, Anda perlu menyimpan objek dalam S3 Standard selama 90 hari. Lalu, Anda ingin memindahkannya ke S3-IA selama 30 hari ke depan. Kemudian setelah total 120 hari, Anda ingin memindahkannya ke S3 Glacier.

Nah, kebutuhan semacam itu dapat Anda capai dengan S3 Lifecycle policies yang juga merupakan contoh lain dari layanan AWS terkelola.

S3 Glacier Deep Archive
Opsi ini merupakan kelas penyimpanan objek yang memiliki biaya terendah dan ideal untuk pengarsipan.

Saat Anda ingin memilih antara menggunakan Amazon S3 Glacier atau Amazon S3 Glacier Deep Archive, coba pertimbangkan seberapa cepat Anda perlu mengakses objek yang diarsipkan.

Di S3 Glacier waktu pengaksesan suatu objek berlangsung beberapa menit hingga jam saja, sementara dengan S3 Glacier Deep Archive Anda memerlukan waktu 12 hingga 48 jam.
Oke, sampai tahap ini, Anda sudah belajar tentang Amazon EBS dan juga Amazon S3. Mungkin sekarang Anda akan mengerutkan dahi, “Kapan kita harus menggunakan Amazon EBS dan Amazon S3?”

Baiklah, mari kita bandingkan dua layanan tersebut secara lebih mendalam.

Amazon EBS	Amazon S3
Block-level storage (penyimpanan tingkat blok), dapat berukuran hingga 16 terabyte, dan tetap tersedia walau Amazon EC2 instance dihentikan.

Object-level storage (penyimpanan tingkat objek) yang memiliki ukuran tak terbatas dan mampu menampung setiap objek hingga 5.000 gigabyte.



Setiap objek di S3 memiliki URL yang dapat Anda kontrol hak aksesnya.

Hadir dalam bentuk hard disk drive (HDD) dan solid state drive (SSD).

Write once/read many (cukup menulis data sekali lalu membacanya berkali-kali) dan menawarkan 99,999999999% ketahanan.

Cocok untuk mengedit video berukuran 80 gigabyte.

Ideal untuk website yang menjalankan analisis foto.

Memecah file menjadi bagian atau blok komponen kecil. Sehingga, saat Anda melakukan perubahan dan menyimpannya, sistem hanya memperbarui blok tempat bit tersebut berada.

Memperlakukan file apa pun sebagai objek yang lengkap dan terpisah sehingga ia cocok digunakan sebagai dokumen, gambar, dan video yang diunggah dan sebagai objek keseluruhan.

Termasuk layanan serverless (tanpa server) sehingga tidak memerlukan Amazon EC2 instance. Tak perlu khawatir akan strategi backup (pencadangan) karena ia merupakan layanan backup di AWS.

Penghematan biaya yang substansial melebihi EBS walau dengan beban penyimpanan yang sama.

Kesimpulannya, jika Anda memiliki objek atau file yang lengkap dan hanya membutuhkan sesekali perubahan, maka pilihlah Amazon S3. Namun, jika Anda membutuhkan proses read (baca) data yang kompleks, maka tentu saja Anda perlu memilih Amazon EBS.

Jadi, memilih penyimpanan yang tepat itu tergantung pada kebutuhan beban kerja Anda. Setiap layanan sebenarnya merupakan solusi yang tepat untuk kebutuhan tertentu. Pahamilah apa yang Anda butuhkan, maka Anda akan tahu layanan mana yang ideal.

Amazon Elastic File System (Amazon EFS)
Di modul ini, kita akan membahas tentang layanan file storage alias penyimpanan file, yang berarti beberapa client--pengguna, aplikasi, server, dsb--dapat mengakses data yang disimpan di folder file secara bersamaan.

Dalam pendekatan ini, file server menggunakan block storage (penyimpanan blok) dengan local file system (sistem file lokal) untuk mengatur file. Nah, client dapat mengakses data di dalamnya melalui file path (jalur file).

Dibandingkan dengan block storage dan object storage, file storage ini sangat ideal untuk kasus penggunaan di mana beberapa layanan dan sumber daya perlu mengakses data yang sama pada waktu yang sama.

Layanan AWS yang termasuk ke dalamnya adalah Amazon Elastic File System, atau juga disebut dengan EFS. Amazon EFS adalah sistem file terkelola yang bisa diskalakan dan dapat digunakan oleh layanan AWS Cloud dan sumber daya di data center on-premise.

Sudah sangat umum bagi perusahaan untuk berbagi sistem file di seluruh aplikasi mereka. Mari kita ambil contoh suatu kasus. Misalnya Anda memiliki beberapa server yang menjalankan analitik pada sejumlah besar data yang disimpan dalam sistem file bersama di data center on-premise.

Karena berjalan di on-premise, tentu saja Anda harus memastikan bahwa kapasitas penyimpanan di sana dapat menyesuaikan dengan jumlah data yang Anda simpan. Anda juga harus memastikan data tersebut telah dicadangkan dan disimpan secara redundan (di beberapa tempat). Satu lagi, Anda pun harus mengelola semua servernya. Repot ya?

Untungnya, AWS hadir memberikan solusi agar Anda tak perlu lagi khawatir untuk mengurus semuanya itu. AWS akan mengelola semua pekerjaan terkait scaling (penyesuaian kapasitas) dan replikasinya untuk Anda.

Dengan EFS, Anda dapat memiliki beberapa instance yang mengakses data secara bersamaan. Ia akan melakukan scaling up dan scaling down--keduanya telah kita bahas di modul tentang penyesuaian kapasitas--sesuai kebutuhan secara otomatis. Sangat keren, bukan?

Oke, mungkin Anda akan berpikir, “Loh, Amazon EBS juga bisa menyimpan file dan dapat diakses dari EC2 instance. Jadi, apa perbedaan sebenarnya?”

Jawabannya sangat sederhana. Amazon EBS volume dilampirkan ke EC2 instance dan merupakan Availability Zone-level resource atau sumber daya tingkat Availability Zone. Itu artinya, EBS akan menyimpan data hanya di satu Availability Zone (AZ). Terlebih lagi, jika Anda ingin memasang EC2 ke EBS, maka Anda harus berada di AZ yang sama.

Dengan Amazon EBS, Anda dapat menyimpan file, menjalankan database, atau menyimpan aplikasi di dalamnya. Ia adalah hard drive (cakram keras). Namun, jika Anda membuat EBS volume sebesar 2 terabyte lalu mengisinya hingga penuh, ia tidak akan serta-merta melakukan proses scaling dengan sendirinya. Itulah EBS.

Lalu bagaimana dengan EFS? Amazon EFS memungkinkan beberapa instance untuk melakukan proses read (membaca) dan write (menulis) data darinya pada saat bersamaan.

Tetapi, ia bukan sekadar hard drive kosong yang dapat Anda gunakan untuk menyimpan data. Amazon EFS adalah sistem file untuk Linux dan merupakan Regional resource (sumber daya regional). Itu berarti data akan disimpan di beberapa AZ. Dengan demikian, setiap EC2 instance yang berada di Region yang sama dapat menyimpan data ke sistem file Amazon EFS.

Nah, jika Anda menyimpan banyak data ke EFS, ia secara otomatis akan melakukan scaling bahkan hingga petabyte tanpa mengganggu aplikasi.

Amazon Relational Database Service (Amazon RDS)
Sampai sini, kita sudah banyak belajar tentang berbagai sistem penyimpanan di AWS yang dapat membantu Anda untuk menyelesaikan persoalan terkait kartu digital untuk pelanggan setia di kedai kopi, sebagaimana yang telah kita paparkan di awal modul.

Tetapi, ketahuilah! Anda juga perlu menjaga relasi antara berbagai tipe data. Tunggu, apa maksudnya?

Begini. Misalnya, seorang pelanggan di kedai kopi telah memesan minuman yang sama beberapa kali. Nah, melihat hal ini, mungkin Anda sebagai pemilik kedai kopi ingin menawarkan diskon promosi untuk pembelian berikutnya.

Tentu, Anda membutuhkan suatu cara untuk melacak relasi/hubungan semacam ini, bukan?

Solusi terbaik untuk masalah tersebut adalah dengan menggunakan relational database management system (RDBMS) alias sistem manajemen database/basis data relasional. Artinya, data yang kita simpan dapat memiliki relasi dengan bagian data lainnya.

Dalam dunia database, Anda akan sering mendengar kata query atau kueri. Itu adalah sekumpulan instruksi khusus untuk mengekstraksi data.

Nah, database relasional menggunakan structured query language (SQL) alias bahasa kueri terstruktur untuk menyimpan dan membuat kueri data. Pendekatan semacam ini memungkinkan data disimpan dengan cara yang mudah dimengerti, konsisten, dan dapat diskalakan.

Inilah solusi dari persoalan di awal tadi. Dengan database relasional, sekarang Anda dapat menulis kueri SQL untuk mengidentifikasi minuman apa yang sering dibeli oleh masing-masing pelanggan.

Contoh sederhana dari database relasional adalah sistem manajemen inventaris di skenario kedai kopi kita. Setiap record (kumpulan data) di database mencakup data untuk satu item, seperti nama produk, ukuran, harga, dsb.

Berikut adalah contoh sederhana dari tabel database relasional:

ID	Product name	Size	Price
1

Kopi gula aren

Besar

Rp25.000

2

Kopi susu

Sedang

Rp15.000

Sekarang pertanyaannya adalah, layanan AWS apa yang mendukung database relasional?

Sambutlah, Amazon Relational Database Service (Amazon RDS). Ia adalah layanan yang memungkinkan Anda untuk menjalankan database relasional di AWS Cloud.

Amazon RDS adalah layanan yang terkelola dan mendukung 6 (enam) mesin database, di antaranya:

Amazon Aurora
PostgreSQL
MySQL
MariaDB
Oracle Database
Microsoft SQL Server
Ketahuilah! Jika Anda memiliki data center on-premise yang menjalankan salah satu mesin database di atas, Anda bisa memindahkannya ke cloud dengan mudah. Bagaimana caranya?

AWS memungkinkan Anda untuk melakukan Lift-and-Shift, yaitu proses memigrasikan beban kerja dari on-premise ke AWS dengan sedikit atau bahkan tanpa modifikasi.

Contohnya, Anda bisa memindahkan database on-premise lalu menjalankannya di Amazon EC2. Dengan begitu, Anda mempunyai kendali atas variabel yang sama dengan keadaan di on-premise, seperti OS, memori, CPU, kapasitas penyimpanan, dsb. Ini merupakan entri yang cepat untuk menuju cloud, bukan?

Salah satu cara yang dapat Anda lakukan untuk mewujudkan proses migrasi ini adalah dengan menggunakan layanan Database Migration Service, yang nanti akan kita bahas.

Sekarang, mari kita kembali ke pembahasan mengenai Amazon RDS. Layanan Amazon RDS hadir dengan berbagai fitur, termasuk:

Automated patching (memperbaiki masalah dengan memperbarui program).
Backup (pencadangan).
Redundancy (memiliki lebih dari satu instance untuk berjaga-jaga jika instance utama gagal beroperasi).
Failover (instance lain akan mengambil alih saat instance utama mengalami kegagalan).
Disaster recovery (memulihkan pascabencana).
Encryption at rest (enkripsi data saat disimpan).
Encryption in-transit (enkripsi data saat sedang dikirim dan diterima).
Semua hal di atas adalah proses yang biasanya harus Anda kelola sendiri jika menggunakan data center on-premise. Tentu ini menjadikannya pilihan menarik karena Anda tak pusing dengan pemeliharaan dan pengelolaan database. Karena faktanya, semua proses tersebut sangat sulit dan memakan waktu yang lama.

Pertanyaan selanjutnya muncul, “Adakah cara yang bahkan bisa lebih mudah lagi untuk menjalankan beban kerja database di cloud?”

Nah, mari kita sedikit membahas tentang layanan Amazon Aurora. Ia adalah opsi database relasional kelas enterprise/perusahaan yang terkelola oleh AWS. Layanan ini memiliki banyak fitur, seperti:

Bisa bekerja secara kompatibel dengan MySQL dan PostgreSQL. Bahkan, dapat 5 kali lebih cepat dari database MySQL standar dan bisa 3 kali lebih cepat dari database PostgreSQL standar.
Memberikan performa yang setara dengan database komersial dengan perbandingan biaya 1/10.
Mampu memastikan replikasi data di seluruh fasilitas.
Menerapkan hingga 15 read replica (replika baca).
Mencadangkan secara berkelanjutan ke Amazon S3.
Menerapkan point-in-time recovery (pemulihan data dari periode tertentu).
Oke, itulah dia penjelasan tentang database relasional. Masih ada loh materi menarik lainnya yang terkait dengan database, nantikan di modul berikutnya ya.