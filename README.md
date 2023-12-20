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

## Router
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

**Heiter**

```bash
auto eth0
iface eth0 inet static
         address 10.7.0.22
         netmask 255.255.255.252
         gateway 10.7.0.21
	 up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth2
iface eth2 inet static
         address 10.7.8.1
         netmask 255.255.248.0

auto eth1
iface eth1 inet static
         address 10.7.4.1
         netmask 255.255.252.0
```

**Frieren**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
         address 10.7.0.18
         netmask 255.255.255.252
         gateway 10.7.0.17
	 up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
         address 10.7.0.13
         netmask 255.255.255.252

auto eth2
iface eth2 inet static
         address 10.7.0.9
         netmask 255.255.255.252
```

**Himmel**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
         address 10.7.0.10
         netmask 255.255.255.252
         gateway 10.7.0.9
	 up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
         address 10.7.0.129
         netmask 255.255.255.128

auto eth2
iface eth2 inet static
         address 10.7.2.1
         netmask 255.255.255.0
```

**Fern**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.7.0.130
	netmask 255.255.255.128
	gateway 10.7.0.129
	up echo nameserver 192.168.122.1 > /etc/resolv.conf


# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.7.0.5
	netmask 255.255.255.252


# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.7.0.1
	netmask 255.255.255.252
```

## Client

**TurkRegion**
```bash
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
#	hostname ubuntu-1-1
```

**GrobeForest**
```bash
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

**LaubHills**
```bash
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

**SchewerMountain**
```bash
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

## Server

**Sein**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.7.4.2
	netmask 255.255.252.0
	gateway 10.7.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

**Stark**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
         address 10.7.0.14
         netmask 255.255.255.252
         gateway 10.7.0.13
	 up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

**Ritcher**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.7.0.6
	netmask 255.255.255.252
	gateway 10.7.0.5
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

**Revolte**
```bash
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.7.0.2
	netmask 255.255.255.252
	gateway 10.7.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

## Routing

**Aura**
```bash
route add -net 10.7.0.0 netmask 255.255.255.252 gw 10.7.0.18
route add -net 10.7.0.4 netmask 255.255.255.252 gw 10.7.0.18
route add -net 10.7.0.128 netmask 255.255.255.128 gw 10.7.0.18
route add -net 10.7.2.0 netmask 255.255.255.0 gw 10.7.0.18
route add -net 10.7.0.8 netmask 255.255.255.252 gw 10.7.0.18
route add -net 10.7.0.12 netmask 255.255.255.252 gw 10.7.0.18

route add -net 10.7.8.0 netmask 255.255.248.0 gw 10.7.0.22
route add -net 10.7.4.0 netmask 255.255.252.0 gw 10.7.0.22
```
**Frieren**
```bash
route add -net 10.7.0.0 netmask 255.255.255.252 gw 10.7.0.10
route add -net 10.7.0.4 netmask 255.255.255.252 gw 10.7.0.10
route add -net 10.7.0.128 netmask 255.255.255.128 gw 10.7.0.10
route add -net 10.7.2.0 netmask 255.255.255.0 gw 10.7.0.10
```

**Himmel**
```bash
route add -net 10.7.0.0 netmask 255.255.255.252 gw 10.7.0.130
route add -net 10.7.0.4 netmask 255.255.255.252 gw 10.7.0.130
```
## Soal:

## 1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.**

Untuk langkahnya mengonfigurasikan `Aura` menggunakan iptables dan tanpa menggunakan MASQUERADE memakai peritah berikut :

`iptables -t nat -A POSTROUTING -s 10.7.0.0/20 -o eth0 -j SNAT --to-source 192.1$`

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/1ab89ec0-c5f0-4e5a-98ab-e0825ae94517)

Hasil

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/30647b13-7561-40a5-9b26-ac00d4d87e84)


## 2. Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

Langkah untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP, menggunakan command berikut ini :

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/43f1d0ed-901a-48a8-a5b4-ab222e19ab41)

```bash
# soal nomor 2
iptables -F

# Izinkan koneksi pada port 8080 TCP
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

# Drop semua koneksi TCP & UDP
iptables -A INPUT -p tcp -j DROP
iptables -A INPUT -p udp -j DROP
```
**Pengujian**

Pengujian Pada Port 8080

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/b7059b9b-7a1b-4060-b97e-7841d9d8aeab)

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/c1aa48af-42ac-49b6-858c-ceb5df24af38)

Pengujian Pada Port 8000

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/560aea29-1c1e-4776-a802-64a7f2e98773)

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/ada21f37-4150-41c2-861e-a9f91b66f38c)


**Hasil**

Hasil Pengujian Pada Port 8080

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/1b0730fe-276b-4df1-9b83-a68b55f8797e)


Hasil Pengujian Pada Port 8000

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/e28cf731-da7f-4e61-81e7-46cf278729d6)

## 3. Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.







