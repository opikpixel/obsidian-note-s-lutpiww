
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

## Amazon DynamoDB

Sebelumnya, kita telah belajar tentang database relasional. Database relasional--misalnya MySQL standar--mengharuskan Anda untuk menentukan skema dengan baik. Ia bisa jadi terdiri dari satu atau banyak tabel yang saling berhubungan. Barulah Anda bisa menggunakan SQL untuk membuat kueri data.

Jenis ini sering dipakai untuk banyak kasus penggunaan dan telah menjadi tipe database standar secara historis. Bagaimanapun, jenis database SQL yang kaku ini dapat memiliki masalah _scaling_ dan kinerja saat berada di bawah tekanan.

Skema yang tetap (_fixed schema_) juga membuatnya tidak dapat memiliki variasi jenis data di dalam tabel. Jadi, database relasional bukanlah solusi terbaik untuk kumpulan data yang fleksibel dan membutuhkan akses kilat.

Selain itu, pada praktiknya, banyak juga yang menjalankan database SQL bukan untuk penggunaan relasional yang kompleks, melainkan hanya untuk tabel pencarian.

Nah, di sinilah Amazon DynamoDB hadir. Ia merupakan database nonrelasional (NoSQL) dan menggunakan jenis pendekatan pasangan _key-value_ (kunci-nilai).

Dengan Amazon DynamoDB, Anda dapat membuat tabel, yakni tempat menyimpan dan membuat kueri data. Data diatur menjadi item/key dan item memiliki atribut/value.

Anda dapat menambah dan menghapus atribut dari item di dalam tabel kapan pun. Setiap item tidak harus memiliki atribut yang sama. Sehingga, ini akan sangat baik untuk kumpulan data yang memiliki beberapa variasi antara satu item dengan item lainnya.

Karena kueri pada database nonrelasional itu cenderung lebih sederhana, ini membuat Anda bisa fokus pada kumpulan item dari satu tabel, bukan kueri dari rentang beberapa tabel.

Berikut adalah contoh sederhana dari tabel database nonrelasional.

|Key|Value|
|---|---|
|1|**Nama**: Budi|
|**Alamat**: Kenanga 123|
|**Minuman favorit**: Kopi gula aren|
|2|**Nama**: Siska|
|**Alamat**: Mawar 321|
|**Tanggal Lahir**: 5 Juli 1994|

Mudah, bukan? Seperti yang telah kita pelajari sebelumnya, setiap item pada tabel tidak harus memiliki atribut yang sama.

Oke, mari kita lanjutkan pembahasannya.

Ketahuilah! Amazon DynamoDB ini adalah layanan yang terkelola sepenuhnya dan merupakan database _serverless_ (tanpa server). Itu artinya Anda tak perlu mengelola instance atau infrastruktur dasarnya. Bahkan, Anda tidak perlu khawatir akan proses _scaling_ (penyesuaian kapasitas) yang terjadi pada sistem.

Selain itu, Amazon DynamoDB juga menyimpan data di beberapa perangkat di seluruh availability zone. Sehingga, ini menjadikannya database yang _highly available_ (sangat tersedia). Layanan ini memiliki kinerja yang sangat tinggi. Ia punya _response time_ (waktu respons) kilat, yakni milidetik, yang akan sangat bermanfaat untuk aplikasi dengan potensi jutaan pengguna.

Ingat! Karena DynamoDB adalah database NoSQL alias nonrelasional, ia sangat ideal untuk kasus penggunaan tertentu, bukan untuk semua beban kerja.

Salah satu contoh penggunaan Amazon DynamoDB yang luar biasa adalah pada saat Amazon Prime Day pada tahun 2019. Prime Day adalah acara belanja tahunan eksklusif untuk anggota Amazon Prime.

Selama 48 jam Prime Day, ada 7,11 triliun panggilan ke API DynamoDB. Puncaknya bahkan ada pada 45,4 juta permintaan per detik. Waw, sangat andal, bukan?

