# PROCESS MANAGEMENT
>Chương này sẽ giới thiệu về khái niệm của tiến trình (process). Bộ quản lý tiến trình là một yếu tố cốt lõi của bất kì hệ điều hành nào, trong đó có cả Linux.
## PROCESS LÀ GÌ ?
Tiền trình là một chương trình (object code stored on some media) . Bên cạnh việc thi hành đoạn mã chương trình (text section in Unix), các tiến trình còn bao gồm:

- Mở các file.
- Chờ các tín hiệu.
- Dữ liệu bên trong kernel.
- Trạng thái bộ xử lý.
- Không gian địa chỉ trong bộ nhớ (with one or more memory mappings).
- Các thread.
- Vùng dữ liệu chứa biến toàn cục.

## THREAD LÀ GÌ ?

>Các thread là các hoạt động bên trong một tiến trình. Mỗi thread chứa:

- Bộ đếm chương trình (program counter).
- Ngăn nhớ tiến trình (process stack).
- Tập các thanh ghi bộ xử lý.

>Kernel lập lịch cho các thread, chứ không phải là các tiến trình (process). Linux không phân biệt giữa thread và process. Với Linux, một thread là một loại tiến trình đặc biệt.

## SƠ BỘ TỔ CHỨC HOẠT ĐỘNG CỦA TIẾN TRÌNH TRÊN LINUX

Như mọi người có thể thấy, trong Task Manager của Window, có rất nhiều process đang chạy:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/163c76e7-a4df-42c1-b382-e8ae265fcd98)

Câu hỏi đặt ra: làm thế nào để máy tính có thể nhận biết được có những tiến trình nào đang hoạt động, tiến trình đó sử dụng bao nhiêu tài nguyên của máy tính bao gồm CPU, RAM, DISK, NETWORK,...

=> Trong thiết kế của hệ điều hành Linux, có những thực thế rất trừu tượng như: User, Thread, process, CPU, MEMORY, NETWORK,...

=> Những thực thể trựu tướng đó sẽ được hệ điều hành hiện thực hóa thông qua các Instance hoặc tệp (file). DEV thông qua việc thao tác với file, có thể thống kê được tài nguyên sử dụng của một tiến trình, thậm chỉ có thể sửa đổi tiến trình đó.

Process trong Linux được định danh tại địa chỉ 

```
/proc/
```

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/81302e85-b182-4eaa-86ad-72a43299caa5)

Hình trên chính là danh sách các folder đại diện cho một tiến trình. các folder được định danh bằng một con số hay còn gọi là PID (processID).

Nhập cmd: ```ps -aux``` để xem các process đang chạy trên Linux:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/88880775-61cd-4524-a7a1-245fd05d5e36)

Thử truy cập vào process có PID #810

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/ab09f8cc-8e7a-4520-8c3b-1ecc54eeb05d)

- Trong folder PID 810, có rất nhiều file thực thể hóa cho mọi thông tin mà tiến trình đang sử dụng.

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/863dfd8a-b37e-4b53-b2fe-430d1dadff7f)

- Ví dụ như trong file ```maps``` sẽ chứa các địa chỉ thư viện mà tiến trình đang sử dụng, thậm chí cả địa của vùng nhớ stack.

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/4ac03527-2776-4a96-9d45-a1201cd1588b)

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/b0dbec1d-8385-4c09-82a0-d2d71a400f17)

## VÒNG ĐỜI CỦA MỘT TIẾN TRÌNH

Một tiến trình (process) là một chương trình được kích hoạt và liên hệ tới các tài nguyên:

- Hai hoặc nhiều tiến trình có thể tồn tại và chạy cùng một chương trình.
- Hai hoặc nhiều tiến trình có thể tồn tại và chia sẻ tài nguyên, ví dụ như là file hoặc một không gian địa chỉ.
