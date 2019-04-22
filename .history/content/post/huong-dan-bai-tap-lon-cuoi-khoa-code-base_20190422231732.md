---
title: "Hướng dẫn bài tập lớn cuối khóa Code Base"
slug: "huong-dan-bai-tap-lon-cuoi-khoa-code-base"
date: 2019-04-21T23:41:03+07:00
categories:
- java
tags:
keywords:
summary: Để hiểu rõ hơn về phần bài tập cuối khóa, mình sẽ viết 1 bài hướng dẫn 2 phần còn lại đó là phần đăng nhập và phần quản lý bán hàng ...
thumbnailImagePosition: left
thumbnailImage: https://img.freepik.com/free-vector/web-page_1300-265.jpg?size=338&ext=jpg
---
Hello các bạn,

Để hiểu rõ hơn về phần bài tập lớn, mình sẽ viết 1 bài hướng dẫn 2 phần còn lại đó là phần đăng nhập và phần quản lý bán hàng

**I. Phần Đăng Nhập:** Phần này chúng ta sẽ đăng nhập bằng cách sử dụng mã nhân viên và mật khẩu của nhân viên đó được lưu trong file.

**Bước 1:** Load file nhân viên<br>
**Bước 2:** Mời người dùng nhập tài khoản (ở đây mình sử dụng mã nhân viên) và mật khẩu của nhân viên đó được lưu trong file.<br>
**Bước 3:** Duyệt vòng for của listNV (Làm như hàm tìm kiếm) và kiềm tra nếu tài khoản và mật khẩu tồn tại trong file thì mình sẽ gọi đến menu chính.Ngược lại thì chúng ta bắt người dụng nhập lại tài khoản và mật khẩu.<br>
**Bước 4:** Nếu bạn nào phân quyền quản trị và nhân viên: Mình xin gợi ý như sau: Quyền quản trị thì ông ta sẽ có tất cả các quyền gồm quản lý nhân viên, khách hàng, sản phẩm, báo cáo thống kê, và ông này thì sẽ không phải bán hàng rồi :D . Còn ông nhân viên thường thì ông sẽ không quản lý được nhân viên mà chỉ quản lý được khách hàng, sản phẩm  và mục quản lý bán hàng.
Vậy thì làm cách nào để ``Phân quyền``

Theo mình cách đơn giản nhất là chúng ta sẽ quy định mã của nhân viên. Đối với nhân viên là ông quản trị (admin) thì mình quy định là AD01, AD02...chẳng hạn. nói chung bắt đầu bằng từ AD. Còn ông nhân viên thường thì mình quy định là NV01, NV02.....nói chung bắt đầu bằng NV. Vì thế lúc kiểm tra ở bước 3 phía trên. Các bạn có thể kèm theo điều kiện là maNV.containt("AD") chẳng hạn thì lúc đó sẽ cho ông này vào menu quản trị còn ông nhân viên thường cho vào menu nhân viên thường.

