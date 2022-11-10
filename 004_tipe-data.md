---
title: Beberapa tipe data di bahasa C
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 4
---

# Beberapa tipe data di bahasa C

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Diambil dari referensi [ini](https://www.tutorialspoint.com/cprogramming/c_data_types.htm), tipe-tipe data pada bahasa C dapat diklasifikasikan dalam 4 kategori:
1. **Tipe-tipe dasar**: tipe ini merupakan tipe aritmatika yang mana terbagi lagi menjadi dua, yaitu **integer** dan **floating-point**.
2. **tipe enum**: tipe ini juga merupakan tipe aritmatika integer namun diwakilkan oleh nama-nama. Yang paling familiar dari tipe enum ini ada boolean, yaitu True untuk 1 dan False untuk 0.
3. **tipe void**: tipe ini menyatakan bahwa variabel tersebut tidak memiliki nilai yang spesifik.
4. **tipe turunan**: tipe ini merupakan tipe yang diturunkan dari tipe-tipe sebelumnya, seperti pointer, array, struct, union, dan fungsi.

## Tipe integer
---
Beberapa tipe-tipe integer yang tersedia pada bahasa C adalah sebagai berikut:

| **Jenis tipe integer** | **Ukuran penyimpanan** | **Batasan nilai** |
|---|---|---|
| char | 1 byte | -128 s.d. 127 atau 0 s.d. 255 |
| unsigned char | 1 byte | 0 s.d. 255 |
| signed char | 1 byte | -128 s.d. 127 |
| int | 2 atau 4 bytes | -32,768 s.d. 32,767 atau -2,147,483,648 s.d. 2,147,483,647 |
| unsigned int | 2 atau 4 bytes | 0 s.d. 65,535 atau 0 s.d. 4,294,967,295 |
| short | 2 bytes | -32,768 s.d. 32,767 |
| unsigned short | 2 bytes | 0 s.d. 65,535 |
| long | 8 bytes (4 bytes untuk sistem operasi 23 bit) | -9223372036854775808 s.d. 9223372036854775807 |
| unsigned long | 8 bytes | 0 s.d. 18446744073709551615 |

Ukuran pasti dari setiap variabel pada komputer tertentu dapat dilihat dengan menggunakan operator `sizeof`.

## Tipe *floating-point*
---
tipe *floating-point* digunakan pada bilangan desimal. Perbedaan dari setiap tipe ini ialah presisi (akurasi nilai) dan sejauh mana angka belakang desimal yang bisa disimpan di memori.

| **Jenis** | **Ukuran penyimpanan** | **Batasan nilai** | **Presisi** |
|---|---|---|---|
| float | 4 byte | 1.2E-38 s.d. 3.4E+38 | 6 angka desimal |
| double | 8 byte | 2.3E-308 s.d. 1.7E+308 | 15 angka desimal |
| long double | 10 byte | 3.4E-4932 s.d. 1.1E+4932 | 19 angka desimal |

## Tipe void
---
Tipe ini sangat berguna di beberapa situasi. Ada 3 kemungkinan tipe void ini digunakan dalam bahasa C:
1. **sebagai tipe kembalian fungsi**: ini merupakan tipe fungsi yang tidak memiliki nilai kembalian apapun.
2. **sebagai argumen pada fungsi**: ini berarti fungsi tersebut tidak menerima parameter apapun.
3. **sebagai tipe pointer**: pointer yang memiliki tipe void dapat diperankan (*casting*) sebagai tipe data yang lainnya. Contoh fungsi `void *malloc( ... )`.