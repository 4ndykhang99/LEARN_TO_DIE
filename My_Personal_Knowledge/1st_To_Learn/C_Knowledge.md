# C PROGRAMMING AND EMBEDDED QUESTION
## 1. Các kiểu dữ liệu của biến - size của từng kiểu dữ liệu ?
- Kiểu int:
  - kích thước 2 - 4 bytes tùy người dùng khai báo
  - định dạng %d, %i

- Kiểu float và double:
  - float: 4 bytes
  - Double: 8 bytes
  - Định dạng: %f, %lf

- Kiểu Char:
  - kích thước: 1 byte
  - định dạng: %c

- Short và Long:
  - Short: 2 bytes
  - Long: 4 đến 8 bytes

- Bool:
  - Kích thước: 1 byte

## 2. Volatile, static, inline, extern.
- Volatile:

  > Định nghĩa: Volatile là một từ khóa được sử dụng để chỉ rằng biến có thể thay đổi bất kỳ lúc nào bởi các yếu tố bên ngoài (ví dụ: ngắt, thiết bị phần cứng).
  
  - Ưu điểm:
    -Đảm bảo rằng trạng thái của biến luôn được cập nhật chính xác.
    -Hữu ích trong việc làm việc với các biến liên quan đến ngắt hoặc thiết bị ngoại vi.
  - Nhược điểm:
    -Có thể làm tăng độ phức tạp của mã nguồn.
    -Không phù hợp cho tất cả các biến.
- Static:

  > Định nghĩa: Static là một từ khóa được sử dụng để chỉ rằng biến hoặc hàm chỉ có phạm vi trong cùng một tệp nguồn.
  
  - Ưu điểm:
    - Biến static không bị xung đột với các biến cùng tên trong các tệp nguồn khác.
    - Hàm static không thể gọi từ bên ngoài tệp nguồn.
  - Nhược điểm:
    - Không thể truy cập từ các tệp nguồn khác.
    - Có thể làm tăng kích thước của tệp thực thi.
- Inline:
  
  > Định nghĩa: Inline là một từ khóa được sử dụng để yêu cầu trình biên dịch thực hiện việc nhúng mã của hàm trực tiếp vào nơi gọi hàm.
  
  - Ưu điểm:
    - Tối ưu hóa hiệu suất bằng cách tránh gọi hàm.
    - Giảm thời gian gọi hàm.
  - Nhược điểm:
    - Tăng kích thước của mã thực thi.
    - Không phù hợp cho các hàm lớn hoặc phức tạp.
- Extern:
  
  > Định nghĩa: Extern là một từ khóa được sử dụng để khai báo biến hoặc hàm đã được định nghĩa ở nơi khác.
  
  - Ưu điểm:
    - Cho phép sử dụng biến hoặc hàm từ các tệp nguồn khác.
    - Hữu ích trong việc chia sẻ mã nguồn giữa các tệp.
  - Nhược điểm:
    - Cần phải đảm bảo rằng biến hoặc hàm đã được định nghĩa ở nơi khác.
    - Có thể gây xung đột tên biến hoặc hàm.
## 3. Pointer
> Con trỏ là một biến đặc biệt trong một số ngôn ngữ lập trình, thường được sử dụng để lưu trữ địa chỉ bộ nhớ của một biến khác. Con trỏ cho phép chúng ta truy cập và thay đổi giá trị của biến được trỏ tới thông qua việc tham chiếu đến địa chỉ bộ nhớ.

- Con trỏ: Con trỏ là một biến chứa địa chỉ bộ nhớ của một biến khác.
  - Để khai báo con trỏ, chúng ta sử dụng dấu ```*``` trước tên biến. Ví dụ:
  
    ```c
    int* ptr;
    ```
  - Để lấy địa chỉ của một biến, chúng ta sử dụng toán tử ```&```. Ví dụ:
    
    ```c
    int num = 10;
    int* ptr = &num;
    ```
  - Để truy cập giá trị của biến được trỏ tới, chúng ta sử dụng toán tử ```*``` trước con trỏ. Ví dụ:

    ```c
    int value = *ptr;
    ```
