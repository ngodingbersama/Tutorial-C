---
title: Perulangan
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 8
---

# Perulangan

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Jika sebuah pernyataan ingin dilakukan beberapa kali, bahasa C mempunyai fitur untuk melakukannya dengan perulangan (looping).

## Perulangan `while`
---
Pernyataan tetap berulang, jika kondisi tetap dalam keadaan benar (TRUE). Sintaks yang digunakan ialah:

```c++
while(kondisi) {
    /* bagian ini dijalankan jika kondisi bernilai benar atau TRUE */;
}
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 2;
	
	while (x < 10) {
	    printf("nilai x = %d lebih kecil dari 10\n", x);
	    x++;
	}
	
	return 0;
}
```

output:
```bash
nilai x = 2 lebih kecil dari 10
nilai x = 3 lebih kecil dari 10
nilai x = 4 lebih kecil dari 10
nilai x = 5 lebih kecil dari 10
nilai x = 6 lebih kecil dari 10
nilai x = 7 lebih kecil dari 10
nilai x = 8 lebih kecil dari 10
nilai x = 9 lebih kecil dari 10
```

[Live Demo](https://ide.geeksforgeeks.org/VkecwGFjKG){: .btn .fs-5 .mb-4 .mb-md-0 }

## Perulangan `for`
---
Perulangan `for` dilakukan jika terdapat spesifikasi dalam melakukan perulangan.

```c++
for(nilai-awal; kondisi; inkremen) {
    /* bagian ini dijalankan jika kondisi bernilai benar atau TRUE */;
}
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 2;
	
	for (int i = 0; i < 10; i++) {
	    printf("nilai i = %d, nilai x = %d\n", i, x);
	    x++;
	}
	
	return 0;
}
```

output:
```bash
nilai i = 0, nilai x = 2
nilai i = 1, nilai x = 3
nilai i = 2, nilai x = 4
nilai i = 3, nilai x = 5
nilai i = 4, nilai x = 6
nilai i = 5, nilai x = 7
nilai i = 6, nilai x = 8
nilai i = 7, nilai x = 9
nilai i = 8, nilai x = 10
nilai i = 9, nilai x = 11
```

[Live Demo](https://ide.geeksforgeeks.org/J64QWWkJWW){: .btn .fs-5 .mb-4 .mb-md-0 }

## Perulangan `do ... while ...`
---
Perulangan `do ... while ...` mirip seperti `while` namun kondisi ditempatkan di bagian bawah. Tujuannya agar program tersebut setidaknya dilakukan sekali sebelum pengecekan kondisi.

```c++
do {
    // pernyataan saat kondisi benar
} while (kondisi);
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 2;
	
	do {
	    printf("x = %d kurang dari 10\n", x);
	    x++;
	} while (x < 10);
	
	return 0;
}
```

output:
```bash
x = 2 kurang dari 10
x = 3 kurang dari 10
x = 4 kurang dari 10
x = 5 kurang dari 10
x = 6 kurang dari 10
x = 7 kurang dari 10
x = 8 kurang dari 10
x = 9 kurang dari 10
```

[Live Demo](https://ide.geeksforgeeks.org/lkbJeADeqA){: .btn .fs-5 .mb-4 .mb-md-0 }

## Perulangan bersarang
---
Semua konsep yang telah disebutkan sebelumnya dapat melakukan perulangan secara bersarang.