Sekarang, mungkin Anda akan bertanya-tanya, “Kapan kita harus menggunakan Amazon RDS dan Amazon DynamoDB?”

Oke, mari kita bandingkan dua layanan tersebut secara lebih detail.

| Amazon RDS                                                                                                                                                   | Amazon DynamoDB                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dirancang untuk mengurangi kerumitan administrator sekaligus memberikan _high availability_ (ketersediaan tinggi) pada _recovery_ (pemulihan) database Anda. | Menggunakan pasangan _key-value_ tanpa memerlukan skema yang rumit serta dapat beroperasi sebagai database global hanya dengan satu klik.            |
| Anda dapat mengontrol data, skema, dan jaringan.                                                                                                             | Memiliki _throughput_ (jumlah data yang dapat dikirim dalam waktu tertentu) yang besar, _scaling_ hingga petabyte, dan akses API secara detail.      |
| Mampu membangun sistem analisis data yang kompleks.                                                                                                          | Memungkinkan Anda membangun database yang kuat dan sangat cepat tanpa perlu fungsionalitas yang rumit.                                               |
| Ideal untuk analisis sistem manajemen _supply chain_ (rantai pasokan).                                                                                       | Cocok untuk penggunaan data yang fleksibel dan sederhana seperti daftar kontak karyawan yang berisikan nama, nomor telepon, email, ID karyawan, dsb. |

Jadi, sebenarnya ini tergantung pada kebutuhan beban kerja Anda. Setiap layanan akan menjadi solusi yang tepat untuk kebutuhan tertentu. Maka pahamilah apa yang Anda butuhkan, dengan begitu Anda akan dapat memilih layanan mana yang ideal.

## Amazon Redshift

Sedari tadi kita telah banyak membahas tentang jenis alur kerja dengan kebutuhan proses data yang cepat, andal, dan terkini. Yup! Database bisa menjadi solusinya karena ia dapat menangani 1.000 transaksi per detik, sangat tersedia, dan berdaya tahan.

Tapi terkadang, mungkin ada kebutuhan bisnis yang melebihi dari apa yang pernah kita alami. Maka dari itu, kita membutuhkan layanan yang dapat menganalisis data.

Tentu Anda dapat menggunakan satu layanan database untuk semua kebutuhan. Namun, database modern yang dirancang untuk penggunaan kueri berkinerja tinggi dan _real time_, bukanlah yang paling ideal. Simak penjelasan berikut.

Database relasional akan sangat ideal untuk jenis pekerjaan yang membutuhkan fungsionalitas _read/write_ (membaca/menulis) data karena ia dapat menanganinya secara real time.

Namun, masalah akan muncul saat Anda menggunakannya untuk jenis pekerjaan yang lain. Misalnya, jika Anda memakai database relasional untuk kebutuhan analisis historis, maka operasi pengumpulan data akan terus memprosesnya dan tak akan pernah berhenti. Dengan telemetri modern, volume data bisa membanjiri database. Bahkan, database relasional tradisional yang terkuat sekalipun tak bisa menanganinya.

Selain itu, data yang bervariasi juga akan menjadi masalah. Misalkan Anda ingin menjalankan proyek _business intelligence_ (inteligensi bisnis) untuk data dari penyimpanan yang berbeda, seperti inventaris, keuangan, dan sistem penjualan ritel.

Mungkin, solusinya adalah dengan menggunakan satu kueri untuk beberapa database sekaligus. Tetapi faktanya, database tradisional tidak bisa menanganinya dengan mudah. Nah, ketika data menjadi semakin kompleks untuk ditangani oleh database relasional tradisional, maka _data warehouse_ (gudang data) adalah solusinya. Data warehouse dirancang secara spesifik untuk jenis _big data_ semacam ini, yaitu analitik historis, bukan analisis operasional.

