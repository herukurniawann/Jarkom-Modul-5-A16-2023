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

## DHCP 
**DHCP Server**

DHCP Server, kita akan menginstall isc-dhcp-server dengan perintah
```bash
apt-get update
wait
apt-get install isc-dhcp-server -y
wait

echo '
INTERFACESv4="eth0"
INTERFACESv6=""
' > /etc/default/isc-dhcp-server

cp ~/dhcpd.conf /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```
Selanjutnya di file `dhcpd.conf`, kita akan mengkonfigurasi seperti berikut

```bash
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

ddns-update-style none;

subnet 10.7.0.0 netmask 255.255.255.252 {
}

subnet 10.7.0.128 netmask 255.255.255.128 {
    range 10.7.0.131 10.7.0.254;
    option routers 10.7.0.129;
    option broadcast-address 10.7.0.255;
    option domain-name-servers 10.7.0.6;
    default-lease-time 180;
    max-lease-time 5760;
}
subnet 10.7.2.0 netmask 255.255.255.0 {
    range 10.7.2.2 10.7.2.254;
    option routers 10.7.2.1;
    option broadcast-address 10.7.2.255;
    option domain-name-servers 10.7.0.6;
    default-lease-time 180;
    max-lease-time 5760;
}
subnet 10.7.8.0 netmask 255.255.248.0 {
    range 10.7.8.2 10.7.15.254;
    option routers 10.7.8.1;
    option broadcast-address 10.7.15.255;
    option domain-name-servers 10.7.0.6;
    default-lease-time 180;
    max-lease-time 5760;
}
subnet 10.7.4.0 netmask 255.255.252.0 {
    range 10.7.4.3 10.7.7.254;
    option routers 10.7.4.1;
    option broadcast-address 10.7.7.255;
    option domain-name-servers 10.7.0.6;
    default-lease-time 180;
    max-lease-time 5760;
}
```

Install isc-dhcp-relay pada route Himmel,Heiter dengan perintah

**DHCP Relay**

```bash
apt-get update
wait
apt-get install isc-dhcp-relay -y
wait

echo '
SERVERS="10.7.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS="-m replace"
' >  /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1
' >  /etc/sysctl.conf
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

**Tidak Berhasil**

## 3. Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

Langkah untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan dan selebihnya akan di drop, menggunakan command berikut ini :

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/ce50dad9-1075-4159-b683-d2b6acafe958)


**Pengujian :**

Melakukan ping Richter pada 4 Device secara bersamaan :

1. Pertama Melakukan Ping pada SchewerMountain
   
![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/d0354701-397e-47ba-bf73-acfc14e6bd2e)


2. Kedua Melakukan Ping pada GrobeForest

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/5195432b-6f23-42a7-9a1f-c4dddf371c4a)

3. Ketiga Melakukan Ping pada TurkRegion

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/a220aff6-5604-4c51-bcb7-f85363598669)


4. Keempat Melakukan Ping pada LaubHills

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/7af9074c-44bd-4bad-a1e2-ebbe73bcf45e)

Pada saat melakukan Ping LaubHills Gagal, karena maksimal ping hanya 3 device secara bersamaan.


## 4. Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

```bash
# Soal No 4
iptables -A INPUT -p tcp --dport 22 -s 10.7.4.0/22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP
```
![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/a4895883-fcc2-4b8c-a0b3-9b9b4561ab8e)

**Hasil**
Untuk melakukan testing tersebut kita akan menggunakan netcat pada node Sein dan TurkRegion dengan perintah

`nmap 10.7.4.2 -p 22`

**Sein**

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/cbd61a9f-a5d6-4099-ad55-fbdd5c231799)

**TurkRegion**

![image](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/4db165b3-6ca3-46e2-bc31-7e5aaa38e7d8)




## 5.Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.

Langkah pertama untuk melakukan pembatasan akses menuju WebServer hanya diperbolehkan saat jam kerja, yaitu Senin-Jumat pada pukul 08.00-16.00, adalah dengan mengkonfigurasi iptables pada node Sein dan Stark menggunakan perintah berikut:

```bash
Izinkan akses ke Web Server pada Senin-Jumat pukul 08.00-16.00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

