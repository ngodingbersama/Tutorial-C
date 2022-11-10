---
title: Dasar-dasar sintaks di bahasa C
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 3
---

# Dasar-dasar sintaks di bahasa C
---
Beberapa hal yang perlu diperhatikan saat menulis kode di bahasa C ialah:
1. Setiap kalimat pada bahasa C selalu diakhiri dengan tanda semi kolon (`;`), kecuali saat menjabarkan fungsi, `#include`, dan makro. Contohnya ada di program Hello World! dimana setiap baris diakhiri dengan tanda `;`, kecuali pada `#include <stdio.h>` dan akhir dari fungsi `int main(){ ... }`.
2. Setiap nama pada variabel, fungsi, dan lainnya didahului oleh alfabet a->z atau A->Z dan boleh ditambahkan angka 0-9, atau garis bawah (`_`) dan tidak boleh menggunakan `@`, `%`, dan `$`. Contoh: `buah buah_mangga buah_1 buah_mangga_1 buahMangga buah1a10`.
3. kata-kata yang sudah ada di C sebagai kata kunci, misal `int`, `if`, `else`, dan lainnya, tidak boleh digunakan sebagai nama untuk variabel atau lainnya.