- Con trỏ hàm: Con trỏ hàm là một biến chứa địa chỉ của một hàm.
  - Để khai báo con trỏ hàm, chúng ta sử dụng cú pháp tương tự như khai báo con trỏ, nhưng với kiểu dữ liệu là kiểu chữ ký của hàm. Ví dụ:

    ```c
    int (*funcPtr)(int, int);
    ```
  - Để gán con trỏ hàm cho một hàm cụ thể, chúng ta chỉ cần sử dụng tên hàm. Ví dụ:

    ```c
    funcPtr = sum;
    ```
  - Để gọi hàm thông qua con trỏ hàm, chúng ta sử dụng cú pháp tương tự như gọi hàm trực tiếp. Ví dụ:

    ```c
    int result = (*funcPtr)(a, b);
    ``` 
    or
    
    ```c
    int result = funcPtr(a, b);
    ```
  
- Con trỏ hằng và hằng con trỏ:
  - Con trỏ hằng (const pointer): Một con trỏ hằng không thể thay đổi địa chỉ mà nó trỏ tới. Ví dụ:

    ```c
    int* const ptr = &num;
    ```
  - Hằng con trỏ (pointer to constant): Một hằng con trỏ không thể thay đổi giá trị của biến được trỏ tới. Ví dụ:

    ```c
    const int* ptr = &num;
    ```
    or
    ```c
    int const* ptr = &num;
    ```
## 4. Truyền tham trị, tham chiếu
> Truyền tham trị (pass by value) và truyền tham chiếu (pass by reference) là hai phương pháp khác nhau để truyền thông tin vào một hàm trong ngôn ngữ lập trình. Dưới đây là mô tả chi tiết về cả hai phương pháp:

- Truyền tham trị (Pass by Value):
  - Khi truyền tham trị, một bản sao của giá trị được tạo ra và truyền vào hàm.
  - Trong hàm, các thay đổi đối với tham số không ảnh hưởng đến giá trị ban đầu của biến gốc.
  - Bản sao giá trị được sử dụng trong hàm và không có tác động đến biến gốc.
  - Khi hàm kết thúc, bản sao giá trị bị hủy và giá trị ban đầu của biến gốc không bị thay đổi.
  - Ví dụ về truyền tham trị trong C:
 
    ```c
    void increment(int num) {
        num++;
    }
    
    int main() {
        int x = 5;
        increment(x);
        // Giá trị của x không thay đổi vì truyền tham trị
        // num trong hàm increment là một bản sao của x
        // Thay đổi giá trị của num không ảnh hưởng đến x
        return 0;
    }
    ```

- Truyền tham chiếu (Pass by Reference):
  - Khi truyền tham chiếu, địa chỉ của biến gốc được truyền vào hàm.
  - Hàm có thể truy cập và thay đổi giá trị của biến gốc thông qua tham chiếu.
  - Bất kỳ thay đổi nào đối với tham chiếu cũng ảnh hưởng đến giá trị của biến gốc.
  - Truyền tham chiếu thường được sử dụng để truyền các đối tượng lớn hoặc để thay đổi giá trị của biến bên ngoài hàm.
  - Ví dụ về truyền tham chiếu trong C:
 
    ```c
    void increment(int& num) {
        num++;
    }
    
    int main() {
        int x = 5;
        increment(x);
        // Giá trị của x tăng lên 1 vì truyền tham chiếu
        // num trong hàm increment là một tham chiếu đến x
        // Thay đổi giá trị của num ảnh hưởng đến x
        return 0;
    }
    ```
## 5. Struct, union, macro
Các khái niệm struct, union và macro là những thành phần cơ bản trong nhiều ngôn ngữ lập trình. Dưới đây là sự khác nhau và ưu nhược điểm của mỗi khái niệm:

