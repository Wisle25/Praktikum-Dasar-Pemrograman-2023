[<< Materi Sebelumnya (Perulangan menggunakan "for") <<](2-PerulanganMenggunakanFor.md)
# 3.3 - While Loop
While adalah perulangan yang akan selalu mengeksekusi perintah yang ada **SELAMA** kondisi masih memenuhi. Apabila kondisi perulangan tersebut **selalu memenuhi**, maka yang dikhawatirkan adalah terjadinya **infinite loop** atau program akan berjalan selamanya sehingga berpotensi crash/hang. Oleh karena itu, perhatikan betul dalam menggunakan operasi perulangan.

## While loop
Format penggunaannya yaitu:
```c
while (/* kondisi */) 
{
    /* perintah... */
}
```

Contoh penggunaan while dalam program C adalah sebagai berikut:

Potongan kode berikut menampilkan "Quack!" sebanyak 10 kali di layar console
```c
int i = 1;
while (i <= 10) 
{
    printf("Quack!\n");
    i++;
}
```

Analisa kode di atas:

1. Variabel `i` dideklarasikan kemudian diisi dengan nilai 1
2. Selagi `i` bernilai kurang dari atau sama dengan 10, maka jalankan perintah `printf("Quack!\n")` kemudian `i++`. Dalam tahap ini, sembari mengulang operasi, program menampilakn "Quack!" ke console kemudian nilai dari variabel `i` di-*increment* (ditambah dengan 1) kemudian kedua perintah tersebut diulang terus menerus sampai tidak memenuhi kondisi `i <= 10` (variabel `i` bernilai 11 dan 11 <= 10 tentu tidak benar) sehingga program dapat keluar dari perulangan.

**Q:** Bagaimana bisa keluar dari perulangan?

**A:** Karena saat `i` mencapai nilai 10, maka akan di-*increment* supaya nilainya menjadi 11 dan dengan demikian, ulangan berikutnya sudah tidak dijalankan lagi karena kondisinya sudah bernilai salah (`i <= 10` untuk nilai `i = 11`).

Potongan kode berikut menampilkan pola 2 4 6 8 ... 100 di layar console
```c
int i = 2;
while (i < 102) 
{
    printf("%d ", i);
    i = i + 2;
}
```

Analisa kode di atas:

1. Variabel `i` dideklarasikan kemudian diisi dengan nilai awal pola yaitu 2
2. Selagi `i` bernilai kurang dari 102, maka jalankan perintah `printf("%d ", i)` kemudian `i = i + 2`. Dalam tahap ini, sembari mengulang operasi, nilai dari variabel `i` ditampilkan di layar kemudian ditambah dengan 2 dan kedua perintah tersebut diulang terus menerus sampai keluar dari perulangan.

## Do-While loop
Do-While loop Merupakan bentuk variasi dari `while` loop. Cara kerja dari `do...while` mirip dengan `while`, perbedaan yang membedakan dengan while adalah `do...while` akan menjalankan perintah yang ada di kode blok sekali sebelum melakukan pengecekan kondisi.

Perhatikan potongan kode dibawah ini
```c
    int i = 0;
    while(i>0) 
    {
        printf("saya berhasil dijalankan");
        i++;
    }
```    

Saat potongan kode dijalankan maka tidak ada nilai yang ditampilkan pada terminal, hal ini dikarenakan kondisi yang dimasukan pada `while` bernilai false. Bandingkan dengan potongan kode `do...while` dibawah ini
```c
    int i = 0;
    do 
    {
        printf("saya berhasil dijalankan");
        i++;
    } while(i>0);
```

Output

    saya berhasil dijalankan

Berbeda dengan kode `while` kode `do..while` diatas akan menampilkan teks sekali meskipun kondisi pada while bernilai salah. Hal ini dikarenakan pada `do...while` program pada blok do akan dijalankan sekali sebelum mengecek kondisi yang ada.

[>> Materi Berikutnya ("break" dan "continue") >>](4-BreakAndContinue.md)
