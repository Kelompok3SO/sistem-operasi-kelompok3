# Laporan Tugas Kelompok: Instalasi Debian 13 Headless Web Server
Mata Kuliah: Sistem Operasi (SI-25)
Program Studi: Sistem Informasi, Universitas Galuh

## 👥 Anggota Kelompok 3 SI-2025B
1. [Zaidan Zidnaffan] - [7020250028]
2. [Faisal Hikayat Padilah] - [7020250026]
3. [Fasha Alvian] - [7020250031]
4. [Aditya Hermawan] - [7020250040]

## 🎯 Spesifikasi Lingkungan Server
* **Hypervisor:** VMware Workstation Pro
* **Sistem Operasi:** Debian 13 (Bookworm) - Headless (CLI / Tanpa GUI)
* **IP Address VM (Guest):** `192.168.150.140`
* **Port Forwarding:** Host Port `8080` -> VM Port `80` (HTTP Web Server) 

## 🛠️ Langkah-Langkah & Dokumentasi Praktikum

### 1. Instalasi Debian 13 Headless
* Melakukan instalasi sistem operasi Debian 13 mode teks dengan partisi guided (single partition).
* Mengatur hostname: `server-SI2025[A/B]` dan memasang bootloader GRUB ke `/dev/sda`.
* Memastikan hanya mencentang **SSH Server** dan **standard system utilities** pada tahap Software Selection.
* *[Tambahkan screenshot proses menu software selection di bawah ini]*
  ![Software Selection](images/01-software-selection.png)

* *[Tambahkan screenshot tampilan login terminal Debian pertama kali di bawah ini]*
  ![Login Terminal](images/02-debian-login.png)

### 2. Konfigurasi User Sudo & Update Repositori
* Masuk sebagai user `root`, menginstal paket `sudo`, dan menambahkan user biasa ke grup sudo.
* Menjalankan pembaruan paket sistem dengan perintah:
  ```bash
  apt update && apt upgrade -y
  apt install sudo -y
  usermod -aG sudo [nama-user-kelompok]
  reboot
  ```
* *[Tambahkan screenshot hasil uji coba perintah sudo oleh user biasa di bawah ini]*
  ![Konfigurasi Sudo](images/02-sudo-config.png) 

### 3. Instalasi Web Server Nginx & Tools Dasar
* Menginstal `net-tools`, `curl`, `git`, dan `nginx` menggunakan command line.
* Menjalankan dan mengaktifkan service Nginx agar berjalan otomatis saat booting.
  ```bash
  sudo apt install net-tools curl git nginx -y
  sudo systemctl start nginx
  sudo systemctl enable nginx
  ```
* *[Tambahkan screenshot status active running dari Nginx]*
  ![Nginx Service Status](images/03-nginx-status.png)

### 4. Pembuatan Halaman Web Profil Kelompok
* Mengubah dokumen default Nginx pada `/var/www/html/index.html` dengan HTML profil anggota kelompok Anda.
* Melakukan restart web server untuk memuat perubahan.
  ```bash
  sudo systemctl restart nginx
  ```
* *[Tambahkan screenshot pengeditan index.html menggunakan nano editor]*
  ![Edit index.html](images/04-edit-html.png)

### 5. Konfigurasi Port Forwarding VMware & Pengujian Host
* Melakukan pemetaan port 8080 pada Windows Host ke port 80 Debian Guest VM lewat menu Virtual Network Editor.
* Menguji akses web server Debian melalui browser di sistem operasi host.
* *[Tambahkan screenshot pengaturan NAT Settings VMware]*
  ![NAT Settings VMware](images/05-nat-settings.png)
  
* *[Tambahkan screenshot halaman profil kelompok yang berhasil diakses dari browser host di http://localhost:8080]*
  ![Akses Browser Host](images/06-browser-host.png)

## 🎥 Link Video Demo
[Tonton Video Demo Pengerjaan Tugas Kelompok di YouTube / Google Drive](https://youtube.com/...)

## 📝 Kesimpulan
Tuliskan simpulan dari praktikum yang telah dilakukan serta poin-poin penting yang didapatkan selama melakukan setup server Linux headless.
