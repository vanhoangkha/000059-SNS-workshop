---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan

Là khách hàng đã đăng ký, khi bạn cần một chuyến đi, bạn có thể sử dụng ứng dụng khách hàng Wild Rydes để yêu cầu một con kỳ lân và quản lý mọi thứ xung quanh nó. Là một kỳ lân đã đăng ký, bạn có thể sử dụng ứng dụng kỳ lân Wild Rydes để quản lý mọi thứ xung quanh doanh nghiệp của mình.

Đặc biệt, những chú kỳ lân quan tâm đến việc sử dụng ứng dụng để gửi hoàn thành chuyến đi sau khi họ đã đưa khách hàng đến đích thành công. Đây là trường hợp sử dụng bây giờ chúng ta sẽ xem xét kỹ hơn.

Tại Wild Rydes, khách hàng người dùng cuối thường giao tiếp thông qua REST API với các backend service. Đối với trường hợp sử dụng của chúng tôi, ứng dụng kỳ lân Wild Rydes tương tác với API được cung cấp bởi dịch vụ quản lý kỳ lân. Nó sử dụng tài nguyên gửi-hoàn thành chuyến đi để gửi các chi tiết liên quan của chuyến đi đến chương trình phụ trợ. Đáp lại điều đó, backend service tạo ra một tài nguyên mới cho chuyến đi đã hoàn thành và trả về mã trạng thái tương ứng, vị trí và biểu diễn của tài nguyên mới cho khách hàng.

Có lẽ không có gì ngạc nhiên khi có các dịch vụ khác trong bối cảnh microservice của Wild Rydes, cũng quan tâm đến một chuyến đi mới đã hoàn thành:

- Dịch vụ thông báo cho khách hàng: Khách hàng sẽ nhận được thông báo trong ứng dụng của họ về chuyến đi đã hoàn thành gần đây nhất của họ.
- Dịch vụ thanh toán khách hàng: Xét cho cùng, Wild Rydes là một doanh nghiệp, vì vậy dịch vụ này sẽ chịu trách nhiệm thu tiền vé từ khách hàng.
- Dịch vụ đi xe đặc biệt: Đây là dịch vụ đặc biệt quan tâm đến các chuyến đi với giá vé hoặc khoảng cách trên ngưỡng nhất định - chuẩn bị dữ liệu tương ứng cho các nhà tiếp thị và quản lý thành công.
- Trường hợp sử dụng này rõ ràng là thích hợp cho việc sử dụng thông báo xuất bản / đăng ký, có thể thoải mái thực hiện bằng cách sử dụng Amazon SNS theo cách không máy chủ và có thể mở rộng. Nó tách rời cả hai bên càng nhiều càng tốt. Các dịch vụ ở phía bên phải có thể tự chủ đăng ký chủ đề, ở phía bên trái.

![Working with SNS](/images/1/0000.png?featherlight=false&width=90pc)