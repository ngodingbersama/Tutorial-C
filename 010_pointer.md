---
title: Pointer
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 10
---

# Pointer

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Pointer adalah fitur penting yang ada dalam bahasa C yang bertugas untuk menyalin alamat dari variabel lain atau dari kembalian sebuah fungsi. Fitur ini penting karena beberapa hal tidak bisa dilakukan tanpa menggunakan pointer atau menyimpan alamat memori tertentu. Pointer mudah untuk dipelajari dan bahasa C tidak akan dikuasai tanpa menguasai pointer.

Asterisk * digunakan untuk mendefinisikan bahwa variabel tersebut merupakan pointer. Penempatan `*` berada di setelah tipe data ditulis.

```c++
tipe-data *nama-variabel;
```

Adapun jika kita ingin mengetahui alamat dari variabel yang sudah ada, operator '&' dapat digunakan. `%p` digunakan sebagai tanda bahwa nilai yang akan dikeluarkan merupakan nilai alamat. Contoh:

```c++
#include <stdio.h>

int main() {
    
    int x = 5;
    
    // print alamat dari variabel x
    printf("alamat dari x adalah %p\n", &x);
    
	return 0;
}
```

output:

```bash
alamat dari x adalah 0x7fff9d9f6b04
```

[Live Demo](https://ide.geeksforgeeks.org/KfXcF78zyP){: .btn .fs-5 .mb-4 .mb-md-0 }

Alamat dari sebuah variabel bisa saja akan berbeda di masing-masing komputer ataupun saat program dijalankan kembali. Sehingga jika ingin menyimpan alamat memori pada sebuah variabel tertentu dapat menggunakan pointer.

```c++
#include <stdio.h>

int main() {
    // variabel x
    int x = 5;
    
    // mendefinisikan pointer
    int *p;
    
    // menyalin alamat x di pointer p
    p = &x;
    
    // print alamat dari variabel x
    printf("alamat dari x adalah %p\n", &x);
    
    // print alamat yang disimpan di p
    printf("nilai yang disimpan di p adalah %p\n", p);
    
	return 0;
}
```

output:

```bash
alamat dari x adalah 0x7fffde1122fc
nilai yang disimpan di p adalah 0x7fffde1122fc
```

[Live Demo](https://ide.geeksforgeeks.org/daiJXreTX4){: .btn .fs-5 .mb-4 .mb-md-0 }

<div class="custom-note" markdown="1">
**Note:**

Perlu diingat bahwa tipe data pointer dan tipe data variabel yang ingin disimpan alamatnya haruslah **sama**.
</div>

