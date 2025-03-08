
# 📖 Daftar Fungsi dalam PDF Ini

Dokumen ini berisi berbagai fungsi dalam PHP yang dapat digunakan untuk berbagai keperluan. Setiap fungsi telah disusun secara rapi dan disertai dengan penjelasan sintaks agar mudah dipahami.

## 📌 Daftar Isi

0. [🎤 Handling Terminal Input in PHP](#-handling-terminal-input-in-php)
1. [📌 Penjumlahan Function](#-penjumlahan-function)
2. [🔠 Hitung Jumlah Karakter yang Sama](#-hitung-jumlah-karakter-yang-sama)
3. [📝 Custom Format Array](#-custom-format-array)
4. [📌 Pisah Angka Genap & Ganjil dalam Array](#-pisah-angka-genap--ganjil-dalam-array)
5. [🍽️ Menambahkan List Menu Makanan](#-menambahkan-list-menu-makanan)
6. [🍽️ Mengatur Harga Menu](#-mengatur-harga-menu)
7. [🍽 Order Menu](#-order-menu)
8. [📌 Cek Umur & Hari Lahir](#-cek-umur--hari-lahir)
9. [🎂 Cek Berapa Bulan & Hari Lagi Ultah Serta Hari Ultahnya](#-cek-berapa-bulan--hari-lagi-ultah-serta-hari-ultahnya)
10. [⏰ Cek Waktu Antar Negara](#-cek-waktu-antar-negara)
11. [🏷️ Cek Harga Setelah Diskon](#-cek-harga-setelah-diskon)
12. [💰 Currency Converter Function in PHP](#-currency-converter-function-in-php)

---
---
## 
---
---

# 🎤 Handling Terminal Input in PHP

## 📌 Deskripsi
Dalam pengembangan aplikasi berbasis **CLI (Command Line Interface)**, sering kali kita perlu menangani input yang diberikan oleh pengguna melalui terminal. PHP menyediakan metode bawaan untuk membaca input dari terminal menggunakan **fgets(STDIN)**. Artikel ini akan membahas cara kerja dan implementasinya dalam berbagai skenario.

## 🎯 Tujuan Pembelajaran
- Memahami cara menerima input dari terminal di PHP.
- Menggunakan `fgets(STDIN)` untuk membaca input pengguna.
- Mengelola data input agar dapat digunakan dalam program.

## 📝 Implementasi Kode
Berikut adalah contoh implementasi sederhana untuk membaca input melalui terminal:

```php
<?php
// Menampilkan pesan ke pengguna
echo "Masukkan nama Anda: ";

// Membaca input dari terminal
$nama = trim(fgets(STDIN));

echo "Halo, $nama! Selamat datang.\n";
?>
```

## 🔍 Penjelasan Kode
1. **Menggunakan `echo`**:
   - `echo "Masukkan nama Anda: ";` digunakan untuk menampilkan instruksi kepada pengguna.

2. **Membaca Input dengan `fgets(STDIN)`**:
   - `fgets(STDIN)` membaca satu baris input dari terminal.
   - `trim()` digunakan untuk menghapus karakter newline (`\n`) atau spasi tambahan.

3. **Menampilkan Output**:
   - Setelah input dimasukkan, program akan mencetak pesan sapaan dengan nama yang dimasukkan.

## 📌 Contoh Output
```
Masukkan nama Anda: Alex
Halo, Alex! Selamat datang.
```

## 📝 Catatan Tambahan
- Pastikan Anda selalu menggunakan `trim()` saat membaca input untuk menghindari karakter ekstra yang dapat menyebabkan error.
- Jika ingin membaca angka, gunakan `(int) fgets(STDIN)` agar hasilnya langsung dikonversi ke integer.

---
---
## 
---
---

# 📌 Penjumlahan Function

---

## 📖 Deskripsi
Fungsi `JumlahAngka` adalah fungsi  yang menerima beberapa digit dalam angka bulat dan mengembalikan output berupa jumlah dari setiap digitnya berdasarkan operator yang diberikan.

---

## 🚀 Cara Kerja
Fungsi ini mengolah angka bulat dengan operator matematika dasar seperti:
- `+` untuk penjumlahan digit
- `-` untuk pengurangan digit
- `*` untuk perkalian digit

Jika operator tidak valid, maka akan menampilkan pesan error.

---

## 📝 Contoh Soal
**Essay:**
> Buatlah fungsi yang menerima beberapa digit dalam angka bulat yang memberikan output jumlah dari total setiap digitnya.

---

**Contoh Input & Output:**
```
172638781627386123 = 1 + 7 + 2 + 6 + ... = ???
```

---

## 💻 Implementasi Kode
```php
function jumlahAngka()
{
    echo "Masukkan angka: ";
    $value = trim(fgets(STDIN));

    // Validasi input angka harus berupa digit
    if (!ctype_digit($value)) {
        return "Error: Input harus berupa angka.\n";
    }

    echo "Masukkan operator (+, -, *): ";
    $operator = trim(fgets(STDIN));

    // Validasi input operator
    if (!in_array($operator, ['+', '-', '*'])) {
        return "Error: Operator tidak valid.\n";
    }

    $angka = strval($value);
    $digits = [];
    $total = ($operator === "-") ? intval($angka[0]) : ($operator === "*" ? 1 : 0);

    for ($i = 0; $i < strlen($angka); $i++) {
        $digit = intval($angka[$i]);
        $digits[] = $digit;

        switch ($operator) {
            case "+":
                $total += $digit;
                break;
            case "-":
                if ($i > 0) {
                    $total -= $digit;
                }
                break;
            case "*":
                $total *= $digit;
                break;
        }
    }

    $digitsString = implode(" $operator ", $digits);
    return "Digit yang diolah: " . $digitsString . "\nHasil: " . $total . "\n";
}

// Eksekusi fungsi
echo jumlahAngka();
```
---


## 📌 Penjelasan Kode
1. **Konversi Angka ke String**: Supaya bisa diakses per digit.
2. **Inisialisasi Total Sesuai Operator**:
   - `+` dimulai dari `0`.
   - `-` dimulai dari digit pertama angka.
   - `*` dimulai dari `1`.
3. **Looping Setiap Digit**:
   - Menjumlahkan (`+`), mengurangkan (`-`), atau mengalikan (`*`).
4. **Menggabungkan Hasil dalam String** untuk output yang lebih jelas.

---

## ✅ Contoh Hasil Output
```
Digit yang diolah: 5 - 5 - 5
Hasil: -5

Digit yang diolah: 5 + 2 + 3 + 4 + 5 + 5
Hasil: 24

Digit yang diolah: 5 * 2 * 3 * 6 * 2 * 3 * 5 * 5
Hasil: 13500
```

---

## 🎯 Kesimpulan
Fungsi ini membantu memproses angka berdasarkan operator matematika secara dinamis. Bisa digunakan untuk operasi berbasis digit pada angka besar dalam berbagai kasus penggunaan.

---
---
## 
---
---

# 🔠 Hitung Jumlah Karakter yang Sama

## 📖 Deskripsi
Fungsi `hitungKarakterSama` adalah sebuah fungsi  yang digunakan untuk menghitung frekuensi kemunculan setiap karakter dalam sebuah string. Hasilnya akan ditampilkan dalam format yang terstruktur dan mudah dibaca.

## ⚙️ Cara Kerja
1. **Mengonversi string menjadi huruf kecil** → Agar perhitungan tidak membedakan huruf kapital dan non-kapital.
2. **Menghitung frekuensi setiap karakter** → Menggunakan fungsi `count_chars`.
3. **Memformat output** → Menampilkan setiap karakter dalam bentuk `[karakter] jumlah_x`.

## 📝 Contoh Soal
**Essay:**
> Buatlah fungsi yang menerima sebuah string dan menghitung jumlah karakter yang sama.

### 📌 Contoh Input & Output
```bash
Input: "aku lapar banget nieh"
Output: [a] 3x, [k] 1x, [u] 1x, [l] 1x, [p] 1x, [r] 1x, [b] 1x, [n] 2x, [g] 1x, [e] 2x, [t] 1x, [i] 1x, [h] 1x
```

## 💻 Implementasi Kode
```php
function hitungKarakterSama($string) {
    $string = strtolower($string); // Konversi string ke huruf kecil
    $frekuensi = count_chars($string, 1); // Hitung jumlah kemunculan setiap karakter
    $hasil = [];

    foreach ($frekuensi as $asci => $jumlahKemunculanChar) {
        if ($jumlahKemunculanChar > 0) {
            $hasil[] = "[".chr($asci)."] $jumlahKemunculanChar"."x";
        }
    }
    return implode(", ", $hasil);
}

// Contoh penggunaan
$teks = "aku lapar banget nieh";
$hasil = hitungKarakterSama($teks);

echo "Dalam kata => ". $teks . "\n";
echo "Karakter " . $hasil ."\n";
```

## 🧐 Penjelasan Kode
1. **Mengonversi string ke huruf kecil**
   - Menggunakan `strtolower($string)` untuk memastikan perhitungan karakter tidak membedakan antara huruf besar dan kecil.
2. **Menggunakan `count_chars($string, 1)`**
   - Fungsi ini menghitung jumlah kemunculan setiap karakter dalam bentuk array ASCII.
3. **Looping untuk memformat output**
   - Setiap karakter dikonversi kembali menggunakan `chr($asci)` lalu ditampilkan dalam format `[karakter] jumlah_x`.

## 🎯 Contoh Hasil Output
```bash
Dalam kata => aku lapar banget nieh
Karakter [a] 3x, [k] 1x, [u] 1x, [l] 1x, [p] 1x, [r] 1x, [b] 1x, [n] 2x, [g] 1x, [e] 2x, [t] 1x, [i] 1x, [h] 1x
```

---
---
## 
---
---

# 📝 Custom Format Array 

## 📌 Deskripsi
Fungsi `formatArray` digunakan untuk menampilkan elemen-elemen dalam array dengan format yang lebih rapi. Fungsi ini mendukung baik array **indeks** maupun **asosiatif**, serta memungkinkan penambahan **prefix** dan **suffix** pada setiap nilai yang ditampilkan.

---

## 🚀 Sintaks
```php
function formatArray(array $array, string $prefix = '', string $suffix = '', bool $useKey = false): void {
    $counter = 1;
    foreach ($array as $key => $value) {
        $index = $useKey ? $key : $counter++;
        echo "$index. $prefix$value$suffix\n";
    }
}
```

---

## 🛠️ Penjelasan Sintaks

| Sintaks | Penjelasan |
|---------|-----------|
| `array $array` | Parameter untuk menerima array input, baik **indeks** maupun **asosiatif**. |
| `string $prefix` | String tambahan yang ditambahkan sebelum nilai array (opsional). |
| `string $suffix` | String tambahan yang ditambahkan setelah nilai array (opsional). |
| `bool $useKey` | Jika `true`, maka akan menggunakan kunci array sebagai indeks; jika `false`, akan menggunakan angka berurutan. |
| `foreach ($array as $key => $value)` | Melakukan iterasi pada setiap elemen dalam array. |
| `$index = $useKey ? $key : $counter++` | Menentukan indeks berdasarkan pilihan pengguna. |
| `echo "$index. $prefix$value$suffix\n";` | Menampilkan hasil akhir dari array dalam format yang rapi. |

---

## 🎯 Contoh Penggunaan

### ✅ Dengan Array Berindeks
```php
$prices = ["10.000", "20.000", "30.000"];
formatArray($prices, "Rp.", " IDR");
```
**Output:**
```
1. Rp.10.000 IDR
2. Rp.20.000 IDR
3. Rp.30.000 IDR
```

### ✅ Dengan Array Asosiatif
```php
$menu = [
    "Nasi Goreng" => "25.000",
    "Mie Goreng" => "20.000",
    "Sate Ayam" => "35.000"
];
formatArray($menu, "Rp.", " IDR", true);
```
**Output:**
```
Nasi Goreng. Rp.25.000 IDR
Mie Goreng. Rp.20.000 IDR
Sate Ayam. Rp.35.000 IDR
```

---

## 📌 Catatan
- Parameter **prefix** dan **suffix** bersifat opsional.
- Jika `useKey = false`, indeks akan berbasis angka urut.
- Cocok digunakan untuk format tampilan menu, daftar harga, atau struktur data lainnya yang membutuhkan format rapi.

---
---
## 
---
---

# 📌 Pisah Angka Genap & Ganjil dalam Array

## 📖 Deskripsi
Fungsi ini bertujuan untuk memisahkan angka genap dan ganjil dari sebuah array menjadi dua array yang berbeda. Angka genap akan dimasukkan ke dalam array `Genap`, sedangkan angka ganjil akan dimasukkan ke dalam array `Ganjil`.

## 🚀 Implementasi Kode

```php
<?php
function PisahArrayGenapGanjil(array $arr) {
    $arrGenap = [];
    $arrGanjil = [];

    for ($i = 0; $i < count($arr); $i++) {
        $valueOfArray = $arr[$i];
        if ($valueOfArray % 2 == 0) {
            $arrGenap[] = $valueOfArray;
        } else {
            $arrGanjil[] = $valueOfArray;
        }
    }

    return ["Genap" => $arrGenap, "Ganjil" => $arrGanjil];
}

$data = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20];

print_r(PisahArrayGenapGanjil($data));
```

## 🔍 Penjelasan Kode

1. **Mendefinisikan Fungsi**
    ```php
    function PisahArrayGenapGanjil(array $arr) {
    ```
    Fungsi `PisahArrayGenapGanjil` menerima satu parameter berupa array `$arr`.

2. **Inisialisasi Dua Array Kosong**
    ```php
    $arrGenap = [];
    $arrGanjil = [];
    ```
    Dua array ini akan digunakan untuk menyimpan angka genap dan ganjil.

3. **Melakukan Iterasi pada Array Input**
    ```php
    for ($i = 0; $i < count($arr); $i++) {
    ```
    Looping dilakukan dari indeks `0` hingga `count($arr) - 1` untuk mengakses setiap elemen.

4. **Mengambil Nilai Elemen Saat Ini**
    ```php
    $valueOfArray = $arr[$i];
    ```
    Variabel `$valueOfArray` menyimpan nilai dari elemen array saat ini.

5. **Memeriksa Bilangan Genap atau Ganjil**
    ```php
    if ($valueOfArray % 2 == 0) {
        $arrGenap[] = $valueOfArray;
    } else {
        $arrGanjil[] = $valueOfArray;
    }
    ```
    - Jika hasil modulus (`% 2`) adalah `0`, berarti bilangan tersebut **genap** dan dimasukkan ke `$arrGenap`.
    - Jika tidak, berarti **ganjil** dan dimasukkan ke `$arrGanjil`.

6. **Mengembalikan Hasil dalam Bentuk Array Asosiatif**
    ```php
    return ["Genap" => $arrGenap, "Ganjil" => $arrGanjil];
    ```
    Fungsi mengembalikan array asosiatif dengan dua kunci: "Genap" dan "Ganjil".

7. **Menjalankan Fungsi dengan Data Uji**
    ```php
    $data = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20];
    print_r(PisahArrayGenapGanjil($data));
    ```
    - `print_r` digunakan untuk mencetak hasil pemisahan array dalam format yang mudah dibaca.

## 🛠️ Perbaikan Kode
Kode asli memiliki bug kecil pada kondisi perulangan:
```php
for($i = 0; $i <= count($arr); $i++) {
```
Seharusnya:
```php
for($i = 0; $i < count($arr); $i++) {
```
Karena `count($arr)` adalah jumlah elemen dalam array, perulangan harus berhenti di indeks terakhir (`count($arr) - 1`), bukan lebih dari itu.

## 📌 Contoh Output
```bash
Array
(
    [Genap] => Array
        (
            [0] => 2
            [1] => 4
            [2] => 6
            [3] => 8
            [4] => 10
            [5] => 12
            [6] => 14
            [7] => 16
            [8] => 18
            [9] => 20
        )

    [Ganjil] => Array
        (
            [0] => 1
            [1] => 3
            [2] => 5
            [3] => 7
            [4] => 9
            [5] => 11
            [6] => 13
            [7] => 15
            [8] => 17
            [9] => 19
        )
)
```

## 🎯 Kesimpulan
- Kode ini berhasil memisahkan bilangan genap dan ganjil dalam array.
- Perbaikan pada kondisi perulangan (`<=` diganti dengan `<`) agar tidak menyebabkan error.
- Output ditampilkan dalam format array asosiatif dengan dua kategori: **Genap** dan **Ganjil**.

---
---
## 
---
---

# 🍽️ Menambahkan List Menu Makanan

## 📌 Deskripsi
Dalam latihan ini, kita akan membuat sebuah **function** untuk menambahkan list menu makanan ke dalam sebuah array. Function ini harus mampu menerima input berupa nama makanan dan menyimpannya ke dalam daftar menu.

---

## 🛠️ Sintaks Dasar

, sebuah function dideklarasikan menggunakan kata kunci `function`, diikuti oleh nama function, tanda kurung `()` untuk parameter, dan blok kode `{}` untuk menampung eksekusi logika.

```php
function nama_function() {
    // Kode eksekusi
}
```

📌 **Penjelasan:**
- `function` → Kata kunci untuk mendeklarasikan function.
- `nama_function` → Nama function yang bisa kita tentukan sesuai kebutuhan.
- `{}` → Blok kode tempat kita menulis logika function.

---

## ✍️ Implementasi
Berikut adalah implementasi function untuk menambahkan list menu makanan:

```php
<?php

// Inisialisasi array untuk menyimpan menu makanan
$menu_makanan = [];

// Function untuk menambahkan menu makanan ke dalam array
function tambahMenu(&$menu, $nama_makanan) {
    $menu[] = $nama_makanan;
    echo "✅ Menu '$nama_makanan' berhasil ditambahkan!\n";
}

// Contoh penggunaan function
tambahMenu($menu_makanan, "Nasi Goreng");
tambahMenu($menu_makanan, "Mie Ayam");
tambahMenu($menu_makanan, "Sate Ayam");

// Menampilkan daftar menu setelah penambahan
print_r($menu_makanan);
```

---

## 🔍 Penjelasan Kode

1. **Inisialisasi Array**
   ```php
   $menu_makanan = [];
   ```
   - Membuat array kosong untuk menyimpan daftar menu makanan.

2. **Membuat Function `tambahMenu()`**
   ```php
   function tambahMenu(&$menu, $nama_makanan) {
       $menu[] = $nama_makanan;
       echo "✅ Menu '$nama_makanan' berhasil ditambahkan!\n";
   }
   ```
   - `&$menu` → Menggunakan **reference** (`&`) agar array `$menu_makanan` dapat diubah langsung.
   - `$menu[] = $nama_makanan;` → Menambahkan item ke dalam array.
   - `echo` → Menampilkan pesan konfirmasi.

3. **Memanggil Function**
   ```php
   tambahMenu($menu_makanan, "Nasi Goreng");
   tambahMenu($menu_makanan, "Mie Ayam");
   tambahMenu($menu_makanan, "Sate Ayam");
   ```
   - Menjalankan function dengan berbagai input makanan.

4. **Menampilkan Daftar Menu**
   ```php
   print_r($menu_makanan);
   ```
   - Menampilkan seluruh menu makanan yang telah ditambahkan.

---

## 🏆 Output Program
Setelah dijalankan, hasilnya:

```
✅ Menu 'Nasi Goreng' berhasil ditambahkan!
✅ Menu 'Mie Ayam' berhasil ditambahkan!
✅ Menu 'Sate Ayam' berhasil ditambahkan!
Array
(
    [0] => Nasi Goreng
    [1] => Mie Ayam
    [2] => Sate Ayam
)
```

---

## 📚 Kesimpulan
Function `tambahMenu()` memungkinkan kita menambahkan makanan ke dalam daftar menu dengan mudah. Dengan pendekatan ini, daftar makanan dapat dikelola secara dinamis dan fleksibel.

🚀 **Selamat mencoba!**

---
---
## 
---
---

# 🍽️ Mengatur Harga Menu 

## 📌 Deskripsi
Dalam tantangan ini, kita diminta untuk membuat sebuah **fungsi** yang dapat **menetapkan atau mengubah harga pada menu** yang tersedia. Fungsi ini akan menerima daftar menu dan harga yang diperbarui.

## 🎯 Tujuan Pembelajaran
- Memahami konsep **array associative** 
- Menggunakan **function** untuk manipulasi data
- Mempraktikkan cara **mengubah nilai dalam array**

---

## 🔥 Implementasi
Berikut adalah kode PHP yang digunakan untuk menyelesaikan tantangan ini:

```php
<?php
// Fungsi untuk mengubah atau menetapkan harga menu
function aturHargaMenu(&$menu, $item, $hargaBaru) {
    if (array_key_exists($item, $menu)) {
        echo "Harga "$item" diperbarui dari ".$menu[$item]." ke $hargaBaru.\n";
    } else {
        echo "Menambahkan item baru: $item dengan harga $hargaBaru.\n";
    }
    
    // Tetapkan atau ubah harga menu
    $menu[$item] = $hargaBaru;
}

// Contoh daftar menu
$menuRestoran = [
    "Nasi Goreng" => 25000,
    "Mie Ayam" => 20000,
    "Es Teh" => 5000
];

// Menampilkan menu awal
print_r($menuRestoran);

// Mengubah harga menu yang sudah ada
aturHargaMenu($menuRestoran, "Nasi Goreng", 27000);

// Menambahkan menu baru
aturHargaMenu($menuRestoran, "Ayam Geprek", 30000);

// Menampilkan menu setelah perubahan
print_r($menuRestoran);
?>
```

---

## 🛠️ Penjelasan Kode

1. **Fungsi `aturHargaMenu(&$menu, $item, $hargaBaru)`**
   - Parameter `$menu` diterima sebagai **referensi** (`&$menu`) agar perubahan langsung diterapkan ke array asli.
   - Mengecek apakah menu sudah ada di array menggunakan `array_key_exists($item, $menu)`.
   - Jika ada, menampilkan pesan bahwa harga diperbarui.
   - Jika tidak ada, menampilkan pesan bahwa item baru ditambahkan.
   - Mengupdate atau menetapkan harga pada array menu.

2. **Contoh Data**
   - `$menuRestoran` menyimpan daftar menu awal dengan harga.
   - Fungsi **dipanggil dua kali** untuk:
     - **Mengubah harga** "Nasi Goreng" dari 25.000 ke 27.000
     - **Menambahkan menu baru** "Ayam Geprek" dengan harga 30.000

3. **Hasil Eksekusi**
   ```bash
   Array
   (
       [Nasi Goreng] => 25000
       [Mie Ayam] => 20000
       [Es Teh] => 5000
   )

   Harga "Nasi Goreng" diperbarui dari 25000 ke 27000.

   Menambahkan item baru: Ayam Geprek dengan harga 30000.

   Array
   (
       [Nasi Goreng] => 27000
       [Mie Ayam] => 20000
       [Es Teh] => 5000
       [Ayam Geprek] => 30000
   )

   ```

---

## ✅ Kesimpulan
- **Menggunakan array associative** untuk menyimpan daftar menu dan harga.
- **Memanfaatkan fungsi dengan parameter referensi** (`&$menu`) untuk mengubah nilai langsung.
- **Menggunakan `array_key_exists()`** untuk menentukan apakah item perlu diperbarui atau ditambahkan.
- **Output yang jelas** untuk memahami perubahan yang terjadi dalam daftar menu.

---
---
## 
---
---

# 🍽 Order Menu

## 📌 Deskripsi

Program ini merupakan implementasi dari sebuah **function** dalam **PHP** yang memungkinkan pengguna untuk memilih beberapa menu makanan atau minuman. Setelah itu, program akan menampilkan daftar pesanan dengan total harga yang dihitung secara otomatis. ✨

---

## 🛠 Teknologi yang Digunakan

- PHP (Hypertext Preprocessor) 🐘
- CLI (Command Line Interface) 💻

---

## 📚 Cara Kerja

1. Program menyediakan daftar menu beserta harganya.
2. Pengguna dapat memilih beberapa menu dengan memasukkan nomor menu.
3. Program akan menghitung total harga berdasarkan pesanan pengguna.
4. Hasil ditampilkan dengan format yang rapi dan mudah dibaca.

---

## 🏢 Struktur Kode

```php
<?php
function orderMenu() {
    // Daftar menu dengan harga
    $menu = [
        1 => ['name' => 'Nasi Goreng', 'price' => 20000],
        2 => ['name' => 'Mie Goreng', 'price' => 18000],
        3 => ['name' => 'Ayam Bakar', 'price' => 25000],
        4 => ['name' => 'Es Teh', 'price' => 5000],
        5 => ['name' => 'Jus Jeruk', 'price' => 8000],
    ];

    echo "\n\ud83d\udccb Daftar Menu:\n";
    foreach ($menu as $number => $item) {
        echo "{$number}. {$item['name']} - Rp. " . number_format($item['price'], 0, ',', '.') . "\n";
    }
    
    echo "\n\ud83d\uded2 Masukkan nomor menu yang ingin dipesan (pisahkan dengan koma): ";
    $input = trim(fgets(STDIN));
    $selectedNumbers = explode(',', $input);
    
    $total = 0;
    echo "\n\ud83d\udcdd Pesanan Anda:\n";
    foreach ($selectedNumbers as $number) {
        $number = trim($number);
        if (isset($menu[$number])) {
            echo "\u2705 {$menu[$number]['name']} - Rp. " . number_format($menu[$number]['price'], 0, ',', '.') . "\n";
            $total += $menu[$number]['price'];
        } else {
            echo "\u274c Nomor menu '{$number}' tidak ditemukan!\n";
        }
    }
    
    echo "\n\ud83d\udcb0 Total Harga: Rp. " . number_format($total, 0, ',', '.') . "\n";
}

// Eksekusi function
orderMenu();
```

---

## 🔍 Penjelasan Kode

1. **Mendefinisikan Function:**
   ```php
   function orderMenu() {
   ```
   - Fungsi `orderMenu()` dibuat untuk menangani pemilihan menu dan menghitung total harga.

2. **Menampilkan Daftar Menu:**
   ```php
   $menu = [
       1 => ['name' => 'Nasi Goreng', 'price' => 20000],
       2 => ['name' => 'Mie Goreng', 'price' => 18000],
       3 => ['name' => 'Ayam Bakar', 'price' => 25000],
       4 => ['name' => 'Es Teh', 'price' => 5000],
       5 => ['name' => 'Jus Jeruk', 'price' => 8000],
   ];
   ```
   - Array asosiatif `$menu` menyimpan daftar makanan/minuman beserta harganya dengan nomor urut.

3. **Input dari Pengguna:**
   ```php
   echo "\ud83d\uded2 Masukkan nomor menu yang ingin dipesan (pisahkan dengan koma): ";
   $input = trim(fgets(STDIN));
   ```
   - Pengguna memasukkan nomor menu yang ingin dipesan, dipisahkan dengan koma.

4. **Memproses Pesanan:**
   ```php
   $selectedNumbers = explode(',', $input);
   ```
   - Input pengguna dipecah menjadi array berdasarkan koma sebagai pemisah.

5. **Menampilkan Pesanan & Menghitung Total:**
   ```php
   if (isset($menu[$number])) {
       echo "\u2705 {$menu[$number]['name']} - Rp. " . number_format($menu[$number]['price'], 0, ',', '.') . "\n";
       $total += $menu[$number]['price'];
   } else {
       echo "\u274c Nomor menu '{$number}' tidak ditemukan!\n";
   }
   ```
   - Program mengecek apakah nomor menu ada dalam daftar. Jika ya, ditampilkan dengan harga dan dihitung totalnya. Jika tidak, muncul peringatan.

6. **Menampilkan Total Harga:**
   ```php
   echo "\ud83d\udcb0 Total Harga: Rp. " . number_format($total, 0, ',', '.') . "\n";
   ```
   - Menampilkan total harga pesanan dalam format yang rapi.

---

## 💌 Contoh Eksekusi

### 📜 Input:
```
📋 Daftar Menu:
1. Nasi Goreng - Rp. 20.000
2. Mie Goreng - Rp. 18.000
3. Ayam Bakar - Rp. 25.000
4. Es Teh - Rp. 5.000
5. Jus Jeruk - Rp. 8.000

🛒 Masukkan nomor menu yang ingin dipesan (pisahkan dengan koma): 1, 5, 3
```

### ✅ Output:
```
📝 Pesanan Anda:
✅ Nasi Goreng - Rp. 20.000
✅ Jus Jeruk - Rp. 8.000
✅ Ayam Bakar - Rp. 25.000

💰 Total Harga: Rp. 53.000
```

---

## 🏆 Kesimpulan

- Program ini mempermudah pelanggan dalam memilih menu dan melihat total harga dengan format yang rapi. 🥇
- Menggunakan **array asosiatif** untuk menyimpan menu dengan harga.
- **Penggunaan `trim()`, `explode()`, dan `isset()`** untuk validasi input.
- **Menggunakan `number_format()`** untuk format harga yang lebih mudah dibaca.

---
---
## 
---
---

# 📌 Cek Umur & Hari Lahir

## 📝 Deskripsi
Buatlah sebuah function dalam PHP yang dapat menghitung umur seseorang berdasarkan tanggal lahir yang diberikan serta menentukan hari dalam minggu saat dia lahir.

---

## 📌 Cara Kerja
Function yang akan dibuat harus menerima input berupa tanggal lahir dalam format `YYYY-MM-DD`. Kemudian function akan:
1. Menghitung umur berdasarkan tahun saat ini.
2. Menentukan hari dalam minggu dari tanggal lahir tersebut.
3. Menampilkan hasil dalam format yang mudah dipahami.

---

## 📚 Contoh Eksekusi & Penjelasan Sintaks

```php
function cekUmurHariLahir($tanggal_lahir) {
    // Mengubah string tanggal menjadi objek DateTime
    $tglLahir = new DateTime($tanggal_lahir);
    $hariIni = new DateTime(); // Mendapatkan tanggal hari ini
    
    // Menghitung selisih tahun untuk mendapatkan umur
    $umur = $hariIni->diff($tglLahir)->y;
    
    // Menentukan hari lahir dalam bahasa Indonesia
    $hariLahir = $tglLahir->format('l');
    $daftarHari = [
        'Sunday' => 'Minggu',
        'Monday' => 'Senin',
        'Tuesday' => 'Selasa',
        'Wednesday' => 'Rabu',
        'Thursday' => 'Kamis',
        'Friday' => 'Jumat',
        'Saturday' => 'Sabtu'
    ];
    $hariLahirID = $daftarHari[$hariLahir];
    
    // Output hasil
    return "Umur Anda: $umur tahun, Anda lahir pada hari: $hariLahirID.";
}

// Contoh penggunaan
echo cekUmurHariLahir('2000-03-06');
```

---

## 🔍 Penjelasan Sintaks

- `new DateTime($tanggal_lahir);` → Mengubah string tanggal lahir menjadi objek `DateTime` untuk mempermudah perhitungan.
- `$hariIni->diff($tglLahir)->y;` → Menghitung selisih tahun antara tanggal lahir dan tanggal sekarang untuk mendapatkan umur.
- `$tglLahir->format('l');` → Mengambil nama hari dalam bahasa Inggris dari tanggal lahir.
- `array $daftarHari` → Digunakan untuk menerjemahkan nama hari dari bahasa Inggris ke bahasa Indonesia.
- `return "Umur Anda: $umur tahun, Anda lahir pada hari: $hariLahirID.";` → Mengembalikan hasil dalam format teks yang mudah dipahami.

---

## 🏆 Output Contoh

Jika input tanggal lahir adalah `2000-03-06`, output yang dihasilkan:
```
Umur Anda: 25 tahun, Anda lahir pada hari: Senin.
```

---

## 🚀 Kesimpulan
Dengan menggunakan function ini, kita dapat dengan mudah mengetahui umur seseorang serta hari dalam minggu saat ia lahir.
Cukup dengan memasukkan tanggal lahir dalam format `YYYY-MM-DD`, function akan melakukan perhitungan otomatis!

📌 **Coba sendiri dan eksperimen dengan berbagai tanggal lahir!** 🚀

---
---
## 
---
---

# 🎂 Cek Berapa Bulan & Hari Lagi Ultah Serta Hari Ultahnya

## 📌 Deskripsi
Buatlah sebuah function dalam PHP untuk menghitung:
1. Berapa bulan dan hari lagi hingga ulang tahun.
2. Hari apa ulang tahunnya jatuh.

Dengan memahami konsep manipulasi tanggal dalam PHP, kita bisa menyelesaikan soal ini dengan mudah.

---

## 🛠️ Implementasi
Berikut adalah implementasi fungsi dalam PHP:

```php
function cekUlangTahun($tanggal_lahir) {
    // Ambil tanggal saat ini
    $sekarang = new DateTime();
    
    // Ambil tanggal ulang tahun tahun ini
    $ulang_tahun = new DateTime(date('Y') . '-' . date('m-d', strtotime($tanggal_lahir)));
    
    // Jika ulang tahun sudah lewat di tahun ini, cek ulang tahun tahun depan
    if ($ulang_tahun < $sekarang) {
        $ulang_tahun->modify('+1 year');
    }
    
    // Hitung selisih waktu
    $selisih = $sekarang->diff($ulang_tahun);
    
    // Ambil nama hari ulang tahun
    $hari_ultah = $ulang_tahun->format('l');
    
    // Hasilkan output
    return "Ulang tahun dalam {$selisih->m} bulan dan {$selisih->d} hari. Jatuh pada hari: $hari_ultah.";
}

// Contoh Penggunaan
$tanggal_lahir = '2000-07-15'; // Format: YYYY-MM-DD
echo cekUlangTahun($tanggal_lahir);
```

---

## 📝 Penjelasan Sintaks

1. **Mengambil Tanggal Saat Ini**
   ```php
   $sekarang = new DateTime();
   ```
   - Menggunakan `DateTime()` untuk mendapatkan tanggal dan waktu saat ini.

2. **Menghitung Ulang Tahun Tahun Ini**
   ```php
   $ulang_tahun = new DateTime(date('Y') . '-' . date('m-d', strtotime($tanggal_lahir)));
   ```
   - Menggunakan `date('Y')` untuk mendapatkan tahun ini.
   - Menggunakan `date('m-d', strtotime($tanggal_lahir))` untuk mendapatkan bulan dan hari dari tanggal lahir.
   - Menggabungkan keduanya menjadi tanggal ulang tahun tahun ini.

3. **Memeriksa Jika Ulang Tahun Sudah Lewat**
   ```php
   if ($ulang_tahun < $sekarang) {
       $ulang_tahun->modify('+1 year');
   }
   ```
   - Jika ulang tahun sudah lewat tahun ini, maka tambahkan satu tahun ke tanggal ulang tahun.

4. **Menghitung Selisih Antara Tanggal Sekarang dan Ulang Tahun**
   ```php
   $selisih = $sekarang->diff($ulang_tahun);
   ```
   - `diff()` digunakan untuk mendapatkan selisih antara dua tanggal.

5. **Menentukan Hari Ulang Tahun**
   ```php
   $hari_ultah = $ulang_tahun->format('l');
   ```
   - `format('l')` digunakan untuk mendapatkan nama hari dalam bahasa Inggris (misalnya: Monday, Tuesday, dll.).

6. **Menghasilkan Output yang Mudah Dibaca**
   ```php
   return "Ulang tahun dalam {$selisih->m} bulan dan {$selisih->d} hari. Jatuh pada hari: $hari_ultah.";
   ```
   - Menggunakan interpolasi string untuk menyusun teks hasil.

---

## 🔥 Contoh Output
Jika hari ini adalah **6 Maret 2025** dan tanggal lahir **15 Juli 2000**, maka outputnya:
```plaintext
Ulang tahun dalam 4 bulan dan 9 hari. Jatuh pada hari: Tuesday.
```

---

## 📚 Kesimpulan
- Kita menggunakan **DateTime** untuk memanipulasi tanggal secara fleksibel.
- **diff()** sangat berguna untuk menghitung selisih antara dua tanggal.
- **format()** membantu mendapatkan informasi spesifik seperti nama hari ulang tahun.

---
---
## 
---
---

# ⏰ Cek Waktu Antar Negara

## 📌 Deskripsi
Program ini memungkinkan pengguna untuk membandingkan perbedaan waktu antara dua negara dengan menggunakan zona waktu masing-masing. Pengguna dapat memasukkan nama dua negara melalui terminal, dan program akan menampilkan waktu saat ini di kedua negara serta selisih waktunya dalam jam dan menit.

## 🚀 Implementasi

```php
<?php
function cekWaktu($negaraA, $negaraB) {
    // Array zona waktu beberapa negara yang didukung
    $zonaWaktu = [
        "Indonesia" => "Asia/Jakarta",
        "Jepang" => "Asia/Tokyo", 
        "Amerika" => "America/New_York",
        "Inggris" => "Europe/London",
        "Australia" => "Australia/Sydney",
        "India" => "Asia/Kolkata",
        "Jerman" => "Europe/Berlin",
        "Brazil" => "America/Sao_Paulo"
    ];

    // Meminta input pengguna dari terminal
    echo "Masukkan negara pertama: ";
    $negaraA = trim(fgets(STDIN)); // fgets(STDIN) digunakan untuk membaca input dari terminal, trim() menghapus spasi ekstra

    echo "Masukkan negara kedua: ";
    $negaraB = trim(fgets(STDIN)); // fgets(STDIN) digunakan untuk membaca input dari terminal, trim() menghapus spasi ekstra
    
    // Validasi apakah negara yang dimasukkan ada dalam daftar zona waktu
    if (!isset($zonaWaktu[$negaraA]) || !isset($zonaWaktu[$negaraB])) {
        return "Negara tidak ditemukan dalam daftar.";
    }
    
    // Mengambil waktu saat ini dari masing-masing zona waktu
    $waktuA = new DateTime("now", new DateTimeZone($zonaWaktu[$negaraA]));
    $waktuB = new DateTime("now", new DateTimeZone($zonaWaktu[$negaraB]));
    
    // Mendapatkan offset zona waktu dalam jam (konversi dari detik)
    $offsetA = $waktuA->getOffset() / 3600; // Mengambil offset waktu negara A dan mengonversinya ke jam
    $offsetB = $waktuB->getOffset() / 3600; // Mengambil offset waktu negara B dan mengonversinya ke jam
    
    // Menghitung selisih waktu absolut dalam jam dan menit
    $selisihJam = abs($offsetA - $offsetB); // Menghitung perbedaan offset dalam jam
    $selisihMenit = ($selisihJam - floor($selisihJam)) * 60; // Menghitung sisa menit dari selisih jam
    
    // Menentukan negara yang memiliki waktu lebih awal
    $lebihDulu = $waktuA < $waktuB ? $negaraA : $negaraB;
    
    // Format hasil dengan output yang lebih jelas
    return "🕒 Waktu di $negaraA: " . $waktuA->format("H:i:s") . "\n" . // Menggunakan format() untuk menampilkan waktu dalam format jam:menit:detik
           "🕒 Waktu di $negaraB: " . $waktuB->format("H:i:s") . "\n" .
           "⏳ Selisih waktu: " . floor($selisihJam) . " jam, " . round($selisihMenit) . " menit\n" . // Menampilkan selisih waktu dengan pembulatan
           "📌 $lebihDulu lebih dulu!\n";
}

// Menampilkan hasil perbandingan waktu
echo cekWaktu();
```

## 📝 Penjelasan Kode
1. **Menyimpan zona waktu beberapa negara**
   - Menggunakan array untuk menyimpan nama negara dan zona waktu masing-masing.
2. **Memvalidasi input negara**
   - Mengecek apakah negara yang dimasukkan pengguna tersedia dalam daftar.
3. **Mengambil waktu saat ini di kedua negara**
   - Menggunakan `DateTime("now", new DateTimeZone(...))` untuk mendapatkan waktu terkini berdasarkan zona waktu.
4. **Menghitung selisih waktu**
   - Menggunakan metode `getOffset()` untuk mendapatkan offset waktu dalam detik, lalu dikonversi ke jam dan menit.
5. **Menentukan negara yang lebih dahulu**
   - Membandingkan waktu kedua negara menggunakan operator `<` untuk menentukan negara mana yang lebih dulu.
6. **Menampilkan hasil dengan format yang jelas**
   - `format("H:i:s")` digunakan untuk menampilkan waktu dalam format jam:menit:detik.
   - `floor()` digunakan untuk membulatkan nilai jam ke bawah.
   - `round()` digunakan untuk membulatkan nilai menit.


## 🎯 Contoh Output
```
Masukkan negara pertama: Indonesia
Masukkan negara kedua: Jepang
🕒 Waktu di Indonesia: 14:30:45
🕒 Waktu di Jepang: 16:30:45
⏳ Selisih waktu: 2 jam, 0 menit
📌 Jepang lebih dulu!
```

## 🎓 Kesimpulan
Program ini mempermudah pengguna dalam membandingkan perbedaan waktu antara dua negara dengan mudah. Dengan menggunakan `DateTime` dan `DateTimeZone`, program dapat menampilkan informasi yang akurat dan real-time berdasarkan zona waktu yang tersedia.

🔥 **Tantangan!** Tambahkan lebih banyak negara ke dalam daftar dan buat tampilan output lebih menarik!

---
---
## 
---
---

# 🏷️ Cek Harga Setelah Diskon

## 📌 Deskripsi
Buatlah sebuah function dalam PHP untuk menghitung harga setelah mendapatkan diskon tertentu. Program ini akan menerima input dari terminal dan mengembalikan harga akhir setelah dikurangi diskon.

## 📖 Cara Kerja
1. Program meminta pengguna memasukkan harga awal.
2. Program meminta pengguna memasukkan persentase diskon.
3. Program menghitung harga setelah diskon.
4. Program menampilkan hasil akhir ke terminal.

---

## 🔧 Implementasi Kode
Berikut adalah contoh function untuk menghitung harga setelah diskon:

```php
<?php
function cekHargaSetelahDiskon() {
    // Meminta input harga awal dari pengguna
    echo "Masukkan harga awal: ";
    $harga_awal = trim(fgets(STDIN));

    // Meminta input persentase diskon dari pengguna
    echo "Masukkan persentase diskon (%): ";
    $diskon = trim(fgets(STDIN));

    // Validasi input harus berupa angka dan tidak negatif
    if (!is_numeric($harga_awal) || !is_numeric($diskon) || $harga_awal < 0 || $diskon < 0 || $diskon > 100) {
        echo "\n❌ Input tidak valid! Pastikan memasukkan angka yang benar.\n";
        return;
    }

    // Menghitung harga setelah diskon
    $harga_akhir = $harga_awal - ($harga_awal * ($diskon / 100));
    
    // Menampilkan hasil
    echo "\n💰 Harga setelah diskon: Rp " . number_format($harga_akhir, 2, ',', '.') . "\n";
}

// Memanggil function
cekHargaSetelahDiskon();
```

---

## 📑 Penjelasan Kode
1. **`trim(fgets(STDIN))`** → Mengambil input dari terminal dan menghapus spasi ekstra.
2. **`is_numeric()`** → Memastikan input adalah angka agar tidak terjadi error.
3. **Validasi Input** → Memeriksa apakah angka valid dan diskon tidak lebih dari 100%.
4. **Perhitungan Diskon** → `(harga_awal * (diskon / 100))` untuk mendapatkan jumlah diskon, lalu menguranginya dari harga awal.
5. **`number_format()`** → Memformat angka agar lebih mudah dibaca dalam format rupiah.

---

## 📌 Contoh Eksekusi
```sh
Masukkan harga awal: 200000
Masukkan persentase diskon (%): 25
💰 Harga setelah diskon: Rp 150.000,00
```

---

## 🎯 Kesimpulan
- Function ini membantu pengguna menghitung harga setelah diskon secara otomatis.
- Input divalidasi agar mencegah error.
- Hasil ditampilkan dalam format yang mudah dibaca.

🚀 **Selamat mencoba!**

---
---
## 
---
---

# 💰 Currency Converter Function in PHP

## 📌 Deskripsi
Buatlah sebuah function dalam PHP yang dapat mengonversi nilai mata uang dari satu negara ke negara lain. Function ini akan menerima input melalui terminal dan mengembalikan nilai mata uang yang telah dikonversi.

## 🎯 Tujuan Pembelajaran
- Memahami cara membuat function dalam PHP.
- Mempelajari cara menangani input melalui terminal.
- Mempraktikkan operasi aritmatika sederhana dalam konversi mata uang.

## 🛠️ Cara Penggunaan
1. Pastikan Anda telah menginstal **PHP** di komputer Anda.
2. Simpan kode program sebagai **currency_converter.php**.
3. Jalankan perintah berikut di terminal:
   ```sh
   php currency_converter.php
   ```

## 📝 Implementasi Kode
Berikut adalah contoh implementasi function untuk mengonversi mata uang:

```php
<?php
function currencyConverter($amount, $from, $to) {
    // Nilai tukar mata uang (contoh static, bisa diganti API)
    $exchangeRates = [
        'USD' => ['IDR' => 15000, 'EUR' => 0.85],
        'IDR' => ['USD' => 0.000067, 'EUR' => 0.000057],
        'EUR' => ['USD' => 1.18, 'IDR' => 17500]
    ];
    
    // Periksa apakah konversi tersedia
    if (isset($exchangeRates[$from][$to])) {
        $convertedAmount = $amount * $exchangeRates[$from][$to];
        return number_format($convertedAmount, 2) . " $to";
    } else {
        return "Konversi mata uang tidak tersedia.";
    }
}

// Eksekusi melalui terminal
echo "Masukkan jumlah uang: ";
$amount = trim(fgets(STDIN));

echo "Masukkan mata uang asal (USD, IDR, EUR): ";
$from = trim(fgets(STDIN));

echo "Masukkan mata uang tujuan (USD, IDR, EUR): ";
$to = trim(fgets(STDIN));

// Panggil function dan tampilkan hasilnya
echo "Hasil konversi: " . currencyConverter($amount, strtoupper($from), strtoupper($to)) . "\n";
?>
```

## 🔍 Penjelasan Kode
1. **Function `currencyConverter()`**:
   - Menerima jumlah uang (`$amount`), mata uang asal (`$from`), dan mata uang tujuan (`$to`).
   - Menggunakan array **$exchangeRates** untuk menyimpan nilai tukar mata uang secara statis.
   - Melakukan pengecekan apakah konversi yang diminta tersedia.
   - Menghitung nilai konversi dan mengembalikannya dengan format angka yang rapi.

2. **Penggunaan `fgets(STDIN)`**:
   - Digunakan untuk menerima input dari pengguna melalui terminal.
   - `trim()` digunakan untuk menghapus spasi atau karakter tidak diinginkan.

3. **Eksekusi Program**:
   - User diminta memasukkan jumlah uang, mata uang asal, dan mata uang tujuan.
   - Function `currencyConverter()` dipanggil dan hasilnya ditampilkan di terminal.

## 📌 Contoh Output
```
Masukkan jumlah uang: 100
Masukkan mata uang asal (USD, IDR, EUR): USD
Masukkan mata uang tujuan (USD, IDR, EUR): IDR
Hasil konversi: 1,500,000.00 IDR
```

## 📚 Catatan Tambahan
- Nilai tukar mata uang bisa diambil dari API real-time seperti **ExchangeRate-API** atau **Open Exchange Rates** untuk hasil yang lebih akurat.
- Pastikan untuk memasukkan kode mata uang dengan benar agar tidak terjadi error.

---
---
## 
---
---
