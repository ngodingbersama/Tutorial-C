---
title: Variabel
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 5
---

# Variabel

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Variabel merupakan nama yang mewakili sebuah area penyimpanan sehingga area tersebut dapat dimanipulasi oleh program. Variabel harus memiliki tipe data tertentu sehingga komputer dapat menyesuaikan ukuran memori/penyimpanan yang sesuai serta dapat dipahami oleh manusia.

## Pendefinisian variabel di C
---
variabel didefinisikan setelah menentukan tipe datanya. Satu tipe data dapat mendefinisikan satu atau lebih variabel yangi dipisahkan dengan tanda koma (`,`). Secara konkritnya seperti ini:

```c++
// satu variabel
tipe nama_variable;
// lebih dari satu variabel
tipe nama_var_1, nama_var_2, nama_var_3;
```

contoh:

```c++
int jumlah;
char karakter;
int a, b, c;
double var1, var2;
float mangga, rambutan, total;
```

Selain ini variabel dapat ditentukan nilainya bersamaan dengan pendefinisian. Contoh:

```c++
int jumlah = 10;
double persentase = 5.54;
float mangga = 2000.0, rambutan = 578.45, total;
```

