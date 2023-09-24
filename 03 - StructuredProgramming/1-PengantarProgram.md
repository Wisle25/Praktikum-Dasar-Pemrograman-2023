# 3.1 - Pengantar Program
## Program Sederhana
Biasanya saat kita ingin menuliskan sebuah kode, pertama-tama kita akan membuat/menuliskan program *hello world* yang terlihat seperti di bawah ini.
```c
/* Menggunakan library stdio.h */
#include <stdio.h>

// Masuk ke fungsi main
int main()
{
    printf("Hello, World!");

    return 0;
}
```
### Memahami kode
Mari kita pisahkan dan pahami masing-masing baris dari kode tersebut, dimulai dari baris paling atas.
```c
#include <stdio.h>
 ```
 Perintah `#include` merupakan sebuah perintah untuk menggunakan sebuah file C atau *library* bawaan C yang dinamakan `stdio.h`, salah satunya adalah `printf`. Baris kode di atas sering disebut *preprocessor directive*. Pada *preprocessor directive* tidak memerlukan titik koma (`;`) pada akhir barisnya.

```c
int main()
{
    // ...
}
```
Selanjutnya, fungsi `main()` di atas adalah fungsi utama dalam sebuah kode C.  Fungsi ini berguna sebagai *endpoint* atau titik awal dari sebuah program. Di belakang fungsi ini terdapat kata kunci `int` yang menandakan *return value* dari kode kalian yang bertipe *int* atau bilangan bulat. Kita akan membahas *return value* dan tipe data di pertemuan mendatang.
```c
printf("Hello, World!");
```
Fungsi `printf()` di atas adalah fungsi bawaan C yang terdapat pada *library* `stdio.h`. Fungsi ini digunakan untuk mencetak *string* atau tulisan yang kalian masukkan sebagai parameter (di dalam kurung fungsi) ke *console* kalian (misal Windows cmd). Di contoh tersebut, kita mencetakkan tulisan **"Hello, World!"** ke *console* kita.
```c
return 0;
```
Kata kunci `return` digunakan untuk menghentikan sebuah fungsi lalu mengembalikan sebuah value tertentu dari fungsi tersebut. Dalam kasus ini `main()` `return` akan mengembalikan kontrol ke pemanggil fungsi. Karena `main()` merupakan fungsi utama, maka memanggil return akan menghentikan program. Angka `0` yang terdapat setelah `return` menandakan kode program. Jika program berjalan lancar, biasanya kode yang dipakai adalah `0`.
```c
// Masuk ke fungsi main
/* Menggunakan library stdio.h */
```
Terakhir, 2 baris di atas merupakan baris komentar yang tidak akan digunakan pada program. Komentar dapat menjadikan kode kalian lebih mudah dipahami, khususnya untuk pemrogram lain. Komentar dalam C mengikuti *syntax* seperti di atas, dengan menambahkan `//` sebelum komentar, atau mengapit komentar dengan `/*` dan `*/`.

## Basic I/O
I/O, yang memiliki kepanjangan Input/Output adalah separuh hati dari banyak program. I/O membuat program yang kalian buat dapat berinteraksi dengan dunia luar, baik dengan file, program lain, atau pengguna/manusia. Untuk kali ini, kita hanya akan membahas I/O yang melibatkan pengguna/manusia.
### Basic Output
Salah satu output (keluaran) yang paling mendasar yang dapat dibuat oleh program C adalah perintah *print to console* atau mencetak *console*. Seperti yang telah kita bahas pada sub-subbab sebelumnya mengenai [memahami kode *hello world*](#program-sederhana), kita dapat menggunakan perintah `printf()` untuk mencetak apapun yang kita mau ke konsol.
```c
printf("Hello, World!");
printf("Hello 1234");
```
Sejauh ini, kita baru mempelajari cara mencetak data yang langsung kita berikan sebagai *string* atau tulisan mentah. Bagaimana jika kita ingin mencetak nilai dari sebuah variabel? Caranya adalah dengan menggunakan format. Perhatikan kode di bawah ini.
```c
#include <stdio.h>
int main() {
	char name[8] = "Michael";
	int number = 150;

	printf("Your Variables: %s %d \n", name, number);
	// '\n' adalah "newline", sama seperti "enter"
	return  0;
}
```
*Output* pada *console*:
```
Your Variables: Michael 150
```
Pada contoh program di atas, kita menggunakan format pada fungsi `printf()` kita untuk mencetak variabel `name[]` dan `number`, di mana `name[]` bertipe *char array* atau string, sedangkan `number` bertipe integer. Seperti yang dapat kita lihat, konstanta format (`%s` dan `%d`) merupakan sebuah placeholder atau tempat dari variabel yang kita berikan di sebelah kanan. `%s` berkorespondensi dengan variabel `name`, sedangkan `%d` dengan `number`. Format bagi masing-masing tipe data berbeda-beda. Lihat tabel dan potongan kode di bawah ini.

|Placeholder|Tipe Data|Penjelasan|
|:---------:|---------|----------|
|%s|string / *char array*|Tulisan alfanumerik|
|%d|integer|Angka/bilangan|
|%f|floating point|Bilangan real|

```c
#include <stdio.h>
int main() {
	char name[9] = "Everglow";
	int number = 42;
	float real = 3.14;

	printf("Your Variables: %s %d %f \n", name, number, real);
	// Pada compiler modern, return pada main() tidak harus dituliskan
	// Referensikan ke perintah dosen kalian mengenai penulisan return pada main()
}
```
*Output* pada *console*:
```
Your Variables: Everglow 42 3.14
```
> Cara terbaik untuk memahami Basic I/O adalah terus mencoba dan bereksperimen pada IDE kalian!

### Basic Input
Jika kita sudah mengetahui bagaimana cara mencetak variabel yang telah kita definisikan, sekarang kita akan mempelajari cara meminta pengguna program kita untuk mengisi sebuah variabel. Perhatikan contoh kode di bawah.
```c
#include <stdio.h>
int main() {
	char name[100];
	int number;
	float real;

    printf("Enter a value: ");
    scanf("%s %d %f", name, &number, &real);

	printf("Your Inputs: %s %d %f \n", name, number, real);
}
```
*Output* pada *console*:
```
Enter a value: Halo 12 43.93
Your Inputs: Halo 12 43.93
```
> Note: "Halo 12 43.93" adalah nilai yang dimasukkan oleh pengguna

Dapat kita lihat bahwa fungsi yang "menangkap" masukan/input pengguna dari *console*, yaitu `scanf()`, menggunakan format placeholder yang sama dengan fungsi `printf()`.
```c
scanf("%s %d %f", name, &number, &real);
```
Potongan fungsi di atas akan menangkap masukan pengguna yang dibatasi oleh spasi, dan urut berupa string, integer, dan float, dari kiri ke kanan. Dengan menginput `Halo 12 43.93`, program akan memasukkan "Halo" ke variabel `name`, 12 ke variabel `number`, dan 43.93 ke variabel `real`.  Diperlukan *ampersand* (`&`) di depan variabel berjenis integer/floating point, namun tidak akan dijelaskan alasannya sekarang. *Do as above*
Fungsi `scanf()` yang kita gunakan ini memiliki sebuah kekurangan, yaitu tidak bisa menerima *string* yang ber-spasi. Namun, kita akan tetap menggunakan metode ini untuk sekarang.
> Cobalah bereksperimen dengan memberikan masukan ber spasi, atau menghapus ampersand (&) di awal variabel integer dan floating point!

<br />

[>> Materi Berikutnya (Variabel dan Tipe Data) >>](2-VariabelTipeData.md)
