# I. Web2
* Đề bài cho ta một trang web cho phép tìm kiếm thông tin thông qua tên đã bị đảo ngược (Reverse of name). Có thể đảo ngược bằng tool trên [kt.gy](https://kt.gy/tools.html#conv/).

* Trang web hiển thị là "LQS search" và đề bài nhắc đến "Đảo ngược" (Reverse) nên khả năng cao database được sử dụng ở đây là SQL

![img](https://github.com/dnamgithub33/wu_svattt/blob/3f064232249fb035d4b0ae225391b5d1829192f2/img/homew2.PNG)
* Thử lệnh ```' ODER BY 1-- -``` để kiểm tra số lượng cột mà câu lệnh truy xuất ra với ```-- -``` là comment loại bỏ các câu lệnh đằng sau (SQL injection), ```1``` là số lượng cột, tăng dần lên tới ```3```, ta biết được nó truy xuất ra 3 cột, lớn hơn thì câu lệnh bị lỗi.



