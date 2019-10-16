#### Java Script Kiddie 2 ([Link](https://2019shell1.picoctf.com/problem/27396))

- OK, tiếp nối bài *Java Script Kiddie 1*, mình cũng không nói nhiều làm gì cho mất công 

- Cũng từ những bit đầu của png để làm bài này

  - `137 80 78 71 13 10 26 10 0 0 0 13 73 72 68 82`

- Ở đây mình cần các bạn đọc hiểu code và thuật toán của đề, chứ mình không giải thích lại. Chịu khó *research* 1 hồi là ra

- Code *js* của đề:

  ```javascript
  		<script>
  			var bytes = [];
  			$.get("bytes", function(resp) {
  				bytes = Array.from(resp.split(" "), x => Number(x));
  			});
  
  			function assemble_png(u_in){
  				var LEN = 16;
  				var key = "00000000000000000000000000000000";
  				var shifter;
  				if(u_in.length == key.length){
  					key = u_in;
  				}
  				var result = [];
  				for(var i = 0; i < LEN; i++){
  					shifter = Number(key.slice((i*2),(i*2)+1));
  					for(var j = 0; j < (bytes.length / LEN); j ++){
  						result[(j * LEN) + i] = bytes[(((j + shifter) * LEN) % bytes.length) + i]
  					}
  				}
  				while(result[result.length-1] == 0){
  					result = result.slice(0,result.length-1);
  				}
  				document.getElementById("Area").src = "data:image/png;base64," + btoa(String.fromCharCode.apply(null, new Uint8Array(result)));
  				return false;
  			}
  		</script>
  ```

- `key` bây giờ là 32 ký tự chứ không phải là 16 ký tự như bài trước. Tuy nhiên nếu chịu khó đọc code thì sẽ thấy biến `shifter` chỉ lấy các ký tự xen kẽ ( nếu đọc không hiểu thì lấy source về thử là sẽ thấy )

  - VD: key là *123456789...* thì `shìter` sẽ lấy các ký tự *1, 3, 5, 7, 9, ...*

- Vậy là 32 bit trở thành 16 bit như bình thường, các ký tự xen kẽ còn lại ta không quan tâm làm gì và có vẻ chữ số ở đây không có tác dụng gì, nên chỉ `brute` các ký tự số

- OK, 16 bit đầu của *png header* này chính là 16 bit đầu của mảng *result*. Tức là giá trị của mảng *bytes* tại vị trí `(((j + shifter) * LEN) % bytes.length) + i`

  - `i` ta đã có, với mỗi *i* là 1 vị trí của bit. Giả sử *bit 137* thuộc vị trí đầu tiên, tức *i=0*,...
  - `LEN` = 16
  - `j` là số nhóm bit, bài này chia ra *n* nhóm bit (bao nhiêu nhóm mình quên rồi, lười mò lại), mỗi nhóm bit có 16 bit, tức là ta chỉ xét 1 nhóm bit đầu. Tức là  *j=0*
  - `bytes.length`: là độ dài của lenght (bằng 688)
  - `shifter` chính là thứ mà ta cần, từ *shifter* ta có thể suy ra được ký tự tạo nên bit đúng của đề