1. Struct:
   - Struct (cấu trúc) là một kiểu dữ liệu tự định nghĩa trong nhiều ngôn ngữ lập trình, cho phép lưu trữ các thành phần dữ liệu khác nhau trong một đối tượng.
   - Các thành phần dữ liệu trong một struct được gọi là các trường (fields) và có thể có các kiểu dữ liệu khác nhau.
   - Mỗi đối tượng struct có thể có các trường riêng biệt và các phương thức (trong một số ngôn ngữ).
   - Ưu điểm:
     - Cho phép tổ chức dữ liệu theo cách tùy chỉnh và lưu trữ nhiều thông tin liên quan trong một đối tượng.
     - Dễ dàng truy cập và xử lý các trường dữ liệu trong struct.
   - Nhược điểm:
     - Chiếm dụng không gian bộ nhớ lớn hơn so với việc sử dụng các kiểu dữ liệu nguyên thủy.
     - Không hỗ trợ tính kế thừa (inheritance) và đa hình (polymorphism) như các đối tượng (object) trong hướng đối tượng.
 ```cpp
   // Định nghĩa một struct để lưu trữ thông tin sinh viên
   struct Student {
       int id;
       std::string name;
       int age;
   };

   int main() {
       // Khởi tạo một đối tượng sinh viên
       Student student1;
       student1.id = 1;
       student1.name = "John";
       student1.age = 20;

       // Truy cập và hiển thị thông tin sinh viên
       std::cout << "Student ID: " << student1.id << std::endl;
       std::cout << "Student Name: " << student1.name << std::endl;
       std::cout << "Student Age: " << student1.age << std::endl;

       return 0;
   }
   ```
2. Union:
   - Union (liên hợp) cũng là một kiểu dữ liệu tự định nghĩa trong nhiều ngôn ngữ lập trình, cho phép lưu trữ các thành phần dữ liệu khác nhau trong cùng một vùng nhớ.
   - Union sử dụng cùng một vùng nhớ cho tất cả các trường, chỉ lưu trữ trường được sử dụng gần nhất.
   - Khi một trường của union được gán giá trị, các trường khác trong union sẽ không còn giá trị hợp lệ.
   - Ưu điểm:
     - Tiết kiệm không gian bộ nhớ bởi vì chỉ cần lưu trữ trường được sử dụng gần nhất.
     - Hữu ích khi cần lưu trữ các kiểu dữ liệu khác nhau trong cùng một vùng nhớ.
   - Nhược điểm:
     - Không đảm bảo tính an toàn về dữ liệu, do không có kiểm tra kiểu dữ liệu trong union.
     - Không thể truy cập đồng thời các trường khác nhau trong union.
 ```cpp
   // Định nghĩa một union để lưu trữ giá trị nguyên hoặc số thực
   union Number {
       int intValue;
       float floatValue;
   };

   int main() {
       // Khởi tạo một đối tượng union và gán giá trị
       Number number;
       number.intValue = 10;

       // Truy cập và hiển thị giá trị nguyên
       std::cout << "Integer Value: " << number.intValue << std::endl;

       // Gán giá trị số thực
       number.floatValue = 3.14;

       // Truy cập và hiển thị giá trị số thực
       std::cout << "Float Value: " << number.floatValue << std::endl;

       // Giá trị nguyên không còn hợp lệ sau khi gán giá trị số thực
       std::cout << "Invalid Integer Value: " << number.intValue << std::endl;

       return 0;
   }
   ```

Union thường được dùng để tiết kiệm tài nguyên, khi mà chỉ một tài nguyên trong số các tài nguyên được khai báo được sử dụng tại một thời điểm:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/6e8cd0d6-9741-498f-b16b-4191fdfaaacf)


3. Macro:
   - Macro là một khái niệm trong ngôn ngữ lập trình cho phép định nghĩa và mở rộng mã nguồn trong quá trình biên dịch.
   - Macro được định nghĩa bằng cách sử dụng từ khóa `#define` hoặc các macro hỗ trợ khác.
   - Macro là một thay thế văn bản trong mã nguồn và được mở rộng trước khi quá trình biên dịch bắt đầu.
   - Ưu điểm:
     - Mở rộng mã nguồn một cách linh hoạt và tiết kiệm thời gian viết mã.
     - Cho phép định nghĩa các hằng số, hàm tắt và các tùy chọn biên dịch.
   - Nhược điểm:
     - Khó theo dõi và gỡ lỗi do macro không có phạm vi (scope) và mở rộng trước thời điểm biên dịch.
     - Có thể dẫnđến các lỗi trong quá trình mở rộng macro, như trùng tên biến hoặc lỗi cú pháp.
  ```cpp
   // Định nghĩa một macro để tính toán bình phương của một số
   #define SQUARE(x) ((x) * (x))

   int main() {
       int num = 5;

       // Sử dụng macro để tính toán bình phương
       int square = SQUARE(num);

       // Hiển thị kết quả
       std::cout << "Square of " << num << " is " << square << std::endl;

       return 0;
   }
   ```
