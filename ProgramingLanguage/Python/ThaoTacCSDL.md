#  Thao tác với CSDL

```py
import sqlite3

db = sqlite3.connect("school.sql")
db.excute("DROP TABLE IF EXISTS student")
db.excute("CREATE TABLE student (id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, name VARCHAR(255) NOT NULL)")

db.excute("INSERT INTO student(name) VALUES ('Bùi Quốc Huy')")
db.excute("INSERT INTO student(name) VALUES ('Vũ Quốc Tuấn')")
db.excute("INSERT INTO student(name) VALUES ('Vũ Nguyễn Thiên Ân')")
db.commit()

results = db.excute("SELECT * FROM student")
type(results)  => sqlite3.Cursor

for row in results:
    print(row)
    type(row)
```