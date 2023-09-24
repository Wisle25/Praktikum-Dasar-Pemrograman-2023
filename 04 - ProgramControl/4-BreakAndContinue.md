[< Materi Sebelumnya (Perulangan menggunakan "do...while")](3-PerulanganMenggunakanDoWhile.md)
# 3.4 - Break and Continue

## Break

Break digunakan untuk keluar/berhenti dari suatu perulangan sebelum saatnya perulangan tersebut selesai. Break dapat digunakan pada semua jenis perulangan (for, while, do...while) dan juga switch case.
```c
    int i = 0;

    while(i < 10) 
    {
        printf("Saya yang ke-%d\n", i);
        i++;
        if(i==6) break;
    }
```

Output
```
    Saya yang ke-0
    Saya yang ke-1
    Saya yang ke-2
    Saya yang ke-3
    Saya yang ke-4
    Saya yang ke-5
    Saya yang ke-6
```

## Continue

Continue digunakan untuk melakukan skip atau melompati suatu iterasi dan melanjutkan ke iterasi selanjutnya.
```c
    int i = 0;
    while(i<10) 
    {
        i++;
        if(i==6) continue;

        // Saat I = 6, Instruksi di bawah tidak akan di eksekusi
        printf("perulangan ke %d kali\n",i);
    }
```

Output
```
    perulangan ke 0 kali
    perulangan ke 1 kali
    perulangan ke 2 kali
    perulangan ke 3 kali
    perulangan ke 4 kali
    perulangan ke 5 kali
    perulangan ke 7 kali
    perulangan ke 8 kali
    perulangan ke 9 kali 
```
