# Pertemuan 1 LBE NCC 2024
## Pengertian Cloud
Cloud merupakan simbol atau perumpamaan dari internet, sedangkan computing berarti pemrosesan menggunakan komputer. Jadi, cloud computing adalah penggunaan sumber daya komputasi (seperti server, storage, network, dsb.) melalui internet yang dilakukan secara on-demand (sesuai kebutuhan) dan tagihannya dibayarkan dengan harga sesuai pemakaian (pay-as-you-go).

## Model Cloud
- **Cloud-based**: Penerapan yang sepenuhnya menggunakan teknologi cloud. Terdapat 2 opsi dalam membangun aplikasi cloud-based:
  - Low-level infrastructure: Kita masih memerlukan staf IT untuk mengelola server.
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

## Layanan Komputasi AWS

Amazon Web Services (AWS) menyediakan berbagai layanan komputasi yang memungkinkan kita untuk menjalankan aplikasi dengan skala yang fleksibel, menghemat biaya, dan menawarkan skalabilitas yang tinggi.

### 1. Amazon EC2 (Elastic Compute Cloud)

Amazon EC2 adalah layanan yang menyediakan instans server virtual yang sangat fleksibel, memungkinkan kita menjalankan aplikasi dengan kontrol penuh atas lingkungan komputasi. EC2 memberikan opsi konfigurasi untuk CPU, RAM, storage, dan jaringan sesuai kebutuhan aplikasi.

**Fitur Utama:**
- Pilihan tipe instans yang bervariasi.
- Opsi auto-scaling dan elastic load balancing.
- Integrasi dengan penyimpanan EBS (Elastic Block Store) dan penyimpanan objek S3.

### 2. AWS Lambda

AWS Lambda adalah layanan komputasi tanpa server (serverless) yang memungkinkan kita menjalankan kode berdasarkan event (peristiwa) tanpa harus memikirkan infrastruktur server di belakangnya. Anda hanya membayar berdasarkan jumlah permintaan dan durasi eksekusi kode.

**Fitur Utama:**
- Otomatis menskalakan sesuai permintaan.
- Tidak ada biaya saat fungsi tidak berjalan.
- Terintegrasi dengan layanan AWS lainnya seperti S3, DynamoDB, API Gateway, dll.

### 3. Amazon ECS (Elastic Container Service)

Amazon ECS adalah layanan manajemen container yang memungkinkan kita menjalankan aplikasi berbasis container (misalnya menggunakan Docker) di AWS. ECS menawarkan kendali penuh atas manajemen container serta orkestrasi dalam sebuah cluster.

**Fitur Utama:**
- Integrasi dengan Amazon EC2 atau AWS Fargate untuk menjalankan container.
- Manajemen otomatis atas deployment, scaling, dan keamanan container.

### 4. Amazon EKS (Elastic Kubernetes Service)

Amazon EKS adalah layanan yang mengelola Kubernetes, platform open-source untuk mengelola container. EKS memungkinkan kita menjalankan dan mengelola aplikasi Kubernetes tanpa harus memelihara control plane Kubernetes.

**Fitur Utama:**
- Pengelolaan Kubernetes yang fully managed.
- Dukungan untuk lingkungan hybrid dan multicloud.
- Terintegrasi dengan layanan AWS lainnya untuk keamanan, storage, dan networking.

### 5. AWS Fargate

AWS Fargate adalah mesin komputasi tanpa server untuk container. Fargate digunakan dengan ECS dan EKS, memungkinkan kita menjalankan container tanpa harus mengelola server atau cluster.

**Fitur Utama:**
- Menghilangkan kebutuhan untuk mengelola infrastruktur server.
- Secara otomatis menskalakan container sesuai kebutuhan.
- Aman dan diisolasi di tingkat task.

### Layanan Lainnya

AWS juga menyediakan beberapa layanan lainnya seperti:
- AWS Elastic Beanstalk
- Amazon Lightsail
- AWS Outposts
- Amazon Batch

---

## Infrastruktur Global dan Keandalan

