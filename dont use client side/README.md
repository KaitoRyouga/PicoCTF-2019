# dont use client side ([Link](https://2019shell1.picoctf.com/problem/45147/))

- *View source* lên thì thấy đoạn code *javascript* như thế này

  ```javascript
  <script type="text/javascript">
    function verify() {
      checkpass = document.getElementById("pass").value;
      split = 4;
      if (checkpass.substring(0, split) == 'pico') {
        if (checkpass.substring(split*6, split*7) == 'a60f') {
          if (checkpass.substring(split, split*2) == 'CTF{') {
           if (checkpass.substring(split*4, split*5) == 'ts_p') {
            if (checkpass.substring(split*3, split*4) == 'lien') {
              if (checkpass.substring(split*5, split*6) == 'lz_4') {
                if (checkpass.substring(split*2, split*3) == 'no_c') {
                  if (checkpass.substring(split*7, split*8) == '3}') {
                    alert("Password Verified")
                    }
                  }
                }
        
              }
            }
          }
        }
      }
      else {
        alert("Incorrect password");
      }
      
    }
  </script>
  ```

- Và ta có 1 *form* thế này:

  ```html
  <form action="index.html" method="post">
  <input type="password" id="pass" size="8" />
  <br/>
  <input type="submit" value="verify" onclick="verify(); return false;" />
  </form
  ```

- Nói đơn giản thì khi ta nhập thì `password` sẽ được đẩy lên hàm `verify()` ngay khi chúng ta click chuột vào submit vào hàm `verify()` nhờ *attribute* `onclick`

- Biến ``checkpass` nhờ vào `checkpass = document.getElementById("pass").value;` sẽ lưu giá tri của *password* mà ta nhập vào

- Hàm *substring*  có cấu trúc sau`string.substring(start, end)`

  - Với `start` : là vị trị bắt đầu cắt chuỗi *string*
  - Với `end` :  là vị trí kết thúc cắt chuỗi *string*

- Bây giờ chỉ cần dựa vào vị trí của hàm `substring` là ta có thể sắp xếp lại thứ tự trong *flag*, có thể viết 1 tool nho nhỏ để ghép lại, không thì ghép lại bằng tay cũng được

- Thực ra không cần dùng hàm, không cần hiểu code thì vẫn có thể ghép lại được, vì flag luôn có ý nghĩa (trừ mấy ký tự cuối) . Ghép rồi submit vài lần thì cũng ra đáp án thôi, không cần cầu kỳ phân tích làm gì cả

  

  

  
