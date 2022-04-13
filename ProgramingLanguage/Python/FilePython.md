# Thao tác với file trong Python
### Read file
```py
fp = open("data/list.txt", "r")
for line in fp:
    print(line, end="")
fp.close() 
```
### Write file
```py
fp = open("data/write.txt","w")
fp.write("Tuan")
fp.write("\n")
fp.write("Tuan")
fp.write("\n")
fp.write("Tuan")
fp.write("\n")

print("Done")
```
### Buffer ghi file
```py
BUFFERSIZE = 25000
rFile = open("data/data.txt", "r")
wFile = open("data/list.txt","w")

buffer = rFile.read(BUFFERSIZE)

i = 0
while (len(buffer)):
    i = i+ 1
    wFile.write(buffer)
    print(i, "{} byte".format(len(buffer)))
    buffer = rFile.read(BUFFERSIZE)
print("Done")
```
### Các method xử lý file
```py
f = open("data/data.txt", "r")
fpos = f.tell()
print("Doc toi vi tri ",fpos)

line = f.readline()
print(line, end = "")

fpos = f.tell()
print("Doc toi vi tri ", fpos)
```
- f.tell(): lấy ra vị trí con trỏ đang ở
- f.seek(a): đưa con trỏ tới vị trí a
