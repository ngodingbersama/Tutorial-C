---
title: Fungsi
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 9
---

# Fungsi

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Fungsi adalah kumpulan atau sebuah grup pernyataan yang memiliki tugas tertentu. Dalam bahasa C, fungsi terbagi menjadi dua, yaitu deklarasi dan definisi. Fungsi deklarasi ialah sebuah pernyataan fungsi yang hanya menunjukkan bahwa terdapat sebuah fungsi di program tersebut sedangkan fungsi definisi menunjukkan fungsi secara utuh (termasuk semua pernyataan di dalam fungsi tersebut). Fungsi deklarasi biasanya digunakan pada file *header* (yang akan dibahas di tulisan-tulisan selanjutnya).

Fungsi definisi dapat dibuat berdasarkan susunan berikut ini:

```c++
tipe-kembalian nama-fungsi(daftar-parameter) {
	/* kumpulan pernyataan dari fungsi tersebut
}
```

Sedangkan fungsi deklarasi hanya menyatakan bentuk dari fungsi tersebut:

```c++
tipe-kembalian nama-fungsi(daftar-parameter);
```

Bahasa C telah memiliki beberapa fungsi yang tersedia pada file header bawaan C. Misalkan fungsi `printf()` yang terdapat pada file header `stdio.h`. Dalam bahasa C, setidaknya sebuah program akan mempunyai fungsi `main()` yang memberitahukan kepada komputer bahwa bagian yang harus dijalankan terlebih dahulu pada sebuah program berada di dalam fungsi `main()`.

Berikut ini contoh dari fungsi dan bagaimana cara memanggilnya di dalam fungsi `main()`:

```c++
#include <stdio.h>

// mendefinisikan fungsi jumlah
int jumlah(int a, int b) {
    // variabel lokal di dalam fungsi
    int c;
    
    // pengolahan di dalam fungsi
    c = a + b;
    
    // kembalian yang punya tipe data yang sama dengan tipe data fungsi
    return c;
}

int main() {
    // variabel lokal di dalam main
    int x = 3;
    int y = 5;
    int total;
    
    // pemanggilan fungsi jumlah
    total = jumlah(x, y);
    
    printf("hasil dari %d ditambah %d yaitu %d", x, y, total);
    
	return 0;
}
```

output:
```bash
hasil dari 3 ditambah 5 yaitu 8
```

[Live Demo](https://ide.geeksforgeeks.org/WvPSloYyhz){: .btn .fs-5 .mb-4 .mb-md-0 }

Pada contoh diatas, dapat dilihat bahwa fungsi `jumlah()` berada di bagian atas fungsi `main()`. Apabila fungsi `jumlah()` ditempatkan di bagian bawah fungsi `main()` maka harus dideklarasikan terlebih dahulu agar apabila fungsi `jumlah()` dipanggil dalam `main()` sehingga `main()` mengetahui bahwa ada fungsi `jumlah()` di lokasi tertentu. Lokasi tersebut bisa di satu file dengan fungsi `main()` atau di file lainnya (pembahasan di file lainnya akan dijelaskan di tulisan-tulisan berikutnya).

```c++
#include <stdio.h>

// mendeklarasikan fungsi jumlah
int jumlah(int a, int b);

int main() {
    // variabel lokal di dalam main
    int x = 3;
    int y = 5;
    int total;
    
    // pemanggilan fungsi jumlah
    total = jumlah(x, y);
    
    printf("hasil dari %d ditambah %d yaitu %d", x, y, total);
    
	return 0;
}

// mendefinisikan fungsi jumlah
int jumlah(int a, int b) {
    // variabel lokal di dalam fungsi
    int c;
    
    // pengolahan di dalam fungsi
    c = a + b;
    
    // kembalian yang punya tipe data yang sama dengan tipe data fungsi
    return c;
}
```

output:

```bash
hasil dari 3 ditambah 5 yaitu 8
```

[Live Demo](https://ide.geeksforgeeks.org/WCbC5RhCUp){: .btn .fs-5 .mb-4 .mb-md-0 }

## tipe-tipe argumen/parameter dalam fungsi
---
Ada dua macam tipe argumen yang bisa ditempatkan di dalam fungsi. Pertama ialah argumen yang diteruskan dengan menyalin **nilai** dari argumen tersebut, kedua ialah menyalin **referensi/alamat** memori dari argumennya.

Bagian pertama telah dicontohkan pada kasus jumlah di atas. Jika hanya meneruskan alamatnya, contoh di atas dapat diubah hingga seperti ini:

```c++
#include <stdio.h>

// mendeklarasikan fungsi jumlah dengan parameter pointer
int jumlah(int *a, int *b);

int main() {
    // variabel lokal di dalam main
    int x = 3;
    int y = 5;
    int total;
    
    // pemanggilan fungsi jumlah dengan
    // meneruskan alamat dari variabel tersebut (&)
    total = jumlah(&x, &y);
    
    printf("hasil dari %d ditambah %d yaitu %d", x, y, total);
    
	return 0;
}

// mendefinisikan fungsi jumlah dengan parameter pointer
int jumlah(int *a, int *b) {
    // variabel lokal di dalam fungsi
    int c;
    
    // pengolahan di dalam fungsi
    c = *a + *b;
    
    // kembalian yang punya tipe data yang sama dengan tipe data fungsi
    return c;
}
```

output:

```bash
hasil dari 3 ditambah 5 yaitu 8
```

[Live Demo](https://ide.geeksforgeeks.org/rWYl0cNt9o){: .btn .fs-5 .mb-4 .mb-md-0 }

Penjelasan lebih lanjut terkait pointer dan referensi akan dijelaskan di tulisan-tulisan berikutnya.