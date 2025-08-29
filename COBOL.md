
# **Computational verbs**
**Standar Nama Cobol:**
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
# **File Organization**
File Organization merupkan cara file disimpan & diakses** oleh program COBOL. Pilihan ini kamu tentukan di `ENVIRONMENT DIVISION > FILE-CONTROL` saat `SELECT` file.

Jenis File Organization

| Jenis           | Analogi sehari-hari       | Cara akses        | Kegunaan utama                      | Deskripsi                                                                                                                                                                                                                                              | Contoh Code                                                                                                                                                              |
| --------------- | ------------------------- | ----------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Sequential      | Kaset tape                | Dari awal → akhir | Tape processing, batch lama         | - File dibaca **record demi record**, tidak bisa langsung lompat ke record tertentu.<br>- Umumnya dipakai di **mainframe tape** atau **file biner fixed-length**.                                                                                      | SELECT SEQ-FILE ASSIGN TO 'DATASEQ.DAT'<br>    ORGANIZATION IS SEQUENTIAL.<br>                                                                                           |
| Line Sequential | File teks baris-per-baris | Dari awal → akhir | Input/output teks sederhana         | - **Seperti file teks biasa** 📄 (tiap baris = 1 record).<br>- Ada “Enter” di akhir record.<br>- Lebih sering dipakai di PC / sistem modern untuk laporan.                                                                                             | SELECT TXT-FILE ASSIGN TO 'REPORT.TXT'<br>    ORGANIZATION IS LINE SEQUENTIAL.<br>                                                                                       |
| Relative        | Loker bernomor            | By nomor record   | Data dengan ID urut                 | - **Seperti deretan loker bernomor** 🔢 (1, 2, 3, …).<br>- Bisa langsung ambil record nomor 57 tanpa harus baca dari awal.<br>- Cocok untuk data kecil-menengah di mana record dikenali dengan “nomor urut”.                                           | SELECT REL-FILE ASSIGN TO 'REL.DAT'<br>    ORGANIZATION IS RELATIVE<br>    ACCESS MODE IS RANDOM<br>    RELATIVE KEY IS REC-NUM.<br>                                     |
| Indexed         | Kamus / database          | By key atau urut  | File transaksi, customer, inventory | - **Seperti kamus atau database mini** 📚 → pakai kata kunci (key) untuk mencari data.<br>- Ada **RECORD KEY** (misalnya Customer-ID).<br>- Bisa **Sequential**, **Random**, atau **Dynamic** (campuran).<br>- Paling fleksibel untuk aplikasi bisnis. | SELECT CUST-FILE ASSIGN TO 'CUSTOMER.DAT'<br>    ORGANIZATION IS INDEXED<br>    ACCESS MODE IS DYNAMIC<br>    RECORD KEY IS CUST-ID<br>    FILE STATUS IS WS-STATUS.<br> |
# **File Procesing**
**File Processing** adalah cara program COBOL **membaca, menulis, mengubah, atau menghapus data di file**. 
Gambaran Besar:
- **Definisikan file**  
    `ENVIRONMENT DIVISION > INPUT-OUTPUT SECTION > FILE-CONTROL`
    - `DATA DIVISION > FILE SECTION` (struktur 1 record).
- **OPEN** file (INPUT/OUTPUT/I-O/EXTEND).
- **Proses**: `READ / WRITE / REWRITE / DELETE` (sesuai organisasi & akses).
- **CLOSE** file.
Langkah Langkah Pemerosesan File:
- **OPEN** → buka file
    - `INPUT` (baca)
    - `OUTPUT` (buat baru + tulis)
    - `I-O` (baca & update)
    - `EXTEND` (tambah di akhir)
- **READ** → baca record
- **WRITE** → tulis record baru
- **REWRITE** → update record yang sudah ada (Indexed/Relative)
- **DELETE** → hapus record (Indexed/Relative)
- **CLOSE** → tutup file
Access Mode:
- **SEQUENTIAL** → baca/tulis berurutan.
- **RANDOM** → langsung ke record tertentu.
- **DYNAMIC** → bisa sequential + random.
Error Handling:
- **"00"** sukses
- **"10"** End-of-file
- **"22"** Duplikat key (WRITE)
- **"23"** Key tidak ditemukan (READ)
- **"35"** File tidak ada saat OPEN
- **"39"** Salah panjang record / definisi tidak cocok
- **"41"/"42"** Sudah/belum di-OPEN
- **"46"** READ setelah EOF
## **File Control (Wajib)**
Tanpa FILE-CONTROL, COBOL **tidak tahu**:
- file apa yang dipakai,
- file itu disimpan di mana,
- bagaimana cara mengaksesnya,
- apa kunci record-nya,
- dan bagaimana menangani error.
Contoh Penggunaan
	FILE-CONTROL.
    SELECT IN-TXT  ASSIGN TO 'input.txt'
        ORGANIZATION IS LINE SEQUENTIAL.

    SELECT CUST-IDX ASSIGN TO 'customer.dat'
        ORGANIZATION IS INDEXED
        ACCESS MODE  IS DYNAMIC
        RECORD KEY   IS CUST-ID
        FILE STATUS  IS FS-IDX.

    SELECT REL-FILE ASSIGN TO 'relative.dat'
        ORGANIZATION IS RELATIVE
        ACCESS MODE  IS RANDOM
        RELATIVE KEY IS REL-NO
        FILE STATUS  IS FS-REL
