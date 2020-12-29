# Đồ án khoa học dữ liệu

<pre>
MSSV: 1712358   Họ và tên: Nguyễn Minh Đức  
MSSV: 1712379   Họ và tên: Đặng Thành Duy
</pre>

# Chủ đề: Dự báo thời tiết

I.  Crawl:
- Chọn https://www.wunderground.com để lấy dữ liệu. Trang này có rất nhiều trạm thời tiết để lấy dữ liệu và độ chính xác khá cao. Ngoài ra có thể crawl api và html nên dữ liệu crawl bằng 2 cách sẽ đồng nhất.
- Dữ liệu được lấy trong 10 năm từ 2010 đến 2020.
- Dữ liệu được lấy từ trạm thời tiết ở sân bay Tân Sơn Nhất(VVTS).
1.  Qua API:
- Do trang API đã đóng cửa từ lâu nên sẽ dùng public api key bằng cách crawl html, search từ khóa apiKey.
- Sau đó sử dụng requests để crawl api thông qua đường dẫn lấy được thông qua browser Devtools>Network>XHR:
![alt images/api_1.png](images/api_1.png)  
![alt images/api_2.png](images/api_2.png)  
- Mỗi lần có thể lấy dữ liệu tương ứng với số ngày trong tháng.
- Lấy được tổng cộng 171694 ngày trong 2 phút.
- Dữ liệu sẽ được lưu trong ở [data/data.csv](data/data.csv).
2.   Qua HTML:
- Do trang web sử dụng javascript để render dữ liệu cần lấy nên phải dùng web driver để chạy javascript.
- Đầu tiên sẽ dùng selenium vô trang cần lấy và đổi sang hệ metric:
![alt images/html_1.png](images/html_1.png)

II.  Preprocessing:

III.  Model:
