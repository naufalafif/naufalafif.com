---
title: Membuat Instance Google Compute Engine
date: 2020-11-22
published: true
tags: ['google cloud platrofm', 'google compute engine']
series: false
cover_image: ./images/membuat-instance-google-compute-engine.png
canonical_url: false
description: "Mengenal Google Compute Engine & Cara Membuat Instance Compute Engine"
---

# Membuat Instance Google Compute Engine

Compute Engine adalah salah satu layanan yang disediakan oleh Google Cloud.  Compute Engine memungkinkan user untuk membuat virtual machine dengan berbagai jenis sistem operasi seperti Linux (Debian, Ubuntu, Suse, Red Hat, CoreOS) dan Windows Server di Infrastuktur Google.  User bisa menjalankan hingga ribuan CPU & Memory untuk menjamin performa sistem. 


## Memahami Region & Zona

Sebuah instance Compute Engine dapat berjalan diberbagai lokasi didunia. Pada Infrastuktur Google, lokasi - lokasi tersebut dibagi menjadi region & zona. Region adalah lokasi geografi dimana instance Compute Engine berjalan. Setiap region dapat memiliki lebih satu atau lebih zona. Sebagai contoh, di region `asia-southeast2` (jakarta) terdapat 3 zona yaitu `asia-southeast2-a`, `asia-southeast2-b` dan `asia-southeast2-c`.

<img src='https://cdn.qwiklabs.com/BErmNT8ZIzd5yqxO0lEJj8lAlKT3jKC%2BtI%2Byj3OSKDA%3D' style="margin: auto;max-width: fit-content;">


Memahami Region & Zona sangatlah penting, karena beberapa resource diharuskan berada di zona yang sama ataupun region yang sama untuk bisa digunakan. Sebagai contoh, Instance Compute Engine hanya bisa menggunakan Persistant Disk yang berada di zona yang sama. Sama halnya ketika ingin menyematkan static IP ke sebuah instance, instance tersebut harus berada di region yang sama dengan static IP



## Membuat Instance Compute Engine

Terdapat beberapa cara yang dapat dilakukan untuk membuat instance Compute Engine yaitu menggunakan cloud console & google cloud sdk


## Cloud Console

pada bagian ini kita akan membuat instance Compute Engine melalui web google cloud atau cloud console


1. Buka website cloud console https://console.cloud.google.com/home/dashboard
2. Pada menu disamping / **navigation menu**, klik **Compute Engine** - **VM Instances**

proses ini bisa membutuhkan waktu beberapa menit untuk selesai saat pertama kali

3. Untuk membuat instance baru klik **Create**
4. Terdapat banyak parameter yang harus diisi. untuk memudahkan, silahkan gunakan configurasi dibawah


<img src='https://miro.medium.com/max/700/1*zYpX3vuWWuxDOIIsnGB38A.png' style="margin: auto;max-width: fit-content;">
<br>

5. Klik **Create**

proses ini akan membutuhkan waktu beberapa menit selesai. jika telah selesai, instance yang sudah dibuat akan tampil di halaman **VM Instances**

![daftar-instance.png](https://paper-attachments.dropbox.com/s_46070C4CFA776435DED056AA2BDD61B32630AD09211602FD03DC99B6E7E3DCC8_1606022096824_screenshot-console.cloud.google.com-2020.11.22-12_14_32.png)

6. Untuk masuk kedalam instance yang sudah dibuat. pilih instance pada tabel daftar instance dan klik **SSH**

halaman web baru akan terbuka dengan interactive terminal yang sudah terhubung dengan instances


## Google Cloud SDK

Selain melalui web cloud console, instance Compute Engine juga bisa di buat menggunakan command terminal menggunakan Google Cloud SDK. 
Google Cloud SDK bisa digunakan melalui 2 cara yaitu dengan menginstall Cloud SDK di sistem operasi atau menggunakan interactive terminal bawaan google yaitu Google Cloud Shell

pada artikel ini kita akan menggunakan Google Cloud Shell


1. Buka website cloud console https://console.cloud.google.com/home/dashboard
2. Pada Header / Navigation Bar, klik **Activate Cloud Shell**

posisi tombol cloud shell terdapat pada header seperti pada gambar dibawah

![google_cloud_shell.png](https://paper-attachments.dropbox.com/s_46070C4CFA776435DED056AA2BDD61B32630AD09211602FD03DC99B6E7E3DCC8_1606021390735_screenshot-console.cloud.google.com-2020.11.22-12_01_10.png)


proses ini akan membuka terminal dihalaman web yang sedang terbuka yang nantinya akan kita gunakan untuk mengeksekusi perintah Google Cloud SDK

3. Jalankan perintah berikut di terminal Cloud Shell 


    gcloud compute instances create belajar-compute-engine --machine-type  e2-medium --zone asia-southeast2-b

Ketika selesai, maka akan tampil pesan seperti dibawah ini pada cloud shell

![gcloud_response.png](https://paper-attachments.dropbox.com/s_46070C4CFA776435DED056AA2BDD61B32630AD09211602FD03DC99B6E7E3DCC8_1606022011826_Screenshot+from+2020-11-22+12-13-18.png)


Instance Compute Engine berhasil dibuat


## **Terima kasih, semoga bermanfaat.**


