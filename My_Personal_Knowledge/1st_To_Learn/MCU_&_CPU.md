## Difference between Microcontroller and microprocessor

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/6cddbd57-87c2-40e3-9077-301a40ffdf41)


The following are some differences between a Microcontroller & Microprocessor:

- ***Architecture***: A microprocessor is just a CPU (i.e. composed of a Control Unit, Register Pairs & some special registers) On the other hand, a Microcontroller has a CPU, Memory & other peripheral Interfaces.

- ***Timers & Counters***: In the Microprocessor there are no Timers & Counters While they are present in the Microcontroller.

- ***Functionality***: Microcontrollers are made to perform a specific function while microprocessors are general in terms of their functionality i.e. they can be used to perform different functions.

- ***Cost***: A Microcontroller is far cheaper than a Microprocessor.

### 1. MicroController.
> Microcontroller hay còn gọi là vi điều khiển, bao gồng MicroProcessors (vi xử lý) đi kèm với một số các ngoại vi giúp cho MCU hình thành một hệ thống điều khiển hoàn chỉnh. MCU thường không có khả năng mở rộng cao, do chỉ có thể mở rộng ngoại vi thông qua các chuẩn giao tiếp như I2C, USB, SPI, CAN, UArt,... MCU có bộ nhớ onboard, tuy nhiên nó sẽ không có ngoại vị dựa phân vùng bộ nhớ này.

- Cấu trúc: Microcontroller bao gồm MicroProcessors, các bộ nhớ, và các ngoại vi.
- Timers và counters: MicroController có tích hợp thạch anh nội, và được tích hợp cả timers và counters.
- Chức năng: MCU chỉ có khả năng chạy đơn luồng, đồng nghĩa với việc trong một thời điểm chỉ có thể xử lý từng tác vụ riêng biệt.
- Giá thành: rẻ hơn nhiều so với MicroProcessors.

### 2. MicroProcessor
> Một vi xử lý vi mô (microprocessor) là tên chung cho bất kỳ CPU nào được triển khai trên một chip duy nhất. Lịch sử cho thấy, CPU từng là một chip, và sau đó nó đã có một bus I/O để truy cập vào bộ nhớ và các thiết bị ngoại vi. Sự phát triển liên tục đã làm cho ý nghĩa của vi xử lý vi mô trở nên mờ mịt hơn. Mặt khác, các CPU mạnh mẽ trên một chip duy nhất ngày nay không còn quá "micro" nữa và trở nên hữu dụng hơn, một hệ thống trên chip hiện đại (SoC) có thể chứa nhiều vi xử lý bên trong nó.

- Cấu trúc: Microprocessor chỉ là một CPU (có thể hiểu nó đại diện cho một đơn vị điều khiển, và một số loại thanh ghi)
- Timers và counters: trong vi xử lý, không có timers và counters.
- Chức năng: Vi xử lý là nơi thực sự tính toán và giải quyết các tác vụ cho một hệ thống, nhiệm vụ của chúng là tìm, nạp và thực thi các lệnh, trong các Soc hiện đại ngày nay, vi xử lý có thể xử lý rất nhiều tác vụ cùng một lúc.
- Giá thành: rất đắt.

![image](https://github.com/4ndykhang99/Hoc_Hanh_Cac_Kieu/assets/78153591/f6064028-0668-42bb-bed6-db6a879baccc)

*Để hiểu rõ hơn, hãy xem xét các ứng dụng sử dụng cả bộ vi xử lý (processor) và bộ điều khiển (controller).*

- Trường hợp 1: ```Điều khiển LED 7 đoạn```

- Trường hợp 2: ```Nhận dạng khuôn mặt```

> Bạn sẽ sử dụng bộ vi xử lý và bộ điều khiển ở đâu và tại sao?

- Trong trường hợp 1, việc điều khiển các LED đòi hỏi một logic đơn giản hơn và ít phép tính hơn, tức là ít năng lượng tính toán và bộ nhớ hơn, nhưng nó sẽ đòi hỏi đầu ra dòng điện cao. Vì các yêu cầu của người dùng hạn chế khi nói đến bộ nhớ và công suất xử lý và đồng thời cần đầu ra dòng điện cao, nhà sản xuất có thể kết hợp đơn vị xử lý, bộ nhớ và các thiết bị I/O, điều này được gọi là bộ điều khiển hoặc vi điều khiển (microcontroller).

- Bây giờ đến trường hợp 2, nhận dạng khuôn mặt đòi hỏi rất nhiều đại số tuyến tính và không gian lưu trữ cho hệ số và mẫu, và thực tế chúng ta không cần điều khiển bất kỳ phần cứng nào từ bên trong chip, vì vậy cần tập trung nhiều hơn vào việc có một đơn vị tính toán đặc biệt để thực hiện các phép tính toán và không lãng phí diện tích chip bằng cách có bộ nhớ trên chip lớn, vì vậy nhà sản xuất cung cấp mạch để giao tiếp với bộ nhớ bên ngoài và các thành phần khác phù hợp với ứng dụng, điểm tập trung chính là làm cho chip mạnh mẽ về tính toán. Và đúng, những chip như vậy được gọi là bộ vi xử lý (processor).

> Vì vậy, để sử dụng một bộ vi xử lý cho trường hợp 1, bạn sẽ phải thêm mạch để điều khiển LED vì đầu ra dòng điện rất ít (tại sao bạn cần nhiều đầu ra dòng điện để chỉ làm các phép toán?), một số bộ nhớ vì bộ vi xử lý chỉ thực hiện các phép toán, tuy nhiên, bạn không thể sử dụng một bộ điều khiển cho trường hợp 2 vì nó không giúp thực hiện nhiều phép toán như vậy.

***Vì vậy, để tóm tắt:***

- Bộ điều khiển = bộ vi xử lý + đầu ra dòng điện nhiều hơn + bộ nhớ + các thiết bị I/O.
- Bộ vi xử lý = Não
- Bộ điều khiển = Cơ bắp
