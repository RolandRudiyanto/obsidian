Untuk melihat progres dari presales
- Menentukan Meeting
- Membuat Docs
- Bikin Dokumen buat flow PRD DOCS
- Menentukan Fitur
- Tujuan
- Scope
- Next dan Golang Fiber
- Sales Stage
- Dummy Option = Sales Stagenya sudah sampe mana
- Sales Stage Exsampe

Latar Belakang Pembuatan Manhattan Projects
Kesulitan dalam melakukan monitoring terhadap progres dari setiap presales yang dimana setiap dokumen presales terpisah pisah
Tujuan:
- Monitoring Progress dari Presales
- Membuat Jadwal Event seperti meeting atau visit
Scope
- Monitoring
- Multi User
- Event Schedule
Fitur Manhattan Projects
- Dashbord
- Pipeline List
- Calender
- Master Data Reqeust
- Master Data
	- Principal List
	- SalesStage List
	- ProductList
	- CustomerList
	- UserManagement(SA (SolutionArchitect), AM (AccountManager))


Jadi untuk flow user itu nanti profile dapat di isi untuk sa dan am yang dimana ketika register awal dia profilenya kosong dan nanti saat admin membuat sa atau am dia bisa pilih untuk user yang mana dimana itu akan mengisi profile_id

Add Query ini di Postgessnya
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";


tambahkan onprogress untuk selain win sama lost

Ubah Activity jadi ProgressUpdate ubah menjadi textarea (FE)

Ganti jadi CutomerVisit (FE)

add image untuk customervisit dengan blob

gak ubah status di detail (FE)

Dashbord List Pipeline yang gak ada update 30 hari 

Dashbord di ubah menjad sankey 

nanti ada add proposal untuk pipline

untuk yang Proposal itu 1to1 dengan pipeline

iaisnya
- Judul*
- NoProposal* Uniq
- File*
- RFA File
- RFI File 

Nama File Ambil dari NumberProposal

NomorUrut/ict/Inisial SA/SCD/TP/Bulan MMYY
001
002
003 is_deleted
004

tambah Kolom SA dan lainnya tambahkan inisial 

Tambahkan Feedback 