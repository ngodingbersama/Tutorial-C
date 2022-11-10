# Pointer
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

[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/KfXcF78zyP)

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

[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/daiJXreTX4)


> **Note**
>
> Perlu diingat bahwa tipe data pointer dan tipe data variabel yang ingin disimpan alamatnya haruslah **sama**.

