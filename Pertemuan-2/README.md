# Pertemuan 2 LBE NCC 2024 
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
