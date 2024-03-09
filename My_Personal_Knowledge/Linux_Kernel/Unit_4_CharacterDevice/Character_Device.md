# DEVICE TREE
## 1. Mở đầu
- Linux chạy trên nhiều Flatform và hỗ trợ nhiều loại Device.
- Linux quản lý chúng dựa trên cây phân cấp device.

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/32916477-9847-4124-bc04-3f7cff2feaab)

=> là một một list Device chung để Dev có thể dựa vào đó cấu hình cho thiết bị của mình mà không cần quan tâm đến cấu trúc Hardware.

- Để dễ hình dung hơn có thể vào [Linux_Device_tree](https://elixir.bootlin.com/linux/v6.5.9/source/drivers) để xem cây thư mục chứa các Drivers của từng module cho từng loại Device khác nhau.
- Trong Drivers sẽ chưa các module chức năng của một thiết bị:

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/0f159880-a09a-46d0-b946-6a5626cd048a)  

- Trong mỗi module chức năng sẽ có các API config cho chức năng hoặc các API đặc trưng cho từng hãng khác nhau.
## 2. Các loại Device tree thủy tổ
- Có 3 loại Device thủy tổ: Character Device, block device và network device:

  - Character Device: tại đây dữ liệu hoạt động đọc ghi một cách tuần tự theo từng byte.
  - Block Device: Dữ liệu được đọc theo từng Block, vd: Ổ cứng, CD-ROM => dữ liệu được đọc tối thiểu 512 byte hoặc 4096 byte.
  - Network Device:

    > Dữ liệu được truyền ra bên ngoài.
    
    > Dữ liệu được gán địa chỉ.
    
    > Dữ liệu có thể bị mất mát hoặc sai lệch.

***==> Trong lập trình Linux Driver, chúng ta có thể code được một driver cho một Device kế thừa các tính chất của Device tree thủy tổ.*** Trong đó Character device là loại phổ biến nhất, đơn giản nhất nhưng lại hiệu quả.
## 3. Template Driver
>Định nghĩa: *Template Driver được ví như một form mẫu cho từng loại Device cụ thế. Về bản chất, template driver sẽ chứa các con trỏ hàm (API) mà hệ điều hành sẽ gọi ra khi thao tác với thiết bị. Nhiệm vụ của Dev là phải điền thông tin phần cứng theo đúng với template mà hệ điều hành quy định.*

VÍ DỤ VỀ TEMPLATE DRIVER THƯỜNG GẶP:
  ### a. Template Character

