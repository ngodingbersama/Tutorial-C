# Struktur (struct)
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

[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/C3iZKSlWOp)

## Contoh 1: Membuat struct dan menampilkannya pada terminal
```c++
#include <stdio.h>

struct Users {
    char *nama;
    int nomor_id;
    char *email;
};

void printUser(struct Users);

int main() {
    struct Users user_1;
    user_1.nama = "Agus Al Hakim";
    user_1.nomor_id = 1;
    user_1.email = "agus@gmail.com";
    printUser(user_1);
    return 0;
}

void printUser(struct Users user) {
    printf("nama: %s\n", user.nama);
    printf("id: %d\n", user.nomor_id);
    printf("email: %s\n", user.email);
}
```
[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/8006ba0c-54c0-485c-b1f9-b5d75b022835)

Selain kita dapat menginisiasi variabel di dalam fungsi utama `main`, kita juga dapat menginisiasi variabel di struct-nya:

```c++
struct Users {
    char *nama;
    int nomor_id;
    char *email;
} user_1; // inisiasi variabel
```

## Contoh 2: Menggunakan pointer pada struct
```c++
#include <stdio.h>

struct Users {
    char *nama;
    int nomor_id;
    char *email;
};

void printUser(struct Users *user);

int main() {
    struct Users user_1;
    user_1.nama = "Agus Al Hakim";
    user_1.nomor_id = 1;
    user_1.email = "agus@gmail.com";
    printUser(&user_1);
    return 0;
}

void printUser(struct Users *user) {
    printf("nama: %s\n", user->nama);
    printf("id: %d\n", user->nomor_id);
    printf("email: %s\n", user->email);
}
```
[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/9067301a-933a-4ca5-99d1-22004e48dae8)

```c++
#include <stdio.h>

struct Users {
    char *nama;
    int nomor_id;
    char *email;
};

void printUser(struct Users *user);
void ubahNama(struct Users *user, char *namabaru);

int main() {
    struct Users user_1;
    user_1.nama = "Agus Al Hakim";
    user_1.nomor_id = 1;
    user_1.email = "agus@gmail.com";
    printUser(&user_1);
    
    printf("\nsetelah ubah nama menjadi:\n");
    
    ubahNama(&user_1, "Bagas Andika");
    printUser(&user_1);
    return 0;
}

void printUser(struct Users *user) {
    printf("nama: %s\n", user->nama);
    printf("id: %d\n", user->nomor_id);
    printf("email: %s\n", user->email);
}

void ubahNama(struct Users *user, char *namabaru) {
    user->nama = namabaru;
}
```

output:
```bash
nama: Agus Al Hakim
id: 1
email: agus@gmail.com

setelah ubah nama menjadi:
nama: Bagas Andika
id: 1
email: agus@gmail.com

```
[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/a4cbc078-36f6-4e3d-8d3d-0a5403b6c6a1)

## Contoh 3: Menggunakan typedef
`typedef` digunakan untuk membuat nama alias untuk sebuah tipe data. Ini umumnya dipakai oleh `struct` untuk menyederhanakan sintaks dalam mendeklarasikan variabel.

```c++
typedef struct Users s_Users;
```

```c++
#include <stdio.h>

typedef struct Users {
    char *nama;
    int nomor_id;
    char *email;
} s_Users;

void printUser(s_Users *user);

int main() {
    s_Users user_1;
    user_1.nama = "Agus Al Hakim";
    user_1.nomor_id = 1;
    user_1.email = "agus@gmail.com";
    printUser(&user_1);
    return 0;
}

void printUser(s_Users *user) {
    printf("nama: %s\n", user->nama);
    printf("id: %d\n", user->nomor_id);
    printf("email: %s\n", user->email);
}
```
[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/5896c043-d784-495e-8ff7-f358b57cbfa3)

## Contoh 4: `struct` bersarang
```c++
#include <stdio.h>

struct Users {
    char *nama;
    int nomor_id;
    char *email;
};

struct Info {
    struct Users *user;
    char *hobi;
};

typedef struct Users s_Users;
typedef struct Info s_Info;

void printUser(s_Users *user);
void printUserInfo(s_Info *info);

int main() {
    s_Users user_1;
    user_1.nama = "Agus Al Hakim";
    user_1.nomor_id = 1;
    user_1.email = "agus@gmail.com";
    printUser(&user_1);
    
    printf("\nMenambahkan info:\n");
    s_Info info_1;
    info_1.user = &user_1;
    info_1.hobi = "Membaca";
    printUserInfo(&info_1);

    printf("\nMengganti nama pada user dan info:\n");
    user_1.nama = "Bagas Andika";
    printUserInfo(&info_1);
    return 0;
}

void printUser(s_Users *user) {
    printf("nama: %s\n", user->nama);
    printf("id: %d\n", user->nomor_id);
    printf("email: %s\n", user->email);
}

void printUserInfo(s_Info *info) {
    printUser(info->user);
    printf("hobi: %s\n", info->hobi);
}
```
output:
```bash
nama: Agus Al Hakim
id: 1
email: agus@gmail.com

Menambahkan info:
nama: Agus Al Hakim
id: 1
email: agus@gmail.com
hobi: Membaca

Mengganti nama pada user dan info:
nama: Bagas Andika
id: 1
email: agus@gmail.com
hobi: Membaca

```

[<kbd> <br> Live Demo <br> </kbd>](https://ide.geeksforgeeks.org/5983196c-9788-4fde-8f9a-2d80f1cafa92)
