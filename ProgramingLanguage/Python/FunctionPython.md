# Function trong Python
```
def hello ():
    print("Hello World)
hello()
```
### Function parameter
```
def tong(*data)
    t = 0
    for item in data:
        t = t + item
    return t
```
- Xử lý more data trong Python
```
chuoi = "{:10} {:10}".format("Apple", 10000)
print(chuoi)

def dienthoai (**data):
    count = 0
    for name, price in data.item():
        row = "{:20}{:10}".format(name, price)
        print(row)
        count = count + price
    return count

dienthoai(iphone=50000,nokia=1000,samsung=5500)
```
- Ví dụ function python
```
def tong (n1, n2, n3, *data, **list):
    t1 = t2 = t3 = 0
    t1 = n1 + n2 + n3
    for item in data:
        t2 = t2 + item
    for k,v in list.item():
        t3 = t3 + v
    t = [t1, t2, t3]
    return t
```
### Iterators in python
- Để truy suất từng phần tử của 1 list or 1 string.
```
l = [1,2,3,4,5,6]
I = iter(l)
type(I) // => list_iterator
I.__next__() => 1
I.__next__() => 2
I.__next__() => 3
I.__next__() => 4
I.__next__() => 5
I.__next__() => 6
```
### Generator Function
- `return`: hàm sẽ ngừng khi gặp return
- `yield`: hàm sẽ trả ra giá trị giống return nhưng sẽ tiếp tục chạy tiếp
Ví dụ:
```
def myRange(start, length, step):
    i = start
    while (i < length):
        yield i
        i = i + 1
```
### Bài tập 1
- Viết 1 function truyền vào 1 list các string, trả ra 1 dict số lượng các ký tự trong string đó.
```
def countChar(*data):
    dic = {}
    for item in data:
        for i in item:
            i = i.upper()
            if i in dic:
                dic[i] = dic[i] + 1
            else:
                dic[i] = 1
    return dic
```
### Bài tập 2
- Viết 1 function truyền vào 1 tham số. xử lý giống hàm range có thể truyền vô 1, 2, 3 param.
```
def myRange (*thamso):
    start = length=step = 0
    if(len(thamso) == 3):
        start = thamso[0]
        length = thamso[1]
        step = thamso[2]
    elif (len(thamso) == 2):
        start = thamso[0]
        length = thamso[1]
        step = 1
    else
        start = 0
        length = thamso[0]
        step = 1
    while(i < length):
        yield i
        i = i + step
```