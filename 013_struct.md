---
title: Struktur
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 13
---

# Struktur (struct)

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Struktur (struct) merupakan tipe data yang dapat mengumpulkan beberapa tipe data yang berbeda dalam satu tempat variabel. Misal terdapat variabel **pengguna** yang mempunyai variabel **nama**, **nomor_id**, **email**, **total_pengikut**, maka dalam C, dapat dituliskan sebagai berikut:

```c++
struct pengguna {
    char *nama;
    int nomor_id;
    char *email;
    int total_pengikut;
};
```

Sehingga, struct dapat didefinisikan dalam C sebagai berikut:

```c++
struct [nama_struct] {
    tipe_data_1 nama_variabel_anggota_1;
    tipe_data_2 nama_variabel_anggota_2;
    tipe_data_3 nama_variabel_anggota_3;
    ...
    tipe_data_N nama_variabel_anggota_N;
} [satu atau lebih nama variabel struct];
```

Pada struct pengguna, dapat dilekatkan variabel setelah nama struct. Contoh:

```c++
int main() {
    struct pengguna pengguna_1;
    pengguna_1.nama = "Agus Al Hakim";
    pengguna_1.nomor_id = 1;
    printf("pengguna 1: %s dengan nomor id %d\n", pengguna_1.nama, pengguna_1.nomor_id);
    return 0;
}
```

[Live Demo](https://ide.geeksforgeeks.org/C3iZKSlWOp){: .btn .fs-5 .mb-4 .mb-md-0 }