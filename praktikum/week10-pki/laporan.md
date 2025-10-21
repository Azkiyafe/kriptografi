# Laporan Praktikum Kriptografi
Minggu ke-: 2  
Topik: cryptosistem  
Nama: Azkiya Fe Sabella
NIM: 230202802  
Kelas: 5 IKKA 

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:

1. Mengidentifikasi komponen dasar kriptosistem (plaintext, ciphertext, kunci, algoritma).
2. Menggambarkan proses enkripsi dan dekripsi sederhana.
3. Mengklasifikasikan jenis kriptosistem (simetris dan asimetris).

## 2. Dasar Teori
Cipher klasik adalah metode penyandian pesan yang digunakan sebelum munculnya teknologi komputer modern. Prinsip dasarnya adalah mengubah pesan asli (plaintext) menjadi bentuk tidak terbaca (ciphertext) menggunakan operasi sederhana seperti pergeseran huruf, penggantian karakter, atau pengacakan posisi huruf. Contoh cipher klasik yang terkenal adalah Caesar Cipher, di mana setiap huruf digeser sejauh beberapa posisi dalam alfabet, dan Vigenère Cipher yang menggunakan kata kunci untuk menentukan pola pergeseran. Tujuan utama cipher klasik adalah menjaga kerahasiaan pesan agar tidak mudah dipahami oleh pihak yang tidak berhak.

Dalam proses enkripsi pada cipher klasik, konsep modular aritmetika memegang peran penting. Modular aritmetika merupakan sistem bilangan yang melakukan operasi berdasarkan nilai sisa pembagian dengan angka tertentu yang disebut modulus. Misalnya, (7 \mod 5 = 2) karena sisa pembagian 7 dengan 5 adalah 2. Dalam kriptografi, operasi ini digunakan untuk menjaga agar hasil pergeseran huruf tetap berada dalam rentang alfabet. Pada Caesar Cipher, perhitungannya dinyatakan dengan rumus (C = (P + K) \mod 26), di mana 26 mewakili jumlah huruf dalam alfabet Latin.

Jenis cipher klasik terbagi menjadi dua kategori utama, yaitu substitution cipher dan transposition cipher. Substitution cipher mengganti setiap huruf dengan huruf lain berdasarkan pola tertentu, sedangkan transposition cipher hanya mengubah posisi huruf tanpa mengubah karakter aslinya. Contohnya, pada substitution cipher, huruf A bisa diganti menjadi D jika menggunakan pergeseran tiga posisi, sedangkan pada transposition cipher, urutan huruf dalam kata diacak mengikuti pola tertentu untuk menghasilkan ciphertext yang berbeda dari bentuk aslinya.

Keamanan dalam cipher klasik sangat bergantung pada kunci (key) yang digunakan. Tanpa kunci yang tepat, pesan sulit dikembalikan ke bentuk semula. Namun, seiring waktu, cipher klasik menjadi mudah dipecahkan dengan metode analisis frekuensi, yaitu teknik yang memanfaatkan pola kemunculan huruf dalam suatu bahasa. Meskipun demikian, konsep dasar dari cipher klasik tetap menjadi fondasi penting dalam pengembangan sistem kriptografi modern yang lebih kompleks dan aman.


## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
# file: praktikum/week2-cryptosystem/src/simple_crypto.py

def encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def decrypt(ciphertext, key):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift - key) % 26 + shift)
        else:
            result += char
    return result

if __name__ == "__main__":
    message = "<nim><nama>"
    key = 5

    enc = encrypt(message, key)
    dec = decrypt(enc, key)

    print("Plaintext :", message)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)
```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```
)

---

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
- Pertanyaan 1: Komponen utama dalam sebuah kriptosistem terdiri dari beberapa elemen penting, yaitu plaintext, yaitu pesan asli yang akan dienkripsi; ciphertext, yaitu hasil penyandian yang tidak dapat dibaca tanpa kunci yang tepat; algoritma enkripsi, yaitu prosedur atau rumus matematika yang digunakan untuk mengubah plaintext menjadi ciphertext; algoritma dekripsi, yaitu proses kebalikan untuk mengembalikan ciphertext menjadi plaintext; serta kunci (key) yang berfungsi sebagai parameter rahasia dalam proses enkripsi dan dekripsi. Selain itu, kriptosistem juga melibatkan pengirim dan penerima sebagai pihak yang melakukan komunikasi aman dengan menggunakan kunci dan algoritma yang disepakati.
- Pertanyaan 2: Sistem kriptografi simetris memiliki kelebihan utama berupa kecepatan dan efisiensi tinggi karena proses enkripsi dan dekripsinya menggunakan algoritma yang relatif sederhana dan cepat. Selain itu, sistem ini tidak memerlukan banyak sumber daya komputasi, sehingga cocok untuk enkripsi data dalam jumlah besar. Namun, kelemahannya terletak pada distribusi kunci, karena pengirim dan penerima harus memiliki kunci rahasia yang sama, yang sulit dijaga keamanannya terutama dalam komunikasi jarak jauh.
Sebaliknya, sistem kriptografi asimetris lebih aman dalam distribusi kunci karena menggunakan sepasang kunci berbeda, yaitu kunci publik dan kunci privat, sehingga tidak perlu bertukar kunci rahasia. Akan tetapi, kelemahannya adalah proses enkripsi dan dekripsi jauh lebih lambat dibandingkan sistem simetris, karena melibatkan operasi matematika yang kompleks dan memerlukan daya komputasi lebih besar. 
- Pertanyaan 3 : Distribusi kunci menjadi masalah utama dalam kriptografi simetris karena sistem ini menggunakan satu kunci yang sama untuk proses enkripsi dan dekripsi. Artinya, baik pengirim maupun penerima harus memiliki kunci rahasia yang identik agar dapat saling bertukar pesan dengan aman. Tantangannya muncul ketika kunci tersebut harus dikirim atau dibagikan kepada pihak lain — jika proses pengiriman dilakukan melalui saluran komunikasi yang tidak aman, kunci bisa disadap atau dicuri oleh pihak yang tidak berwenang. Jika kunci jatuh ke tangan penyerang, maka seluruh pesan terenkripsi dapat dengan mudah dibuka. Oleh karena itu, menjaga kerahasiaan dan keamanan saat menyebarkan atau menukar kunci menjadi salah satu kelemahan terbesar dari kriptografi simetris.

## 8. Kesimpulan
Berdasarkan percobaan pada program tersebut, dapat disimpulkan bahwa fungsi encrypt() berhasil mengubah teks asli (plaintext) menjadi ciphertext dengan melakukan pergeseran huruf sebanyak nilai kunci yang ditentukan menggunakan metode Caesar Cipher. Fungsi decrypt() kemudian mampu mengembalikan ciphertext tersebut ke bentuk semula menggunakan kunci yang sama, sehingga membuktikan bahwa sistem kriptografi simetris bekerja dengan prinsip kunci enkripsi dan dekripsi yang identik.


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
commit abc12345 
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
