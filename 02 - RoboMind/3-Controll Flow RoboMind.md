# Control Flow dengan RoboMind
Memahami dan menggunakan function, perulangan, dan kondisional dengan menggunakan RoboMind

## Kondisional
Dalam pemrograman, kondisional berguna untuk mengendalikan alur program berdasarkan kondisi atau kriteria tertentu. Dengan kata lain, kondisional memungkinkan kita untuk menjalankan bagian kode tertentu jika suatu kondisi terpenuhi, dan bagian kode lain jika kondisi tersebut tidak terpenuhi. Contoh syntaxnya pada RoboMind adalah **if** **else** dan **else if**.

Pada RoboMind, kondisional diletakan di dalam kurung biasa **()** untuk menentukan kondisi yang akan dievaluasi. Tanda kurung ini digunakan untuk mengelilingi ekspresi kondisional. Ekspresi (expression) sendiri adalah kombinasi dari nilai, variabel, operator, atau fungsi yang mengembalikan/menghasilkan tipe data **boolean** (Ya atau Tidak).
Kondisional di RoboMind dapat menerima beberapa 

Contohnya:
```c++
if (LeftIsClear)
{
    left
}
else
{
    right
}
```

## Perulangan
Dalam Pemrograman, kita perlu untuk menganut prinsip "D.R.Y" yaitu "Dont Repeat Yourself". Jadilah programmer yang malas, yaitu malas untuk menuliskan kode yang sama berulang-ulang kali tetapi impact yang dihasilkan tidak terlalu besar. Daripada seperti itu, kita bisa menuliskan program sekali saja tetapi impact yang dihasilkan bisa lebih besar dari apa yang kita tuliskan. Oleh karena itu, kita memerlukan adanya "perulangan".

Perulangan dapat memungkinkan kita untuk mengeksekusi beberapa instruksi berulang kali berdasarkan kondisi atau selama iterasi tertentu. Perulangan berguna supaya kita tidak perlu repot-repot menuliskan kode yang sama . Dalam RoboMind, terdapat dua jenis perulangan utama yaitu:
- perulangan iterasi sebanyak N (Menggunakan **repeat(N)**).
- perulangan kondisi (Menggunakan **repeatWhile(Kondisi)**).

Contohnya:
```c++
// Melakukan perulangan sebanyak 10 kali
repeat(10)
{
    forward
}

// Melakukan perulangan dengan kondisi yang diketahui
repeat()
{
    if (Kondisi)
    {
        break
    }
}

repeatWhile(frontIsClear)
{
    forward
}
```

## Function
Dalam pemrograman, Fungsi adalah blok kode/instruksi yang digunakan untuk melakukan tugas tertentu atau operasi tertentu. Fungsi dapat digunakan/dipanggil kembali dari program yang memungkinkan.

Sesuai yang ada pada definisi, Jika kode kita terprediksi akan selalu digunakan lebih baik "bungkus" beberapa intruksi tersebut menjadi sebuah function sehingga kita menerapkan kembali prinsip DRY alias tidak perlu menuliskan kembali instruksi yang sama.

Contohnya:
```c++
procedure TurnAround()
{
    repeat(2)
    {
        right
    }

    forward
}

// Memanggil fungsi untuk melakukan 360 dan kembali ke posisi semula
TurnAround()
TurnAround()
```