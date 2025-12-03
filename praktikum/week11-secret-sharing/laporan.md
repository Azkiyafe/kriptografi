# Laporan Praktikum Kriptografi
Minggu ke-: 3  
Topik: [judul praktikum]  
Nama: [Azkiya Fe Sabella]  
NIM: [230202802]  
Kelas: [5 IKKA]  

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:

Menyelesaikan operasi aritmetika modular.
Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.


---

## 2. Dasar Teori
Modular arithmetic adalah sistem aritmatika yang berfokus pada sisa hasil pembagian, sering disebut "aritmatika jam" karena sifatnya yang siklis seperti penunjukkan jam yang kembali ke nol setelah mencapai angka tertentu. Secara formal, dua bilangan dikatakan kongruen modulo n jika selisihnya habis dibagi n, atau dengan kata lain keduanya memberikan sisa yang sama ketika dibagi n. Misalnya, 17 kongruen dengan 5 modulo 6 karena 17 − 5 = 12, yang merupakan kelipatan 6. Konsep ini mendasari banyak aplikasi praktis, termasuk kriptografi, pengecekan kesalahan, dan pengindeksan array dalam pemrograman. Operasi seperti penjumlahan, pengurangan, dan perkalian dapat dilakukan dalam modular arithmetic dengan terlebih dahulu mengambil sisa masing-masing operand terhadap modulus yang diberikan, kemudian mengoperasikannya, dan akhirnya mengambil sisa lagi terhadap modulus yang sama. Sifat refleksif, simetris, dan transitif menjadikan relasi kongruensi modulo n suatu relasi ekuivalen yang penting dalam struktur matematika diskrit.

Greatest Common Divisor (GCD) atau Faktor Persekutuan Terbesar (FPB) adalah bilangan bulat positif terbesar yang dapat membagi habis dua bilangan bulat tanpa menyisakan sisa. Jika GCD dua bilangan adalah 1, mereka disebut coprime atau relatif prima, yang berarti tidak memiliki faktor bersama selain 1. GCD memainkan peran krusial dalam menentukan keberadaan invers modular—suatu bilangan a memiliki invers modulo n jika dan hanya jika gcd(a, n) = 1. Algoritma Euclidean memberikan cara efisien untuk menghitung GCD dengan berulang kali mengganti pasangan bilangan dengan bilangan kedua dan sisa hasil bagi, sampai sisanya nol. Versi diperluas dari algoritma ini tidak hanya menghasilkan GCD, tetapi juga menemukan koefisien Bézout, yaitu bilangan bulat x dan y yang memenuhi persamaan ax + by = gcd(a, b). Pengetahuan ini esensial untuk menyelesaikan persamaan kongruensi linear dan penerapan dalam kriptografi seperti algoritma RSA.

Hubungan antara modular arithmetic dan GCD sangat erat dan saling mendukung. Dalam menyelesaikan persamaan linear modular ax ≡ b (mod n), keberadaan solusi bergantung pada apakah gcd(a, n) membagi b. Jika ya, solusi dapat ditemukan dengan memanfaatkan invers modular atau perluasan algoritma Euclidean. Teorema Sisa Tiongkok (Chinese Remainder Theorem) memanfaatkan sifat gcd yang bernilai 1 antar modulus untuk menggabungkan beberapa kongruensi menjadi satu solusi unik modulo hasil kali modulus-modulus tersebut. Dalam kriptografi, keamanan RSA bertumpu pada pemilihan bilangan e yang relatif prima terhadap φ(n), yaitu gcd(e, φ(n)) = 1, agar memiliki invers dekripsi yang valid. Euler's theorem, yang menyatakan bahwa a^φ(n) ≡ 1 (mod n) jika gcd(a, n) = 1, menjadi dasar bagi banyak protokol kriptografi modern. Dengan demikian, penguasaan konsep GCD dan modular arithmetic tidak hanya penting dalam teori bilangan, tetapi juga dalam aplikasi keamanan informasi dan ilmu komputer secara luas

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Tuliskan fungsi untuk menghitung operasi modular dasar.
2. Implementasikan fungsi GCD dengan algoritma Euclidean.
3. Tambahkan fungsi untuk mencari invers modular.
4. Simulasikan logaritma diskrit sederhana: mencari x sehingga a^x ≡ b (mod n).

