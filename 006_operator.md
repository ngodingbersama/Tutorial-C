---
title: Operator
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 6
---

# Operator

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Operator merupakan simbol yang digunakan untuk melakukan operasi matematika atau logika.

## Operator aritmatika
---
Misalkan x = 50 dan y = 10.

| Operator | Deskripsi | Contoh |
|---|---|---|
| \+ | penjumlahan | x + y = 60 |
| − | pengurangan | x - y = 40 |
| \* | perkalian | x * y = 500 |
| / | pembagian | x / y = 5 |
| % | modulus (sisa dari pembagian) | x % y = 0 |
| ++ | penjumlahan dengan nilai satu | x++ = 51 |
| -- | pengurangan dengan nilai satu | x-- = 49 |

## Operator relasi (hubungan)
---
dengan menggunakan nilai x dan y yang sama, maka:

| Operator | Deskripsi | Contoh (x operator y) |
|---|---|---|
| == | cek kesamaan dari 2 variabel | False |
| != | cek ketidaksamaan dari 2 variabel | True |
| > | cek lebih besar dari | True |
| < | cek lebih kecil dari | False |
| >= | cek lebih besar dari atau sama dengan | True |
| <= | cek lebih kecil dari atau sama dengan | False |

## Operator logika
---
Telah diketahui sebelumnya nilai True = 1 dan nilai False = 0 untuk boolean. Maka jika x = True dan y = False, maka:

| Operator | Deskripsi | Contoh |
|---|---|---|
| && | operator "dan" (AND), yang mana jika keduanya True maka True, selain itu False | (x && y) adalah False |
| \|\| | operator "atau" (OR), yang mana jika salah satunya True maka True, selain itu False | (x \|\| y) adalah True |
| ! | operator "bukan" (NOT), yang mana merubah nilai True menjadi False, begitupun sebaliknya | !(x && y) adalah True |

## Operator bitwise
---
Operator yang beroperasi pada setiap bit dari sebuah nilai.

| Operator | Deskripsi |
|---|---|
| & | operasi bit dari "dan" (AND) |
| \| | operasi bit dari "atau" (OR) |
| ^ | operasi bit dari XOR, yang sama dengan OR kecuali jika keduanya 0 atau 1 maka False |
| ~ | operasi bit dari NOT |
| << | operasi yang menggeser nilai bit ke kiri |
| >> | operasi yang menggeser nilai bit ke kanan |

## Operator penugasan (assigment)
---
Langsung saja ke tabel agar lebih paham

| Operator | Contoh |
|---|---|
| = | c = a + b |
| += | c += 1 sama dengan c = c + 1 |
| -= | c -= a sama dengan c = c - a |
| *= | x *= y sama dengan x = x * y |
| /= | x /= y sama dengan x = x / y |
| %= | a %= b sama dengan a = a % b |
| <<= | a <<= 1 sama dengan a = a << 1 |
| >>= | b >>= 2 sama dengan b = b >> 2 |
| &= | x &= y sama dengan x = x & y |
| ^= | x ^= y sama dengan x = x ^ y |
| \|= | x \|= y sama dengan x = x \| y |

## Operator lainnya
---
Selain yang telah disebutkan sebelumnya. Ada beberapa operator yang penting untuk diketahui. Diantaranya:

| Operator | Deskripsi | Contoh |
|---|---|---|
| sizeof() | mengembalikan ukuran dari variabel | jika x sama dengan integer, maka sizeof(x) = 4 (ukuran integer) |
| & | mengembalikan alamat dari variabel | &x mengeluarkan alamat dari x |
| * | pointer dari variabel | *a adalah pointer untuk variabel a |
| ?: | operator kondisi | jika kondisi benar ? maka bernilai A : selain itu B |

