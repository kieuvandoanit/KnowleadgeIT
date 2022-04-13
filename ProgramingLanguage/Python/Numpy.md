# Thao tác với thư viện Numpy
```py
import numpy as np

a = [1,2,3,4]
type(a) //=> list

arr1 = np.array(a)
type(arr1) //=> numpy.ndarray

A = np.arange(10)
A //=> array([0,1,2,3,4,5,6,7,8,9])

B = np.arange(5,50,3)
B //=> array([5,8,11,14,17,20,23,26,29,32,35,38,41,44,47])
```
```py
mangA = np.array([1,2,3,4,5])
mangA //=> array([1,2,3,4,5])

mangB = np.arange(10)
mangB //=> array([0,1,2,3,4,5,6,7,8,9])

mangB.reshape(2,5)
mangB //=> array([[0,1,2,3,4], [5,6,7,8,9]])

abc = np.array([[12,3,2,1,2,2],[23,2,3,2,1,2]])
abc.shape //=> (2,6)
```
# Array Arithmetic
```py
import numpy as np
arr = np.array([[1,2,3,4],[5,6,7,8]])

arr + 10 //=> array([[11,12,13,14],[15,16,17,18]])

# Transpose
A = np.arange(25).reshape(5,5)
A //=> array([[0,1,2,3,4],[5,6,7,8,9],[10,11,12,13,14],[15,16,17,18,19],[20,21,22,23,24]])

A.T //=> 1 mảng đảo ngược dòng thành cột
```

```py
import numpy as np

A = np.arange(25).reshape(5,5)
A 
# array([[ 0,  1,  2,  3,  4],
#        [ 5,  6,  7,  8,  9],
#        [10, 11, 12, 13, 14],
#        [15, 16, 17, 18, 19],
#        [20, 21, 22, 23, 24]])

A.sum() //=> 300
```
# Các hàm xử lý trong Array Numpy
```py
import numpy as np
x = np.random.randint(1,10)

x = []
y = []

for i in range(10):
    x.append(np.random.randint(1,10))
    y.append(np.random.randint(1,10))

# Tổng 2 mảng x, y
np.add(x, y) //=> array([17, 12, 8, 17, 11, 8, 12, 6, 11, 8])
# maximum(x, y) => trả ra 1 array lấy các phần tử lớn hơn ở 2 mảng tương ứng
np.maximum(x, y)
# minimum(x, y) => trả ra 1 array lấy các phần tử nhỏ hơn ở 2 mảng tương ứng
np.minimum(x, y)
np.sqrt(x)
np.square(x)
np.divide(x,y)
np.power(x, y) # x mũ y

x.sort() # sap xep tang dan
np.unique(y) # Loai cac phan tu giong nhau
b = np.greater(x,y) # Tra ra mang boolean neu X[i] > Y[i]
b.all() # tra ve false neu  b chua 1 gia tri False
b.any() # Tra ve true b chua 1 gia tri True
```