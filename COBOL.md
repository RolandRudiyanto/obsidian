
**Computational verbs**# **Standar Nama Cobol:**
- **Hanya huruf, angka, dan tanda hubung (-)** yang boleh digunakan.
- **Tidak boleh** ada spasi.
- **Tidak boleh** diawali atau diakhiri dengan tanda hubung.
- **Tidak boleh** ada dua tanda hubung berurutan (`--`).
- **Tidak boleh** menggunakan kata kunci COBOL (reserved words).
- Panjang nama **umumnya maksimal 30 karakter** (tergantung compiler, beberapa modern COBOL mendukung lebih panjang).
- Penulisan biasanya **huruf besar semua** (UPPERCASE)
# **Defining Varibale:**
![[Pasted image 20250815094941.png]]
##### **Table Level Variable**

| Level   | Fungsi                                                                                   |
| ------- | ---------------------------------------------------------------------------------------- |
| 01      | Menandakan _top-level item_ atau _record_. Bisa berupa grup data atau item tunggal.      |
| 02 – 49 | Menandakan sub-level dari grup data di atasnya. Semakin besar angka, semakin "ke dalam". |
| 66      | Digunakan untuk **RENAMES** (menggabungkan beberapa field menjadi satu nama baru).       |
| 77      | Untuk **independent data item** (bukan bagian dari grup).                                |
| 88      | Untuk **condition name** (memberikan nama kondisi pada nilai tertentu).                  |
| FD      | Untuk File, biasanya menggunakan UPPERCASE dan mendeskripsikan isinya                    |
##### **Table Tipe Variabale** 

| Tipe              | Penjelasan                                 | Contoh            |
| ----------------- | ------------------------------------------ | ----------------- |
| **X(n)**          | Alfanumerik, panjang `n` karakter          | `PIC X(20)`       |
| **9(n)**          | Numerik, panjang `n` digit                 | `PIC 9(5)`        |
| **V**             | Titik desimal implisit                     | `PIC 9(3)V99`     |
| **S9(n)**         | Numerik dengan tanda (+/-)                 | `PIC S9(4)`       |
| **COMP / COMP-3** | Bentuk biner atau packed decimal (efisien) | `PIC 9(6) COMP-3` |
| **A(n)**          | Alfabet, panjang `n`                       | `PIC A(10)`       |
# **COMP-3 dan COMP**
Data type ini sering digunakan untuk perhitungan untuk menghemat memori dan mempercepat proses aritmatika
Kapan dipakai COMP dan COMP-3:
- **COMP** → kalau datanya **integer murni** (tanpa pecahan) dan butuh kecepatan.
- **COMP-3** → kalau datanya **punya pecahan desimal** atau butuh presisi digit per digit (misalnya uang).
# **Numeric Literal**
**Numeric Literal** adalah **angka langsung** yang kita tulis di program COBOL untuk:
- Mengisi nilai awal (_initial value_) variabel.
- Melakukan perhitungan.
- Memberikan nilai pada saat program berjalan.
📌 Bedanya dengan variabel → numeric literal tidak punya nama, nilainya langsung dipakai.
	**Aturan Penulisan**
	1. Hanya angka (`0–9`), tanda `+/-`, dan titik (`.`) untuk desimal.
	2. Tidak boleh ada **koma** pemisah ribuan.
	3. Tidak boleh ada spasi di tengah angka.
	4. Panjang angka maksimal **18 digit** (tergantung compiler COBOL).
	5. Titik desimal hanya boleh ada **satu**.

# **Computational verbs**
##### **ADD**
![[Pasted image 20250815164814.png]]
##### **SUBTRACT**
![[Pasted image 20250815165034.png]]
##### **MULTIPLY**
![[Pasted image 20250815165121.png]]
##### **DIVIDE**
![[Pasted image 20250815165216.png]]
# **Conditional Expressions**
| Jenis Kondisi            | Bentuk Penulisan                                                                                                                                                | Kegunaan / Fungsi                                                                                                                                              |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Relational Condition** | `IF A > B``IF A = B``IF A NOT = B``IF A GREATER THAN B`                                                                                                         | Membandingkan dua nilai (angka, teks) untuk menentukan apakah lebih besar, lebih kecil, sama, atau tidak sama.                                                 |
| **Sign Condition**       | `IF BALANCE IS POSITIVE``IF BALANCE IS NEGATIVE``IF BALANCE IS ZERO`                                                                                            | Mengecek tanda dari sebuah angka, apakah positif, negatif, atau nol.                                                                                           |
| **Class Condition**      | `IF ITEM IS NUMERIC``IF NAME IS ALPHABETIC``IF CODE IS ALPHANUMERIC`                                                                                            | Mengecek tipe data dari isi variabel, misalnya apakah hanya angka, huruf, atau kombinasi huruf dan angka.                                                      |
| EVALUATE                 | EVALUATE GRADE<br>   WHEN "A"<br>      DISPLAY "Excellent"<br>   WHEN "B"<br>      DISPLAY "Good"<br>   WHEN OTHER<br>      DISPLAY "Try Again"<br>END-EVALUATE | _multi-branch selection_ (mirip `switch-case` di bahasa lain) yang bisa mengevaluasi satu atau lebih ekspresi/kondisi, lalu menjalankan blok kode yang sesuai. |
# **Perform Statement**
| Jenis `PERFORM` | Bentuk Sintaks                                                      | Kegunaan                                                                                   | Contoh                                                      |
| --------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| Simple PERFORM  | `PERFORM paragraf-name`                                             | Menjalankan satu paragraf sekali saja.                                                     | `PERFORM Hitung-Komisi`                                     |
| PERFORM THRU    | `PERFORM paragraf-1 THRU paragraf-2`                                | Menjalankan beberapa paragraf berurutan.                                                   | `PERFORM Proses-A THRU Proses-C`                            |
| PERFORM TIMES   | `PERFORM paragraf-name n TIMES`                                     | Mengulang eksekusi paragraf sebanyak `n` kali.                                             | `PERFORM Cetak-Data 5 TIMES`                                |
| PERFORM UNTIL   | `PERFORM paragraf-name UNTIL kondisi`                               | Mengulang paragraf sampai kondisi terpenuhi (loop dengan syarat berhenti).                 | `PERFORM Baca-File UNTIL EOF`                               |
| PERFORM VARYING | `PERFORM paragraf-name VARYING var FROM awal BY step UNTIL kondisi` | Loop dengan variabel counter, mirip `for` di bahasa lain.                                  | `PERFORM Tampilkan-Data VARYING I FROM 1 BY 1 UNTIL I > 10` |
| PERFORM INLINE  | `PERFORM ... END-PERFORM`                                           | Menjalankan kode langsung di antara `PERFORM` dan `END-PERFORM` (tanpa paragraf terpisah). | `PERFORM DISPLAY "HELLO" END-PERFORM`                       |