## 6. Dynamic memory allocation
> Dynamic memory allocation (phân bổ bộ nhớ động) là quá trình cấp phát và giải phóng bộ nhớ trong quá trình thực thi chương trình. Thay vì sử dụng bộ nhớ tĩnh được cấp phát tĩnh trước khi chương trình chạy, dynamic memory allocation cho phép chương trình yêu cầu và giải phóng bộ nhớ theo nhu cầu thực tế trong quá trình thực thi.

Ưu điểm của dynamic memory allocation:
1. Linh hoạt: Cho phép cấp phát và giải phóng bộ nhớ theo nhu cầu thực tế của chương trình.
2. Tiết kiệm tài nguyên: Chỉ cấp phát bộ nhớ khi cần thiết, giúp tối ưu sử dụng tài nguyên hệ thống.
3. Địa chỉ bộ nhớ liên tục: Dynamic memory allocation cho phép cấp phát một khối bộ nhớ liên tục, giúp tối ưu việc truy cập và xử lý dữ liệu.

Nhược điểm của dynamic memory allocation:
1. Quản lý bộ nhớ phức tạp: Việc quản lý bộ nhớ động có thể phức tạp hơn so với bộ nhớ tĩnh, đòi hỏi kiểm soát và giải phóng bộ nhớ một cách chính xác để tránh rò rỉ bộ nhớ hoặc tràn bộ nhớ.
2. Hiệu suất thấp: Dynamic memory allocation có thể tốn kém về hiệu suất so với việc sử dụng bộ nhớ tĩnh vì quá trình cấp phát và giải phóng bộ nhớ đòi hỏi thời gian và tài nguyên hơn.

Ví dụ sử dụng dynamic memory allocation trong ngôn ngữ C++:

```cpp

//Cpp
#include <iostream>

int main() {
    int size;
    std::cout << "Enter the size of the array: ";
    std::cin >> size;

    // Cấp phát bộ nhớ động cho một mảng số nguyên
    int* dynamicArray = new int[size];

    std::cout << "Enter " << size << " integers: ";
    for (int i = 0; i < size; i++) {
        std::cin >> dynamicArray[i];
    }

    std::cout << "You entered: ";
    for (int i = 0; i < size; i++) {
        std::cout << dynamicArray[i] << " ";
    }
    std::cout << std::endl;

    // Giải phóng bộ nhớ động sau khi hoàn thành công việc
    delete[] dynamicArray;

    return 0;
}
```

Trong ví dụ trên, chương trình yêu cầu người dùng nhập số lượng phần tử của một mảng số nguyên và sau đó cấp phát bộ nhớ động cho mảng đó. Sau khi người dùng nhập giá trị cho từng phần tử, chương trình hiển thị các giá trị đã nhập và sau đó giải phóng bộ nhớ động bằng cách sử dụng toán tử `delete[]`.


```c
//C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int size;
    printf("Enter the size of the array: ");
    scanf("%d", &size);

    // Cấp phát bộ nhớ động cho một mảng số nguyên
    int* dynamicArray = (int*)malloc(size * sizeof(int));

    printf("Enter %d integers: ", size);
    for (int i = 0; i < size; i++) {
        scanf("%d", &dynamicArray[i]);
    }

    printf("You entered: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", dynamicArray[i]);
    }
    printf("\n");

    // Giải phóng bộ nhớ động sau khi hoàn thành công việc
    free(dynamicArray);

    return 0;
}
```

Trong ví dụ này, chương trình yêu cầu người dùng nhập số lượng phần tử của một mảng số nguyên và sau đó cấp phát bộ nhớ động cho mảng đó bằng cách sử dụng hàm `malloc()`. Sau khi người dùng nhập giá trị cho từng phần tử, chương trình hiển thị các giá trị đã nhập và sau đó giải phóng bộ nhớ động bằng cách sử dụng hàm `free()`.