**II. Phần nâng cao** <br>
Đầu tiên các bạn đọc hết phần yêu cầu trong cái ảnh bên dưới đã nhé :D :D 
![alt text](https://1.bp.blogspot.com/-zBevuImBrso/WkOQdyi7P_I/AAAAAAAABEE/0MlYaUHzec8321YVG5HJnwLhtNG2-yj8ACLcBGAs/s640/26104939_1024247994381553_427149392_o.png "Anh")
<br>
Sau khi đọc xong thì một phần đã hình dung được cách làm bài đó như nào rồi đúng ko ? Kết hợp lúc tối a cũng giảng nên là bạn nào cũng có thể hiểu hiểu 1 ít và bắt tay vào làm thôi nào :D
Mình sẽ phân tích từng bước nhé.
Đầu tiên chúng ta vẫn cần 1 class HoaDon với các thuộc tính cơ bản như ảnh trên, 1 class quản lý bán hàng vào trong packet Quản lý chẳng hạn, 1 file hoadon.txt
**Bước 1:** Ở đây chúng ta khởi tạo Arraylist giỏ hàng để lưu thông tin về giỏ hàng

**Bước 2:** Chúng ta sẽ nhập mã khách hàng và kiểm tra xem KH có trong file ko ? Nếu có thì in ra dạng bảng còn không thì thêm mới khách hàng (Làm tương tự phần quản lý khách hàng thôi)

**Bước 3:** Chúng ta nhập mã sản phẩm. Kiểm tra xem nếu có thì in ra sản phẩm đó.

**Bước 4:** Nhập số lượng mua. Kiểm tra số lượng mua luôn luôn phải nhỏ hơn hoặc bằng số lượng của sản phẩm trong kho. (trong file). Nhập số lượng rồi thì add thông tin của sản phẩm muốn mua đó vào arraylist giỏ hàng đã tạo từ đầu ấy.

**Bước 5:** Chỗ này có menu quay vòng hỏi là bạn có mua nữa ko. Chọn 1 để tiếp tục mua. Chọn 2 để thanh toán.
Nếu chọn 1 thì sẽ quay lên bước 3 để nhập mã sp và tiếp tục mua. ( Lưu ý khi họ mua nhiều sản phẩm trong cùng lúc như thế thì mã hóa đơn nó sẽ phải giống nhau nhé. ) 

Nếu chọn 2: khi bấm nút thanh toán. Chúng ta sẽ lưu cái arraylist kia vào file hoadon.txt tất cả các thông tin mà class HoaDon có. (Nó cũng giống mình lưu thông tin nhân viên vào file thôi vì thế nó cũng có hàm loadfile và savefile nha)
``Lưu ý: Để tránh mã hóa đơn trùng nhau, đây là cách tạo ra mã hóa đơn mình khuyên nên sử dụng. Mọi người lưu dưới dạng: MaKH_Năm_Tháng_ngày_giờ_phut_giây (Cái này mình lấy từ hệ thống qua hàm Date của java nha)``
![alt text](https://1.bp.blogspot.com/-8swwpT0fqVE/WkOTXn3XlXI/AAAAAAAABEQ/GleB-u7rUc0yCWmMpmqCIAeBx7Wyfu74wCLcBGAs/s640/maHoaDon.PNG)


Sau khi lưu được vào file hóa đơn rồi thì chúng ta phải ``TRỪ`` số lượng của sản phẩm đó trong file sản phẩm đúng không ? Vì mua rồi phải trừ đi chứ.
Cuối cùng là in ra một cái hóa đơn trên màn hình dạng bảng như dưới đây là xong.

Các bạn có thể in ra dạng đơn giản hơn. Vì ở đây mình tính thuế VAT các kiểu nên nó hơn nhiều thông tin ở tờ hóa đơn.
![alt text](https://2.bp.blogspot.com/-A-0OOTdGe0g/WkOTYmvME4I/AAAAAAAABEY/yRLtJoZfCS8quIBkEjNzn7oS8UOdGcRiACEwYBhgL/s640/hoadon.PNG "Anh-3")

**III. Phần báo cáo thống kê.**

``Phần này chỉ làm được khi mình đã có dữ liệu trong file hoadon.txt. Và chỉ ông quản trị mới được phép xem :D``

![alt text](https://4.bp.blogspot.com/-mjqivjS4KrM/WkOVtCdNijI/AAAAAAAABEg/cNd2B1IhNJwQyYdMWz2IWrkM-wTN_k_BQCEwYBhgL/s640/hoadonfile.PNG)

1.``Thống kê theo ngày hoặc tháng`` thì chúng ta sẽ load file hoadon.txt lên. Căn cứ vào ngày bán được lưu trong file hoadon.txt thì lấy ra được tất cả các sản phẩm được bán đã đc lưu trong file đó và in ra thông tin các sản phẩm đã được mua.
- Nhập ngày tháng cần thống kê.
- Kiểm tra trong file hóa đơn các sản phẩm nào được bán trong ngày đấy. Nếu có thì in ra thôi. In ra kiểu như ảnh dưới đây.
![alt text](https://1.bp.blogspot.com/-qybaGJvjui8/WkUlQ2yV2sI/AAAAAAAABFU/XcSRjNNsxfw-N6B1LE1jY1zNzt9Bb4OVwCLcBGAs/s640/bctk.PNG)
Cái này như mình tìm kiếm qua cái ngày bán thôi mà :D

2.Thống kê  theo nhân viên trong tháng. Thì mình cũng load file hoadon.txt xong sau đó nhập mã nhân viên và tháng cần thống kê. Sau đó kiểm tra xem ông nhân viên có mã đó đã bán được bao nhiêu sản phẩm trong tháng đó. (Như tìm kiếm trong file).

Các bạn làm phần nâng cao tham khảo thêm cách chương trình chạy ở dưới đây nha :D 

Cảm ơn các bạn đã đọc bài viết, nếu thấy có ích hãy để lại comment nhận xét nhé :)
[![](http://img.youtube.com/vi/a5VeeJyfRmg/0.jpg)](http://www.youtube.com/watch?v=a5VeeJyfRmg "")
<!--more-->
