---
layout: post
title: Phương pháp tách chữ số từ bên trái!
subtitle: <My tự nghĩ ra đó nè>
tags: [code]
comments: true
---

**Đề bài:** Nhập vào 1 số nguyên, yêu cầu xuất ra chữ số ở vị trí i của số đó, nếu không có thì xuất ra -1.
(Lưu ý thứ tự đếm từ trái sang phải - bắt đầu là vị trí thứ 0)

**input:**
1
1234

**output**
2


Đọc đề này, mình tin là có rất nhiều bạn sẽ nảy sinh ý tưởng đầu tiên trong đầu là tách từng số bằng cách chia dư, tách dần từ phía sau (bên phải), mình cũng nằm trong số những người có suy nghĩ này.
Nhưng cách này có 1 nhược điểm là giá trị nạp vào mảng arr[] để lưu trữ lưu trữ sẽ bị lấy từ phía sau. Tức là, khi so sánh pos và arr[j] thì sẽ xuất sai giá trị.
Ví dụ: 12345 thì khi xuất ngược hay xuôi thì vị trí arr[1] đều là 4 chứ không phải 2 như ý đồ mong muốn. Vì tách chữ số từ phía sau thì phần tử arr[0]=5...
Muốn làm theo cách này thì vẫn được, nhưng dộ phức tạp về không - thời gian có vẻ sẽ tăng, mình bỗng có ý tưởng là tại sao ko tách từ phía trước.

~~~
while (num!=0) {
 // Tìm số hàng của chữ số đầu tiên:
    int digits = (int)log10(num);  //Ví dụ 1234 thì digits = 3 <=> 10^3 = hàng nghìn
   
    // Tìm chữ số đầu tiên
    r = (int)(num / pow(10, digits));  //Số đầu tiên = 1234/10^3 = 1
    a[k]=r; //Lưu r vào mảng arr[]
    k++;
 
        num=num-pow(10,digits)*r; //Tách hàng tiếp theo, num = 1234-1*10^3 = 234 , đoạn này mình tự chế chứ không có code mẫu trên mạng đâu (1)
 
        if (x<10)  //Tới hàng đơn vị nếu tiếp tục chạy dòng code (1) thì số cuối sẽ bị trừ đi 1 đơn vị (thành 1233 chứ không phải 1234), nên ta phải đặt điều kiện, nếu chạy tới hàng đơn vị thì x bằng chính nó.
        {
            x=x;
        }
}
~~~

{: .box-note}
Kết quả: Thứ tự các phần tử trong mảng được xếp đúng thứ tự y hệt thứ tự các chữ số trong số cần xử lý, chỉ cần 1 vòng lặp, j chạy từ 0 tới n-1 là xong.

Thế giới 7 tỉ người, cao thủ lớp lớp, có lẽ đã có ai đó nghĩ ra ý tưởng này trước mình, mình không biết nữa. ^^ Biết đâu 1 ngày nào đó, những người có cùng ý tưởng sẽ tìm thấy nhau, giúp đỡ nhau tiến xa hơn trên con đường học vấn đầy thử thách nhưng vô cùng tươi đẹp.

Chúc mọi người an vui.

Bình Dương,

18/08/2021

(Viết lại cho 20/11/2020)