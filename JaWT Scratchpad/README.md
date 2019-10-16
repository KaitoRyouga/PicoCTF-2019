#### JaWT Scratchpad ([Link](https://2019shell1.picoctf.com/problem/49726/))

-  OK, bài này thuộc dạng máy thằng nào mạnh thì thằng đó ăn. Máy yếu yêu cầu chỉ đọc tham khảo. Về phần mình thì mình nhờ người khác chạy hộ để lấy key chứ máy mình không chạy nổi 
- Về phần lý thuyết để vào bài thì xin xui lòng đọc ở [đây](https://jwt.io/), nó khá là hay, và trong năm 2019 này thì nó có nhiều bài liên quan về `jwt`
- Đây là các payload và các phương pháp liên quan đến `jwt` và cho khá nhiều lỗ hổng kh, nó khá là hay nên mình show ra cho mọi người cùng tham khảo: [Link](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/JSON%20Web%20Token)
- Nói luôn key của nó là: `ilovepico` cho ai muốn làm
- Tool để crack mình sẽ up lên. Tuy nhiên để load được file `rockyou.txt` thì nó khá là không tưởng. Nó chứa gần 11 triệu pass cho đủ mọi thể loại :v
- Ngoài ra các bạn có thể viết tool để chạy all trường hợp, không phải cứ chạy file `rockyou.txt` là sẽ ra, hên xui thôi. Nếu máy mạnh thì để chạy all trường hợp, chắc vài ngày là xong, mình chưa chạy thử nên cũng không biết
- Link gốc tool ở đây, các bạn đọc để biết cách dùng: [Link](https://github.com/ticarpi/jwt_tool)
