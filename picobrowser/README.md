# picobrowser ([Link](https://2019shell1.picoctf.com/problem/37878/))

- Vừa vào *challenge* thì thấy 1 *button flag*, thử click vào xem sao

  ![1](images/Selection_001.png)

- Nhìn sơ qua thì có vẻ liên quan tới *User-Agent* của *HTTP Request Header*. Có vẻ *server* lấy *User-Agent* để *acess* quyền *admin*.

- Nếu chưa biết về *HTTP Request Header* thì tham khảo: [Link](https://techtalk.vn/http-header-la-cai-gi-phan-1.html)

- Đây là *User-Agent* mặc định của máy mình

  ![2](images/Selection_002.png)

- Ta có thể thay đổi giá trị đó nhờ `Burp suite`

- Vào `Burp suite` để *intercept* request  lại, chỉnh sửa giá trị của *User-Agent* thành *picobrowser* như đề yêu cầu

  ![3](images/Selection_003.png)

- *Forward* và nhận *flag*

  ![4](images/Selection_004.png)