---

## 5. Source Code

# Import fungsi yang dibutuhkan
from modular_math import modular_inverse, gcd_euclidean, modular_exp

# Contoh penggunaan
inv = modular_inverse(7, 26)  # Output: 15
gcd_val = gcd_euclidean(48, 18)  # Output: 6
pow_mod = modular_exp(3, 10, 17)  # Output: 8


## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1:
  Aritmetika modular adalah jantung kriptografi modern, menyediakan fondasi matematis yang memungkinkan keamanan digital melalui sifat-sifat bilangan yang "melingkar" dan perhitungan satu-arah (one-way functions). 
Peran Utamanya:
1. Menciptakan Fungsi Trapdoor (Pintu Jebakan)
   Operasi modular seperti eksponensiasi modular mudah dihitung ke depan tetapi sangat sulit dibalik tanpa kunci tertentu. Misalnya, menghitung \( m^e \mod n \) mudah, tetapi mencari \( m \) dari \( c = m^e \mod n \) tanpa kunci \( d \) (discrete log problem) secara komputasi tidak feasible untuk bilangan besar.
2. Mengimplementasi Algoritma Kunci Publik
   - RSA: Bergantung pada kesulitan faktorisasi bilangan besar \( n = p \times q \) dan teorema Euler \( m^{\phi(n)} \equiv 1 \pmod{n} \)
   - Diffie-Hellman: Pertukaran kunci aman berdasarkan kesulitan masalah Diffie-Hellman (mencari \( g^{ab} \mod p \) dari \( g^a \mod p \) dan \( g^b \mod p \))
   - ElGamal & ECC: Berbasis masalah logaritma diskrit dalam grup siklik
3. Membatasi Ruang Kunci dan Memastikan Ketertutupan
   Aritmetika modular membatasi hasil dalam rentang terbatas (0 hingga \( n-1 \)), yang memastikan:
   - Operasi selalu menghasilkan nilai dalam ruang yang sama
   - Enkripsi tidak menghasilkan output yang membesar tak terkendali
   - Implementasi hardware/software lebih efisien
4. Menyediakan Struktur Grup dan Lapangan Terhingga
   Himpunan \( \mathbb{Z}_n^* \) (bilangan bulat modulo \( n \) yang relatif prima dengan \( n \)) membentuk grup perkalian, memungkinkan:
   - Eksistensi invers (untuk dekripsi)
   - Penggunaan generator/elemen primitif
   - Struktur aljabar untuk pembuktian keamanan
5. Mengamankan Hash dan Checksum
   Fungsi hash kriptografi menggunakan operasi modular untuk:
   - Kompresi pesan (seperti dalam SHA/MD5)
   - Memastikan avalanche effect (perubahan kecil input mengubah output signifikan)
   - Penghitungan MAC (Message Authentication Codes)
6. Mendukung Kriptografi Elliptic Curve (ECC)
   Operasi titik pada kurva eliptik didefinisikan dalam aritmetika modular, memberikan keamanan setara dengan kunci lebih pendek (256-bit ECC ≈ 3072-bit RSA).
Contoh Konkret:
Dalam RSA, ketika mengenkripsi pesan \( m \), dihitung \( c = m^e \mod n \). Dekripsi menggunakan \( m = c^d \mod n \). Keamanan terletak pada kesulitan menghitung \( d \) dari \( e \) dan \( n \) tanpa faktorisasi \( n \), yang bergantung pada sifat aritmetika modular.
Mengapa Modular?
- Deterministik: Operasi yang sama selalu menghasilkan hasil sama
- Efisien: Operasi pada bilangan besar bisa dioptimasi
- Sulit dibalik: Masalah seperti faktorisasi dan log diskrit masih "hard" untuk komputer kuantum sekalipun (kecuali dengan algoritma Shor)
- Universal: Bisa diimplementasi di semua platform
tanpa aritmetika modular, sistem kriptografi modern seperti HTTPS, blockchain, enkripsi disk, tanda tangan digital, dan komunikasi aman tidak mungkin eksis. Ini adalah bahasa matematika yang menerjemahkan kebutuhan keamanan menjadi operasi komputasi praktis sekaligus aman secara teoretis.

