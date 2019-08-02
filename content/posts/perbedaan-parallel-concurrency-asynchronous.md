---
title: Perbedaan Parallel, Concurrency & Asynchronous
date: 2019-08-02
published: true
tags: ['execution', 'hardware', 'performance', 'Javascript']
series: false
cover_image: ./images/concurrency-parallel-asynchronous.jpg
canonical_url: false
description: "Penjelasan sederhana perbedaan Parallel, Concurrency & Asynchronous"
---
# Sekilas Cerita

Kali ini saya akan menjelaskan sedikit tentang hasil dari kebingungan saya beberapa hari yang lalu. 
beberapa waktu yang lalu, saya tertarik untuk belajar bahasa pemrograman **Golang**. materi demi materi saya pelajari sampai akhirnya saya sampai ke topik **go routine** & **channel**. awalnya terdengar sederhana sampai saya merasa ada yang ganjal, yaitu pengertian **concurrent**. ya, concurrent. untuk seorang programmer yang lumayan sering berkutat dengan javascript, konsep concurrent (*yangsayapahami) terdengar sangat mirip dengan asynchonous. beberapa hari pun berlalu, & akhirnya saya paham perbedaannya. thanks untuk perjelasan singkat dari salah satu jawaban diquora. 

so, mari kita bahas satu per satu

## Parallel
> Parallel computing is a type of computation in which many calculations or the execution of processes are carried out **simultaneously**. Wikipedia

Parallel adalah eksekusi beberapa/banyak tugas yang dilakukan secara bersamaan. Ibaratkan didunia nyata, parallel itu ibarat seorang pria yang sedang berkendara sambil nelpon. pria tersebut melakukan 2 tugas sekaligus pada waktu bersamaan, yaitu naik motor & menelpon.

<img src="https://i.ibb.co/NjGPYMY/talking-while-driving.jpg" alt="talking while driving" title="talking while driving" style="border-radius:10px;display:block;margin:auto;width:60%;margin-bottom:10px;" />

Perlu diketahui juga, parallel tidak harus dilakukan oleh satu orang, bisa lebih. contoh, 2 orang sedang mencuci baju diwaktu yang sama. kasus itu juga termasuk parallel. jika dalam komputasi, kedua orang tersebut adalah core/thread. tetapi parallel tidak bisa dilakukan oleh single core/thread.

## Concurrency
> Concurrency means multiple computations are happening **at the same time**. MIT Edu

Concurrency adalah beberapa komputasi yang terjadi pada waktu yang sama. jika kita membaca sekilas tanpa memperhatikan setiap kata, mungkin akan terdengar sama dengan pengertian **parallel**. letak perbedaannya adalah pada kata "at the same time". pada waktu yang sama bukan berarti dilakukan secara sepenuhnya bersamaan. jika diibaratkan, concurrent ibarat temen kita yang nyanyi sambil makan. temen kita ngelakuin 2 hal pada waktu yang sama, tetapi bergantian. karena 2 hal tersebut tidak bisa dilakukan bersamaan.

<img src="https://i.ibb.co/SQdS2Tr/eating-jackson.gif" alt="talking while driving" title="talking while driving" style="border-radius:10px;display:block;margin:auto;width:60%;margin-bottom:10px;" />

sedangkan parallel diibaratkan orang yang berkendara sambil nelpon. 2 hal tersebut bisa dilakukan secara bersamaan.

## Asynchronous
> Asynchrony, in computer programming, refers to the occurrence of events independent of the main program flow and ways to deal with such events. Wikipedia

Asynchrony dalam pemrograman komputer, mengacu pada terjadinya peristiwa yang tidak tergantung pada alur program utama dan cara untuk menangani peristiwa tersebut. terdengar agak sulit ? awalnya saya juga  gagal paham. 

Jika dibuatkan ilustratsi, maka asynchronous akan mirip dengan kasus pada gambar dibawah 

<img src="https://i.ibb.co/vcXV4t1/wait-laundry.png" alt="talking while driving" title="talking while driving" style="border-radius:10px;display:block;margin:auto;width:60%;margin-bottom:10px;" />

pada gambar diatas, bapak itu sedang melakukan 2 hal yaitu bermain HP dan menunggu cucian. dalam kasus ini, bapak tersebut mengalihkan aktivitasnya dari mencuci ke aktivitas lain yang itu bermain HP. ibarat program, ini seperti menlanjutkan eksekusi kode ke line berikutnya padahal proses yang sekarang belum selesai. aktifitas inilah yang dimaksud asychronous. perlu diketahui, asynchronous berbeda dengan concurrency. karena, asynchronous melakukan pengalihan aktivitas/tugas dikarenakan kode yang sedang dieksekusi dapat berjalan dengan sendirinya. contoh : ketika kita melakukan request get pada sebuah website, sebenarnya kita tidak melakukan aktivitas apapun selain menunggu response. asynchronous berguna untuk mengefisiensikan kode kita agar melakukan aktifitas lain, tanpa harus menunggu response.


beberapa penjelasan sederhana lainnya yang mungkin bisa membantu

https://medium.com/swift-india/concurrency-parallelism-threads-processes-async-and-sync-related-39fd951bc61d

https://www.quora.com/What-are-the-differences-between-parallel-concurrent-and-asynchronous-programming


## Demikian artikel ini, semoga bermanfaat…

