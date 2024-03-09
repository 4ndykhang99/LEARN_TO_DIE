# C++ What is OOP?
OOP stands for Object-Oriented Programming.

Procedural programming is about writing procedures or functions that perform operations on the data, while object-oriented programming is about creating objects that contain both data and functions.

Object-oriented programming has several advantages over procedural programming:

- OOP is faster and easier to execute.
- OOP provides a clear structure for the programs.
- OOP helps to keep the C++ code DRY "Don't Repeat Yourself", and makes the code easier to maintain, modify and debug.
- OOP makes it possible to create full reusable applications with less code and shorter development time.

Tip: The "Don't Repeat Yourself" (DRY) principle is about reducing the repetition of code. You should extract out the codes that are common for the application, and place them at a single place and reuse them instead of repeating it.

# C++ What are Classes and Objects?

> Classes and objects are the two main aspects of object-oriented programming.

Look at the following illustration to see the difference between class and objects:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/065357c1-bf96-4612-a523-70437fa0c43c)

Another example:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/713a1af4-1ad0-44b7-8e6c-cbaa53c5f291)

So, a class is a template for objects, and an object is an instance of a class.

When the individual objects are created, they inherit all the variables and functions from the class.
# Tinh chất của OOP trong C++
> OOP (Object-Oriented Programming - Lập trình hướng đối tượng) ra đời với mục đích giải quyết một số vấn đề trong lập trình truyền thống dựa trên hướng thủ tục. Dưới đây là một số lý do chính về tại sao OOP ra đời:
> 1. Quản lý phức tạp hóa: Trong lập trình hướng thủ tục, khi chương trình trở nên lớn và phức tạp, việc quản lý mã nguồn và tương tác giữa các thành phần trở nên khó khăn. OOP giúp tổ chức mã nguồn theo các đối tượng riêng biệt, từ đó giảm thiểu sự phức tạp và dễ dàng quản lý.
> 2. Tái sử dụng mã nguồn: OOP khuyến khích việc sử dụng lại mã nguồn thông qua khái niệm kế thừa và đa hình. Điều này giúp giảm thiểu việc viết lại mã nguồn và tăng tính tái sử dụng, giúp tiết kiệm thời gian và công sức lập trình.
> 3. Tăng tính linh hoạt và mở rộng: OOP cho phép mở rộng và mở rộng chức năng của chương trình một cách linh hoạt thông qua kế thừa, đa hình và đóng gói. Ta có thể thêm mới các đối tượng, thuộc tính và phương thức mà không ảnh hưởng đến các phần khác của chương trình.
> 4. Tính module cao: OOP giúp tạo ra các module (đối tượng) độc lập, có khả năng tái sử dụng và dễ dàng kiểm tra. Điều này giúp tăng tính module và giảm sự phụ thuộc giữa các phần của chương trình.
> 5. Tính bảo mật và ổn định: OOP hỗ trợ việc ẩn thông tin và thiết kế chặt chẽ, giúp tăng tính bảo mật và ổn định của chương trình. Thông qua việc sử dụng đóng gói (encapsulation), ta có thể ẩn thông tin và cung cấp các phương thức công khai để tương tác với đối tượng.
>
>  Tóm lại, OOP ra đời để giải quyết các vấn đề trong lập trình truyền thống và mang lại tính linh hoạt, tái sử dụng, mở rộng, module, bảo mật và ổn định cho các dự án phần mềm.

## 1. Phương thức khai báo trong class - Class Methods
> Methods trong class giúp định nghĩa một hàm, chương trình con thuộc về class đó

Có 2 cách để khai báo một hàm trong class: Khai báo bên trong và khai báo bên ngoài.
### a. Khai báo bên trong
Trong example dưới đây, sẽ định nghĩa một chương trình con bên trong class và có tên là ```myfunction```.
```cpp
class MyClass {        // The class
  public:              // Access specifier
    void myMethod() {  // Method/function defined inside the class
      cout << "Hello World!";
    }
};

int main() {
  MyClass myObj;     // Create an object of MyClass
  myObj.myMethod();  // Call the method
  return 0;
}
```

Để định nghĩa một hàm bên ngoài định nghĩa lớp, bạn phải khai báo nó bên trong lớp và sau đó định nghĩa nó bên ngoài lớp. Điều này được thực hiện bằng cách chỉ định tên của lớp, tiếp theo là toán tử phân giải phạm vi ```::```và tiếp theo là tên của hàm.
```cpp
class MyClass {        // The class
  public:              // Access specifier
    void myMethod();   // Method/function declaration
};

// Method/function definition outside the class
void MyClass::myMethod() {
  cout << "Hello World!";
}

int main() {
  MyClass myObj;     // Create an object of MyClass
  myObj.myMethod();  // Call the method
  return 0;
}
```
Hoặc cũng có thể truyền tham chiếu vào hàm:
```cpp
#include <iostream>
using namespace std;

class Car {
  public:
    int speed(int maxSpeed);
};

int Car::speed(int maxSpeed) {
  return maxSpeed;
}

int main() {
  Car myObj; // Create an object of Car
  cout << myObj.speed(200); // Call the method with an argument
  return 0;
}
```
## 2. Hàm dựng trong OOP - Constructor
> Trong lập trình hướng đối tượng, hàm dựng (constructor) là một phương thức đặc biệt của một lớp được gọi tự động khi một đối tượng của lớp đó được tạo. Nó được sử dụng để khởi tạo các thuộc tính và trạng thái ban đầu của đối tượng. Hàm dựng có cùng tên với lớp và không có kiểu trả về.

Dưới đây là một ví dụ về hàm dựng trong ngôn ngữ C++:

```cpp
#include <iostream>

class Person {
private:
    std::string name;
    int age;

public:
    // Hàm dựng
    Person(std::string personName, int personAge) {
        name = personName;
        age = personAge;
        std::cout << "A new person object is created." << std::endl;
    }

    void displayInfo() {
        std::cout << "Name: " << name << std::endl;
        std::cout << "Age: " << age << std::endl;
    }
};

int main() {
    // Tạo một đối tượng Person và gọi hàm dựng
    Person person1("John", 25);

    // Gọi phương thức để hiển thị thông tin
    person1.displayInfo();

    return 0;
}
```

Trong ví dụ trên, chúng ta có một lớp `Person` đại diện cho một người. Lớp này có một hàm dựng có hai tham số `personName` (tên người) và `personAge` (tuổi người). Trong hàm dựng, chúng ta khởi tạo các thuộc tính `name` và `age` của đối tượng dựa trên các giá trị được truyền vào.

Trong hàm `main()`, chúng ta tạo một đối tượng `person1` của lớp `Person` và truyền tên "John" và tuổi 25 vào hàm dựng. Khi đối tượng được tạo, hàm dựng sẽ được tự động gọi và thông báo "A new person object is created". Sau đó, chúng ta gọi phương thức `displayInfo()` để hiển thị thông tin của đối tượng `person1`, bao gồm tên và tuổi.
