# Đồ án khoa học dữ liệu

<pre>
MSSV: 1712358   Họ và tên: Nguyễn Minh Đức  
MSSV: 1712379   Họ và tên: Đặng Thành Duy
</pre>

Phân công công việc:

# Chủ đề: Dự báo thời tiết

I.  Câu hỏi:

II.  Ý nghĩa:

III.  Cách thức thu thập dữ liệu:
- Chọn https://www.wunderground.com để lấy dữ liệu. Trang này có rất nhiều trạm thời tiết để lấy dữ liệu và độ chính xác khá cao. Ngoài ra có thể crawl api và html nên dữ liệu crawl bằng 2 cách sẽ đồng nhất.
- Dữ liệu được lấy trong 10 năm từ 2010 đến 2020.
- Dữ liệu được lấy từ trạm thời tiết ở sân bay Tân Sơn Nhất(VVTS).

1.  Qua API:
- Do trang API đã đóng cửa từ lâu nên sẽ dùng public api key bằng cách crawl html, search từ khóa apiKey.
- Sau đó sử dụng requests để crawl api thông qua đường dẫn lấy được thông qua browser Devtools>Network>XHR:  
![alt images/api_1.png](images/api_1.png)  
![alt images/api_2.png](images/api_2.png)  
- Mỗi lần có thể lấy dữ liệu tương ứng với số ngày trong tháng.
- Dữ liệu sẽ được lưu trong ở [data/data.csv](data/data.csv).
- Lấy được tổng cộng 171694 hàng dữ liệu trong 2 phút.

2.   Qua HTML:
- Do trang web sử dụng javascript để render dữ liệu cần lấy nên phải dùng web driver để chạy javascript.
- Đầu tiên sẽ dùng selenium vô trang cần lấy và đổi sang hệ metric:  
![alt images/html_1.png](images/html_1.png)
- Do thời gian crawl khá lâu nên để tránh các vấn đề có thể xảy ra như rớt mạng..., trước tiên lưu phần html chứa dữ liệu cần lấy ở [data_html/html/](data_html/html/):  
![alt images/html_2.png](images/html_2.png)
- Do mỗi trang lấy được 1 ngày nên sẽ lưu tên html file bằng ngày để khi chạy lại sẽ không crawl những ngày đã lấy được. 
- Sử dụng mult-threading, mỗi thread sẽ mở 1 browser để tăng tốc độ crawl do trang web load khá lâu khoảng 5-7s. Lấy được tổng công 3644 ngày trong thời gian 55 phút.
- Sau đó rút trích dữ liệu từ các file html đã lấy được bằng BeautifulSoup:  
![alt images/html_3.png](images/html_3.png)
- Dữ liệu sẽ được lưu trong ở [data_html/data.csv](data_html/data.csv).
- Lấy được tổng cộng 171694 hàng dữ liệu trong 22 phút. Tổng thời gian crawl khoảng 1 giờ 20 phút.

IV.  Tiền xử lý:

V.  Dự đoán:

VI.  Tổng quan dữ liệu:
- Dữ liệu sau khi xử lý có 3638 dòng và 45 cột.
  - temp: là nhiệt độ.
  - dewPt: là điểm sương.
  - press: là áp suất.
  - humid: là độ ẩm.
  - wdir: là hướng gió.
  - wspeed: là tốc độ gió.
  - rain: là tỉ lệ mưa trong ngày.
  - is_rain: là ngày hôm đó có mưa hay không.
  - Postfix _min, _max, 

VII.  Tự đánh giá:

VIII.  Hướng dẫn chạy các file notebook:
1.  Thu thập dữ liệu:
- Mở và run all file Crawl_API nếu muốn crawl api hoặc Crawl_HTML đối với html.
2.  Tiền xử lý:
- Mở và run all file Clean_API nếu muốn tiền xử lý dữ liệu lấy bằng api hoặc Clean_HTML đối với html.
3.  Dự đoán:
- Mở và run all file Predict để train và predict dữ liệu đã thu thập được.