- Code *js* mình chỉnh lại để lấy ra ký từ có thể tạo nên các bit đúng

  ```javascript
  		<script>
  			var bytes = ['143', '224', '86', '71', '69', '249', '251', '10', '253', '96', '0', '114', '121', '72', '68', '119', '179', '127', '191', '114', '13', '159', '207', '114', '249', '0', '0', '79', '9', '192', '95', '0', '174', '239', '118', '2', '0', '187', '54', '65', '21', '0', '156', '36', '0', '65', '138', '0', '222', '49', '59', '95', '114', '34', '0', '202', '155', '120', '200', '95', '73', '55', '11', '82', '0', '179', '231', '31', '69', '252', '68', '176', '174', '7', '54', '87', '0', '73', '110', '108', '137', '121', '0', '226', '165', '127', '26', '90', '66', '3', '247', '88', '155', '20', '191', '220', '0', '0', '78', '241', '113', '78', '1', '122', '0', '110', '206', '219', '212', '188', '243', '57', '164', '80', '1', '91', '158', '10', '68', '193', '1', '14', '163', '228', '11', '171', '193', '55', '48', '0', '0', '24', '188', '0', '94', '243', '84', '3', '52', '0', '20', '73', '175', '84', '82', '0', '69', '149', '143', '73', '16', '35', '48', '146', '241', '13', '239', '48', '63', '206', '201', '16', '96', '126', '32', '134', '80', '52', '151', '209', '216', '0', '0', '227', '252', '92', '191', '110', '25', '46', '34', '15', '126', '135', '152', '89', '211', '237', '183', '239', '252', '102', '59', '36', '54', '34', '210', '90', '213', '47', '23', '205', '187', '81', '127', '140', '199', '23', '127', '164', '252', '225', '221', '53', '7', '32', '216', '173', '65', '63', '198', '105', '180', '7', '214', '239', '158', '226', '141', '149', '210', '249', '73', '123', '71', '91', '199', '235', '203', '239', '133', '187', '217', '95', '103', '243', '204', '107', '255', '226', '207', '59', '127', '249', '131', '249', '241', '7', '181', '66', '38', '73', '218', '102', '0', '159', '106', '117', '171', '231', '197', '32', '249', '218', '75', '217', '199', '221', '178', '128', '159', '248', '128', '213', '51', '0', '241', '75', '127', '73', '46', '210', '252', '250', '102', '59', '122', '13', '85', '56', '199', '31', '11', '248', '152', '209', '107', '15', '240', '46', '223', '54', '125', '135', '132', '231', '216', '105', '2', '227', '187', '226', '175', '222', '96', '2', '43', '109', '191', '83', '213', '211', '184', '91', '86', '238', '172', '97', '100', '16', '85', '139', '32', '191', '110', '223', '37', '238', '155', '133', '251', '210', '252', '18', '157', '210', '139', '176', '9', '11', '128', '241', '38', '204', '1', '183', '168', '13', '153', '223', '60', '107', '16', '62', '241', '154', '32', '223', '90', '51', '73', '22', '121', '55', '20', '177', '73', '161', '177', '164', '252', '206', '255', '103', '110', '141', '196', '163', '141', '94', '4', '138', '31', '91', '182', '108', '250', '173', '200', '127', '113', '69', '154', '126', '59', '82', '253', '84', '253', '200', '7', '242', '61', '96', '149', '226', '52', '134', '223', '96', '237', '180', '91', '21', '73', '56', '0', '235', '73', '243', '173', '176', '100', '242', '47', '147', '44', '156', '149', '38', '11', '8', '127', '196', '228', '226', '174', '95', '88', '57', '40', '71', '65', '24', '91', '127', '84', '9', '109', '37', '91', '223', '157', '254', '228', '103', '157', '213', '146', '72', '203', '211', '0', '77', '239', '180', '218', '205', '189', '91', '126', '191', '40', '31', '242', '131', '90', '19', '164', '82', '53', '211', '246', '171', '243', '121', '69', '249', '243', '31', '169', '20', '195', '178', '32', '181', '244', '236', '95', '191', '16', '183', '191', '174', '249', '204', '169', '167', '176', '59', '241', '41', '43', '52', '211', '183', '59', '157', '251', '156', '228', '119', '254', '11', '107', '25', '101', '108', '153', '44', '43', '12', '113', '171', '39', '254', '193', '77', '92', '92', '146', '0', '206', '183', '126', '196', '196', '254', '127', '17', '80', '173', '159', '38', '246', '101', '212', '196', '16', '201', '81', '90', '245', '215', '61', '166', '176', '105', '227', '248', '189', '173', '179', '197', '198', '60', '54', '181', '62', '143', '231', '163', '247', '126', '79', '118', '145', '96', '54', '169', '16', '109', '206', '11', '72', '27', '106', '154', '55', '183', '26', '184', '111', '251', '85', '210', '55', '127', '242', '205', '23', '221', '46', '212', '29', '27', '128', '73', '71', '19', '252', '203', '231', '51', '212', '59', '127', '198', '12', '65', '191', '254', '233', '231', '157', '89', '47', '250', '254', '79', '244', '230', '238', '183', '155', '255', '142', '223', '229', '214', '110', '157', '115', '236', '243', '73', '231', '126', '193', '174', '175', '251', '130', '89', '213', '0', '0', '185'];
  
  			function assemble_png(){
  				var LEN = 16;
  				var key = "123456789123456789123456789";
  				var char = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'];
  				var shifter;
  				var result = [];
  				var I = 15;
  				var Bit = 82;
  				// 137 80 78 71 13 10 26 10 0 0 0 13 73 72 68 82
  				for (var i = 0; i < char.length; i++) {
  					shifter = Number(char[i].slice((0*2),(0*2)+1));
  					result[(0 * LEN) + I] = bytes[(((0 + shifter) * LEN) % bytes.length) + I]
  					if (result[I] == Bit) {alert(char[i]);}
  				}
  			}
  			assemble_png();
  		</script>
  ```

- Mảng *bytes* mình lấy từ [link](https://2019shell1.picoctf.com/problem/27396/bytes) này để thuận tiện giải off

- Code trên để lấy ký tự đầu với *i = 0*

- Muốn lấy ở bit thứ 2 ta chỉ cần chỉnh lại thông số i và bit đúng

- Ở đây mình lười viết 1 tool hoàn chình nên làm tay từng cái 1 luôn cho tiện :v

- Sau 1 hồi làm tay thì mình có các ký tự có thể tạo ra bit đúng là đây (mình thấy cũng khá nhanh, không đến nỗi quá chậm)

  ```javascript
  i = 0 => ['5']
  i = 1 => ['7']
  i = 2 => ['6']
  i = 3 => ['0']
  i = 4 => ['1']
  i = 5 => ['7']
  i = 6 => ['5']
  i = 7 => ['0']
  i = 8 => ['6']
  i = 9 => ['1', '2']
  i = 10 => ['0', '1']
  i = 11 => ['9']
  i = 12 => ['3']
  i = 13 => ['0']
  i = 14 => ['0']
  i = 15 => ['3']
  ```

- OK, giờ key của mình có dạng:

  - 5760175061093003
  - 5760175061193003
  - 5760175062093003
  - 5760175062193003

- Tuy nhiên key là 32 ký tự nên ta cần xen kẽ thêm các ký tự khác, VD: `5a7a6a0a1a7a5a0a6a1a0a9a3a0a0a3a`

- 

- OK, chạy ngay cái key đầu đã ra flag, khá hên

  ![1](Selection_001.png)