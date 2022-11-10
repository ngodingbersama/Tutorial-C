---
title: Penjelasan kode C Hello World
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 2
---

# Penjelasan kode C di Hello World

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Tentu sudah tidak asing lagi bahwa setiap bahasa pemrograman punya cara tersendiri dalam menuliskan perintah-perintah dan sintaksnya di editor, begitupun dengan bahasa C. Mungkin bisa ditelisik kembali program sebelumnya yaitu:

```c++
#include <stdio.h>

int main() {
	printf("hello world!\n");
	return 0;
}
```

output:
```bash
hello world!
```

[Live Demo](https://ide.geeksforgeeks.org/7RLvziw1p1){: .btn .fs-5 .mb-4 .mb-md-0 }

---
Ada beberapa komponen penting yang bisa dibagi dari kode tersebut. Hal tersebut ialah:

1. `#include <stdio.h>`: ini adalah tulisan yang **tidak harus ada** atau opsional pada saat menulis program C. `#include` merupakan perintah *preprocessor* yang digunakan untuk mengatakan pada kompiler bahwa isi dari file `stdio.h` harus dimasukkan ke dalam file tersebut sebelum dikompilasi. Sehingga `#include` dilakukan jika ada fungsi atau komponen lain yang berada di file lain yang ingin digunakan di file utama. Adapun penjelasan mengenai file `.h` (header file) akan dibahas di tempat yang lain.
2. Selanjutnya ialah `int main(){ ... }`. Sintaks ini digunakan apabila file tersebut merupakan file yang akan menjadi program eksekusi utama (misal .exe pada Windows).
3. `printf(...)` adalah fungsi yang terdapat di file `stdio.h`. Hal inilah yang menjelaskan kebutuhan menggunakan `#include` pada saat ada sebuah fungsi yang ingin digunakan pada program tersebut.
4. `return 0` adalah nilai kembalian dari sebuah fungsi main yaitu 0. Nilai 0 ini biasanya digunakan sebagai tanda bahwa fungsi tersebut berhasil dijalankan, sedangkan kembalian bukan 0 (misal 1 atau -1) menandakan bahwa fungsi tersebut tidak berhasil dijalankan. Hal ini penting mengingat tidak ada aturan khusus dan bahasa C dalam menghadapi error atau kesalahan pada sebuah fungsi. Sebagai informasi, nilai kembalian (return) bergantung kepada tipe data dari sebuah fungsi tersebut. Untuk fungsi `main()`, tipe datanya berupa `int` atau *integer* (bilangan bulat) sehingga kembaliannya haruslah bilangan bulat juga.

## Komentar pada bahasa C
---
Penambahan komentar pada bahasa C tidak akan mengganggu proses program tersebut. Hal ini karena komentar tidak akan dibaca pada saat kompilasi. Komentar sangat penting jika digunakan untuk menjabarkan sesuatu atau memperjelas dari sebuah variabel yang dibuat.

Komentar dalam bahasa C dapat menggunakan `/* ... */` untuk banyak baris atau `// ...` untuk satu baris saja. Namun perlu diingat bahwa saat menulis program, konsistensi dari cara penulisan komentar perlu diperhatikan agar program dapat mudah dibaca. 

<div class="custom-tips" markdown="1">
**Tips**

Bentuk penulisan komentar pada C maupun C++ dapat mengikuti gaya dari [Doxygen](https://www.doxygen.nl/manual/docblocks.html) untuk konsistensi. Hal ini juga akan membantu dalam mempermudah dokumentasi C atau C++ kedepannya.
</div>

## Kompilasi sederhana di bahasa C
---
Program Hello World! tersebut dapat disimpan dalam file `helloworld.c`. Setelah itu, program dikompilasi dengan menggunakan perintah di terminal:

```bash
gcc helloworld.c -o helloworld.out
```

Perintah tersebut menghasilkan program eksekusi `helloworld.out`. Di tutorial-tutorial, ekstensi `*.out` sering dipakai dalam program sederhana dan ekstensi tersebut dapat diubah ke ekstensi yang lebih familiar seperti `*.exe` untuk program yang ada di sistem operasi Windows. Di terminal, program tersebut dapat dijalankan melalui program eksekusi tersebut.

```bash
./helloworld.out
```