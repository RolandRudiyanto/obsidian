# Instalasi Cobol
- VisualStudioCode
	-> Untuk membuat project Cobol di VSCode dapat mengikuti tutorial pada blog https://mainframize.blogspot.com/2025/01/the-ultimate-guide-install-cobol-for.html
	-> Tools yang diperlukan: 
		- Debian: Dapat Diinstall dari MicrosoftStore
		- WSLExtension : Dapat di install di VsCode
		- CobolExtension
	-> Instalasi
		1. Install Install Windows Subsystem for Linux (WSL2) dengan command *wsl --install --no-distribution* pada PowerShell as Administrator
		2. Install Debian pada MicrosoftStore
		3. Install GnuCobol di Debian *sudo apt install gnucobol*
		4. Install WSLExtension di VSCode dengan mengetik WSL pada Extension
		5. Tekan Ctrl+Shift+P lalu cari WSL: connect to WSL using Distro lalu select Debian
		6. Buat Project Baru
- OpenCobolIDE
	-> ini merupakan IDE khusus untuk menjalankan program Cobol 
		1. Bukan Link https://github.com/OpenCobolIDE/OpenCobolIDE
		2. Scroll Kebawah hingga menemukan Resources, Klik Download
		3. Pilih Windows Instaler
		4. Install OpenCobol pada Device
# Struktur Program COBOL
- IDENTIFICATION DIVISION
	-> Ini merupakan bagian identitas dari program cobol sebagai contoh di C++ itu merupakan int main()
- ENVIRONMENT DIVISION
	-> Menjelaskan lingkungan tempat program berjalan
		- Biasanya berhubungan dengan file input/output.
		- Tidak selalu dipakai dalam program kecil.
- DATA DEVISION
	-> Mendefinisikan semua variabel & struktur data
		- FILE SECTION -> Digunakan untuk mendeviniskan file external
		- WORKING-STORAGE SECTION -> Global Variable
		- LOCAL-STORAGE SECTION -> Local Variable (Variable yanng harus di inisialisasi ulang setiap program berjala)
		- LINKAGE SECTION -> - Untuk parameter yang diterima dari program lain (mirip `function parameter`).
- PROCEDURE DIVISION
	-> Bagian utama berisi logika program.
		- Di sinilah perintah dieksekusi.
		- Bisa dibagi menjadi **PARAGRAPH** (blok logika).
# **Variable**
![[Pasted image 20250815094941.png]]
- Standar nama variable pada Cobol
	- **Hanya huruf, angka, dan tanda hubung (-)** yang boleh digunakan.
	- **Tidak boleh** ada spasi.
	- **Tidak boleh** diawali atau diakhiri dengan tanda hubung.
	- **Tidak boleh** ada dua tanda hubung berurutan (`--`).
	- **Tidak boleh** menggunakan kata kunci COBOL (reserved words).
	- Panjang nama **umumnya maksimal 30 karakter** (tergantung compiler, beberapa modern COBOL mendukung lebih panjang).
	- Penulisan biasanya **huruf besar semua** (UPPERCASE)
- Level Varibale

| Level   | Fungsi                                                                                   |
| ------- | ---------------------------------------------------------------------------------------- |
| 01      | Menandakan _top-level item_ atau _record_. Bisa berupa grup data atau item tunggal.      |
| 02 – 49 | Menandakan sub-level dari grup data di atasnya. Semakin besar angka, semakin "ke dalam". |
| 66      | Digunakan untuk **RENAMES** (menggabungkan beberapa field menjadi satu nama baru).       |
| 77      | Untuk **independent data item** (bukan bagian dari grup).                                |
| 88      | Untuk **condition name** (memberikan nama kondisi pada nilai tertentu).                  |
| FD      | Untuk File, biasanya menggunakan UPPERCASE dan mendeskripsikan isinya                    |
- Tipe Data

| Tipe              | Penjelasan                                 | Contoh            |
| ----------------- | ------------------------------------------ | ----------------- |
| **X(n)**          | Alfanumerik, panjang `n` karakter          | `PIC X(20)`       |
| **9(n)**          | Numerik, panjang `n` digit                 | `PIC 9(5)`        |
| **V**             | Titik desimal implisit                     | `PIC 9(3)V99`     |
| **S9(n)**         | Numerik dengan tanda (+/-)                 | `PIC S9(4)`       |
| **COMP / COMP-3** | Bentuk biner atau packed decimal (efisien) | `PIC 9(6) COMP-3` |
| **A(n)**          | Alfabet, panjang `n`                       | `PIC A(10)`       |
- COMP-3