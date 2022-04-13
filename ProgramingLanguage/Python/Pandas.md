# Pandas Series
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

S1 = Series([10, 20, 30, 40])
S1
#   0   10
#   1   20
#   2   30
#   3   40
#   dtype: int64

S2 = Series([10, 20, 30, 40], index=['A', 'B', 'C', 'D'])
#   A   10
#   B   20
#   C   30
#   D   40
#   dtype: int64

diem = [10, 9, 10, 7]
hocsinh = ["Teo", "Ti", "Tuan", "Tun"]

S3 = Series(diem, index = hocsinh)
S3
#   Teo   10
#   Ti     9
#   Tuan  10
#   Tun    7
#   dtype: int64

s3d = S3.to_dict()
s3d
# {'Teo': 10, 'Ti': 9, 'Tuan': 10, 'Tun': 7}
S4 = Series(s3d)
S4
#   Teo   10
#   Ti     9
#   Tuan  10
#   Tun    7
#   dtype: int64
S4.name = "Danh sach"
S4
#   Teo   10
#   Ti     9
#   Tuan  10
#   Tun    7
#   Name: Danh sach, dtype: int64
```
- Thao tác index và reindex trong python

```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

diem = [10, 9, 10, 7]
hocsinh = ["Teo", "Ti", "Tuan", "Tun"]
S3 = Series(diem, index = hocsinh)

S3.index
# Index(['Teo', 'Ti', 'Tuan', 'Tun'], dtype='object')

S3.values
# array([10, 9, 10, 7], dtype=int64)

x = list(range(11, 16))
ind = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

S5 = Series(x, ind)
S6 = S5.reindex(ind2, fill_value = 0)

S6
#   A   11
#   B   12
#   C   13
#   D   14
#   E   15
#   F    0
#   G    0
# dtype: int64
```
- Lấy và lọc dữ liệu trong array
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

diem = [10, 9, 10, 7]
hocsinh = ["Teo", "Ti", "Tuan", "Tun"]
S3 = Series(diem, index = hocsinh)
S4 = S3 * 2
#   Teo   20
#   Ti    18
#   Tuan  20
#   Tun   14
#   dtype: int64
S4[['Ti', 'Tun']]
#   Ti    18
#   Tun   14
#   dtype: int64
S4[S4 < 20]
#   Ti    18
#   Tun   14
#   dtype: int64
S4[S4 == 20]
#   Teo    20
#   Tuan   20
#   dtype: int64
```
- Sắp xếp và lọc dữ liệu
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

diem = [10, 9, 10, 7]
hocsinh = ["Teo", "Ti", "Tuan", "Tun"]
S3 = Series(diem, index = hocsinh)

S8 = Series([0, 1, 2], index = ['A', 'B', 'C'])
S9 = Series([3, 4, 5, 6], index = ['A', 'B', 'C', 'D'])
S8 + S9
#   A   3.0
#   B   5.0
#   C   7.0
#   D   NaN
#   dtype: float64

ind = "a b c d e f g h i j".split()
ind
# ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
type(ind)
# list
x = []
for i in range(10):
    x.append(np.random.randint(1, 100))
x
# [30, 36, 99, 27, 62, 19, 94, 56, 14, 99]
S10 = Series(x, index = ind)
```
- Dataframe
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

df1 = pd.read_clipboard()
df1
df1.columns # trả ra list các column
df1.head() # trả ra dataframe các dòng đầu 5 dòng
df1.tail() # trả ra dataframe các dòng cuối 5 dòng cuối
df1.ColumnName
```
- Tạo dataframe bằng Dictionary
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

diem = [10,8,6,9]
sinhvien = ["Teo", "Ti", "Tun", "Tuan"]

data = {'diem': diem, 'sinhvien':sinhvien}
data
# {'diem':[10, 8, 6, 9], 'sinhvien':['Teo', 'Ti', 'Tun', 'Tuan']}

df2 = DataFrame(data)
ind = "A B C D E F".split()
cols = "col1 col2 col3 col4 col5 col6".split()

x = []
for i in range(36)
    x.append(np.random.randint(1,100))

x = np.array(x)
x = x.reshape(6,6)

df3 = DataFrame(x, index = ind, columns = cols)

new_ind = "A B C D E F G H K".split()
df4 = df3.reindex(new_ind, fill_value = 0)
```
- Lấy và lọc dữ liệu trong DataFrame
```py
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
from numpy.random import randn

# Lấy 1 column ra
df1['col1']

# lấy 2 column ra
df1[['col1','col2']]

# Lấy những dòng có giá trị lớn hơn 50
df1[df1['col4'] > 50]

# Lấy dòng E
df1.ix['E']
```
- Xóa hàng/cột
```py
# Xóa dòng
df1.drop('D')

# Xóa cột
df1.drop('col1', axis = 1)
```
- Các phép toán DataFrame
```py
# Tổng các cột
df1.sum()

# Tổng các dòng
df1.sum(axis = 1)

# Lấy giá trị max ở các cột
df1.max()

# Lấy Id của dòng có giá trị lớn nhất trong cột
df1.idxmax()
```