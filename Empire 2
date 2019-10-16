#### Empire2 ([Link](https://2019shell1.picoctf.com/problem/39830/))

- Bài này để ý hint thì mình linh cảm là 1 dạng *ssti* của jinja2 (ssti pico2018 toàn là jinja2, hehe)

- 1 link chứa gần đầy đủ payload load và phương pháp bypass ssti: [Link]([https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server Side Template Injection))

- Nếu không biết *ssti* là gì thì *research* để tìm hiểu

- Mới vào bài thì đập ngay cái payload kinh điển nhất của jinja2

  - `{{ config.items() }}`

- Đã ra flag, tuy nhiên đây là 1 flag troll, hm hm

  ![1](Selection_001.png)

- Tuy nhiên khi xem *cookie* thì khá nghi ngờ, nên mình đem nó đi *decrypt* xem nó là cái gì nào

  ![2](Selection_002.png)

- Link để *decrypt flask cookie* : [Link](https://www.kirsle.net/wizards/flask-session.cgi)

- Cuối cùng cũng flag thật chứ không phải troll 

  ![3](Selection_003.png)
