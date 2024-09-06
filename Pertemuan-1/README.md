# Pertemuan 1 LBE NCC 2024
## Pengertian Cloud
Cloud merupakan simbol atau perumpamaan dari internet, sedangkan computing berarti pemrosesan menggunakan komputer. Jadi, cloud computing adalah penggunaan sumber daya komputasi (seperti server, storage, network, dsb.) melalui internet yang dilakukan secara on-demand (sesuai kebutuhan) dan tagihannya dibayarkan dengan harga sesuai pemakaian (pay-as-you-go).

## Model Cloud
- **Cloud-based**: Penerapan yang sepenuhnya menggunakan teknologi cloud. Terdapat 2 opsi dalam membangun aplikasi cloud-based:
  - Low-level infrastructure: Kita masih memerlukan staf IT Anda untuk mengelola server.
  - Higher-level service: Dengan layanan serverless yang mampu mengurangi kebutuhan pengelolaan, arsitektur, dan scaling (penyesuaian kapasitas) pada infrastruktur. **serverless** disini memiliki arti bahwa server masih digunakan tetapi sepenuhnya dikelola oleh penyedia cloud, sehingga client hanya fokus pada penulisan dan menjalankan kode, tanpa perlu khawatir tentang infrastruktur di belakangnya.
- **On-Premise** : Terkadang disebut sebagai private cloud,  di mana perusahaan harus memiliki pusat data (data center) sendiri. Ini berarti mereka perlu mengelola semua aspek seperti virtualisasi server, pemeliharaan  hardware, cabling, penyusunan rak, update software, dll.
- **Hybrid** : Menggabungkan model penerapan cloud dan on-premise. Misalnya: Front-End (web layer) di-hosting di AWS. Back-End (API dan Database) dijalankan dari data center pribadi. Keduanya dihubungkan melalui jaringan pribadi: AWS VPN (via internet) atau AWS Direct Connect (via dedicated fiber cable).

## Pengenalan AWS
AWS (Amazon Web Services) adalah platform layanan cloud yang disediakan oleh Amazon, yang menawarkan berbagai layanan komputasi seperti penyimpanan data, server virtual, database, jaringan, analisis data, kecerdasan buatan, IoT, hingga layanan satelit. Dengan fleksibilitas, keamanan, dan skalabilitasnya, AWS memungkinkan client membangun dan menjalankan aplikasi tanpa harus mengelola infrastruktur fisik, serta membayar hanya sesuai dengan penggunaan (pay-as-you-go).

**Dulu vs Sekarang**
- Sebelum hadirnya cloud computing, perusahaan harus membangun data center sendiri untuk membuat sebuah aplikasi.
- Perusahaan harus membayar banyak hal, seperti:
    - Rak komputer
    - Instalasi jaringan
    - Sistem penyimpanan
    - Sewa bangunan, kebersihan, listrik, pendingin, dan keamanan.
- Dengan AWS, Perusahaan dapat menggunakan server dan sumber daya IT lainnya yang ada di data center mereka dan cukup membayar penggunaan sumber daya sesuai pemakaian saja.

## Layanan Komputasi 
## Infrastruktur Global dan Keamanan
## Layanan Penyimpanan
### Instance Store
Instance store adalah penyimpanan block-level storage sementara untuk Amazon EC2 instance. Ketika meluncurkan (launching) EC2 instance, ada kalanya sudah tersedia penyimpanan lokal alias instance store volume di dalamnya. Namun, hal ini tergantung tipe EC2 instance yang dipilih.

Volume ini secara fisik terpasang ke host (mesin fisik), yaitu tempat di mana EC2 instance berjalan. Kita dapat melakukan proses write (menulis) data padanya seperti hard drive pada umumnya.

Namun masalahnya, jika EC2 instance tersebut diberhentikan atau sesinya diakhiri, maka semua data di sana akan terhapus. Ini terjadi karena EC2 instance pada dasarnya adalah mesin virtual. Ketika kita memulai instance dari status stop alias berhenti, kemungkinan EC2 instance akan berjalan di host lain, yang mana instance store volume sebelumnya tidak berada di host yang baru. 

Karena sifatnya yang sementara inilah biasanya instance store volume digunakan untuk penyimpanan data yang sering berubah, seperti cache, temporary file (file sementara), data yang dapat dibuat ulang dengan mudah, dan konten sementara lainnya.

### Amazon Elastic Block Store (Amazon EBS)
Amazon Elastic Block Store (Amazon EBS) adalah layanan yang menyediakan block-level storage (penyimpanan tingkat blok) yang dapat digunakan bersama dengan Amazon EC2 instance.

Amazon EBS memungkinkan kita untuk membuat hard drive virtual (EBS volume) yang kemudian bisa di-attach (dipasang) ke EC2 instance. EBS volume ini merupakan penyimpanan yang terpisah dari instance store volume dan tak terikat langsung ke host yang menjalankan EC2 instance.

Karena EBS volume digunakan untuk kebutuhan data yang persisten, maka penting untuk melakukan backup (pencadangan) data. Kita dapat menjalankan incremental backup (pencadangan secara inkremental) dari EBS volume dengan membuat Amazon EBS snapshot. Amazon EBS snapshot disimpan secara bertahap/inkremental. Artinya, pada saat pertama kali proses pencadangan dilakukan, EBS snapshot akan menyalin semua data yang ada di EBS volume. Namun, untuk pencadangan berikutnya, EBS snapshot hanya menyimpan blok data yang berubah dari snapshot terakhir.

