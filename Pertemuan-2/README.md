# Pertemuan 2 LBE NCC 2024
## Network Service AWS
AWS (Amazon Web Services) menawarkan berbagai network service (layanan jaringan) yang direncang untuk  menyediakan infrastruktur jaringan yang aman, scalable, dan fleksibel bagi pengguna untuk menghubungkan, mengelola, dan mengamankan sumber daya mereka di cloud.
## Daftar Network Service AWS
### 1. Amazon Virtual Private Cloud (Amazon VPC)
Amazon VPC memungkinkan pengguna untuk membuat jaringan virtual di dalam AWS yang terisolasi dari jaringan lain. Pengguna dapat mendefinisikan ruang alamat IP, subnet, tabel routing, dan gateway jaringan untuk mengontrol lalu lintas yang masuk dan keluar. Amazon VPC memungkinkan pengaturan yang aman untuk menjalankan sumber daya AWS dalam lingkungan yang sepenuhnya terpisah.

![image](https://github.com/user-attachments/assets/2cb0803f-21a5-4445-a885-304e15883150)
- Virtual Private Cloud (VPC) vs Private Cloud:
  - Virtual Private Cloud (VPC) adalah jaringan virtual yang berjalan di dalam infrastruktur cloud publik yang disediakan oleh penyedia layanan, dalam hal ini AWS. Pengguna (tenant) membuat dan mengelola VPC mereka sendiri di atas cloud publik, seperti AWS, dengan kontrol penuh terhadap lingkungan jaringan virtual mereka.
  - Private Cloud adalah infrastruktur cloud yang dimiliki dan dioperasikan oleh sebuah organisasi, di mana semua sumber daya fisik dan virtual disediakan dan dikelola secara eksklusif oleh organisasi itu sendiri. Dalam private cloud, unit bisnis organisasi tersebut bertindak sebagai tenant, dan perusahaan IT internal adalah penyedia layanannya.
### 2. AWS Direct Connect
AWS Direct Connect menyediakan koneksi jaringan pribadi yang aman dan performa tinggi antara pusat data pengguna dan AWS. Layanan ini memungkinkan transfer data yang lebih cepat dengan latensi rendah dan lebih konsisten dibandingkan koneksi internet publik. Direct Connect juga mendukung berbagai opsi bandwidth yang dapat disesuaikan dengan kebutuhan bisnis.
### 3. AWS Transit Gateway
AWS Transit Gateway memungkinkan pengguna untuk menghubungkan beberapa VPC dan jaringan on-premises ke dalam satu gateway pusat. Ini mempermudah pengelolaan dan skala jaringan yang besar, mengurangi kompleksitas routing, dan meningkatkan efisiensi jaringan. Transit Gateway mendukung konektivitas yang aman dan efisien antar wilayah AWS (AWS Regions).
### 4. AWS Global Accelerator
AWS Global Accelerator meningkatkan kinerja aplikasi global dengan memanfaatkan jaringan AWS global. Layanan ini menyediakan endpoint statis yang memudahkan distribusi trafik aplikasi ke berbagai wilayah geografis berdasarkan kondisi jaringan real-time, sehingga mengurangi latensi dan meningkatkan kecepatan aplikasi bagi pengguna di seluruh dunia.
### 5. Amazon CloudFront
Amazon CloudFront adalah layanan Content Delivery Network (CDN) yang mengantarkan konten (seperti situs web, video, aplikasi, dan API) dengan latensi rendah dan kecepatan tinggi. CloudFront menggunakan jaringan edge locations di seluruh dunia untuk menyimpan salinan konten yang sering diakses dekat dengan lokasi pengguna, yang mempercepat waktu pemuatan dan mengurangi beban server asli.
### 6. AWS PrivateLink
AWS PrivateLink memungkinkan layanan yang di-host di AWS, seperti Amazon S3 atau layanan pengguna yang berjalan pada Amazon ECS, diakses secara aman melalui VPC endpoint tanpa harus melalui internet publik. PrivateLink meningkatkan keamanan dengan meminimalkan eksposur data dan mengurangi risiko serangan.
### 7. Elastic Load Balancing (ELB)
Elastic Load Balancing mendistribusikan lalu lintas aplikasi secara otomatis di beberapa target, seperti instance Amazon EC2, container, alamat IP, dan fungsi Lambda, untuk memastikan aplikasi tetap tersedia dan dapat diskalakan. AWS menawarkan tiga jenis load balancer: Application Load Balancer, Network Load Balancer, dan Gateway Load Balancer.
### 8. Amazon Route 53
Amazon Route 53 adalah layanan Domain Name System (DNS) web yang sangat tersedia dan dapat diskalakan. Layanan ini mengarahkan pengguna akhir ke aplikasi internet dengan cara yang paling andal dan efisien, menggunakan jaringan global AWS untuk memastikan kecepatan resolusi yang cepat dan tingkat ketersediaan yang tinggi.
### 9. AWS VPN
AWS VPN menyediakan konektivitas jaringan yang aman antara jaringan on-premises dan AWS, menggunakan dua tipe koneksi: 
- AWS Site-to-Site VPN untuk koneksi jaringan yang lebih besar
- AWS Client VPN untuk koneksi pengguna jarak jauh.
Keduanya menawarkan enkripsi data yang kuat untuk melindungi informasi sensitif selama transmisi.
### 10. AWS Network Firewall
AWS Network Firewall adalah firewall jaringan yang terkelola yang dapat digunakan untuk mengontrol lalu lintas masuk dan keluar dari VPC berdasarkan aturan yang telah ditentukan. Ini mencakup fitur filtering konten, deteksi intrusi, dan pencegahan serangan yang dapat dikustomisasi untuk memenuhi persyaratan keamanan khusus.
