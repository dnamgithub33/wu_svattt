# I. Web2
* Đề bài cho ta một trang web cho phép tìm kiếm thông tin thông qua tên đã bị đảo ngược (Reverse of name). Có thể đảo ngược bằng tool trên [kt.gy](https://kt.gy/tools.html#conv/).

* Trang web hiển thị là "LQS search" và đề bài nhắc đến "Đảo ngược" (Reverse) nên khả năng cao database được sử dụng ở đây là SQL

![img](https://github.com/dnamgithub33/wu_svattt/blob/3f064232249fb035d4b0ae225391b5d1829192f2/img/homew2.PNG)
* Thử lệnh ```' ODER BY 1-- -``` hoặc ```' UNION SELECT NULL,NULL,NULL-- -``` để kiểm tra số lượng cột mà câu lệnh truy xuất ra với ```-- -``` là comment loại bỏ các câu lệnh đằng sau (SQL injection), ```1``` là số lượng cột mà trang truy vấn, tăng dần lên tới ```3```, ta biết được nó truy xuất ra 3 cột, lớn hơn thì câu lệnh bị lỗi.

![img](https://github.com/dnamgithub33/wu_svattt/blob/fc0f4da1a6435d589a4e3c2abe5c0bbfcff5d5b3/img/img.png)

* Đã biết được câu lệnh truy vấn 3 cột, có thể còn nhiều bảng khác chưa được truy vấn ra, sử dụng câu lệnh ```' UNION SELECT NULL,table_name,NULL FROM information_schema.tables-- -``` 



