
<div align="center" class="tip" markdown="1" style>

![screenshot](images/Screenshot.png)

![wine version](https://img.shields.io/badge/wine-%E2%96%B25.22-red) ![Tested on arch](https://img.shields.io/badge/Tested%20on-Archlinux-brightgreen) ![GitHub stars](https://img.shields.io/github/stars/Gictorbit/photoshopCClinux) ![rep size](https://img.shields.io/github/repo-size/gictorbit/photoshopCClinux) ![bash](https://img.shields.io/badge/bash-5.0-yellowgreen)
</div>

# Photoshop CC v19 installer for Linux
Skrip bash ini membantu Anda menginstal Photoshop CC versi 19 di mesin Linux Anda menggunakan wine di belakang layar
dan mengatur beberapa komponen yang diperlukan untuk kinerja terbaik

## :rocket: Features
* mengunduh komponen yang diperlukan dan menginstalnya (`vcrun`, `atmlib`, `msxml`...)
* unduh penginstal `photoshop.exe`
* membuat perintah photoshop dan entri desktop
* mode gelap wine
* mendukung kartu grafis seperti (`intel`, `Nvidia`)
* menyimpan file yang diunduh di direktori cache Anda
* Gratis dan Anda tidak memerlukan kunci lisensi apa pun
* bekerja pada semua distribusi Linux

## :warning: Requirements
1- gunakan edisi 64bit dari distro Anda
2-pastikan paket-paket berikut sudah terinstal di distro Linux Anda
* `wine`
* `wine64`
* `winetricks`
* `md5sum`

Saya sendiri jujur masih butuh Wine karena tools pembuat backdoor seperti Veil-Evasion dll membutuhkan wine dan wine32 untuk membuat backdoor yang bisa dijalankan di Windows.
Pertama, jalankan perintah

    sudo apt-get install wine

Sampai disini wine sudah terinstall. Namun masih ada dependensi yang kurang yaitu wine32.

Nah cara install wine32 sebagai berikut:

    sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install wine32

Lalu tunggu sampai proses install selesai. Lama tidaknya proses instalasi tergantung dari koneksi kalian.

Untuk menjalankan wine cukup ketik command

    wine


Done. Mudah bukan.
Baiklah mungkin sekian tutorial kali ini semoga bermanfaat. Jika ada yang kurang paham silahkan ditanyakan.

jika belum diinstal, Anda dapat menginstalnya menggunakan manajer paket Anda misalnya di Arch Linux
```bash
sudo pacman -S wine winetricks
``` 
3- pastikan Anda memiliki penyimpanan yang cukup di partisi `/home` Anda sekitar `5 GiB`
> 1 GiB akan gratis setelah instalasi

Anda juga dapat menginstal photoshop di direktori yang berbeda

4- pastikan Anda memiliki koneksi internet dan lalu lintas sekitar 1,5 Gib untuk mengunduh photoshop dan komponennya

## :computer: Installation

skrip penginstal menggunakan drive virtual wine dan membuat `winprefix` baru untuk photoshop

pertama-tama, Anda perlu mengkloning repositori dengan perintah ini:
```bash
git clone https://github.com/Gictorbit/photoshopCClinux.git
cd photoshopCClinux
```
maka Anda dapat dengan mudah menjalankan skrip `setup.sh` untuk menginstal photoshop cc di distro Linux Anda

```bash
chmod +x setup.sh
./setup.sh
```

Anda dapat menggunakan `-d` untuk menentukan jalur instalasi, dan `-c` untuk direktori cache.
Misalnya:
```bash
./PhotoshopSetup.sh -d /mnt/myfiles/photoshop
```
or
```bash
./PhotoshopSetup.sh -d /mnt/myfiles/photoshop -c /mnt/cache
```
ketika tidak ada opsi yang diberikan, skrip penginstal akan menggunakan jalur default,
skrip uninstaller dan lainnya akan mendeteksi jalur khusus Anda sehingga tidak ada masalah,
Saya sarankan menggunakan opsi `-d` dan memiliki direktori cache default.
fitur ini sedang diuji, dan akan ditambahkan ke `setup.sh` nanti


<div align="center" class="tip" markdown="1" style>

![setup-screenshot](images/setup-screenshot.png)
</div>

during installation please pay attention to the script messages

> **NOTE :** make sure OS version in wine is on windows 7

installer script use `winetricks` to install necessary components

## :wine_glass: wineprefix Configuration
if you need to configure the wineprefix of photoshop you can use `winecfg.sh` script just run the command below
```bash
chmod +x winecfg.sh
./winecfg.sh
```
## :hammer: Tools

<details>
<summary>:sparkles: Liquify Tools</summary>
seperti yang Anda ketahui photoshop memiliki banyak alat yang berguna seperti `Liquify Tools`.</br>

jika Anda mendapatkan beberapa kesalahan saat bekerja dengan alat ini,
Mungkin karena kartu grafisnya.</br>

photoshop menggunakan `GPU` untuk memproses alat-alat ini jadi sebelum menggunakan alat-alat ini pastikan bahwa kartu grafis Anda `(Nvidia, AMD)` dikonfigurasi dengan benar di mesin Linux Anda.
</br>Solusi lainnya adalah Anda dapat mengkonfigurasi photoshop untuk menggunakan `CPU` Anda untuk pemrosesan gambar. untuk melakukannya, ikuti langkah-langkah di bawah ini:

* buka tab edit dan buka `preferences` atau `[ctrl+K]`
* lalu buka tab `kinerja`
* di bagian pengaturan prosesor grafis, hapus centang `Gunakan prosesor grafis`

![](https://user-images.githubusercontent.com/34630603/80861998-117b7a80-8c87-11ea-8f56-079f43dfafd9.png)
</details>

---
<details>
<summary>:camera: Adobe Camera Raw</summary>

software adobe lain yang berguna adalah `camera raw` jika Anda ingin bekerja dengannya selain photoshop Anda harus menginstalnya secara terpisah untuk melakukan ini, setelah instalasi photoshop jalankan skrip `cameraRawInstaller.sh` dengan perintah di bawah ini:
```bash
chmod +x cameraRawInstaller.sh
./cameraRawInstaller.sh
```
kemudian restart photoshop. Anda dapat membukanya dari
`Edit >> Preferences >> Camera Raw`

> **_NOTE1:_** ukuran file instalasi mentah kamera sekitar 400MB


> **_NOTE2:_** performa mentah kamera bergantung pada driver kartu grafis Anda dan konfigurasinya

</detail>

## :mata air panas: Copot pemasangan
untuk uninstall photoshop Anda bisa menggunakan script uninstaller dengan perintah di bawah ini
```bash
chmod +x uninstaller.sh
./uninstaller.sh
```


## :bookmark: License
![GitHub](https://img.shields.io/github/license/Gictorbit/photoshopCClinux?style=for-the-badge)

---
<a href="https://poshtiban.com">
<img src="images/poshtibancom.png" width="25%"> 
</a>
<a href="https://github.com/Gictorbit/illustratorCClinux">
<img src="https://github.com/Gictorbit/illustratorCClinux/raw/master/images/AiIcon.png" width="9%">
</a>
