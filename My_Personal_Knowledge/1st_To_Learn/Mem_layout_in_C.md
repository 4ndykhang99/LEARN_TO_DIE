## MEMORY LAYOUT IN C PROGRAMMING
### 1. Tiếp cận vấn đề

Thông thường, khi thực hiện một dự án lập trình embedded C, chúng ta sẽ thực hiện các trình tự sau:
- Viết, chỉnh sửa code file (C/Cpp) -> Chương trình được lưu trong ổ cứng.
- Biên dịch (compile chương trình) sang ngôn ngữ máy tính (Binary file) -> binary file cũng được lưu trong ổ cứng.
- Chạy chương trình -> Load chương trình vào bộ nhớ của vi xử lý

### 2. Layout của một memory trong ngôn ngữ C
![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/6361e835-2341-43ed-af79-c8df199c2016)

### A. Text segment

> Đây là vùng nhớ chứa mã máy đã được biên dịch của chương trình. Nó chứa các hàm, lệnh điều khiển và các phần mã khác. Khu vực này được thiết kế ở dạng sharable, điều này cho phép vùng nhớ chỉ cần một copy duy nhất để các tiến trình thực thi có thể truy cập và đọc dự liệu, tuy nhiên, text segment chỉ có thể truy cập ở mức độ read only, để tránh các chỉnh sửa trái phép.

### B. DS - Data segment - initialized data segment
> initialized data segment chứa các tất cả các dạng biến global, static, constant, và biến ngoại (được khai báo với từ khóa extern) được khởi tạo trước, data segment không phải ở dạng read only có thể bị thay đổi trong quá trình chạy chương trình.

> segment này có thể được thiết lập ở cả read only và read write

eg:

```c
#include <stdio.h>

char c[]="rishabh tripathi";     /*  global variable stored in Initialized Data Segment in read-write area*/
const char s[]="HackerEarth";    /* global variable stored in Initialized Data Segment in read-only area*/

int main()
{
    static int i=11;          /* static variable stored in Initialized Data Segment*/
    return 0;
}
```
### C. BSS - Block Started by Symbol
> Đây là vùng nhớ chứa các biến chỉ được khai báo nhưng chưa gán giá trị hoặc có giá trị bằng 0

eg:
Dưới đây là một ví dụ về cách khai báo và sử dụng vùng nhớ BSS trong C:

```c
#include <stdio.h>

char c;               /* Uninitialized variable stored in bss*/
int D = 0;            /* Uninitialized variable stored in bss*/
int main()
{
    static int i;     /* Uninitialized static variable stored in bss */
    return 0;
}
```
### D. Heap

> Heap là segment mà dữ liệu khi sử dụng các hàm liên quan đến dynamic Memory allocation được lưu trữ.

Heap là một phân đoạn bộ nhớ trong chương trình mà thường được sử dụng để cấp phát bộ nhớ động. Nó được dùng để cấp phát bộ nhớ động trong thời gian chạy bằng cách sử dụng các hàm như malloc() và calloc(). Heap mở rộng lên theo hướng tăng địa chỉ bộ nhớ khi cần thêm bộ nhớ được cấp phát.

Một điểm quan trọng của heap là nó được chia sẻ bởi tất cả các thư viện chia sẻ (còn được gọi là thư viện động) và các module được tải động động trong một tiến trình. Điều này có nghĩa là nhiều phần khác nhau của một chương trình, bao gồm các thư viện khác nhau, có thể cấp phát và giải phóng bộ nhớ từ cùng một heap.

Việc chia sẻ heap cho phép tận dụng bộ nhớ một cách hiệu quả và cho phép các phần khác nhau của chương trình tương tác và chia sẻ dữ liệu một cách linh hoạt trong thời gian chạy. Điều này cũng có nghĩa là cần chú ý trong việc quản lý bộ nhớ trong môi trường đa luồng hoặc đa tiến trình để đảm bảo đồng bộ hợp lý và tránh xung đột.

Cần lưu ý rằng mỗi tiến trình có một heap riêng biệt, vì vậy heap của một tiến trình không thể truy cập bởi tiến trình khác. Tuy nhiên, trong cùng một tiến trình, nhiều thư viện chia sẻ và các module được tải động có thể truy cập và chia sẻ cùng một heap.

```c
#include <stdio.h>
int main()
{
    char *p=(char*)malloc(sizeof(char));    /* memory allocating in heap segment */
    return 0;
}
```
![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/8de10eef-2801-4cbc-b66a-9cb2114b7b78)

### E. Stack
> Segment stack (ngăn xếp) trong một chương trình được sử dụng để quản lý các biến cục bộ và các hàm gọi trong thời gian chạy. Nó cung cấp một cơ chế để lưu trữ các biến cục bộ, các tham số hàm, và các địa chỉ trả về của các hàm gọi.

Stack được thiết kế theo cấu trúc LIFO - Last in first out
Stack có các function frame, mỗi khi func được gọi, func sẽ được push vào trong stack theo trình tự gọi của chương trình.

Segment stack được sử dụng để lưu trữ các biến cục bộ và được dùng để truyền các đối số vào các hàm, cùng với địa chỉ trả về của lệnh sẽ được thực thi sau khi cuộc gọi hàm kết thúc. Các biến cục bộ có phạm vi chỉ trong khối mà chúng được định nghĩa, chúng được tạo ra khi điều khiển nhập vào khối đó. Tất cả các cuộc gọi hàm đệ quy được thêm vào stack.

Ngăn xếp và heap truyền thống được đặt ở hai đầu đối lưu trích ảo của tiến trình.

- Segment stack được sử dụng để lưu trữ các biến cục bộ và có trách nhiệm truyền các đối số vào các hàm, cũng như lưu trữ địa chỉ trả về của lệnh sẽ được thực thi sau khi cuộc gọi hàm hoàn thành. Các biến cục bộ có phạm vi giới hạn trong khối mà chúng được định nghĩa, và chúng được tạo ra khi điều khiển nhập vào khối đó. Ngoài ra, các cuộc gọi hàm đệ quy được thêm vào ngăn xếp.

- Về mặt tổ chức bộ nhớ, ngăn xếp và heap truyền thống được đặt ở hai đầu đối lưu trích ảo của không gian địa chỉ ảo của tiến trình. Ngăn xếp thường bắt đầu từ địa chỉ bộ nhớ cao và mở rộng xuống dưới, trong khi heap bắt đầu từ địa chỉ bộ nhớ thấp và mở rộng lên trên. Sắp xếp này cho phép ngăn xếp và heap mở rộng về phía nhau khi cần, tối đa hóa không gian bộ nhớ có sẵn cho cả hai.

- Bằng cách đặt ngăn xếp và heap ở hai đầu trái và phải, không gian bộ nhớ của tiến trình được sử dụng một cách hiệu quả. Sự phân tách giữa ngăn xếp và heap giúp ngăn ngừa va chạm và xung đột giữa bộ nhớ được cấp phát động trên heap và frame ngăn xếp của các cuộc gọi hàm. Nó cũng cho phép quản lý ngăn xếp hiệu quả, vì con trỏ ngăn xếp có thể được điều chỉnh dễ dàng bằng cách tăng hoặc giảm giá trị của nó.

- Nhìn chung, segment stack đóng vai trò quan trọng trong việc quản lý biến cục bộ, cuộc gọi hàm và truyền đối số, trong khi đoạn heap xử lý việc cấp phát bộ nhớ động. Vị trí riêng biệt của chúng trong không gian địa chỉ ảo đảm bảo việc sử dụng bộ nhớ hiệu quả và hoạt động đúng đắn của một chương trình.
