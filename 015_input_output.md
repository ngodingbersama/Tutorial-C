# Input dan Output
Ketika kita katakan Input, berarti kita memasukkan beberapa data ke sebuah program. Input dapat diberikan dalam bentuk sebuah file atau berasal dari baris perintah pada terminal/konsole.
Ketika kita katakan Output, berarti kita menampilkan beberapa data pada layar, printer, atau disimpan dalam file yang lain.

## scanf() dan printf()
fungsi `int scanf(const char *format, ...)` terdiri dari bagian pertama `const char *format` untuk menentukan tipe data masukan berdasarkan format dan bagian variabel yang akan menyimpan nilai pada scanf `, ...`. Perlu diperhatikan bahwa, variabel yang akan menyimpan sebuah nilai musti berupa pointer. pada variabel kata, kalimat, atau array, `char *` atau `char[1000]` sudah merupakan bentuk pointer. Adapun variabel yang menggunakan tipe data dasar seperti `int`, `float`, dan lainnya harus diubah ke bentuk pointer dengan cara menambahkan ampersand `&`.

Adapun `int printf(const char *format, ...)`, variabel yang akan ditampilkan pada layar tidak perlu diubah dalam bentuk pointer.

```c++
#include <stdio.h>

int main() {
    
    char kata[50];
    int nilai;
    
    printf("masukkan sebuah kata:");
    scanf("%s", kata);
    
    printf("masukkan sebuah nilai:");
    scanf("%d", &nilai);
    
    printf("kata yang Anda masukkan adalah '%s', ", kata);
    printf("adapun nilai adalah %d\n", nilai);

    return 0;
}
```

output:
```bash
masukkan sebuah kata:kurcaci
masukkan sebuah nilai:12
kata yang Anda masukkan adalah 'kurcaci', adapun nilai adalah 12
```

Penggunaan spasi pada input `scanf()` harus menjadi perhatian. Hal ini karena spasi memisahkan input menjadi beberapa bagian. Contoh, ketika input berupa `kurcaci hitam`, maka setiap kata merupakan input yang berbeda. Sehingga, inputan kedua yaitu `hitam` dianggap sebagai input untuk `scanf()` yang kedua.

```bash
masukkan sebuah kata:kurcaci hitam
masukkan sebuah nilai:kata yang Anda masukkan adalah 'kurcaci', adapun nilai adalah 21949
```

Agar lebih jelas, kita masukkan kata setelah spasi menjadi angka:

```bash
masukkan sebuah kata:kurcaci 19
masukkan sebuah nilai:kata yang Anda masukkan adalah 'kurcaci', adapun nilai adalah 19
```

Untuk mengantisipasi hal ini, `scanf()` pertama perlu mengakomodir input berupa dua kata.

```c++
#include <stdio.h>

int main() {
    
    char kata1[50];
    char kata2[50];
    int nilai;
    
    printf("masukkan sebuah kata:");
    scanf("%s %s", kata1, kata2);
    
    printf("masukkan sebuah nilai:");
    scanf("%d", &nilai);
    
    printf("kata yang Anda masukkan adalah '%s %s', ", kata1, kata2);
    printf("adapun nilai adalah %d\n", nilai);

    return 0;
}
```

output:
```bash
masukkan sebuah kata:kurcaci hitam
masukkan sebuah nilai:11
kata yang Anda masukkan adalah 'kurcaci hitam', adapun nilai adalah 11
```

> **Warning**
> 
> Perlu diketahui bahwa, hindarkan penggunaan pointer string kosong `char *` pada `scanf()` karena pointer string kosong ditempatkan pada sebuah alamat acak yang bisa saja program kita akan mengalami `segmentation fault`. 
> 
> ```c++
> char *kata1;
> char *kata2;
> ```
> 
> output:
> ```bash
> masukkan sebuah kata:kurcaci hitam
> Segmentation fault
> ```
> walaupun terkadang jika salah satu tipe data string adalah pointer dan lainnya adalah array itu tidak terjadi `segmentation fault`, penggunaan ini perlu dihindari untuk menjaga kestabilan program kita.

# Input dan Output pada File
Sebuah file mewakili kumpulan _bytes_, terlepas apakah itu file teks ataupun file binary. 

## Membuka file
Kita dapat menggunakan fungsi `fopen()` yang terdapat di header `stdio.h` untuk membuat file baru ataupun membuka file yang telah ada. Pemanggilan fungsi ini akan mengeluarkan tipe objek pointer `FILE *` yang mengandung informasi yang dibutuhkan untuk mengatur file tersebut. Prototipenya adalah:

```c++
FILE *fopen( const char * filename, const char * mode );
```

Dari protopite tersebut, terdapat beberapa parameter yaitu `filename` yang merupakan string literal yang berisi nama dari file tersebut, dan `mode` akses yaitu sebagai berikut:

|Mode|Penjelasan|
|---|---|
|r|Membuka file teks yang tersedia dan hanya untuk tujuan dibaca. Jika file tidak ada, maka `FILE *` bernilai NULL.|
|w|Membuka file teks untuk ditulis, jika tidak ada file tersebut maka file tersebut dibuat. Di sini, program akan menulis isi dari awal file, sehingga tulisan sebelumnya akan terhapus.|
|a|Sama seperti mode 'w'. Perbedaannya, tulisan terbaru akan ditambahkan setelah tulisan sebelumnya, sehingga tulisan sebelumnya tidak terhapus.|
|r+|Membuka file teks untuk dibaca dan ditulis. Jika file tidak ada, maka `FILE *` bernilai NULL.|
|w+|Membuka file teks untuk dibaca dan ditulis. Jika file tidak ada, maka file akan dibuat. Jika ada, maka konten file tersebut akan terhapus jika ditulis.|
|a+|Membuka file teks untuk dibaca dan ditulis. Jika file tidak ada, maka file akan dibuat. Jika ada, konten baru akan ditambahkan setelah konten sebelumnya.|

## Menutup file
Setelah mengolah file dalam pointer `FILE *`, file tersebut perlu ditutup agar memori yang terpakai dapat dibersihkan. Prototipe untuk menutup file adalah:

```c++
int fclose( FILE *fp );
```

Fungsi `fclose()` akan mengeluarkan (mengembalikan) nilai nol apabila berhasil, dan mengembalikan nilai EOF apabila terdapat error (file tidak dapat ditutup karena masalah tertentu). Fungsi `fclose()` dan EOF sudah tersedia di folder `stdio.h`.

## Contoh 1: Membuka file yang tidak ada
```c++
#include <stdio.h>
#include <stdlib.h> // untuk mendapatkan fungsi exit

int main()
{
    FILE *fp;
    fp = fopen("coba.txt","r");
    
    if (fp == NULL) {
        printf("file tidak ada");
        exit(1);
    }
    
    fclose(fp);

    return 0;
}
```

output:
```bash
file tidak ada

...Program finished with exit code 1
```

## Contoh 2: Membuat file kosong dan membaca file yang sudah ada
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // membuat file kosong
    fp = fopen("coba.txt","w");
    fclose(fp);
    
    // membaca file
    fp = fopen("coba.txt","r");
    
    if (fp == NULL) {
        printf("file tidak ada");
        exit(1);
    } else {
        printf("file ada");
    }
    
    fclose(fp);

    return 0;
}
```

output:
```bash
file ada

...Program finished with exit code 0
```

## Menulis file

## Membaca file
