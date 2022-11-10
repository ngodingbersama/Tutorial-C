# Union
Union merupakan tipe data spesial yang menyimpan beberapa tipe data di dalam lokasi memori yang sama. Kita dapat mendefinisikan sebuah union dengan banyak anggota, namun hanya satu anggota saja yang punya nilai dalam satu waktu.

Mendefinisikan union:
```c++
union nama_union {
    definisi_tipe_data_1;
    definisi_tipe_data_2;
    .
    .
    .
    definisi_tipe_data_N;
} satu_atau_lebih, variabel_union;
```

## Contoh 1: Menggunakan union
```c++
#include <stdio.h>

typedef union Data {
    int x;
    char y;
} u_Data;

void printData(u_Data *data);

int main() {
    u_Data data_1;
    data_1.x = 65;
    printData(&data_1);
    return 0;
}

void printData(u_Data *data) {
    printf("x: %d\n", data->x);
    printf("y: %c\n", data->y);
}
```

output:
```bash
x: 65
y: A
```
[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/3f0291c6-1f75-44bb-ae4e-24098a72ce95)
