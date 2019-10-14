# Open to admins ([Link](https://2019shell1.picoctf.com/problem/37878/))

- Bài này thì phần tích 2 cái hint mà đề đưa cho:

  - This secure website allows users to access the flag only if they are **admin** and if the **time** is exactly 1400
  - Can cookies help you to get the flag?

- Lại 1 vấn đề nữa về *cookie*, sau khi phân tích thì có vẻ ta cần thêm 2 bộ *key* và *value* để được *access* với tư cách là *admin*.

  - `admin=true`
  - `time=1400`

- Ở đây mình vẫn dùng add-on `editthiscookie` để edit cookie

- F5 lại để nhận flag

  ![flag](Selection_001.png)
