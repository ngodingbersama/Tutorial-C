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

## Contoh 2: Implementasi
union bermanfaat dalam beberapa situasi, salah satunya pada `struct` bersarang. Misal, kita ingin membuat `struct` yang berisi `struct` yang sama dan sebuah nilai (struktur data pohon). Pada kondisi ini, struct diminta untuk memilih isian apakah berupa struct kembali atau nilai.

Jika bentuknya seperti ini:
```c++
struct Cabang {
    struct Cabang *kanan;
    struct Cabang *kiri;
    int nilai;
} s_Cabang;
```

maka saat `struct Cabang` memilih isian berupa struct, `int nilai` menjadi sia-sia. Sehingga, kita membuatuhkan union sebagai kriteria untuk memilih tipe data yang mana yang akan digunakan.

```c++
#include <stdio.h>
#include <stdbool.h>

typedef struct Cabang {
    bool kepala_cabang;
    char *nama_cabang;
    union {
        struct Cabang *cabang;
        int jumlah_pekerja;
    } info;
} s_Cabang;

void isiKepalaCabang(s_Cabang *cabangUtama, 
                     char *nama_cabang,
                     s_Cabang *cabangBawah);

void isiCabangBawah(s_Cabang *cabangUtama, 
                     char *nama_cabang,
                     int jumlah_pekerja);

void printCabang(s_Cabang *cabang);

int main() {
    s_Cabang toko_utama, toko_cabang[2];
    isiKepalaCabang(&toko_utama, "MejaKerja", toko_cabang);

    // isi informasi menggunakan variabel toko_utama
    isiCabangBawah(&toko_utama.info.cabang[0], "MejaCerdas", 10);
    isiCabangBawah(&toko_utama.info.cabang[1], "MejaMawas", 12);

    printCabang(&toko_utama);
    printCabang(&toko_utama.info.cabang[0]);
    printCabang(&toko_utama.info.cabang[1]);

    return 0;
}

void isiKepalaCabang(s_Cabang *cabangUtama, 
                     char *nama_cabang,
                     s_Cabang *cabangBawah) {
    cabangUtama->kepala_cabang = true;
    cabangUtama->nama_cabang = nama_cabang;
    cabangUtama->info.cabang = cabangBawah;
}

void isiCabangBawah(s_Cabang *cabangUtama, 
                     char *nama_cabang,
                     int jumlah_pekerja) {
    cabangUtama->kepala_cabang = false;
    cabangUtama->nama_cabang = nama_cabang;
    cabangUtama->info.jumlah_pekerja = jumlah_pekerja;
}

void printCabang(s_Cabang *cabang) {
    if(cabang->kepala_cabang == false) {
        printf("nama: %s\n", cabang->nama_cabang);
        printf("jumlah pekerja: %d\n\n", cabang->info.jumlah_pekerja);
    } else {
        printf("nama: %s\n", cabang->nama_cabang);
        printf("merupakan kepala cabang\n\n");
    }
}
```

output:
```bash
nama: MejaKerja
merupakan kepala cabang

nama: MejaCerdas
jumlah pekerja: 10

nama: MejaMawas
jumlah pekerja: 12
```

[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/730cc752-8605-44cc-ba28-3117f0dfb1a3)