Mari kita perjelas. Analitik historis itu seperti pertanyaan, “Tunjukkan angka penjualan satu jam terakhir di semua toko.” Intinya, data sudah siap pada saat diproses. Data tidak akan berubah lagi karena data ini adalah data historis yang sudah terjadi sebelumnya.

Bandingkan pertanyaan itu dengan, "Berapa kantong kopi yang masih ada di inventaris kita sekarang?" Yang mana data tersebut bisa berubah bahkan pada saat kita bertanya. Selama pertanyaan Anda melihat ke belakang alias lampau, maka data warehouse adalah solusi yang tepat untuk lini _business intelligence_ tersebut.

Ada banyak solusi data warehouse yang beredar di pasaran. Namun, dengan itu semua, Anda mungkin tetap harus melakukan banyak _undifferentiated heavy lifting_ (proses kerja yang tidak menambah nilai bagi perusahaan) guna menjaga data warehouse agar tetap dikonfigurasi, senantiasa tangguh, dan _scaling_ secara berkelanjutan.

Tetapi, bukankah lebih baik jika Anda fokus pada data daripada perawatan dan pengelolaan mesin yang tak terhindarkan?

Anda mungkin perlu berkenalan dengan layanan yang satu ini, yaitu Amazon Redshift. Amazon Redshift adalah layanan data warehousing yang dapat Anda gunakan untuk analitik big data. Layanan ini menawarkan kemampuan untuk mengumpulkan data dari banyak sumber dan membantu Anda memahami hubungan dan tren di seluruh data. Selain itu, ia juga dapat diskalakan secara masif.

Adalah hal yang wajar untuk Redshift nodes (kumpulan sumber daya komputasi) tersedia dalam berbagai ukuran _petabyte_. Kolaborasikan Redshift nodes dengan Amazon Redshift Spectrum sehingga Anda pun dapat langsung menjalankan satu kueri SQL untuk _exabyte_ data tidak terstruktur yang berjalan di _data lake_ (penyimpanan untuk data terstruktur dan tidak terstruktur pada skala apa pun).

Selebihnya lagi, Amazon Redshift ini bukan hanya sekadar mampu menangani _data set_ (kumpulan data) yang sangat besar, melainkan juga dapat mencapai kinerja hingga 10 kali lebih tinggi--dengan menggunakan berbagai inovasi--daripada database tradisional dalam hal beban kerja business intelligence.

Kita tidak akan memaparkan terperinci tentang cara kerja Amazon Redshift ya. Intinya, pahami bahwa saat Anda perlu solusi business intelligence big data, ia hadir memudahkan Anda untuk memulainya hanya dengan satu panggilan API. Dengan begitu, akan lebih sedikit waktu buat menunggu hasil dan lebih banyak waktu untuk mendapatkan jawaban.

AWS Database Migration Service
Wah, tak terasa ya kita telah banyak membahas berbagai opsi database di AWS. Nah, sekarang mungkin Anda akan mengerutkan dahi, “Bagaimana kalau kita sudah punya database di on-premise atau mungkin di platform lain? Apa itu berarti kita harus memulai dari awal?”

Oh, tak perlu khawatir akan itu! AWS punya cara yang ajaib.

Mari berkenalan dengan AWS Database Migration Service (AWS DMS). Ia dapat memigrasikan database yang Anda miliki--baik relasional, nonrelasional (NoSQL), atau tipe penyimpanan data lain--ke AWS dengan mudah dan aman.

Pada dasarnya, proses migrasi itu membutuhkan sumber dan target database. Nah, dengan AWS DMS:

Database sumber tetap beroperasi penuh selama proses migrasi.
Downtime (waktu henti) diminimalkan untuk aplikasi yang bergantung pada database tersebut.
Database sumber dan target tidak harus bertipe sama.
Oke. Meski tak harus bertipe sama, mari mulai pembahasan kita dari proses migrasi database yang bertipe sama (homogen) terlebih dahulu, atau dikenal sebagai homogenous database migration. Proses semacam ini dapat memigrasikan database dari:

