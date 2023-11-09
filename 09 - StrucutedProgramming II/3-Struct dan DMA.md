# 9.3 Struct dan DMA
## Pointer Pada Struct

Dalam prakteknya, umumnya variabel dengan tipe data struct jika dimasukkan sebagai salah satu argumen dalam fungsi adalah dalam bentuk **pointer**. Mengapa? Karena teknik tersebut mencegah terjadinya penyalinan obyek yang mana membuat ruang penyimpanan (memori) tidak efisien. Dengan demikian, kita lebih memilih untuk mengambil referensi (pointer) suatu obyek kemudian mengaksesnya daripada mengambil salinan dari obyek yang sudah ada yang mana membuat memori menjadi lebih boros, apalagi jika ukuran struct besar (terdapat banyak member dengan ukuran yang besar pula). Berikut adalah perbandingannya:
```c
/* Mengambil referensi (pointer) suatu obyek */
void print_weapon(const struct Weapon *wpn) {
    /* Akses member variable menggunakan -> jika pointer */
    /* Total memori terpakai dalam scope ini: sesuai dengan ukuran pointer `wpn` (4 atau 8 bytes tergantung CPU masing-masing) */
    printf("Weapon name: %s\n", wpn->name);
    printf(" Price: $%d\n", wpn->price);
    printf(" Damage: %d%%\n", wpn->damage);
    printf(" Rounds: %d\n", wpn->rounds);
}
```
```c
/* Mengambil salinan suatu obyek */
void print_weapon(struct Weapon wpn) {
    /* Akses member variable menggunakan . jika bukan pointer */
    /* Total memori terpakai dalam scope ini: sesuai dengan ukuran `wpn` (sekitar 62 bytes menurut ukuran `struct Weapon`) */
    printf("Weapon name: %s\n", wpn.name);
    printf(" Price: $%d\n", wpn.price);
    printf(" Damage: %d%%\n", wpn.damage);
    printf(" Rounds: %d\n", wpn.rounds);
}
```

**Pass By Reference - Read/Write Access:**
```c
void upgrade_weapon(struct Weapon *wpn) {
    /* Pointer `wpn` tidak read-only (const) sehingga nilai yang terkandung di dalamnya dapat dimanipulasi */
    wpn->damage = wpn->damage + 10; /* Tambah damage sebesar 10 */
}

int main() {
    struct Weapon deagle = {"Desert Eagle", 750, 35, 7};

    printf("Damage sebelum diupgrade: %d\n", deagle.damage);
    upgrade_weapon(&deagle); /* Pass by reference */
    printf("Damage setelah diupgrade: %d\n", deagle.damage);

    return 0;
}

/*
Output:

Damage sebelum diupgrade: 35
Damage setelah diupgrade: 45
*/
```

**Pass By Reference - Read Only Access:**
```c
void print_weapon(const struct Weapon *wpn) {
    /* Ingat bahwa `wpn` hanya bisa dibaca saja (read-only) karena pointer bertipe `const` */
    printf("Weapon name: %s\n", wpn->name);
    printf(" Price: $%d\n", wpn->price);
    printf(" Damage: %d%%\n", wpn->damage);
    printf(" Rounds: %d\n", wpn->rounds);
}

int main() {
    struct Weapon deagle = {"Desert Eagle", 750, 35, 7};

    print_weapon(&deagle); /* Pass by reference (read-only) */

    return 0;
}

/*
Output:

Weapon name: Desert Eagle
 Price: $750
 Damage: 35%
 Rounds: 7
*/
```

## Dynamic Memory Allocation:
Pada DMA, kita telah mengenal fungsi malloc, calloc, realloc untuk mengalokasikan suatu objek ke heap memory atau dynamic memory dan free untuk medealokasikan dari heap memory. Sehingga pada DMA pada struct, kita juga tidak jauh-jauh dari fungsi tersebut.

- Membuat Satu objek:
```c
Weapon *deagle = (Weapon*)malloc(sizeof(Weapon));
strcpy(deagle->name, "Desert Eagle");
deagle->price = 750;
deagle->damage = 35;
deagle->rounds = 7;

print_weapon(deagle); /* Pass by reference */
```

- Implementasi dalam array (lebih dari satu obyek):
```c
Weapon *weapon_list;
int weapon_count = 2;

weapon_list = (Weapon*)malloc(weapon_count * sizeof(Weapon));

strcpy(weapon_list[0].name, "Desert Eagle");
weapon_list[0].price = 750;
weapon_list[0].damage = 35;
weapon_list[0].rounds = 7;

strcpy(weapon_list[1].name, "M4A1");
weapon_list[1].price = 3100;
weapon_list[1].damage = 20;
weapon_list[1].rounds = 30;

print_weapons(weapon_list, weapon_count); /* Masukkan array (otomatis pass by reference) */
```
### Nullpointer checker
Sebelum kita melakukan apapun pada pointer kita, lebih baiknya jika kita melakukan validasi terlebih dahulu. Karena ingat! Jika kita mengakses pointer yang NULL maka program akan melakukan **undefined behavior** yang nantinya menyebabkan program crash atau hal lainnya.

Untuk melakukan pengecekan, kita dapat dengan mudah menggunakan **if statement**

```c
void print_weapon(const struct Weapon *wpn) {
    if (!wpn) /* Ini berarti wpn tidak valid */
    {
        // Code lainnya
    }

    if (wpn) /* Ini berarti wpn valid */
    {

    }

    // Code lainnya
}
```

### Menghapus objek:
Untuk menghapus sebuah objek pada C, kita dapat menggunakan fungsi free.
Tidak cukup hanya itu, kita juga perlu untuk mengubah pointer yang menunjuk pada objek tadi menjadi NULL sehingga tidak ada yang namanya ***dangling pointer***.

Berikut merupakan contoh kodenya:
```c
free(deagle);
deagle = NULL;
```

Dan jika kita ingin menghapus objek tersebut di dalam fungsi, maka kita harus memberi referensi dari pointer tersebut. Contohnya:

```c
void HapusSenjata(Weapon** /* Perhatikan di sini, terdapat dua bintang */ weapon)
{
    free(*Weapon);
    *Weapon = NULL;
}

// Memanggil HapusSenjata
HapusSenjata(&deagle);
```

Ini berguna untuk memastikan variabel deagle yang ada di fungsi **main** tersebut akan berubah "penunjuknya" yang sebelumnya menunjuk deagle yang ada di *heap memory* sekarang sudah tidak menunjuk apa-apa lagi karena memang deagle sudah terhapus.
