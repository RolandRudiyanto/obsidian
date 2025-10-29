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

Dashbord List Pipeline yang gak ada update 30 hari (p.updated_at;<;NOW() - INTERVAL '30 days') (Done)

Dashbord di ubah menjad sankey (Tunggu Data)

nanti ada add proposal untuk pipline

untuk yang Proposal itu 1to1 dengan pipeline (Done)

iaisnya
- Judul*
- NoProposal* Uniq
- File*
- RFA File
- RFI File 

Nama File Ambil dari NumberProposal 

NomorUrut/ict/Inisial SA/SCD/TP/Bulan MMYY (Done)
001
002
003 is_deleted
004

tambah Kolom SA dan lainnya tambahkan inisial 

Tambahkan Feedback 

Tambahkan Edit dan Delete untuk Proposal (Done)


SELECT 
    ss.sales_stage AS sales_stage_name,
    COUNT(p.id) AS total_pipelines,
    COUNT(DISTINCT pro.id) AS total_pipelines_with_proposal
FROM pipelines p
JOIN sales_stages ss ON p.sales_stage_id = ss.id
LEFT JOIN proposals pro ON pro.pipeline_id = p.id
WHERE ss.sales_stage ILIKE 'win' OR ss.sales_stage ILIKE 'lost'
GROUP BY ss.sales_stage
ORDER BY ss.sales_stage;



SELECT 
    ss.sales_stage AS sales_stage_name,
    COUNT(p.id) AS total_pipeline
FROM sales_stages ss
LEFT JOIN pipelines p ON p.sales_stage_id = ss.id
GROUP BY ss.sales_stage
ORDER BY ss.sales_stage;

