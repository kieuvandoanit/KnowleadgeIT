# Module trong Python
### Các module có sẵn trong Python
```py
import random as ra

print(ra.randint(1,100000)) // 41989
```
- Document: [Tài liệu](https://docs.python.org/3/py-modindex.html)

### Tự xây dựng module trong python
- Tạo module myCode.py
```py
def greet(n):
    i = 0
    while i < n:
        i = i + 1
        print("Hello QHONLINE.EDU.VN")
def sumNums(*args):
    sum = 0
    for item in args:
        sum += item
    return sum
def myRange (start, stop, step):
    i = start
    while i <= stop
        yield i
        i += step
```
- Import my module
```py
import myCode as my

my.greet(10)

my.sumNums(10,20,30,40,50) => 10

l = my.myRange(1,10,2)

list(l)
```
### Exception-handling
```py
try:
    a = 100
    b = 0

    x = a/b
except:
    print("Loi: So b phai khac 0")
```
```py
try: 
    a = 100
    b = 0
    x = a/b
except ZeroDivisionError as error:
    print("Lỗi : ", error)
```
```py
try: 
    a = 100
    b = 10

    x = (a * b) + (1000 * a) / (a / b)
    print("x = ", x)

    f = open("teo.txt","r")
    for line in f:
        print(line)
except ZeroDivisionError as error:
    print("Lỗi : ", error)
except FileNotFoundError as error:
    print("Lỗi : ", error)

```