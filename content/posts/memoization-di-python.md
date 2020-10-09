---
title: Memoization di Python
date: 2020-10-10
published: true
tags: ['python', 'optimization']
series: false
cover_image: ./images/speed-cars.jpg
canonical_url: false
description: "Apa itu memoization & implementasinya di bahasa pemrogaraman python"
---
# Memoization di Python
di artikel kali ini saya akan mengenalkan sedikit tentang apa itu memoization & bagimana implementasinya di bahasa pemrograman python


## Apa itu Memoization ?

memoization adalah teknik optimasi program dengan cara menyimpan hasil eksekusi function untuk digunakan untuk eksekusi - eksekusi selanjutnya. kita pasti sudah pernah mendengar istilah caching, sebagai contoh ketika menggunakan browser. membuka sebuah halaman situs untuk kali pertama, akan terasa lebih lama dibanding kali kedua dst. hal itu bisa terjadi dikarenakan ketika pertama kali memuat halaman, browser mengunduh data dari halaman website lalu menyimpannya di sebuah memory. ketika membuka halaman tersebut kedua kalinya, browser tidak lagi mengunduhnya dari halaman tersebut dari 0, melainkan mengambil beberapa bagian dari memory yang sebelumnya sudah tersimpan, yang tentunya jauh lebih cepat. 
nah, memoization adalah salah satu bentuk implementasi dari caching. hanya saja memoization berfokus pada caching terhadap function. 


## Bagaimana Memoization di Python ?

pertama kita buat program yang mensimulasikan proses yang berat.

<script src="https://gist.github.com/naufalafif/a1a365dd32034e51033df2dce54bf12f.js"></script>

eksekusi function diatas menghabiskan waktu 2 detik untuk selesai, dengan kata lain jika kita menjalankan function diatas sebanyak 100x maka akan menghabiskan waktu kurang lebih 200 detik. lama bukan

selanjutnya buat function memoize yang menerima function lain sebagai argument & mengembalikan function yang telah menggunakan caching


    def memoize(func):
        """ function ini menerima function lain sebagai argument & menyimpan hasil dari function tersebut"""
        
        memory = {} # variable yang menyimpan hasil dari eksekusi function
        def wrapper(*args, **kwargs):
            # menyimpan arguments sebagai key dari memory
            key = (args,tuple(kwargs))
    
            # jika pemanggilan function serupa ada dimemory maka return hasil dari memory
            if key in memory.keys():
                return memory[key]
    
            # memanggil function sebenarnya
            result = func(*args, **kwargs)
    
            # menyimpan hasil dari eksekusi function
            memory[key] = result 
            
            return result
        return wrapper

jalankan function fake_heavy_computation dengan memoize


    memoized_fake_heavy_computation = memoize(fake_heavy_computation)
    
    memoized_fake_heavy_computation(3) # selesai dalam 2 s
    memoized_fake_heavy_computation(3) # selesai dalam 4 ms
    memoized_fake_heavy_computation(4) # selesai dalam 2 s
    [memoized_fake_heavy_computation(3) for _ in range(10000)] # selesai dalam 600 ms

dari hasil eksekusi diatas, eksekusi pertama selesai dalam 2 detik, eksekusi kedua selesai dalam waktu 4 milidetik & eksekusi ke 3 dengan diulang sebanyak 10000x selesai dalam waktu 600 milidetik. dari hasil diatas kita bisa melihat perbedaan waktu eksekusi antara fake_heavy_computation dan memoized_fake_heavy_computation. kita coba jabarkan satu per satu


    memoized_fake_heavy_computation(3) # selesai dalam 2 s

eksekusi pertama membutuhkan waktu 2 detik, ini terjadi karena saat pertama kali mengeksekusi kode, memory atau cache masih kosong & tidak ada data yang bisa direturn dari memory.


    memoized_fake_heavy_computation(3) # selesai dalam 2 ms

eksekusi kedua membutuhkan waktu 4 milidetik, ini terjadi karena function memoized_fake_heavy_computation mereturn value yang sudah tersimpan dimemory dari hasil eksekusi pertama.


    [memoized_fake_heavy_computation(3) for _ in range(10000)] # selesai dalam 600 ms

eksekusi ketiga membutuhkan waktu 600 milidetik. meskipun diulang sebanyak 10000x, eksekusi bisa selesai kurang dari 2 detik


    memoized_fake_heavy_computation(4) # selesai dalam 2 s

eksekusi terakhir membutuhkan waktu 2 detik, pada eksekusi ini argument yang digunakan berbeda dari eksekusi sebelumnya. ketika membuka isi memory, function tidak menemukan data dengan argument yang sama, oleh karena itu function tersebut melakukan ulang proses heavy_computation yang membutuhkan waktu kurang lebih 2 detik. 



## Memoize Menggunakan functools.lru_cache

di penejelasan sebelumnya kita telah mengimplementasikan caching & memoize menggunakan wrapper function. selanjutnya kita akan melakukan hal yang sama menggunakan module bawaan python.

menerapkan caching pada function menggunakan module bawaan sangatlah mudah, cukup dengan memasang decorator pada function yang dituju


    import functools
    
    @functools.lru_cache
    def fake_heavy_computation(value):
        """ function ini mensimulasikan komputasi berat"""
        time.sleep(2) # menunggu 2 detik untuk lanjut ke statement berikutnya
        return value

sekarang function **fake_heavy_computation** akan memberikan hasil yang sama dengan **memoize(fake_heavy_computation)**. ****mudah kan


## Kapan Menerapkan Memoization ?

dari penjelasan & contoh diatas kita bisa melihat bagaimana memoizaton dapat mengoptimasi proses eksekusi function secara signifikan. tetapi memoization tidak selalu cocok diterapkan pada setiap function, hal itu tergantung apakah return dari function konsisten terhadap argumen yang diberikan. function yang memberikan hasil yang tidak konsisten tidak cocok untuk diterapkan memoization. sebagai contoh function berikut, ekspektasi dari function berikut adalah mereturn hasil perkalin argument number terhadap angka random.


    import random
    
    def multiply_by_random_number(number):
        """ function ini mengambalikan hasil number dikalikan angka random """
        return number * random.randint(1, 1000)
    
    multiply_by_random_number(2) # contoh, 925
    multiply_by_random_number(2) # contoh, 12
    multiply_by_random_number(2) # contoh, 564
    multiply_by_random_number(2) # contoh, 623

perhatikan function diatas, hasil dari eksekusi nya mengambalikan value yang semuanya berbeda meskipun diberikan argument yang sama. menerapkan memoization pada function tersebut akan membuat function tersebut mereturn hasil yang sama disetiap pemanggilan. hal itu tidak sesuai dengan ekspektasi dari function tersebut.

## Terima kasih, semoga bermanfaat.

