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
> Perlu diketahui bahwa, hindarkan penggunaan pointer string kosong `char *` pada `scanf()` karena pointer string kosong ditempatkan pada sebuah alamat acak yang bisa saja program kita akan mengalami `segmentation fault`. 


## Membuka file

## Menutup file