MySQL ke Amazon RDS for MySQL.
Microsoft SQL Server ke Amazon RDS for SQL Server.
Bahkan, Oracle ke Amazon RDS for Oracle.
Karena sumber database dan target memiliki struktur skema, tipe data, dan kode database yang sama, hasilnya proses migrasi akan berlangsung mudah.

Nah, contoh dari sumber database ini dapat berupa database yang berjalan di on-premise, Amazon EC2 instance, ataupun Amazon RDS. Sementara untuk database target, ia bisa saja database yang berada di Amazon EC2 maupun Amazon RDS.

Cara kerja migrasi homogen ini pun cukup sederhana. Anda hanya perlu membuat tugas migrasi, mengoneksikannya ke database sumber dan target, lalu mulai prosesnya dengan mengeklik tombol. Sisanya, akan ditangani oleh AWS DMS. Keren, bukan?



Sekarang, mari kita beralih ke jenis kedua, yakni migrasi database heterogen alias heterogeneous database migration. Berbeda dengan jenis pertama, migrasi heterogen ini terjadi saat database sumber dan target memiliki tipe yang berbeda. Ia juga merupakan proses dua langkah.

Maksudnya, karena struktur skema, tipe data, dan kode database asal berbeda dengan database target, maka kita perlu mengubahnya terlebih dahulu menggunakan AWS Schema Conversion Tool. Setelah itu, barulah kita gunakan AWS DMS untuk memigrasikannya.

Nah, selain dari yang dijelaskan di atas, AWS DMS juga dapat digunakan untuk:

Migrasi ke database pengembangan dan pengujian
Contoh penggunaannya adalah ketika Anda ingin melakukan pengujian aplikasi pada database produksi tanpa memengaruhi pengguna. Nah, dengan AWS DMS, Anda dapat memigrasikan salinan dari database produksi tersebut ke lingkungan pengembangan (development) atau pengujian (testing).
Konsolidasi database
Dengan AWS Database Migration Service, Anda dapat menggabungkan beberapa database menjadi satu database pusat.
Replikasi database yang berkelanjutan
AWS DMS memungkinkan Anda untuk melakukan replikasi data yang berkelanjutan. Ini berguna untuk disaster recovery (pemulihan bencana) atau pemisahan geografis.
Oke, itulah dia materi tentang AWS Database Migration Service. Perjalanan kita belum berakhir ya, masih ada materi menarik lain di modul berikutnya. Ganbatte!

Layanan Database Tambahan
Masih ingatkah Anda dengan kalimat yang ada di materi pengantar? “Pilihlah penyimpanan dan database yang tepat untuk masing-masing kebutuhan Anda.”

Yap, itu benar! Memang akan lebih baik jika kita menjalankan database yang sesuai dengan data daripada memaksakan data agar kompatibel dengan database. Ketahuilah! Tak ada satu pun database yang mampu menangani semua kebutuhan sekaligus.

Sejauh ini, kita telah membahas beberapa jenis database. Sebenarnya, masih ada banyak loh layanan database lain yang ditawarkan oleh AWS guna memenuhi kebutuhan-kebutuhan tertentu.

Tentu kita tidak akan membahas semuanya secara detail di modul ini, tapi tak ada salahnya juga untuk sedikit menyentuhnya agar Anda mengetahui bahwa layanan-layanan tersebut ada.

Amazon DocumentDB
Sebelumnya, kita telah menilik tentang layanan DynamoDB yang dapat digunakan untuk database pasangan key-value (kunci-nilai). Tetapi, bagaimana jika Anda memiliki kebutuhan yang lebih dari sekadar atribut sederhana? Seperti sistem manajemen konten yang lengkap misalnya.