# Menolak akses selain dari aturan yang telah ditentukan
iptables -A INPUT -p tcp --dport 80 -j DROP
```

Untuk melakukan pengujian (testing), gunakan netcat pada node Sein dan Stark dengan perintah berikut:
`nc -l -p 80`

Kemudian, lakukan akses pada node Aura menggunakan perintah berikut:

`curl 10.7.4.2 -v`

Dengan demikian, akses ke Web Server hanya akan diizinkan pada hari Senin hingga Jumat pada jam 08.00-16.00, dan permintaan akses di luar waktu tersebut akan ditolak. Pastikan konfigurasi iptables berjalan dengan benar untuk mengimplementasikan pembatasan akses ini.

## 6. Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

Pada langkah ini, kita akan menambahkan pembatasan akses ke server web pada waktu-waktu tertentu agar dapat memberikan kesempatan bagi administrator jaringan untuk beristirahat dan juga mengakomodasi waktu Jumat saat umat Islam pergi ke masjid untuk salat Jumat.

Langkah-langkahnya adalah sebagai berikut:
Larangan Akses pada Hari Senin - Kamis pada Jam 12.00 - 13.00: Pada langkah pertama, kita akan menerapkan larangan akses pada hari Senin hingga Kamis pada jam 12.00 - 13.00. Ini bertujuan untuk memberikan waktu istirahat maksimal bagi administrator jaringan. Untuk melakukannya, kita menggunakan perintah berikut:

```bash
Larangan akses pada hari Senin-Kamis pada jam 12.00-13.00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j DROP
```
Dengan perintah ini, semua permintaan akses ke port 80 (web) akan ditolak selama waktu yang telah ditentukan pada hari Senin hingga Kamis.

Larangan Akses pada Hari Jumat pada Jam 11.00 - 13.00: Pada langkah kedua, kita akan menerapkan larangan akses pada hari Jumat pada jam 11.00 - 13.00. Ini bertujuan untuk menghormati waktu salat Jumat, yang umumnya dilaksanakan pada jam tersebut. Untuk melakukannya, kita menggunakan perintah berikut:
```
Larangan akses pada hari Jumat pada jam 11.00-13.00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j DROPs
```
Dengan perintah ini, semua permintaan akses ke port 80 akan ditolak selama waktu yang telah ditentukan pada hari Jumat.

**Testing**
Setelah mengkonfigurasi aturan-aturan di atas, kita dapat melakukan pengujian (testing) untuk memastikan bahwa pembatasan akses berjalan dengan benar. Pengujian ini mencakup mengaktifkan layanan netcat pada node Sein dan Stark untuk memantau permintaan akses serta menguji akses dari node Aura menggunakan perintah curl atau nmap, sesuai dengan instruksi dalam teks.

Untuk melakukan testing tersebut kita akan menggunakan netcat pada node Sein dan Stark dengan perintah

`nc -l -p 80`

dan melakukan akses pada node Aura dengan perintah

`bash nmap 10.7.4.2 -p 80`

Dengan ini, kita dapat memastikan bahwa aturan-aturan yang telah ditentukan berfungsi sesuai yang diharapkan.

![WhatsApp Image 2023-12-24 at 10 02 40_9d6fe6ad](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/63f580b5-e272-44c4-9359-9811e10c8a13)

![WhatsApp Image 2023-12-24 at 10 03 09_fc771373](https://github.com/herukurniawann/Jarkom-Modul-5-A16-2023/assets/93961310/e92bbfe0-5b5a-44f5-b62a-e687b4ec1716)

## 7. Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

Untuk melakukan pembagian beban pada web server, kita akan mengkonfigurasi iptables pada node Sein dan Stark dengan perintah

```bash
# Soal7
iptables -A PREROUTING -t nat -p tcp -d 10.7.4.2 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.7.4.2:80
iptables -A PREROUTING -t nat -p tcp -d 10.7.4.2 --dport 80 -j DNAT --to-destination 10.7.0.14:80

