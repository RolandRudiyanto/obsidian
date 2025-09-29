# DDL (Data Definition Language)
->  Command dalam sql untuk mendefinisikan schema dalam database seperti:
- Create : Untuk membuat table
- Drop : Untuk menghapus table dalam database
- Alter : Digunakan untuk mengubah struktur dari table
- Truncate : untuk menghapus semua record dalam database
# DML(Data Manipulation Language)
-> Command dalam sql yang digunakan untuk memanipulasi data dalam database seperti:
- Insert : Memasukan data ke dalam table
- Update : Memperbarui data dalam table
- Delete : Menghapus record dalam table
- Select : Untuk memanggil data dalam table
# DB2
-> DB2 merupakan model database server yang dikembangkan oleh IBM, yang dapat dijalankan secara single user atau multi user
Bahasa yang digunkaan pada DBMS DB2 menggunakan standar SQL (Structure Query Language)

https://www.ibm.com/docs/en/db2/11.5.x?topic=system-linux (Docker Install DB2)

(Make Docker)
docker run -h db2server --name db2server --restart=always --detach --privileged=true -p 50000:50000 --env-file .env_list -v /Docker:/database icr.io/db2_community/db2

. ~db2inst1/sqllib/db2profile