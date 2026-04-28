# 🧺 Sistem Manajemen Del-Laundry (Java OOP)

Sistem Manajemen Del-Laundry adalah aplikasi berbasis *Command Line Interface* (CLI) yang tangguh dan dibangun menggunakan bahasa pemrograman Java. Sistem ini dirancang untuk mengotomatisasi pencatatan pesanan laundry, kalkulasi harga (kiloan/satuan), penerapan promo dinamis, hingga pencatatan riwayat transaksi secara permanen ke dalam file lokal.

## ✨ Fitur Utama
1. **Pencatatan Pesanan Dinamis:** Mendukung berbagai layanan (Cuci Komplit, Setrika Saja, Cuci Jas, Cuci Sepatu, dll).
2. **Kalkulasi Otomatis & Keranjang (Cart):** Menghitung total biaya banyak pesanan sekaligus secara instan menggunakan struktur data `ArrayList`.
3. **Sistem Promo & Diskon:** Menerapkan potongan harga khusus (10%) untuk pelanggan VIP dan gratis ongkos kirim (Delivery) secara otomatis jika syarat terpenuhi.
4. **Cetak Struk & Logging Transaksi:** Menghasilkan ringkasan pesanan ke layar terminal dan menyimpannya secara otomatis ke dalam file `.txt` (File I/O).
5. **Validasi Input Anti-Crash:** Menggunakan `try-catch` untuk menangani kesalahan saat pengguna salah memasukkan tipe data (misal: memasukkan huruf saat diminta angka).
6. **Simulasi Loading (Multithreading):** Menampilkan *progress bar* untuk simulasi pemrosesan data sistem.

## 🧠 Konsep Java & OOP yang Diterapkan
Sistem ini dirancang dengan standar *Software Engineering* yang baik melalui penerapan:

* **Inheritance (Pewarisan) & Polymorphism (Banyak Bentuk):** Kelas `LayananLaundry` bertindak sebagai *Superclass* abstrak, yang kemudian diturunkan menjadi `LaundryKiloan` dan `LaundrySatuan`. Keduanya memiliki implementasi metode `hitungTotal()` yang berbeda bentuknya sesuai dengan satuan perhitungannya.
* **Encapsulation (Pengkapsulan):** Seluruh atribut data bersifat `private` dan hanya dapat dikendalikan melalui *Getter* / *Setter* untuk menjaga validitas data.
* **Interface:** Penggunaan antarmuka `Promosiable` untuk menstandarisasi perhitungan diskon pada sistem.
* **Exception Handling:** Menangkap `InputMismatchException` agar program tidak berhenti mendadak akibat *human error* dari input terminal.
* **Collections Framework:** Menggunakan `List` dan `ArrayList` untuk menampung keranjang belanja pelanggan tanpa batasan ukuran *array* statis.
* **File I/O:** Menerapkan `FileWriter` dan `BufferedWriter` untuk menyimpan struk transaksi ke `logs/history_transaksi.txt`.
* **Multithreading:** Menggunakan `Thread.sleep()` dalam iterasi untuk menyimulasikan proses *loading* secara *asynchronous*.


## 📂 Struktur Proyek
Sistem memisahkan logika bisnis (Model) dan antarmuka (Driver) agar kode tetap modular.
```text
src/
 ├── driver/
 │    └── Driver4.java          # Entry point aplikasi & UI Terminal
 ├── model/
 │    ├── Promosiable.java      # Interface diskon/promo
 │    ├── LayananLaundry.java   # Abstract Superclass
 │    ├── LaundryKiloan.java    # Subclass untuk layanan berbasis berat
 │    ├── LaundrySatuan.java    # Subclass untuk layanan berbasis jumlah pcs
 │    └── Model4.java           # Pengelola keranjang pesanan & File I/O
 └── logs/
      └── history_transaksi.txt # (Terbuat otomatis) Rekap log transaksi
	  
##🛠️ Prasyarat (Prerequisites)
Java Development Kit (JDK) versi 8 atau lebih baru.

Terminal / Command Prompt / IDE (seperti IntelliJ IDEA, Eclipse, atau VS Code).

##🚀 Cara Menjalankan Program (How to Run)
Buka terminal atau IDE pilihan Anda dan arahkan ke direktori root proyek (src).

Kompilasi program menggunakan perintah:
javac driver/Driver4.java model/*.java

Jalankan program dengan perintah:
java driver.Driver4




**## 📂 Output**

=============================================
               STRUK DEL-LAUNDRY             
=============================================
NAMA PELANGGAN : ARYA SINAMBELA (VIP)
TIPE PESANAN   : Delivery
---------------------------------------------
Cuci Komplit (3.5 kg x Rp 8.000)   Rp  28.000
--------------------------------------------- +
SUBTOTAL                           Rp  28.000
DISKON VIP (10%)                   Rp  -2.800
ONGKIR                             Rp       0 (FREE)
---------------------------------------------
TOTAL BAYAR                        Rp  25.200
=============================================
[SYSTEM LOG] Struk berhasil disimpan secara permanen.
