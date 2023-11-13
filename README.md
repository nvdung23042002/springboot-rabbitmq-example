# springboot-rabbitmq-tutorial

- `RabbitMQ là một AMQP (Advanced Message Queue Protocol) message broker hay còn gọi là phần mềm quản lý hàng đợi message. Nói đơn giản, đây là phần mềm định nghĩa hàng đợi một ứng dụng khác có thể kết nối đến để bỏ message vào và gửi message dựa trên nó` 

- `RabbitMQ chạy trên nhiều OS, Cloud và cung cấp một loạt các công cụ dành cho nhà phát triển với hầu hết các ngôn ngữ phổ biến. `

Cách thức hoạt động 
 

Bước 1: Producer Gửi Tin Nhắn 

Trong quá trình hoạt động, producer, một ứng dụng hoặc thành phần, tạo một tin nhắn và gửi nó tới RabbitMQ. Điều quan trọng là producer không gửi tin nhắn trực tiếp đến một hàng đợi mà thay vào đó gửi nó thông qua một exchange. 

Bước 2: Exchange Định Tuyến Tin Nhắn 

Sau khi producer gửi tin nhắn, RabbitMQ broker nhận nó. Tuy nhiên, thay vì đẩy tin nhắn trực tiếp vào hàng đợi, broker sử dụng exchange để quyết định điều hướng tin nhắn. Exchange là một phần quan trọng trong việc định tuyến và quyết định điểm đích của tin nhắn. 

Bước 3: Exchange Chịu Trách Nhiệm Định Tuyến 

Exchange chịu trách nhiệm định tuyến tin nhắn đến các hàng đợi tương ứng dựa trên quy tắc đã được thiết lập. Exchange sử dụng các routing key hoặc tiêu đề của tin nhắn cùng với các bindings để quyết định hàng đợi nào sẽ nhận tin nhắn. Có nhiều loại exchange, bao gồm sàn trực tiếp (direct exchange), sàn theo chủ đề (topic exchange), sàn theo tiêu đề (headers exchange), và sàn fanout. 

Bước 4: Hàng Đợi Nhận Tin Nhắn 

Tin nhắn, sau khi đã được định tuyến bởi exchange, sẽ được đưa vào các hàng đợi tương ứng. Mỗi hàng đợi là nơi lưu trữ tạm thời tin nhắn cho đến khi consumer sẵn sàng xử lý chúng. Hàng đợi đảm bảo tính bất đồng bộ trong gửi và nhận tin nhắn. 

Bước 5: Consumer Nhận Tin Nhắn 

Consumer, là một ứng dụng hoặc thành phần khác, đăng ký với hàng đợi và nhận các tin nhắn từ hàng đợi mà nó đã đăng ký. Consumer xử lý tin nhắn theo logic của ứng dụng và có thể gửi xác nhận (acknowledgment) cho RabbitMQ để thông báo rằng tin nhắn đã được xử lý thành công hoặc cần được xử lý lại. 