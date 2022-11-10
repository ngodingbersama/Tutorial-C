# String
String pada dasarnya ialah array karakter 1 dimensi yang diakhiri dengan karakter **null** `'\0'`. Sehingga, jika ingin menuliskan kata "hello", maka dalam bentuk array dituliskan sebagai berikut:

```c++
char kata[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
```

Di dalam tulisan lain, string dapat dinyatakan dalam bentuk berikut ini:

```c++
char kata[] = "Hello";
```

Dalam penulisan kedua, karakter `'\0'` tidak perlu dituliskan karena kompiler C akan secara otomatis menaruh karakter tersebut diakhir kata/kalimat.