![image](https://github.com/user-attachments/assets/7c47be9f-2476-44c8-8caa-933b0323caff)

Gambar di atas menunjukkan konsep high availability dan fault tolerance yang AWS terapkan dalam menjalankan industrinya.

### AWS Regions

AWS Regions adalah wilayah geografis yang terdiri dari beberapa data center terisolasi yang disebut Availability Zones (AZ). Setiap Region memiliki beberapa AZ untuk menyediakan high availability dan disaster recovery.

Setiap Region terisolasi dari Region lain, dan data tidak akan berpindah antar Region kecuali diizinkan secara eksplisit, menjaga kedaulatan data.

**Faktor Utama Memilih Region**
- Compliance (Kepatuhan): Mengikuti aturan hukum setempat terkait penyimpanan data.
- Proximity (Kedekatan): Memilih Region terdekat dengan pelanggan untuk mengurangi latensi.

- Feature Availability (Ketersediaan Fitur): Beberapa fitur mungkin hanya tersedia di Region tertentu.
- Pricing (Harga): Biaya bervariasi antar Region karena faktor lokal, seperti pajak.

## AWS Edge Locations

![image](https://github.com/user-attachments/assets/7ae7e990-a706-4b77-b246-e0eb8df35318)

Edge Locations digunakan oleh Amazon CloudFront sebagai cache yang menyimpan data lebih dekat dengan pelanggan, yang membantu mempercepat pengiriman konten dan mengurangi latensi.

## Berinteraksi dengan Layanan AWS

AWS menyediakan berbagai alat untuk berinteraksi dan mengelola layanan cloud-nya. Berikut adalah beberapa alat yang paling umum digunakan:

### 1. AWS Management Console

Antarmuka berbasis browser yang memungkinkan Anda mengelola layanan AWS secara visual.

**Fitur Utama:**
- Mencari layanan dengan mudah.
- Membangun lingkungan pengujian.
- Melihat tagihan dan biaya.
- Memantau sumber daya AWS.
- Tersedia aplikasi mobile untuk pemantauan dan penagihan.

### 2. AWS Command Line Interface (CLI)

Alat berbasis baris perintah yang memungkinkan Anda mengelola layanan AWS secara otomatis dengan skrip. Sangat cocok untuk lingkungan produksi karena mengurangi risiko human error dan memungkinkan tugas-tugas dijalankan secara berulang tanpa perlu interaksi manual.

### 3. AWS Elastic Beanstalk

Layanan managed yang membantu penyediaan dan pengelolaan lingkungan berbasis Amazon EC2. AWS Elastic Beanstalk mengotomatisasi pembuatan infrastruktur, termasuk jaringan, instance, dan load balancing, sehingga Anda bisa lebih fokus pada pengembangan aplikasi tanpa harus menggunakan AWS Management Console atau CLI.

**Fitur Utama:**
- Otomatisasi penuh dari provisioning hingga pengelolaan infrastruktur.
- Fokus pada pengembangan aplikasi tanpa perlu memikirkan manajemen infrastruktur.

---

Dengan menggunakan alat-alat ini, AWS membantu pengguna untuk mengelola dan menjalankan aplikasi mereka di cloud dengan lebih efisien dan efektif.
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
Selain database relasional atau yang bisa disebut sebagai database SQL, ada juga sebuah konsep yang menerapkan database nonrelasional atau NoSQL. Amazon DynamoDB memungkinkan kita membuat sebuah database NoSQL dan menggunakan jenis pendekatan pasangan key-value. 

Dengan Amazon DynamoDB, kita dapat membuat tabel, yakni tempat menyimpan dan membuat kueri data. Data diatur menjadi item/key dan item memiliki atribut/value. kita dapat menambah dan menghapus atribut dari item di dalam tabel kapan pun. Setiap item tidak harus memiliki atribut yang sama. Sehingga, ini akan sangat baik untuk kumpulan data yang memiliki beberapa variasi antara satu item dengan item lainnya.

Berikut adalah contoh sederhana dari tabel database nonrelasional.

![image](https://github.com/user-attachments/assets/d3239bd8-4728-4622-95a8-ea9f71161553)

Amazon DynamoDB ini adalah layanan yang terkelola sepenuhnya dan merupakan database serverless (tanpa server). Itu artinya kita tak perlu mengelola instance atau infrastruktur dasarnya. Selain itu, Amazon DynamoDB juga menyimpan data di beberapa perangkat di seluruh availability zone. Sehingga, ini menjadikannya database yang highly available (sangat tersedia). Layanan ini memiliki kinerja yang sangat tinggi. Ia punya response time (waktu respons) kilat, yakni milidetik, yang akan sangat bermanfaat untuk aplikasi dengan potensi jutaan pengguna.

### Amazon Redshift
Amazon Redshift adalah layanan data warehousing yang dapat kita gunakan untuk analitik big data. Layanan ini menawarkan kemampuan untuk mengumpulkan data dari banyak sumber dan membantu kita memahami hubungan dan tren di seluruh data. Selain itu, Amazon Redshift juga dapat diskalakan secara masif.

Amazon Redshift ini bukan hanya sekadar mampu menangani data set (kumpulan data) yang sangat besar, melainkan juga dapat mencapai kinerja hingga 10 kali lebih tinggi daripada database tradisional dalam hal beban kerja business intelligence.

### AWS Database Migration Service
“Bagaimana kalau kita sudah punya database di on-premise atau mungkin di platform lain? Apa itu berarti kita harus memulai dari awal?”

Tenang, AWS menyediakan layanan AWS Database Migration Service (AWS DMS) yang dapat memigrasikan database yang kita miliki, baik relasional, nonrelasional (NoSQL), atau tipe penyimpanan data lain ke AWS dengan mudah dan aman. 

Migrase database dapat dilakukan pada database yang bertipe sama maupun tidak bertipe sama. Contoh migrasi database yang bertipe sama:
- MySQL ke Amazon RDS for MySQL.
- Microsoft SQL Server ke Amazon RDS for SQL Server.
- Bahkan, Oracle ke Amazon RDS for Oracle.

Pada migrasi database bertipe sama, kita hanya perlu menggunakan Amazon DMS untuk migrasi data. Sedangkan pada migrasi database bertipe beda, kita perlu menggunakan AWS Schema Conversion Tool untuk mengubah tipe database sumber menjadi sesuai dengan database target sebelum menggunakan Amazon DMS.

Selain dari yang dijelaskan di atas, AWS DMS juga dapat digunakan untuk:
- Migrasi ke database pengembangan dan pengujian
- Menggabungkan beberapa database menjadi satu database pusat
- Replikasi database berkelanjutan

### Database Tambahan
- Amazon DocumentDB
- Amazon Neptune
- Amazon Managed Blockchain
- Amazon Quantum Ledger Database (Amazon QLDB)
- Amazon ElastiChace
- Amazon DynamoDB Accelerator (DAX)

## Launch VM di AWS
Sebelum memulai penjelasan tentang cara launching virtual machine (VM) atau instance di AWS, kami menyarankan kalian untuk mengaktifkan free-tier AWS agar dapat mengakses layanan yang dibutuhkan secara gratis. Kalian bisa mengaksesnya pada laman berikut https://aws.amazon.com/free

![image](https://github.com/user-attachments/assets/6181f5b6-0643-43ef-b2ac-37a9d7392398)

Pilih "Create Free Account" dan ikuti semua instruksinya, termasuk mengisi informasi kartu kredit atau debit. Setelah semua proses pendaftarana akun selesai, masuk ke konsol AWS.

Pada kesempatan kali ini, kita akan melakukan launching VM menggunakan layanan instance EC2. Pilih layanan **Compute** pada **Services**, lalu pilih **EC2**
![image](https://github.com/user-attachments/assets/1bd357bb-1bfe-447c-bad7-c8537cab8345)

Selanjutnya, kita akan membuat sebuah instance baru dengan melakukan Launch Instance. Kalian dapat memilih tombol **Launch Instance** yang tersedia pada EC2 Dashboard atau memilih halaman **Instance** terlebih dahulu, lalu memilih tombol **Launch Instance** di pojok kanan atas.

Atur konfigurasi instance
- **Nama Instance dan Tag**
  ![image](https://github.com/user-attachments/assets/724c37cb-ec57-4378-9bbd-61e90656a7f1)

  Tag adalah label yang kita tetapkan ke sumber daya AWS. Setiap tag terdiri dari kunci dan nilai opsional, dan keduanya dapat kita tetapkan.
  ![image](https://github.com/user-attachments/assets/2355b470-4bb8-4275-9ba3-18f44b9a2381)


- **Application dan OS Images (Amazon Machine Image)**
<br>AMI berisi konfigurasi perangkat lunak (sistem operasi (OS), server aplikasi, dan aplikasi) yang diperlukan untuk meluncurkan instance.
Katalog AMI berisi aplikasi dan image OS yang disusun sebagai berikut
  ![image](https://github.com/user-attachments/assets/834bb5db-5ae4-4faf-93e9-a46054bb168c)

- **Instance Type**
<br>Pilih jenis instance yang memenuhi kebutuhan komputasi, memori, jaringan, atau penyimpanan.
  ![image](https://github.com/user-attachments/assets/6b03ef85-d3c8-4b38-8dda-e1fe07f3d66d)

- **Key Pair**
<br> Key pair digunakan untuk memastikan instance diakses dengan aman.
  ![image](https://github.com/user-attachments/assets/345ce75a-0875-4253-a746-7fa1e722954d)

  Menambahkan key pair baru
  
  ![image](https://github.com/user-attachments/assets/90f3ed6c-3a13-402b-8fba-8c96729aa5df)

- **Network Settings**
  - Network : VPC tempat meluncurkan instance
  - Subnet : Subnet yang digunakan untuk menempatkan antarmuka jaringan
  - Public IP : Ketika statusnya Enable, maka instance akan memiliki public IP ketika dibuat
  - Firewall / Security Group : Sekumpulan aturan yang mengontrol lalu lintas jaringan yang masuk ke dan keluar dari instance

- **Storage**
<br>Mengatur spesifikasi penyimpanan yang menempel pada instance.
  ![image](https://github.com/user-attachments/assets/a0b88640-4dc2-498c-9971-0543923db37e)

Setelah semua hal diatur sesuai kebutuhan, pilih tombol Launch Instance untuk memulai proses pembuatan instance. Kita juga dapat mengatur berapa instance yang akan dibuat.

Setelah proses pembuatan instance selesai, buka halaman Instance untuk melihat daftar instance yang sudah dibuat. Pastikan Instance State dalam keadaan "Running" dan instance memiliki public IP. Jika Instance State tidak dalam kedaan "Running", pilih instance yang akan diaktifkan kemudian pilih dropdown "Instance State" yang ada di bagian atas halaman Instance, lalu pilih "Start Instance".

![image](https://github.com/user-attachments/assets/455fa061-85cc-477b-a878-9f7fb540ec6f)

Salah satu cara untuk memastikan instance sudah berhasil dibuat adalah dengan melakukan perintah "ping (public ip)" melalui terminal komputer kita. Namun jika kita coba perintah ping sekarang, respon yang didapatkan masih belum sesuai dengan konsep yang seharusnya. Hal ini belum tentu karena kita gagal membuat instance, melainkan kita perlu menambahkan firewall atau rule terkait ping pada instance yang kita buat.

Untuk menambahkan firewall terkait ping, kita pilih instance dengan nama instance yang ingin kita ping. Lalu pilih section **Security** dari instance tersebut dan pilih nama security group yang sudah tersedia di instance tersebut. Dengan begitu, kita sekarang berada di halaman untuk edit security group. Pada bagian **Inbound Rule**, pilih **Edit Inbound Rule**, kemudian pilih **Add rule**. Atur spesifikasi rule baru seperti berikut. Kemudian pilih **Save rule**

![image](https://github.com/user-attachments/assets/d3d9c1e9-90ef-43d6-a367-b5a42222acfa)

Sekarang, kita coba ping public ip instance melalui terminal komputer kita.
![image](https://github.com/user-attachments/assets/57781124-e313-46f8-80f2-0cf60381acd9)

Yeeey, kita berhasil memastikan instance telah berjalan dengan mengirim ping request ke public ip instance dan menerima balasan dari instance yang telah kita buat.

Selanjutnya, kami ingin kalian juga mencoba membuat instance seperti di atas.