# **Advanced Sequential Files**
**Advanced Sequential Files** → melibatkan:
1. **SORT** → mengurutkan record berdasarkan kunci tertentu.
2. **MERGE** → menggabungkan beberapa file yang sudah diurutkan.
3. **Update Master File** → gabungkan file transaksi dengan file master (umum di payroll, inventory, dll).
### **SORT**
- `SORT-FILE` = file kerja sementara.
- `ON ASCENDING KEY` = urutan naik (bisa juga `DESCENDING`).
- `USING` = file input yang belum terurut.
- `GIVING` = file output hasil sort.
### **MERGE**
- Sintaks:
    `MERGE SORT-FILE ON ASCENDING KEY EMP-ID      USING FILE1 FILE2      GIVING FILE-MERGED.`
- Aturan:
    - File input harus **sudah terurut** berdasarkan key yang sama.
    - Cocok untuk update data master dari transaksi.
### **Perbedaan Sort dan Merge**

| Fitur    | SORT                                | MERGE                               |
| -------- | ----------------------------------- | ----------------------------------- |
| Input    | 1 file (belum terurut)              | 2+ file (sudah terurut)             |
| Output   | 1 file terurut                      | 1 file gabungan terurut             |
| Kegunaan | Membersihkan/urutkan data transaksi | Update master file dari banyak file |
# **Table**
OCCURS n TIMES ini dugunakan untuk menyatakan bahwa item dari data tersebut berulan
01 STUDENT-TABLE.
   05 STUDENT-ID   PIC 9(5) OCCURS 100 TIMES.
Artinya:
- `STUDENT-ID` = array dengan 100 elemen.
- Tiap elemen punya 5 digit angka.
### **Searching Tables**
- Sequential Search
	-  Digunakan kalau tabel **tidak terurut**.
	- COBOL periksa elemen dari awal sampai cocok.
- Binary Search
	-  Digunakan kalau tabel **sudah diurutkan**.
	- Lebih cepat karena metode binary search.
# **String Handling**
- **STRING** → menggabungkan string.
- **UNSTRING** → memecah string.
- **INSPECT** → menghitung/replace karakter.
# **Troubleshooting**
- Error umum di COBOL:
    - **Numeric overflow** → hasil lebih besar dari PIC.
    - **Logic error** → program jalan tapi hasil salah.
- Pencegahan:
    - Gunakan `ON SIZE ERROR` pada COMPUTE.
    - Pakai PIC field yang lebih panjang.
    - Debug dengan `DISPLAY` isi variabel.

# **DDL Operations**
**DDL (Data Definition Language)** = perintah untuk **mendefinisikan/ubah struktur** database:
- `CREATE` (schema, table, index, view, sequence)
- `ALTER` (ubah struktur tabel: tambah kolom, ubah tipe—tergantung dukungan)
- `DROP` (hapus objek)
- `RENAME` (ganti nama objek—tergantung versi)
- `GRANT/REVOKE` (izin akses)
**Praktik umum di mainframe**: DDL biasanya dieksekusi oleh DBA lewat script (SPUFI/DSNTEP2/DSNTEP4) **di luar program COBOL**.  
**Kalau tetap perlu dari COBOL** → harus lewat **Dynamic SQL** (`EXECUTE IMMEDIATE`/`PREPARE ... EXECUTE`). DDL tidak “dibekukan” sebagai **static SQL** saat bind.
Objek-objek DDL yang perlu kamu kenal
- **SCHEMA**: “nama depan” objek (mis. `PAYROLL.EMPLOYEE` → `PAYROLL` adalah schema).
- **TABLE**: tempat data disimpan (kolom + tipe data + constraint).
- **INDEX**: mempercepat pencarian/penyortiran (bukan data, tapi struktur bantu).
- **VIEW**: “tabel virtual” hasil query.
- **SEQUENCE/IDENTITY**: generator angka bertambah otomatis.
- **CONSTRAINT**: aturan data (PRIMARY KEY, UNIQUE, FOREIGN KEY, CHECK, NOT NULL).
Pola dalam DLL:
- EXECUTE IMMEDIATE
	-> Ini akan menjalankan lansung string querynya
- `PREPARE` + `EXECUTE`
	-> Dipakai kalau query **dibangun dinamis** (misalnya tabel/kolom berdasarkan input user).
	Langkah:
    1. `PREPARE` → mendaftarkan string SQL ke DB2.
    2. `EXECUTE` → menjalankan SQL yang sudah diprepare.
**Error Handling**
-  `-601` → objek sudah ada (misalnya CREATE TABLE pada tabel yang sudah ada).
- `-204` → objek tidak ditemukan (DROP TABLE pada tabel yang tidak ada).
- `-104` → syntax error.
- Selalu log **SQLCODE** dan **SQLSTATE**.
**Performance**
- Dynamic SQL lebih berat dibanding static, karena DB2 harus parsing di runtime.
- Makanya DDL biasanya tidak ditaruh di program COBOL bisnis, tapi di script SQL khusus (SPUFI/DSNTEP2).
# **DML Operations**
**DML (Data Manipulation Language)** adalah perintah SQL untuk **mengelola isi tabel**
Contoh DML:
- `INSERT` → menambah data.
- `UPDATE` → mengubah data.
- `DELETE` → menghapus data.
- `SELECT` → mengambil data.
Contoh Penulisan di Cobol:
EXEC SQL
   <SQL Statement>
END-EXEC.
- Semua dijalankan lewat `EXEC SQL ... END-EXEC` dengan **host variable**.
- Harus selalu cek `SQLCODE` untuk pastikan hasilnya.
- Gunakan **COMMIT** / **ROLLBACK** untuk kontrol transaksi.
# **Keys and Index**