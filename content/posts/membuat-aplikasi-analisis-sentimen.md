---
title: Membuat Aplikasis Analisis Sentiment Part 1
date: 2019-10-02
published: true
tags: ['python','sentiment analisys','classification']
series: false
cover_image: ./images/membuat-aplikasi-analisis-sentimen.png
canonical_url: false
description: "Cara membuat aplikasis analisis sentimen sederhana menggunakan bahasa pemrograman Python"

---

# Membuat Aplikasi Analisis Sentimen #1
Pernah melihat review aplikasi di play store ? jumlah review untuk satu aplikasi terkadang bisa mencapai jutaan, tergantung jumlah penggunanya. mungkin kita pernah penasaran bagaimana pengembang aplikasi tersebut menganalisis review dari semua penggunanya. tentu saja itu tidak dilakukan secara manual, pengembang aplikasi akan menggunakan sebuah cara yang lebih efektif & efisien. salah satunya bisa dengan menggunakan aplikasi analisis sentimen. 

#### Apa Itu Aplikasi Analisis Sentimen ?
Secara sederhananya aplikasi analisis sentimen adalah program yang menerima input data berupa text dan memproses text tersebut dan menentukan apakah text tersebut bersentiment negatif, positif ataupun netral

#### Bagaimana Cara Kerja Aplikasi Analisis Sentimen ?
<g-image src="https://raw.githubusercontent.com/naufalafif/naufal.netlify.com/master/content/posts/images/how-sentiment-app-work.png"/>

Secara sederhana aplikasi Analisis Sentimen bekerja seperti gambar diatas dengan memproses dataset yang kita berikan lalu diproses hingga data tersebut layak untuk dijadikan sebagai data latih, untuk selanjutnya digunakan untuk melatih model yang digunakan. 

#### Bagaimana Tahapan Pembuatan Aplikasi Analisis Sentimen ?
Pada artikel ini kita melakukan 5 tahapan untuk membuat aplikasi hingga siap deploy. tetapi jumlah tersebut bisa berbeda2 bergantung pada pembuat aplikasi maupun metode2 yang digunakan.

Secara sederhana tahapan pembuatan aplikasi adalah seperti gambar berikut

<g-image src="https://raw.githubusercontent.com/naufalafif/naufal.netlify.com/master/content/posts/images/sentiment-analisys-process.png"/>

**- Dataset** adalah kumpulan text2 yang mengandung sentimen. Contoh : data review pelanggan, data quisioner dll.

**- Preprocessing** adalah proses pembersihan text dari kata imbuhan, tanda baca dll untuk menghasilkan akar2 kata dari masing2 text. Contoh : `Andi Menyukai Baju Putih` diubah menjadi `andi suka baju putih`

Proses ini dilakukan agar program dapat menentukan sentimen berdasarkan akar kata, bukan kata mentah. Karena variatifnya penggunaan kata yg mungkin digunakan

**- Weighting** adalah proses pembobotan dari setiap kata berdasarkan kemunculan kata tersebut. Proses ini dilakukan agar program tidak memberikan nilai tinggi pada kata2 yang sebenarnya kurang relevan untuk dijadikan sebagai acuan sentimen seperti kata `ini`, `yang` dan lain lain yang pada umumnya sering kali muncul pada setiap kaliman atau text.
 
 **- Training & Testing** adalah proses memilih, melatih & menguji model yang kita gunakan. Pada proses ini, data yang telah melalui tahapan2 sebelumnya akan digunakan sebagai data latih.
 
 **- Build API & Frontend** adalah tahapan deploy model yang telah dilatih ke aplikasi web.
 
 
 Untuk part #2 kita akan mulai menuliskan programnya. Ditunggu gaes

