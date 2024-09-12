# Pertemuan 2 LBE NCC 2024

1. [Network Service AWS](#network-service-aws)
    - [Fondasi Jaringan](#fondasi-jaringan)
    - [Jaringan Aplikasi](#jaringan-aplikasi)
    - [Jaringan Edge](#jaringan-edge)
    - [Konektivitas Hibrid](#konektivitas-hibrid)
    - [Keamanan Jaringan](#keamanan-jaringan)
2. [Membangun Infrastruktur AWS Sederhana](#membangun-infrastruktur-aws-sederhana)
    - [Konfigurasi Jaringan](#konfigurasi-jaringan)
    - [Web Server](#web-server)
    - [Database](#database)
3. [Deploy Aplikasi](deploy-aplikasi)
    - [Konfigurasi Aplikasi](#konfigurasi-aplikasi)
    - [Port Forwarding pada NGINX](#port-Forwarding-pada-nginx)
    - [Menjalankan Aplikasi sebagai Layanan dengan Systemd](#menjalankan-aplikasi-sebagai-layanan-dengan-systemd)

## Network Service AWS
AWS (Amazon Web Services) menawarkan berbagai network service (layanan jaringan) yang direncang untuk  menyediakan infrastruktur jaringan yang aman, scalable, dan fleksibel bagi pengguna untuk menghubungkan, mengelola, dan mengamankan sumber daya mereka di cloud.
## Daftar Network Service AWS
### Fondasi Jaringan
#### 1. Amazon Virtual Private Cloud (Amazon VPC)
Amazon VPC memungkinkan pengguna untuk membuat jaringan virtual di dalam AWS yang terisolasi dari jaringan lain. Pengguna dapat mendefinisikan ruang alamat IP, subnet, tabel routing, dan gateway jaringan untuk mengontrol lalu lintas yang masuk dan keluar. Amazon VPC memungkinkan pengaturan yang aman untuk menjalankan sumber daya AWS dalam lingkungan yang sepenuhnya terpisah.

![image](https://github.com/user-attachments/assets/2cb0803f-21a5-4445-a885-304e15883150)
- Virtual Private Cloud (VPC) vs Private Cloud:
  - Virtual Private Cloud (VPC) adalah jaringan virtual yang berjalan di dalam infrastruktur cloud publik yang disediakan oleh penyedia layanan, dalam hal ini AWS. Pengguna (tenant) membuat dan mengelola VPC mereka sendiri di atas cloud publik, seperti AWS, dengan kontrol penuh terhadap lingkungan jaringan virtual mereka.
  - Private Cloud adalah infrastruktur cloud yang dimiliki dan dioperasikan oleh sebuah organisasi, di mana semua sumber daya fisik dan virtual disediakan dan dikelola secara eksklusif oleh organisasi itu sendiri. Dalam private cloud, unit bisnis organisasi tersebut bertindak sebagai tenant, dan perusahaan IT internal adalah penyedia layanannya.

#### 2. AWS Transit Gateway
AWS Transit Gateway memungkinkan pengguna untuk menghubungkan beberapa VPC dan jaringan on-premises ke dalam satu gateway pusat. Ini mempermudah pengelolaan dan skala jaringan yang besar, mengurangi kompleksitas routing, dan meningkatkan efisiensi jaringan. Transit Gateway mendukung konektivitas yang aman dan efisien antar wilayah AWS (AWS Regions).
![image](https://github.com/user-attachments/assets/3afd0793-c468-41e8-88f4-7a860bc3b211)

#### 3. AWS PrivateLink
AWS PrivateLink memungkinkan layanan yang di-host di AWS, seperti Amazon S3 atau layanan pengguna yang berjalan pada Amazon ECS, diakses secara aman melalui VPC endpoint tanpa harus melalui internet publik. PrivateLink meningkatkan keamanan dengan meminimalkan eksposur data dan mengurangi risiko serangan.
![image](https://github.com/user-attachments/assets/937f7bfe-8092-4e25-8dcf-270a89e82b0c)

### Jaringan Aplikasi
#### 1. AWS VPC Lattice
Amazon VPC Lattice adalah layanan jaringan aplikasi yang secara konsisten menghubungkan, memantau, dan mengamankan komunikasi antarlayanan Anda, dengan membantu meningkatkan produktivitas sehingga developer Anda dapat berfokus membangun fitur yang penting bagi bisnis Anda. Anda dapat menentukan kebijakan manajemen lalu lintas jaringan, akses, serta pemantauan untuk menghubungkan layanan komputasi dengan cara yang sederhana dan konsisten di seluruh instans, kontainer, dan aplikasi nirserver.
![image](https://github.com/user-attachments/assets/22618ed1-ff91-4099-99f9-3945b0e02bda)

#### 2. AWS App Mesh
AWS App Mesh adalah mesh layanan yang menyediakan jaringan tingkat aplikasi untuk mempermudah layanan Anda berkomunikasi satu sama lain di beberapa tipe infrastruktur komputasi. App Mesh memberikan visibilitas menyeluruh dan ketersediaan yang tinggi untuk aplikasi.

Aplikasi modern biasanya terdiri dari beberapa layanan. Setiap layanan dapat dibuat menggunakan beberapa tipe infrastruktur komputasi, seperti Amazon EC2, Amazon ECS, Amazon EKS, dan AWS Fargate. Seiring bertambahnya jumlah layanan dalam aplikasi, menjadi sulit untuk menunjukkan dengan tepat lokasi kesalahan, merutekan ulang lalu lintas setelah kegagalan, dan men-deploy perubahan kode secara aman. Sebelumnya, Anda diharuskan untuk membangun logika pemantauan dan kontrol secara langsung ke dalam kode Anda dan men-deploy kembali layanan Anda setiap kali ada perubahan.

![image](https://github.com/user-attachments/assets/11c3df12-c1bc-484e-8f78-64e10868731f)

#### 3. AWS API Gateaway
Amazon API Gateway adalah layanan yang dikelola secara penuh yang memudahkan pengembang untuk membuat, menerbitkan, memelihara, memantau, dan mengamankan API pada segala skala. API bertindak sebagai "pintu depan" bagi aplikasi untuk mengakses data, logika bisnis, atau fungsi dari layanan backend Anda. Dengan menggunakan API Gateway, Anda dapat membuat API RESTful dan API WebSocket yang memungkinkan aplikasi berkomunikasi dua arah secara real time. API Gateway mendukung beban kerja terkontainer dan tanpa server, serta aplikasi web.

API Gateway menangani semua tugas yang terlibat dalam penerimaan dan pemrosesan hingga ratusan ribu panggilan API secara bersamaan, termasuk pengelolaan lalu lintas, dukungan CORS, otorisasi dan kontrol akses, pembatasan, pemantauan, dan pengelolaan versi API. API Gateway tidak memiliki biaya minimum atau uang muka. Anda membayar panggilan API yang Anda terima dan jumlah data yang ditransfer keluar, dan dengan model harga bertingkat API Gateway, Anda dapat mengurangi biaya saat penggunaan API diskalakan.
![image](https://github.com/user-attachments/assets/61551209-ac0b-4f46-be14-039e3b9364be)

#### 4. AWS Cloud Map
AWS Cloud Map adalah layanan penemuan sumber daya cloud. Dengan Cloud Map, Anda dapat menentukan nama kustom untuk sumber daya aplikasi Anda, dan layanan ini akan mengelola lokasi terbaru dari sumber daya yang berubah secara dinamis. Layanan ini akan meningkatkan ketersediaan aplikasi Anda karena layanan web Anda selalu menemukan lokasi terbaru dari sumber dayanya.

![image](https://github.com/user-attachments/assets/4d58dcd8-d19b-4ed6-8254-c32af8b343a0)

#### 5. Elastic Load Balancing (ELB)
Elastic Load Balancing mendistribusikan lalu lintas aplikasi secara otomatis di beberapa target, seperti instance Amazon EC2, container, alamat IP, dan fungsi Lambda, untuk memastikan aplikasi tetap tersedia dan dapat diskalakan. AWS menawarkan tiga jenis load balancer: Application Load Balancer, Network Load Balancer, dan Gateway Load Balancer.
![image](https://github.com/user-attachments/assets/f87bf8fe-dee9-4007-a53f-08f81c0efbe3)

### Jaringan Edge
#### 1. Amazon CloudFront
Amazon CloudFront adalah layanan Content Delivery Network (CDN) yang mengantarkan konten (seperti situs web, video, aplikasi, dan API) dengan latensi rendah dan kecepatan tinggi. CloudFront menggunakan jaringan edge locations di seluruh dunia untuk menyimpan salinan konten yang sering diakses dekat dengan lokasi pengguna, yang mempercepat waktu pemuatan dan mengurangi beban server asli.
![image](https://github.com/user-attachments/assets/8e765127-9ecc-4792-b060-63022d0c34d1)

#### 2. Amazon Route 53
Amazon Route 53 adalah layanan Domain Name System (DNS) web yang sangat tersedia dan dapat diskalakan. Layanan ini mengarahkan pengguna akhir ke aplikasi internet dengan cara yang paling andal dan efisien, menggunakan jaringan global AWS untuk memastikan kecepatan resolusi yang cepat dan tingkat ketersediaan yang tinggi.
![image](https://github.com/user-attachments/assets/80494904-2a2e-4342-9e57-b6f60819ca08)

#### 3. AWS Global Accelerator
AWS Global Accelerator meningkatkan kinerja aplikasi global dengan memanfaatkan jaringan AWS global. Layanan ini menyediakan endpoint statis yang memudahkan distribusi trafik aplikasi ke berbagai wilayah geografis berdasarkan kondisi jaringan real-time, sehingga mengurangi latensi dan meningkatkan kecepatan aplikasi bagi pengguna di seluruh dunia.
![image](https://github.com/user-attachments/assets/ab734df7-58b6-4d0c-9d3e-f6bd46f3b3d5)

### Konektivitas Hibrid
#### 1. AWS Direct Connect
AWS Direct Connect menyediakan koneksi jaringan pribadi yang aman dan performa tinggi antara pusat data pengguna dan AWS. Layanan ini memungkinkan transfer data yang lebih cepat dengan latensi rendah dan lebih konsisten dibandingkan koneksi internet publik. Direct Connect juga mendukung berbagai opsi bandwidth yang dapat disesuaikan dengan kebutuhan bisnis.
![image](https://github.com/user-attachments/assets/748470ea-da01-4e31-bc3c-c43cb0b06703)

#### 2. AWS Site-to-site VPN
AWS Site-to-Site VPN adalah layanan terkelola penuh yang menciptakan koneksi aman antara pusat data atau kantor cabang Anda dengan sumber daya AWS Anda dengan menggunakan terowongan Keamanan IP (IPSec). Saat menggunakan Site-to-Site VPN, Anda dapat terhubung baik ke Cloud Privat Virtual (VPC) maupun AWS Transit Gateway Anda, dan dua terowongan per koneksi digunakan untuk meningkatkan redundansi.

Untuk aplikasi yang didistribusikan secara global, opsi Accelerated Site-to-Site VPN memberikan kinerja yang lebih besar dengan bekerja sama dengan AWS Global Accelerator untuk mengarahkan lalu lintas Anda secara cerdas ke titik akhir jaringan AWS terdekat dengan kinerja terbaik.

#### 3. VPN Klien
VPN Klien AWS adalah solusi VPN akses jarak jauh terkelola penuh yang dapat digunakan oleh karyawan di lokasi yang jauh untuk mengakses sumber daya dengan aman baik dalam jaringan bisnis AWS maupun on-premise Anda. Karena bersifat sepenuhnya elastis, VPN Klien AWS secara otomatis menaikkan atau menurunkan skala sesuai permintaan. Saat memigrasikan aplikasi ke AWS, pengguna Anda akan mengaksesnya dengan cara yang sama seperti sebelum, selama, dan setelah migrasi. VPN Klien AWS, termasuk klien perangkat lunak, mendukung protokol OpenVPN.

#### 4. WAN AWS Cloud
AWS Cloud WAN menyediakan dasbor pusat untuk membuat koneksi antara kantor cabang, pusat data, dan Amazon Virtual Private Clouds (Amazon VPC) Anda—membangun jaringan global hanya dengan beberapa klik. Anda menggunakan kebijakan jaringan untuk mengotomatiskan manajemen jaringan dan tugas keamanan di satu lokasi. Cloud WAN menghasilkan tampilan lengkap jaringan on-premise dan AWS Anda untuk membantu memantau kondisi, keamanan, dan performa jaringan.
![image](https://github.com/user-attachments/assets/59e94bf5-6988-4857-a563-1d98906a5285)

### Keamanan Jaringan
#### 1. AWS Shield
AWS Shield adalah layanan perlindungan DDoS terkelola yang menjaga aplikasi yang berjalan di AWS.
![image](https://github.com/user-attachments/assets/4cb4a720-96de-49c7-bdec-4e88c3c9bc34)

#### 2. AWS WAF
AWS WAF membantu melindungi Anda dari eksploit web umum dan bot yang dapat memengaruhi ketersediaan, mengancam keamanan, atau menghabiskan sumber daya secara berlebihan.
![image](https://github.com/user-attachments/assets/e2e245aa-9fcc-4417-a298-aeef7824747c)

#### 3. AWS Network Firewall
AWS Network Firewall adalah firewall jaringan yang terkelola yang dapat digunakan untuk mengontrol lalu lintas masuk dan keluar dari VPC berdasarkan aturan yang telah ditentukan. Ini mencakup fitur filtering konten, deteksi intrusi, dan pencegahan serangan yang dapat dikustomisasi untuk memenuhi persyaratan keamanan khusus.
![image](https://github.com/user-attachments/assets/ecbae69a-5ce4-48f1-83b9-4eb334910b01)

#### 4. AWS Firewall Manager
AWS Firewall Manager adalah layanan manajemen keamanan yang memungkinkan Anda mengonfigurasi dan mengelola aturan firewall secara terpusat di seluruh akun dan aplikasi Anda di AWS Organizations. Saat aplikasi baru dibuat, Firewall Manager mempermudah pengguna untuk membawa aplikasi dan sumber daya baru ke dalam kepatuhan dengan memberlakukan seperangkat aturan keamanan umum.
![image](https://github.com/user-attachments/assets/7c626b1c-92c8-4266-8433-d5ce90994a76)

## Membangun Infrastruktur AWS Sederhana
Setelah mengetahui berbagai macam layanan pada AWS, kita akan mencoba membuat infrastruktur AWS sederhana. Infrastruktur ini terdiri dari web server yang berada di public subnet dan database yang berada di private subnet. Agar database dapat diakses oleh web server, kita akan menambahkan route table yang mengatur lalu lintas jaringan antara public subnet dengan private subnet. Konfigurasi security group dan network ACL juga perlu dilakukan agar hak akses masing-masing resource sesuai dengan yang dibutuhkan. Struktur infrasturktur dapat lebih jelas dilihat pada ilustrasi berikut:<br>
<center>
<img src="assets/infrastructur-structure.png" alt="Structure of Infrastructure" height=500/>
</center>

### Konfigurasi Jaringan
#### VPC
Sebelum meluncurkan ec2 untuk web server dan rds, kita perlu membuat vpc beserta subnet yang diperlukan. Hal tersebut dapat dilakukan dengan mengakses VPC dashboard pada AWS console. Selanjutnya, anda dapat menekan tombol "Create VPC" seperti pada gambar berikut:<br>
<center>
<img src="assets/vpc-dashboard.png" alt="VPC Dashboard" width=500/>
</center>

Pada halaman pembuatan VPC, pilih "VPC and more" lalu masukkan nama project seperti pada layar berikut:<br>
<center>
<img src="assets/vpc-settings.png" alt="VPC Settings" width=500/>
</center>

Selanjutnya, pilih `2` pada jumlah availibility zone, jumlah public subnet, dan jumlah private subnet. Pilih `None` pada VPC endpoints serta biarkan pilihan lainnya.<br>
<center>
<img src="assets/vpc-az.png" alt="VPC AZ" width=500/>
</center>

#### Auto-assign Public IPv4 pada Public Subnet
Setelah VPC terbuat, kita perlu mengaktifkan `auto-assign public IPv4` pada public subnet. Dengan begitu, web server yang nantinya diletakkan pada public subnet dapat diakses melalui internet.<br>
<center>
<img src="assets/auto-assing1.png" alt="VPC Settings" width=500/>
</center>
<center>
<img src="assets/auto-assing2.png" alt="VPC Settings" width=500/>
</center>
<center>
<img src="assets/auto-assign3.png" alt="VPC Settings" width=500/>
</center>

#### Mengatur route table utama
Secara default, route table utama akan terbuat ketika kita membuat VPC. Namun, kita akan menjadikan `lbe-ncc-rtb-public` sebagai route table utama kita. Karenanya, pilih `lbe-ncc-rtb-private` pada pilihan route table lalu klik `Actions > Set main route table`.<br>
<center>
<img src="assets/main-rt.png" alt="Main Route Table" width=500/>
</center>

### Web Server
Web server merupakan perangkat yang menyediakan konten web pada pengguna melalui internet. Kali ini, kita akan menggunakan `linux ec2` dan `Nginx` sebagai web server.

#### Launch instance ec2
Launch instance ec2 dapat dilakukan seperti pada pertemuan 1. Masukkan `webServer-ec2` sebagai nama instance dan pilih `Ubuntu` sebagai os image. Pada `Network Settings`, pilih vpc yang telah kita buat `lbe-ncc-vpc` dan `subnet public`.
<center>
<img src="assets/launch-ec2-1.png" alt="Launch ec2" width=500/>
</center>

Selain itu, buat pula security group untuk menerima koneksi `ssh` dan `http`.
<center>
<img src="assets/launch-ec2-2.png" alt="Launch ec2" width=500/>
</center>

Klik `launch instance` lalu tunggu hingga berhasil.
<center>
<img src="assets/launch-ec2-3.png" alt="Launch ec2" width=500/>
</center>

Jika telah berhasil, kita dapat melihat public IP web server dengan menekan instance terkait.
<center>
<img src="assets/launch-ec2-4.png" alt="Launch ec2" width=500/>
</center>

#### Mengakses ec2 dengan SSH
Setelah ec2 terbuat, kita dapat mengaksesnya dengan menggunakan SSH. SSH (Secure Shell) merupakan salah satu protokol jaringan yang biasa digunakan untuk memberikan `command` pada remote server. Command dasar ssh adalah `ssh username@host`, dengan username merupakan nama pengguna pada server dan host merupakan hostname atau alamat IP dari server. Selain itu, kita perlu juga menambahkan private key dengan memberikan opsi `-i <nama-file>.pem`. Berikut cara mengakses web server melalui SSH (jangan lupa berpindah ke direktori yang sama dengan file `.pem`).
<center>
<img src="assets/ssh-1.png" alt="SSH" width=500/>
</center>
<center>
<img src="assets/ssh-2.png" alt="SSH" width=500/>
</center>

#### Install dan menjalankan NGINX
Meskipun telah membuka port HTTP, kita belum dapat mengakses apapun pada browser.
<center>
<img src="assets/nginx-1.png" alt="Nginx" width=500/>
</center>

Hal ini dikarenakan belum ada software yang menerima request pada port 80. Karenanya, kita membutuhkan Nginx sebagai web server yang akan menerima request dari pengguna. Untuk mengaktifkannya, kita perlu menginstal terlebih dahulu.
<center>
<img src="assets/nginx-2.png" alt="Nginx" width=500/>
</center>

Selanjutnya, kita dapat mengaktifkannya dengan command `sudo systemctl start nginx` dan memeriksa status nginx dengan `sudo systemctl status nginx`.
<center>
<img src="assets/nginx-3.png" alt="Nginx" width=500/>
</center>

Sekarang, kita dapat mengakses web pada browser seperti berikut:
<center>
<img src="assets/nginx-4.png" alt="Nginx" width=500/>
</center>

### Database
Sebagian besar aplikasi web membutuhkan database untuk menyimpan data yang dibutuhkan. Pada kali ini, kita akan menggunakan database postgresql pada Amazon RDS.

#### Mengatur Security Group
Web server yang telah kita buat perlu berkomunikasi dengan database. Karenanya, kita perlu mengatur security group agar database dapat menerima koneksi postgresql (port 5432) dari web server, begitupun sebaliknya.
Pertama, kita perlu membuat `ncc-db-sg` melalui menu `Security Groups` pada `VPC Dashboard`. Selanjutnya, klik `Create Security Group`.
<center>
<img src="assets/sg-1.png" alt="Security Group" width=500/>
</center>

Pada halaman `Create Security Group`, masukkan nama dan deskripsi yang sesuai. Selain itu, pilih juga VPC sesuai yang telah dibuat sebelumnya.
<center>
<img src="assets/sg-2.png" alt="Security Group" width=500/>
</center>

Selanjutnya, kita perlu menambahkan aturan pada `inbound rule` untuk mengirim dan menerima koneksi postgresql (port 5432) dari/ke web server (pilih source dan destination ke security group web server, `webServer-sg`).
<center>
<img src="assets/sg-3.png" alt="Security Group" width=500/>
</center><center>
<img src="assets/sg-4.png" alt="Security Group" width=500/>
</center>

Kita juga perlu mengubah security group pada web server agar dapat menerima koneksi postgresql seperti di atas.
<center>
<img src="assets/sg-5.png" alt="Security Group" width=500/>
</center>
<center>
<img src="assets/sg-6.png" alt="Security Group" width=500/>
</center>
<center>
<img src="assets/sg-7.png" alt="Security Group" width=500/>
</center>

#### Membuat DB Subnet Group
Pada `Amazon RDS > Subnet Groups`, klik `Create DB Subnet Group`
<center>
<img src="assets/subnet-group-1.png" alt="Subnet Group" width=500/>
</center>

Pada halaman `create DB Subnet Group`, masukkan nama yang sesuai dan pilih VPC sesuai dengan VPC yang telah dibuat (ncc-vpc).
<center>
<img src="assets/subnet-group-2.png" alt="Subnet Group" width=500/>
</center>

Selanjutnya, pilih subnet yang sesuai dengan `private subnet`. Karena dropdown tidak menampilkan nama subnet, kalian bisa mencari id dari `private subnet`.
<center>
<img src="assets/subnet-group-3.png" alt="Subnet Group" width=500/>
</center>
<center>
<img src="assets/subnet-group-4.png" alt="Subnet Group" width=500/>
</center>

Klik `create` dan subnet group berhasil dibuat.
<center>
<img src="assets/subnet-group-5.png" alt="Subnet Group" width=500/>
</center>

#### Launch RDS
Pertama, akses Amazon RDS dashboard dan pilih menu `Database`. Selanjutnya, klik tombol `Create Database` yang terdapat di kanan atas sebelah `Restore from S3`.
<center>
<img src="assets/rds-1.png" alt="RDS" width=500/>
</center>

Pada halaman `Create Database`, pilih metode `Standard Create` dan opsi engine `PostgreSQL` (bukan Aurora postgreSQL compatible).
<center>
<img src="assets/rds-2.png" alt="RDS" width=500/>
</center>

Agar mendapatkan konfigurasi yang sesuai dengan ketentuan layanan gratis, pilih `Free Tier` pada menu `Templates`.
<center>
<img src="assets/rds-3.png" alt="RDS" width=500/>
</center>

![alt text](image-16.png)
Masukkan nama instance, username database, dan password.
<center>
<img src="assets/rds-4.png" alt="RDS" width=500/>
</center>

Pada bagian `Connectivity`, pilih `Don't connect to an EC2 compute resource`. Selain itu, pilih vpc `lbe-ncc-vpc` dan subnet group `lbe-ncc-db-subnetgroup`
<center>
<img src="assets/rds-5.png" alt="RDS" width=500/>
</center>

Pilih `No` pada bagian `public access` dan `db-sg` (security group yang telah dibuat) pada security group.
<center>
<img src="assets/rds-6.png" alt="RDS" width=500/>
</center>

Klik `Create Database` dan database berhasil dibuat.
<center>
<img src="assets/rds-7.png" alt="RDS" width=500/>
</center>

#### Mengakses database dari web server
Karena berada di 1 VPC dan kita telah mengatur security group, maka web server seharusnya dapat mengakses private IP database. Untuk mengakses, kita perlu menginstal postgresql pada web server.
<center>
<img src="assets/web-server-1.png" alt="Web Server" width=500/>
</center>

Selanjutnya, kita dapat mencoba akses ke database menggunakan `psql` sesuai dengan nama host/endpoint dan portnya.
<center>
<img src="assets/web-server-2.png" alt="Web Server" width=500/>
</center>
<center>
<img src="assets/web-server-3.png" alt="Web Server" width=500/>
</center>
Selamat, anda telah berhasil membuat database di AWS dan mengaksesnya dari ec2.

## Deploy Aplikasi
Setelah berhasil membangun infrastruktur di AWS, kita akan mencoba melakukan deploy aplikasi. Aplikasi yang akan dideploy merupakan aplikasi CRUD sederhana dan dapat diclone dari https://github.com/arizki787/API-Project.
<center>
<img src="assets/deply-1.png" alt="Deploy" width=500/>
</center>

Pindah ke directory `API-Project` dan kita dapat melihat file-file yang terdapat pada direktori.
<center>
<img src="assets/deply-2.png" alt="Deploy" width=500/>
</center>

### Konfigurasi Aplikasi
Aplikasi yang akan dideploy merupakan aplikasi nodejs sehingga kita perlu menginstall `nodejs` dan `npm` terlebih dahulu.
<center>
<img src="assets/node-1.png" alt="Node Js" width=500/>
</center>
<center>
<img src="assets/node-2.png" alt="Node Js" width=500/>
</center>

Selanjutnya, buat database beserta tabelnya dengan terlebih dahulu mengakses postgresql di RDS. Buat database `school` dan tabel `student` dengan query berikut:
```R
CREATE DATABASE school;
CREATE TABLE student (
    sid VARCHAR(20),
    sname VARCHAR(100),
    uktstatus VARCHAR(15),
    alamat VARCHAR(100),
    email VARCHAR(100)
);
```
Jika berhasil, maka akan terlihat seperti ini.
<center>
<img src="assets/konfig-1.png" alt="Konfigurasi" width=500/>
</center>

Kita juga akan membuat file `.env` untuk mendefinisikan `environment variable` yang diperlukan dengan template sebagai berikut. Jangan lupa untuk mengubah `RDS EndPoint`, `RDS User`, dan `RDS Password` sesuai dengan RDS yang telah kalian buat.
```R
DB_HOST=<RDS EndPoint>
DB_USER=<RDS User>
DB_PORT=5432
DB_PASSWORD=<RDS Password>
DB_NAME=school
```
Dengan menggunakan `nano`, kita dapat menulis file `.env` seperti berikut. 
<center>
<img src="assets/konfig-3.png" alt="Konfigurasi" width=500/>
</center>
<center>
<img src="assets/konfig-2.png" alt="Konfigurasi" width=500/>
</center>

### Port Forwarding pada NGINX
Sebenarnya, aplikasi di atas sudah bisa dijalankan dengan command `npm start`, maka server akan mendengar pada port 3000. Namun, pada praktiknya, tidak lazim kita membuka port secara custom. Biasanya port yang dibuka untuk akses api ada pada port 80 (http) atau 443 (https). Hal tersebut sesuai dengan aturan `security group` pada instance `webServer` yang hanya menerima koneksi ke port 22 (ssh) dan 80 (http). Oleh karena itu, kita perlu melakukan port forwarding dari port 80 ke port 3000 di mana aplikasi kita berjalan.
1. Buat salinan konfigurasi server Nginx dengan command 
```R
sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/backup
```
2. Modifikasi file `/etc/nginx/sites-available/default` dengan menggunakan `nano` menjadi sebagai berikut:
```R
server {
    listen 80;

    location / {
        proxy_set_header   X-Forwarded-For $remote_addr;
        proxy_set_header   Host $http_host;
        proxy_pass         "http://127.0.0.1:3000";
    }
}
```
3. Aktifkan konfigurasi dengan membuat symbolic link di folder `/etc/nginx/sites-enabled` dengan command berikut.
```R
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/
```
4. Restart Nginx dan jalankan aplikasi
```R
sudo systemctl restart nginx
node ./index.js
```
5. Akses web server pada browser, maka aplikasi kita telah dapat terlihat.
<center>
<img src="assets/port-forward.png" alt="Port Forwarding Result" width=500/>
</center>

### Menjalankan Aplikasi sebagai Layanan dengan Systemd
Sebelumnya, kita perlu secara manual menjalankan aplikasi dengan command `node index.js` atau `npm start`. Namun, kita tidak mungkin dapat menjalankan server setiap saat. Oleh karena itu, kita perlu menjalankan aplikasi di latar belakang sebagai suatu layanan. Dengan demikian, aplikasi pada server dapat tetap berjalan dan dapat diakses kapanpun. Hal ini dapat dilakukan dengan mudah di linux dengan menggunakan `systemd`.
1. Buat systemd file dengan `sudo nano /lib/systemd/system/server.service`, lalu isi sebagai berikut. Jangan lupa untuk mengubah `username` dan `path-to-project` sesuai dengan server masing-masing.
```R
[Unit]
Description=Server service
After=network.target

[Service]
Type=simple
User=<username>
ExecStart=/usr/bin/node <path-to-project>
Restart=on-failure
WorkingDirectory=<path-to-project>

[Install]
WantedBy=multi-user.target
```
2. Restart daemon dan jalankan service server. Periksa juga apakah layanan server telah berjalan.
```R
sudo systemctl daemon-reload
sudo systemctl start server
sudo systemctl status server
```
3. Akses kembali public ip. Kalian akan mendapati bahwa server berjalan walaupun kalian tidak mengeksekusi npm start pada root project. Dengan demikian, project kalian sudah berjalan pada background.
