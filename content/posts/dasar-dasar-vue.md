---
title: Mencoba Svelte JS
date: 2019-01-07
published: true
tags: ['Svelte', 'Javascript']
series: false
cover_image: ./images/mencoba-sveltejs-svelte.png
canonical_url: false
description: "Belajar dasar dasar Svelte JS"
---
# Mencoba Svelte JS

beberapa waktu yang lalu, saya membaca sebuah artikel yang ditulis oleh salah satu developer di tokopedia, disana beliau menceritakan bagaimana mereka mengatasi masalah performa web mereka. yang menarik adalah apa yang mereka gunakan untuk meningkatkan performa website tersebut yaitu Svelte JS. Diartikel ini saya akan menjelaskan sedikit tentang dasar Svelte JS

## Sekilas Tentang Svelte JS
> Svelte is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app. https://svelte.dev/

Jika kita membaca dari penjelasan di official websitenya, Svelte JS adalah pendekatan baru dalam membangun user interface. Sederhananya Svelte JS bekerja mirip dengan Framework UI seperti React & Vue yang mengupdate DOM setiap kali ada perubahan pada data/state, hanya saja program Svelte lebih fleksibel dalam penulisan kodenya dan program Svelte JS di compile menjadi vanilla js sehingga lebih cepat.

## Dasar Dasar Svelte JS
untuk instalasi bisa dilihat di official repo
Penulisan kode pada Svelte JS sangat sederhana seperti kode berikut

````
<script>
 let name = ‘world’;
</script>
<h1>Hello {name}!</h1>
````

kode diatas akan menghasilkan halaman web dengan tampilan Hello World . Svelte js mengcompile value dari variabel `name` sehingga dapat ditampilkan dengan mudah di elemen HTML. Svelte JS juga menyingkat penulisan kode dengan baik dibandingkan cara tradisional seperti kode berikut

````
Hello <span id=”text”></span>
<script>
let word = “World”
document.getElementById(‘text’).innerHTML = word
</script>
````

Penulisan kode di Svelte JS sedikit berbeda dengan cara tradisional seperti penulisan event & penulisan logika di html. berikut adalah contoh penulisan kode event


````
// PENULISAN EVENT
<script>
function log(text='logged'){
 console.log(text)
}
</script>
// Penulisan Event menggunakan titik dua : , dengan format on:event
<button on:click="{log}"></button>
/* Pemanggilan Fungsi dengan parameter 
ditulis sedikit berbeda dengan membuka fungsi baru
*/  
<button on:click="{()=>{ log('Log With Param') }}"></button>
berikut adalah contoh penulisan logika di html
<script>
let listOfNum = [1,2,3,4,5]
</script>
// Melakukan perulangan di html
{#each listOfNum as num}
 <span> {num} </span>
{/each}
````

sedikit catatan, Svelte JS melakukan update dom dengan mengecek apakah terdapat assignment, jadi kode seperti push dll tidak akan mengubah tampilan page. kode tersebut bisa diakali seperti kode dibawah
````<script>
let listOfNum = [1,2,3,4,5]
listOfNum.push(6) // Tidak reaktiv, sehingga dom tidak diupdate
// Solusi,mengganti dengan assignment
listOfNum = [...listOfNum, 6]
</script>
````
Mudah kan ? :D

Banyak contoh2 yang lain yang bisa dilihat dilink berikut https://svelte.dev/examples

Berikut adalah contoh aplikasi sederhana yang saya coba buat. bisa dibuka dilink berikut 

Link Github : [cart-on-svelte](https://github.com/naufalafif/cart-on-svelte)

## Demikian artikel ini, semoga bermanfaat…