![image](https://github.com/user-attachments/assets/6e24507f-e941-41c9-b30c-57b25ed43767)

Lakukanlah snapshot untuk EBS volume secara teratur. Dengan begitu, jika sebuah drive corrupted atau rusak, maka kita tidak akan kehilangan data, melainkan kita dapat memulihkannya dari snapshot.

### Amazon Simple Storage Service (Amazon S3)
Amazon S3 merupakan object-level storage (penyimpanan tingkat objek). Dengan Amazon S3, data disimpan sebagai objek. Objek tersebut akan disimpan di dalam bucket. Setiap objek terdiri dari data, metadata, dan kunci. 

![image](https://github.com/user-attachments/assets/0eb4a7bb-5e3a-4721-ace6-144bbf923e92)

**Data** yang dimaksud itu bisa bermacam-macam, seperti gambar, video, dokumen teks, atau jenis file lainnya. Lalu, **metadata** adalah informasi yang berisi tentang apa itu data, cara penggunaannya, ukuran objeknya, dan sebagainya. Kemudian, **key** (kunci) pada suatu objek adalah identifier/pengenal yang unik.

Amazon S3 mendukung fitur versioning yang memungkinkan kita tetap memiliki objek dengan versi sebelumnya walaupun objek tersebut sudah ditimpa dengan objek lain yang berbeda. Selain itu, setiap bucket di Amazon S3 dapat diberi hak akses untuk membatasi siapa yang dapat melihat atau mengakses objek di dalamnya.

Beberapa kelas penyimpanan yang ada pada Amazon S3:
- **S3 Standard**
<br>Data disimpan setidaknya di tiga data center. Sehingga, ini membuatnya dapat menawarkan high availability (ketersediaan tinggi) bagi objek.
  
- **S3 Standard-Infrequent Access (S3 Standard-IA)**
<br>Kelas penyimpanan jenis ini digunakan untuk data yang jarang diakses tetapi membutuhkan proses cepat saat dibutuhkan. Artinya, opsi ini adalah tempat yang ideal untuk menyimpan backup (cadangan), disaster recovery file (file pemulihan bencana), atau objek apa pun yang memerlukan penyimpanan jangka panjang.
  
- **S3 One Zone-Infrequent Access (S3 One Zone-IA)**
<br>Kelas penyimpanan S3 One Zone-IA menyimpan data hanya di satu Availability Zone.

- **S3 Intelligent-Tiering**
<br>Pada kelas penyimpanan S3 Intelligent-Tiering, Amazon S3 memantau pola akses objek. Jika kita tidak pernah mengakses objek selama 30 hari berturut-turut, Amazon S3 akan memindahkannya secara otomatis dari S3 Standard ke S3 Standard-IA.
  
- **S3 Glacier**
<br>Kelas penyimpanan ini ideal untuk menyimpan data selama beberapa tahun untuk tujuan audit.
  
- **S3 Glacier Deep Archive**
<br>Kelas penyimpanan objek yang memiliki biaya terendah dan ideal untuk pengarsipan. Di S3 Glacier waktu pengaksesan suatu objek berlangsung beberapa menit hingga jam saja, sementara dengan S3 Glacier Deep Archive Anda memerlukan waktu 12 hingga 48 jam.
  
### Amazon Elastic File System (Amazon EFS)
Amazon EFS merupakan layanan file storage atau sistem file terkelola yang bisa diskalakan dan dapat digunakan oleh layanan AWS Cloud. Dengan EFS, kita dapat memiliki beberapa instance yang mengakses data secara bersamaan. Ia akan melakukan scaling up dan scaling down, serta replikasi sesuai kebutuhan secara otomatis.

Sebenarnya, kita juga dapat menggunakan Amazon EBS untuk menyimpan file. Namun, Amazon EBS hanya memungkinkan penyimpanan data hanya di satu Availability Zone (AZ). Sedangkan Amazon EFS dapat menyimpan data di beberapa Availability Zone (AZ) karena menerapkan konsep regional resource. Selain itu, Amazon EFS memungkinkan auto-scalling, yang tidak tersedia pada Amazon EBS.

### Amazon Relational Database Service (Amazon RDS)
Adakalanya, kita membutuhkan pengelolaan data menggunakan relational database management system (RDBMS) alias sistem manajemen database/basis data relasional. Database relasional menggunakan structured query language (SQL) alias bahasa kueri terstruktur untuk menyimpan dan membuat kueri data.

Layanan AWS yang mendukung database relasional adalah Amazon RDS. Amazon RDS adalah layanan yang terkelola dan mendukung 6 (enam) mesin database, di antaranya:
- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle Database
- Microsoft SQL Server

Layanan Amazon RDS hadir dengan berbagai fitur, termasuk:
- Automated patching (memperbaiki masalah dengan memperbarui program).
- Backup (pencadangan).
- Redundancy (memiliki lebih dari satu instance untuk berjaga-jaga jika instance utama gagal beroperasi).
- Failover (instance lain akan mengambil alih saat instance utama mengalami kegagalan).
- Disaster recovery (memulihkan pascabencana).
- Encryption at rest (enkripsi data saat disimpan).
- Encryption in-transit (enkripsi data saat sedang dikirim dan diterima).
  
### Amazon DynamoDB
### Amazon Redshift
### AWS Database Migration Service

## Launch VM di AWS
