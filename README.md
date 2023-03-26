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
* Đề bài cho ta 2 file [bases.txt](https://github.com/dnamgithub33/wu_svattt/blob/fc717071cb839e8c3d7fae78a3ac43416e559ee3/img/bases.txt) và [enc.cpp](https://github.com/dnamgithub33/wu_svattt/blob/fc717071cb839e8c3d7fae78a3ac43416e559ee3/img/enc.cpp).

* File bases.txt cho ta một dòng số:

```101 84 54 84 173 77 65 111 167 95 6d 101 157 119 5f 109 145 111 77 95 155 101 6f 119 137 116 72 97 137 108 61 105 137 116 61 109 137 116 72 105 137 116 6f 105 137 100 61 121 175```

* File enc.cpp cho ta một đoạn code đang mã hóa chuỗi ```ATTT{fake_flag}```.

```
#include <iostream>
#include <string>
using namespace std;

#define EL printf("\n")

string flag = "ATTT{fake_flag}";

void bases(string &s) {
    for (int i = 0; i < s.size(); i += 4)
        printf("%o %u %x %u ", (unsigned char) s[i], (unsigned char) s[i + 1], (unsigned char) s[i + 2], (unsigned char) s[i + 3]);
    EL;
}

int main() {
    freopen("bases.txt", "w", stdout);
    bases(flag);

    return 0;
}
```

    
* Có thể thấy đoạn code này đang viết vào ```bases.txt``` nên để tránh dữ liệu bị sai lệch, ta tạm loại bỏ dòng ```freopen("bases.txt", "w", stdout);```, chạy code và nhận được kết quả:







