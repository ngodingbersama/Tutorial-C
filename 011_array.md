---
title: Array
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 11
---

# Array

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Array merupakan rangkaian data yang mempunyai tipe-data yang sama. Daripada mendefinisikan variabel berurutan secara terpisah, misalkan var1, var2, var3, ..., varN, variabel-variabel tersebut dapat dipadukan dalam satu array sehingga setiap nilainya dapat dipanggil berdasarkan urutannya (dimulai dari 0), misalkan var\[0\], var\[1\], var\[2\], ..., var\[N-1\].

array dapat dideklarasikan sebagai berikut:

```c++
tipe-data nama-array[ukuran-array];
```

contoh:

```c++
// membuat array nilai dengan ukuran 10
double nilai[10];
```

---
Array juga dapat sekaligus diinisialisasikan nilainya dengan beberapa contoh di bawah ini:

```c++
// inisialisasi array
double nilai[5] = {1.0, 5.0, 2.0, 3.0, 4.0};
```

atau bisa dilakukan tanpa memasukkan ukurannya (hanya dalam proses inisialisasi saja);

```c++
// inisialisasi array
double nilai[] = {1.0, 5.0, 2.0, 3.0, 4.0};
```

mengakses atau mengubah nilai pada indeks tertentu dalam sebuah array dapat dilakukan dengan cara memasukkan indexnya ke dalam kurung tegak setelah array dideklarasi atau diinisialisasi.

```c++
nilai[0] = 7.0
nilai[4] = 2.5
// ini sama dengan nilai[] = {7.0, 5.0, 2.0, 3.0, 2.5}

// akses nilai dari array
double x;
x = nilai[1] //-> sama dengan x = 5.0;
```

