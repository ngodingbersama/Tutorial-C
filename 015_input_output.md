# Input dan Output
Ketika kita katakan Input, berarti kita memasukkan beberapa data ke sebuah program. Input dapat diberikan dalam bentuk sebuah file atau berasal dari baris perintah pada terminal/konsole.
Ketika kita katakan Output, berarti kita menampilkan beberapa data pada layar, printer, atau disimpan dalam file yang lain.

## scanf() dan printf()
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
