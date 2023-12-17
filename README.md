## Praktikum Modul 5 Jaringan Komputer

**Kelompok A16 :**

| Nama | NRP |
| ----------- | ----------- |
| Clarissa Luna Maheswari | 5025211003 |
| Heru Dwi Kurniawan | 5025211055 

## Soal 

Setelah pandai mengatur jalur-jalur khusus, kalian diminta untuk membantu North Area menjaga wilayah mereka dan kalian dengan senang hati membantunya karena ini merupakan tugas terakhir.

Tugas pertama, buatlah peta wilayah sesuai berikut ini:

![image](https://github.com/herukurniawann/Jarkom-Modul-4-A16-2023/assets/93961310/1803d6aa-689c-4a85-9479-fe29e3cfff7c)

Keterangan:	Richter adalah DNS Server
		Revolte adalah DHCP Server
		Sein dan Stark adalah Web Server
		Jumlah Host pada SchwerMountain adalah 64
		Jumlah Host pada LaubHills adalah 255
		Jumlah Host pada TurkRegion adalah 1022
		Jumlah Host pada GrobeForest adalah 512

Untuk menghitung rute-rute yang diperlukan, gunakan perhitungan dengan metode VLSM. Buat juga pohonnya, dan lingkari subnet yang dilewati.
Kemudian buatlah rute sesuai dengan pembagian IP yang kalian lakukan. 
Tugas berikutnya adalah memberikan ip pada subnet SchwerMountain, LaubHills, TurkRegion, dan GrobeForest menggunakan bantuan DHCP.

## Penentuan Subnet

<img width="2004" alt="Frame 9" src="https://github.com/herukurniawann/Jarkom-Modul-4-A16-2023/assets/93961310/f65f8a62-45f7-4cb0-8882-fc2484eeaabf">

## Penentuan Rute dan Pembagian IP VLSM

![image](https://github.com/herukurniawann/Jarkom-Modul-4-A16-2023/assets/93961310/655f8ec9-9487-49dc-ae03-5a56eb5a3a7e)

![image](https://github.com/herukurniawann/Jarkom-Modul-4-A16-2023/assets/93961310/229ebd89-3df1-48f6-82e8-cee91655cf55)


## Tree 
<img width="4875" alt="Frame 10" src="https://github.com/herukurniawann/Jarkom-Modul-4-A16-2023/assets/93961310/60f6ef61-4454-4cf0-80d4-e1ea4b86fee5">


## Konfigurasi Setiap Node

**Aura**
```bash
auto eth0
iface eth0 inet static
    address 192.168.122.2
    netmask 255.255.255.0
    gateway 192.168.122.1

auto eth1 
iface eth1 inet static
      address 10.7.0.21
      netmask 255.255.255.252

auto eth2
iface eth2 inet static
       address 10.7.0.17
       netmask 255.255.255.252
```
 

