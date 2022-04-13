# Hướng đối tượng 
### Create class
```py
class Car:
    fuel = "Xăng"
    maxspeed = 150
polo = Car()
print(polo.fuel) => // Xăng

class Car:  
    fuel = "Xăng"
    maxspeed = 150

    def drive(self):
        print("Xe chạy với tốc độ: ", self.maxspeed)
mini = Car()
mini.drive() => //Xe chạy với tốc độ: 150
```
### Constructor
```py
class Student:
    def __init__(self, name, age):
        print("Name: ", name, "Age :", age)
jackson = Student("Tony Teo", 26) => // Name: Tony Teo Age : 26
```
```py
class Student:
    def __init__(self, name, age):
        print("Name: ", name, "Age :", age)
    def __str__(self):
        return("-------------------------")
tuan = Student("Vu Quoc Tuan", 26)
print(tuan) 
====> // Nam : Vu Quoc Tuan Age : 26
====> // ------------------------------
```
```py
class Student:
    def __init__(self, name, age):
        print("Name: ", name, "Age :", age)
    def __str__(self):
        return("-------------------------")
    def __del__(self):
        print("Destroyed")
tony = Student("Tony Teo", 26)
del tony // => Destroyed
```
### Inheritance (Kế thừa)
```py
class Person:
    def name(self, ten):
        return("Tôi tên là: ", ten)
asia = Person()
print(asia.name("Vũ Quốc Tuấn"))

class Student (Person):
    def age(self, age):
        return("Tuổi là : ", age)
teo = Student()
print(teo.name("Tony Teo"))
print(teo.age(96))
```
```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def info(self):
        print("Chào bạn tôi tên là ", self.name, "tuổi của tôi là ", self.age)
asia = Person("Vũ Quốc Tuấn", 26)
asia.info() 
```
```py
class Student (Person):
    def __init__(self,name, age, grade):
        Person.__init__(self, name, age)
        self.grade = grade
    def infoGrade (self):
        print("Lớp của bạn là ", self.grade)
hsb = Student("Conan Vu", "15", "9/9")
hsb.info()
hsa.infoGrade()
```

- Kế thừa đa lớp
```py
class Person:
    def __init__ (self, name, age):
        self.name = name
        self.age = age
    def hoten (self):
        print("Ho ten: ", self.name)
class Addr:
    def __init__(self, phone, email):
        self.phone = phone
        self.email = email
    
    def dienthoai(self):
        print("Dien thoai: ", self.phone)
class Student(Person, Addr):
    def __init__(self, name, age, phone, email, grade):
        Person.__init__(self, name, age)
        Addr.__init__(self, phone, email)
        self.grage = grade
    def lop(self):
        print("Lop hoc cua ban : ",self.grade)
teo = Student("Vu Quoc Tuan", "26", "9/9","0930493002", "tuandeaptrai@gmail.com")
```