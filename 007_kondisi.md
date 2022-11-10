---
title: Pengambilan keputusan
parent: Dasar-dasar praktis pemrograman C
has_children: false
nav_order: 7
---

# Pengambilan keputusan

<details open markdown="block">
<summary>
Table of contents
</summary>
1. TOC
{:toc}
</details>

---
Pada bahasa C, pengambilan keputusan dapat dinilai dari nilai dari sebuah kondisi. Sebuah kondisi dianggap benar jika bernilai bukan nol atau bukan NULL, sedangkan dianggap salah jika nol atau NULL.

Ada beberapa contoh kondisi dalam bahasa C, diantaranya:

## Penggunaan `if`
---
sintaks yang digunakan ialah:

```c++
if(kondisi) {
    /* bagian ini dijalankan jika kondisi bernilai benar atau TRUE */;
}
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 5;
	
	// jika kondisi x lebih dari 3, maka buat pernyataan
	if (x > 3) {
	    printf("nilai x = %d lebih besar dari 3", x);
	}
	return 0;
}
```

output:
```bash
nilai x = 5 lebih besar dari 3
```

[Live Demo](https://ide.geeksforgeeks.org/AvleolBbL7){: .btn .fs-5 .mb-4 .mb-md-0 }

## Penggunaan `if ... else ...`
---
sintaks yang digunakan ialah:

```c++
if(kondisi) {
    /* bagian ini dijalankan jika kondisi bernilai benar atau TRUE */;
} else {
    /* bagian ini dijalankan jika kondisi bernilai salah atau FALSE */;
}
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 2;
	
	// jika kondisi x lebih dari 3, maka buat pernyataan
	if (x > 3) {
	    printf("nilai x = %d lebih besar dari 3", x);
	} else {
	    printf("nilai x = %d kurang dari atau sama dengan dari 3", x);
	}
	
	return 0;
}
```

output:
```bash
nilai x = 2 kurang dari atau sama dengan dari 3
```

[Live Demo](https://ide.geeksforgeeks.org/2aDGEpw2yp){: .btn .fs-5 .mb-4 .mb-md-0 }

## Penggunaan `switch`
---
`switch` digunakan saat sebuah nilai ingin diujikan dalam beberapa kondisi. sintaks yang digunakan ialah:

```c++
switch(variabel) {
    case variabel-konstan:
        /* bagian yang dijalankan pada `case` ini */;
    case
        .
        .
        .
    default:
        /* bagian ini dijalankan pada kondisi umum */;
}
```

contoh:

```c++
#include <stdio.h>

int main() {
    // definisi
	int x = 2;
	
	switch (x) {
	    case 1:
	        printf("nilai x sama dengan satu\n");
	    case 2:
	        printf("nilai x sama dengan dua\n");
	    default:
	        printf("nilai x = %d\n", x);
	}
	
	return 0;
}
```

output:
```bash
nilai x sama dengan dua
nilai x = 2
```

[Live Demo](https://ide.geeksforgeeks.org/lVg1ZsJPMS){: .btn .fs-5 .mb-4 .mb-md-0 }

## Kondisi bersarang (nested conditions)
---
Kondisi bisa bercabang atau bersarang jika pada kasus tertentu dan mungkin saja hal ini sering dijumpai saat memecahkan suatu masalah. `if` maupun `switch` dapat dilakukan secara bersarang dalam bahasa C.

```c++
if (kondisi 1) {
    // pernyataan untuk kondisi 1
} else if (kondisi 2) {
    // pernyataan untuk kondisi 2
} else {
    // pernyataan jika tidak termasuk pada kondisi keduanya
}
```

```c++
switch (nilai 1) {
    case nilai-konstan:
        switch (nilai 2) {
            case nilai-konstan:
                // pernyataan
            case 
                .
                .
                .
            default:
                // pernyataan 
        }
    case
        .
        .
        .
    default:
        // pernyataan
}
```