Nah, berarti Anda harus berkenalan dengan Amazon DocumentDB. Ia adalah layanan yang dapat membantu Anda untuk menangani manajemen konten, katalog, ataupun profil pengguna.

Amazon DocumentDB merupakan layanan database dokumen yang mendukung beban kerja MongoDB (program database dokumen).

Amazon Neptune
Katakanlah Anda memiliki aplikasi web jejaring sosial dan ingin melacak: siapa terhubung dengan siapa. Pastinya akan sangat kaku dan sulit jika Anda mengelolanya di database relasional tradisional.

Nah, Amazon Neptune dapat membantu Anda dalam hal tersebut. Ia adalah layanan graph database (database grafik) yang berguna untuk membuat dan menjalankan aplikasi dengan kumpulan data yang sangat terhubung, seperti social networking (jejaring sosial), recommendation engines (mesin pemberi rekomendasi), fraud detection (sistem pendeteksi penipuan), dan knowledge graph (grafik pengetahuan: kumpulan deskripsi yang saling terkait dari entitas).

Amazon Managed Blockchain
Jika Anda memiliki sistem supply chain (rantai pasokan) yang harus Anda lacak untuk menjamin tak akan ada suplai yang hilang, atau mungkin jika Anda mempunyai catatan perbankan/finansial yang aman, atau dalam kata lain adalah blockchain maka Anda dapat menggunakan Amazon Managed Blockchain.

Dengannya, Anda dapat membuat dan mengelola jaringan blockchain dengan framework (kerangka kerja) yang open-source. Mungkin Anda kurang familier dengan blockchain? Yup, ia adalah sistem ledger (kumpulan catatan riwayat aktivitas) terdistribusi yang memungkinkan banyak pihak menjalankan transaksi dan berbagi data tanpa otoritas pusat.

Amazon Managed Blockchain menggunakan desain decentralized ownership (kepemilikan yang terdesentralisasi). Artinya, beberapa pihak dapat bertransaksi tanpa harus saling mengenal atau mempercayai satu sama lain.

Amazon Quantum Ledger Database (Amazon QLDB)
Kalau memang Amazon Managed Blockchain tak dapat memenuhi kebutuhan Anda, gunakanlah Amazon Quantum Ledger Database (Amazon QLDB).

Amazon QLDB adalah sistem pencatatan yang immutable di mana entri apa pun tidak akan pernah bisa dihapus dari audit. Layanan ini menyediakan log transaksi yang terpusat, tidak dapat diubah, dan dapat diverifikasi secara kriptografi.

Amazon QLDB menggunakan desain centralized ownership (kepemilikan yang tersentralisasi). Maksudnya, otoritas pusat nan tepercaya memiliki, mengelola, dan membagikan ledger dengan sejumlah pihak tertentu.
Oke, kita berhenti sejenak terlebih dahulu. Seperti yang kita tahu bersama, database itu sesungguhnya adalah sistem yang hebat, bukan? Tetapi, bukankah akan jauh lebih baik jika ada cara yang dapat membuatnya lebih cepat?

Nah, AWS menawarkan beberapa opsi akselerator database yang dapat Anda gunakan untuk sejumlah skenario tertentu.

Amazon ElastiCache
AWS memungkinkan Anda untuk menambahkan lapisan cache pada database yang dapat meningkatkan read time (waktu baca) untuk permintaan umum dengan menggunakan Amazon ElastiCache. Ia mendukung dua jenis penyimpanan data: Redis dan Memcached.

Amazon DynamoDB Accelerator (DAX)
Jika Anda menggunakan Amazon DynamoDB, maka Anda harus mencoba layanan Amazon DynamoDB Accelerator (DAX), yakni native caching layer yang dirancang untuk meningkatkan waktu read (baca) untuk data nonrelasional.
Oke, itulah beberapa layanan database tambahan yang AWS miliki. Gunakanlah setiap layanan dengan tepat untuk masing-masing kebutuhan Anda.