- Pertanyaan 2: Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?
  Invers modular penting dalam algoritma kunci publik seperti RSA karena menjadi mekanisme pembalikan (dekripsi/tanda tangan) yang aman.
Dalam RSA:
1. Kunci publik = \((e, n)\) di mana \(e\) dipilih sehingga \(\gcd(e, \phi(n)) = 1\)
2. Kunci privat = \(d\) yang merupakan invers modular dari \(e\) modulo \(\phi(n)\), yaitu \(d \equiv e^{-1} \pmod{\phi(n)}\)
Mengapa penting:
- Fungsi Trapdoor: Enkripsi: \(c = m^e \mod n\) mudah. Dekripsi: \(m = c^d \mod n\) hanya mungkin jika memiliki \(d\)
- Keamanan: Menemukan \(d\) tanpa mengetahui \(\phi(n)\) setara dengan memfaktorisasi \(n\) (masalah komputasi sulit)
- Kebalikan Sempurna: Karena \(ed \equiv 1 \pmod{\phi(n)}\), maka \(m^{ed} \equiv m \pmod{n}\) (menggunakan Teorema Euler)
Tanpa invers modular, tidak ada cara untuk mendapatkan kembali pesan asli dari ciphertext atau memverifikasi tanda tangan. Invers modular menciptakan pasangan matematis \((e, d)\) yang memungkinkan operasi kebalikan secara aman — mudah dalam satu arah (dengan kunci publik) tetapi hampir mustahil dibalik tanpa kunci privat.

- Pertanyaan 3: Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?
Tantangan utama penyelesaian logaritma diskrit untuk modulus besar adalah sifat komputasinya yang tumbuh eksponensial terhadap ukuran bilangan, membuatnya secara praktis tidak terpecahkan dengan teknologi komputasi saat ini.
Inti Kesulitan:
1. Tidak Ada Algoritma Efisien: Masalah logaritma diskrit (DLP) belum ditemukan algoritma polinomial waktu-nya (seperti faktorisasi punya "General Number Field Sieve" yang sub-eksponensial). Algoritma terbaik seperti Pollard's Rho atau Baby-step Giant-step masih membutuhkan \(O(\sqrt{n})\) operasi.
2. Pertumbuhan Eksponensial: Untuk modulus \(n\) bit, kompleksitas waktu terbaik saat ini sekitar \(O(2^{n/2})\). Menggandakan ukuran modulus bukan menggandakan kesulitan, tapi meningkatkan eksponensial.
   - 256-bit: \(~2^{128}\) operasi
   - 512-bit: \(~2^{256}\) operasi (tidak feasible)
3. Kurangnya Struktur Matematis yang Dieksploitasi: Berbeda dengan faktorisasi yang punya banyak celah matematis (kesamaan kuadrat, bidang bilangan), DLP di grup umum lebih "rata" dan sulit dipecah.
4. Sifat One-Way Function yang Kokoh: Fungsi \(g^x \mod p\) mudah dihitung, tetapi inversnya (mencari \(x\) dari hasil) seperti mencari jarum di tumpukan sekam dengan \(p\) elemen.
Contoh Konkret: 
Untuk prime 2048-bit, ruang pencarian \(x\) memiliki sekitar \(2^{2048}\) kemungkinan. Superkomputer tercepat pun membutuhkan waktu miliaran tahun untuk brute-force.
Pengecualian: 
- Komputer Kuantum dengan algoritma Shor bisa memecah DLP dalam waktu polinomial, tapi teknologi ini belum praktis untuk modulus besar saat ini.
- Grup dengan struktur khusus (seperti grup aditif modulo) mudah dipecah, tetapi grup kriptografi sengaja memilih grup siklik yang "umum".
Inilah mengapa DLP menjadi fondasi Diffie-Hellman, DSA, dan ECC — karena kesulitan intrinsiknya yang menjaga keamanan meski algoritmanya publik dan modulusnya diketahui.

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit week3-modmath-gcd
Author: Azkiya Fe Sabella <azkiyafesabella14@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
