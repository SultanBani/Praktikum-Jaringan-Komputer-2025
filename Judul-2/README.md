# Praktikum-Jaringan-Komputer-2025

## Judul-2 Build a Switch and Router Network


### Topologi Jaringan 
Topologi jaringan ini menggambarkan koneksi dasar antara dua komputer pribadi, PC-A dan PC-B, yang terhubung melalui perangkat inter jaringan. PC-A terhubung ke Switch0 (model Cisco 2960-24TT), dan Switch0 selanjutnya terhubung ke Router0 (model Cisco ISR4331). Router0 berfungsi sebagai penghubung dan pemisah antara jaringan lokal PC-A dan Switch0 dengan jaringan lokal PC-B, di mana PC-B terhubung langsung ke Router0. Dengan Router0 di tengah, PC-A dan PC-B kemungkinan berada pada dua subnet IP yang berbeda, sehingga Router0 bertanggung jawab untuk merutekan lalu lintas data di antara keduanya.
![alt text](ImageFolder/Topologi.jpg)



###  Ping PC-A ke PC-B Sebelum Konfigurasi
Awalnya ketika PC-A melakukan ping ke PC-B (alamat IP 192.168.0.3) sebelum Router R1 dikonfigurasi, ping tersebut gagal dan menghasilkan pesan "Request timed out" untuk semua paket. Kegagalan ini terjadi karena PC-A dan PC-B berada pada subnet jaringan yang berbeda (PC-A di 192.168.1.0/24 dan PC-B di 192.168.0.0/24). Komunikasi antar-subnet (Lapisan 3) membutuhkan perangkat perutean, namun antarmuka default gateway pada Router R1 belum dikonfigurasi dan diaktifkan, sehingga lalu lintas tidak dapat dirutekan di antara kedua subnet tersebut.
![alt text](ImageFolder/PCA-PCBSblm.jpg)



### Ping PC-A ke PC-B Setelah Konfigurasi
Setelah Router R1 dikonfigurasi dengan alamat IP yang benar pada kedua antarmukanya (G0/0/1 untuk jaringan PC-A dan G0/0/0 untuk jaringan PC-B) dan fitur perutean diaktifkan, ping dari PC-A ke PC-B (alamat IP 192.168.0.3) berhasil sepenuhnya. Hasilnya menunjukkan 4 paket terkirim dan 4 paket diterima (0% loss) dengan balasan yang cepat (time=<1ms atau 2ms). Keberhasilan ini membuktikan bahwa router kini berfungsi sebagai default gateway dan telah berhasil merutekan lalu lintas Layer 3 antar-jaringan 192.168.1.0/24 dan 192.168.0.0/24.
![alt text](ImageFolder/PCA-PCBStlh.jpg)



### Ping Switch ke PC-B
Hasil ping dari Switch S1 ke PC-B (alamat IP 192.168.0.3) menunjukkan keberhasilan 100% (5 dari 5 paket terkirim diterima). Keberhasilan ini menunjukkan bahwa switch telah berhasil menggunakan default gateway yang telah dikonfigurasi (192.168.1.1 pada R1) untuk mengirim lalu lintas ICMP ke jaringan lain (192.168.0.0/24) dan menerima balasan dari PC-B. Hal ini memverifikasi bahwa Switch S1, Router R1, dan PC-B semuanya telah dikonfigurasi dengan benar dan memiliki konektivitas Layer 3 end-to-end yang berfungsi.
![alt text](ImageFolder/Switch-PCB.jpg)


### Link YouTube
https://youtu.be/d4qd6esvR34


