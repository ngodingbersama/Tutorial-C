# Input dan Output
Ketika kita katakan Input, berarti kita memasukkan beberapa data ke sebuah program. Input dapat diberikan dalam bentuk sebuah file atau berasal dari baris perintah pada terminal/konsole.
Ketika kita katakan Output, berarti kita menampilkan beberapa data pada layar, printer, atau disimpan dalam file yang lain.

## scanf() dan printf()
fungsi `int scanf(const char *format, ...)` terdiri dari bagian pertama `const char *format` dan bagian variabel yang akan menyimpan nilai pada scanf `, ...`. Perlu diperhatikan bahwa, variabel yang akan menyimpan sebuah nilai musti berupa pointer. pada variabel kata, kalimat, atau array, `char *` atau `char[1000]` sudah merupakan bentuk pointer. Adapun variabel yang menggunakan tipe data dasar seperti `int`, `float`, dan lainnya harus diubah ke bentuk pointer dengan cara menambahkan ampersand `&`.

Adapun `int printf(const char *format, ...)`, variabel yang akan ditampilkan pada layar tidak perlu diubah dalam bentuk pointer.

```c++
#include <stdio.h>

int main() {
    
    char *kata;
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


## Membuka file

## Menutup file
