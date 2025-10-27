AccountManager (Done)
Login (Done)
Register (Done)
Customer (Done)
Principal (Done)
Product (Done)
SalesStage (Done)
SalesType (Done)
SolutionArchitect (Done)



Buat Table Pengah untuk Principal dan Product
Next API Update
- PATCH API in all master data (Done)
- DELETE API in all master data (Done)
- Add FIlter in Pagination API
- Add API Pipeline, CustomerVisit, PipelineUpdate
- Add configuration email to @infracom-tech.com (Done)
Bug : ID Value Tidak Sesuai

FIX CODE:
- Make Session API 
	-> Session API ini tidak di perlukan karena (https://infoseminar.teknokrat.ac.id/2025/09/04/perang-sesi-login-kapan-sebaiknya-pakai-jwt-dan-kapan-pakai-session/)
		- Backend login saya menggunakan JWT yang dimana sudah menggirimkan token saat login
		- membangun **arsitektur _microservices_ atau sistem terdistribusi** yang kompleks
		- Lalu JWT juga sudah mendukung untuk Multiuser karena masing masing login menyimpan kode JWT maising masing.
- Fix Res Error Code 
	500 (Internal Server Error) → means the server crashed or misbehaved internally.
	400 (Bad Request) → means the client sent invalid data, which fits your case perfectly.
	![[WhatsApp Image 2025-10-13 at 18.18.27_160fe4de.jpg]]
	![[WhatsApp Image 2025-10-13 at 18.18.34_cae5d4f6.jpg]]
	![[WhatsApp Image 2025-10-13 at 18.18.44_2d2daa18.jpg]]![[WhatsApp Image 2025-10-13 at 18.18.58_82358404.jpg]]![[WhatsApp Image 2025-10-13 at 18.19.11_bfeb4f48.jpg]]![[WhatsApp Image 2025-10-13 at 18.19.20_0d1dd9bd.jpg]]
	
	{
	  "success": false,
	  "error": {
	    "code": "INVALID_EMAIL_DOMAIN",
	    "message": "Email must use @infracom-tech.com domain",
	    "status": 422,
	    "details": {
	      "field": "email",
	      "expected_domain": "@infracom-tech.com"
	    },
	    "timestamp": "2025-10-13T10:25:45.000Z",
	    "path": "/api/v1/register"
	  }
	}

Wireframe untuk bagian Pipeline dan Details Pipeline 
lalu untuk dashbord


Tambah Fitur Supervisor bisa kirim email (tanya ke pak pintong tantang ini)

![[Pasted image 20251022204138.png]]