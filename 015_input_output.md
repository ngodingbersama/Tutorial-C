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

Fungsi `fclose()` akan mengeluarkan (mengembalikan) nilai nol apabila berhasil, dan mengembalikan nilai EOF apabila terdapat error (file tidak dapat ditutup karena masalah tertentu). Fungsi `fclose()` dan EOF sudah tersedia di folder `stdio.h`. EOF merupakan alias untuk bilangan integer -1.

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
Dalam menulis karakter, kata, atau kalimat ke dalam file teks, C sudah mempersiapkan beberapa fungsi yang dibutuhkan. Beberapa diantaranya adalah:
```c++
int fputc( int c, FILE *fp ); // menulis satu karakter
int fputs( const char *s, FILE *fp ); // menulis satu string
int fprintf(FILE *fp,const char *format, ...); // menulis satu string dengan beberapa format untuk input variabel (mirip printf)
```

## Membaca file
Dalam membaca karakter, kata, atau kalimat dan menampilkannya ke terminal/layar atau ke variabel tertentu, C juga sudah mempersiapkan beberapa fungsi yang dibutuhkan. Beberapa diantaranya adalah:
```c++
int fgetc( FILE * fp ); // membaca satu karakter
char *fgets( char *buf, int n, FILE *fp ); // membaca satu string dan menampilkan ke layar/terminal
int fscanf(FILE *fp, const char *format, ...); // membaca satu string dan menyimpannya di variabel, titik berhenti adalah spasi (mirip scanf)
```

## Contoh 3: Contoh menulis file
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // menulis ke file baru
    fp = fopen("coba.txt","w");
    
    if (fp == NULL) exit(1);
    
    char *nama = "Jason Tiramisu";
    char *alamat = "Jalan Kenangan";
    
    // memanfaatkan fputs
    fputs("Informasi pegawai: ", fp);
    
    // memanfaatkan fputc
    fputc('A', fp);
    fputc('\n', fp);
    
    // memanfaatkan fprintf
    fprintf(fp, "Nama: %s\n", nama);
    fprintf(fp, "Alamat: %s\n", alamat);
    
    fclose(fp);

    return 0;
}
```

isi `coba.txt`:
```bash
Informasi pegawai: A
Nama: Jason Tiramisu
Alamat: Jalan Kenangan

```

## Contoh 4: Penggunaan fgetc()
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // menulis ke file baru
    fp = fopen("coba.txt","r");
    
    if (fp == NULL) exit(1);
    
    char huruf; 
    
    // mendapatkan karakter pertama
    huruf = fgetc(fp);
    printf("huruf: %c\n", huruf);
    
    // mendapatkan karakter selanjutnya
    huruf = fgetc(fp);
    printf("huruf: %c\n", huruf);
    
    fclose(fp);

    return 0;
}
```

output:
```bash
huruf: I
huruf: n
```

## Contoh 5: Penggunaan fgets()
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // menulis ke file baru
    fp = fopen("coba.txt","r");
    
    if (fp == NULL) exit(1);
    
    // hindari penggunaan `char *` untuk menyimpan string
    char string[500];
    
    // mendapatkan string satu baris pertama
    fgets(string, 500, fp);
    printf("string: %s", string);
    
    // mendapatkan string satu baris selanjutnya
    fgets(string, 500, fp);
    printf("string: %s", string);
    
    fclose(fp);

    return 0;
}
```
output:
```bash
string: Informasi pegawai: A
string: Nama: Jason Tiramisu
```

## Contoh 6: Penggunaan fscanf()
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // menulis ke file baru
    fp = fopen("coba.txt","r");
    
    if (fp == NULL) exit(1);
    
    // hindari penggunaan `char *` untuk menyimpan string
    char string1[20];
    char string2[20];
    
    // mendapatkan 2 kata pertama
    fscanf(fp, "%s %s", string1, string2);
    printf("hasil: %s %s\n", string1, string2);
    
    // mendapatkan 2 kata selanjutnya
    fscanf(fp, "%s %s", string1, string2);
    printf("hasil: %s %s\n", string1, string2);
    
    // mendapatkan 2 kata selanjutnya
    fscanf(fp, "%s %s", string1, string2);
    printf("hasil: %s %s\n", string1, string2);
    
    fclose(fp);

    return 0;
}
```

output:
```bash
hasil: Informasi pegawai:
hasil: A Nama:
hasil: Jason Tiramisu
```

## Contoh 7: Penggunaan `r+`
Terdapat file `coba.txt` yang berisi:
```
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```

Maka pembacaan dan penulisan ke file tersebut dengan menggunakan mode `r+` mengikuti posisi terakhir pembacaan atau penulisan sebelumnya.
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // membaca file coba.txt
    fp = fopen("coba.txt","r+");
    
    if (fp == NULL) exit(1);
    
    char string[500];
    fgets(string, 500, fp);
    printf("%s", string);
    
    fputs("input teks terbaru", fp);
    
    fclose(fp);

    return 0;
}
```

output di terminal:
```bash
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```

dan isi file `coba.txt` menjadi:
```bash
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaainput teks terbaru
```

Apabila menulis pertama kali dan membacanya kemudian, maka:
```c++
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    // membaca file coba.txt
    fp = fopen("coba.txt","r+");
    
    if (fp == NULL) exit(1);
    
    fputs("input teks terbaru", fp);
    
    char string[500];
    fgets(string, 500, fp);
    printf("%s", string);
    
    fclose(fp);

    return 0;
}
```
Yang terdapat di file `coba.txt`:
```bash
input teks terbaruaaaaaaaaaaaaaa
```

sedangkan yang ada di terminal adalah dari posisi terakhir penulisan di file hingga akhir:
```bash
aaaaaaaaaaaaaa
```
