Mode User
- Username
- Password
- RoleID (FK)
Model Role
- Name
Model Permision
- Name
Model RolePermission
- RoleID (FK)
- PermissionID(FK)

Example:
Kita Punya 2 Role yaitu Admin dan Role A yang dimana Admin dapat mengakes semua api sedangan Role A hanya bisa mengakses beberapa api saja
Untuk konsep midlewarenya:
- Mengecek Role dari user
- Mencari Permision apa saja yang bisa di akses oleh Role itu
Alasan menggunakan konsep seperti ini agar role lebih dinamis yang dimana jika nantinya terdapat Role baru yang hanya bisa mengakses hal lain lagi dapat di tambahkan kembali