iptables -A PREROUTING -t nat -p tcp -d 10.7.0.14 --dport 443 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.7.0.14:443
iptables -A PREROUTING -t nat -p tcp -d 10.7.0.14 --dport 443 -j DNAT --to-destination 10.7.4.2:443
```

Kemudian Untuk mencoba soal no 7 langkah pertama melakukan pemangilan berulang kali dengan menggunakan curl pada node dengan ip 10.7.4.2

Maka akan didapatkan hasil sebagai berikut :


## 8. Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

Langkah pengerjaan nomor 8 diperlukan bantuan `--datestart` dan `--datestop` untuk melakukan pembatasan akses pada hari-hari tertentu. Disini diperlukan subnet dari Revolte karena pembatasan yang diinginkan adalah terhadap subnet. Disini subnet kami adalah terdapat pada A1 dimana memiliki ip `10.7.0.0/30` dan menentukan protokol yang digunakan sebagai berikut

`iptables -A INPUT -p tcp --dport 80 -s 10.7.0.0/30 -m time --datestart 2023-12-10 --datestop 2024-02-15 -j DROP`
`iptables -A INPUT` adalah opsi untuk menambahkan rule pada chain INPUT untuk menolak koneksi TCP pada port 80 yang berasal dari subnet A1
`-p tcp` adalah opsi untuk menentukan protokol yang digunakan
`--dport 80` adalah opsi untuk menentukan port yang digunakan
`--datestart` adalah opsi untuk menentukan tanggal mulai pembatasan akses
`--datestop` adalah opsi untuk menentukan tanggal berakhirnya pembatasan akses
`-j DROP` adalah opsi untuk menolak koneksi

Untuk melakukan testing tersebut kita akan menggunakan netcat pada node Sein dan Stark dengan perintah `nc -l -p 80`

## 9. Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. (clue: test dengan nmap)

Untuk mengerjakan nomor ini diperlukan bantuan `--hitcount` dan `--seconds` untuk melakukan pembatasan akses pada hari-hari tertentu. Selanjutnya kita bisa mengatur settingan dari iptables sebagai berikut :
```bash
iptables -N PORTSCAN
iptables -A PORTSCAN -m recent --set --name portscan
iptables -A PORTSCAN -m recent --update --seconds 600 --hitcount 20 --name portscan -j DROP
iptables -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 2/s -j ACCEPT
iptables -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -j PORTSCAN
```

Untuk melakukan testing untuk menentukan apakah port tersebut terbuka atau tidak dengan menggunakan nmap pada node `SchewerMountain` dengan perintah
```bash
nmap 10.7.0.14 -p 1-10 # Masi bisa ngescan
nmap 10.7.0.14 -p 1-30 # Langsung di block
```

## 10. Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 

Langkah untuk melakukan logging paket yang di-drop, kita akan mengkonfigurasi `iptables` pada `Sein` dan `Stark` dengan perintah

Pada kali ini kita akan meneruskan Soal nomor 9 dan menambahakan script berikut ini :

`iptables -A PORTSCAN -m recent --update --seconds 600 --hitcount 20 --name portscan -j LOG --log-prefix "Portscan Detected: " --log-level 4`

`LOG --log-prefix "Portscan detected: " --log-level 4` untuk mengarahkan paket yang memenuhi aturan untuk dilakukan logging.

`j LOG`` digunakan untuk melakukan logging.
`--log-prefix "Portscan detected: ":` untuk menambahkan prefix kedalam log yaitu teks "Portscan detected: {isi log}".
`--log-level 4:` menentukan tingakatan atau level log pada syslog, dalam hal ini level 4 berarti 'Warning'.
Karena pada log sebelumnya kita menentukan level log 4 (warning), selanjutnya kita perlu melakukan konfigurasi pada `etc/rsyslog.d/50-default.conf` untuk menambahkan configurasi `kernel.warning -/var/log/iptables.log` sehingga seperti configurasi dibawah ini

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
kernel.warning                  -/var/log/iptables.log
#lpr.*                          -/var/log/lpr.log
mail.*                          -/var/log/mail.log
#user.*                         -/var/log/user.log

```bash
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info                      -/var/log/mail.info
#mail.warn                      -/var/log/mail.warn
mail.err                        /var/log/mail.err
```
jika sudah kita perlu melakukan menjalankan command touch `/var/log/iptables.log` dan menjalankan `/etc/init.d/rsyslog restart` untuk melakukan restart syslog supaya konfigurasi baru dapat diterapkan kedalam syslog dan hasil log bisa masuk kedalam `iptables.log`


## Kendala
1. GNS Corrupt mendadak


