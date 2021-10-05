<!-- Banner -->
<p align="center">
  <a href="https://www.uit.edu.vn/" title="Trường Đại học Công nghệ Thông tin" style="border: none;">
    <img src="https://i.imgur.com/WmMnSRt.png" alt="Trường Đại học Công nghệ Thông tin | University of Information Technology">
  </a>
</p>

<h1 align="center"><b>NHẬP MÔN THỊ GIÁC MÁY TÍNH</b></h>

## THÀNH VIÊN NHÓM
| STT    | MSSV          | Họ và Tên              |Chức Vụ    | Github                                                  | Email                   |
| ------ |:-------------:| ----------------------:|----------:|--------------------------------------------------------:|-------------------------:
| 1      | 19521676      | Đỗ Trọng Khánh         |Nhóm trưởng|[trong-khanh-1109](https://github.com/trong-khanh-1109)  |19521676@gm.uit.edu.vn   |
| 2      | 19521383      | Võ Phạm Duy Đức        |Thành viên |[ducducqn123](https://github.com/ducducqn123)            |19521383@gm.uit.edu.vn   |
| 3      | 19521326      | Trịnh Công Danh        |Thành viên |[danhtrinh15092001](https://github.com/danhtrinh15092001)|19521326@gm.uit.edu.vn   |

## GIỚI THIỆU MÔN HỌC
* **Tên môn học:** Nhập môn thị giác máy tính
* **Mã môn học:** CS231
* **Mã lớp:** CS231.M13.KHCL
* **Năm học:** HK1 (2021 - 2022)
* **Giảng viên**: ThS.Lê Minh Hưng

## QUÁ TRÌNH
### Week 1: OpenCV Tutorial and Face Detection
   1. [OpenCV Tutorial 1](Week_1/opencv_tutorial_01.ipynb) and [OpenCV Tutorial 2](Week_1/opencv_tutorial_02.ipynb) 
   2. [Face Detection](Week_1/Face_detection.ipynb)

### Week 2: Computer vision AI
  - Based on Loos functions:
    + Classification
    + Regression
  - Based on task:
    + Classification: 0, 1, 2, ...
    + Localization: only object in the image.
    + Detection: multiple object in the image.
    + Segmentation: draw borders (boudaires) around the object.
    + Identification: face identication.
  - Assignment: [Harris Corner Detector](Week_2/Harris_Corner_Detector.ipynb).

### Week 3: Overview about Convolutional neural network (CNN)
  - Khi có ảnh kích thước 7x7(thực tế là 7x7x3) và bộ lọc 3x3 thì kích thước ảnh sau khi sử dụng bộ lọc với stride = 1 là (kích thước ảnh - kích thước bộ lọc)/stride + 1 = 5x5
  - Khi áp bộ lọc vào ảnh, 1 ô tại ảnh output 5x5 được tính nhờ vào phép tích chập (pixel wei multiplication). Ảnh có kích thước 7x7 có các giá trị cố định x1,...,x9 , bộ lọc kích thước 3x3 có các giá trị thay đổi w1,...,w9 . Vậy công thức tính tổng quát cho 1 ô của output 5x5 là: (Tổng wi.xi) + bias (i = (1, 9)) (Phép này còn gọi là convolution)
  - Depth của kernel phải bằng với với depth của ảnh đầu vào
  - Các bước thực hiện của bài toán CNN
    + Đầu tiên thực hiện áp các bộ lọc tương ứng vào ảnh đầu vào, quá trình này gọi là CONVOLUTION LAYERS (+ MAXPOOLING). Kết quả cuối cùng của bước này sẽ cho ra 1 bức ảnh có kích thước nhỏ nhưng depth rất lớn (Ví dụ như trong ảnh)
    + Tiếp theo, thực hiện FLATTEN VECTOR cho bức ảnh kết quả từ bước trên sẽ thu được 1 vector ... chiều
    + Sau đó thực hiện FULLY CONNECTED LAYERS (giảm kích thước của vector đến 1 mức tốt nhất)
    + Cuối cùng, phân loại để ra được kết quả mong muốn. Thiết kế các nơ ron ứng với các label, nơ ron nào cho tỉ lệ phần trăm cao hơn thì là kết quả dự đoán (Tổng xác suất của các nơ ron = 1)
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/Quy_tr%C3%ACnh_th%E1%BB%B1c_hi%E1%BB%87n_CNN.png"> 
  - FULLY CONNECTED là mỗi nơ ron ở mỗi layer kết nối đầy đủ với nơ ron ở layer cạnh nó
  - Cách tính số lượng trọng số của 1 feature (trọng số là parameter: w) : dài x rộng x depth + bias
  - Cách thực hiện bài toán CNN:
    + Khởi tạo ngẫu nhiên các trọng số cho F(Wi)
    + Đưa bức ảnh đầu vào qua F(Wi) sẽ cho ra kết quả dự đoán yi'
    + Để đo đạc sự khác nhau giữa yi' với yi(Thực tế) ta dùng hàm Loss (Loss càng nhỏ kết quả càng tốt). Loss = yi' - yi mà yi cố định(hay là label) nên Loss = f'(Wi) hay có thể nói Loss phụ thuộc vào Wi, tăng giảm của Wi sẽ ảnh hưởng đến Loss.
    + Cách để tối ưu bài toán là giảm Loss. Tính đạo hàm riêng của Loss với từng Wi, sau đó thực hiện cập nhật lại trọng số Wi bằng công thức 
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/C%C3%B4ng_th%E1%BB%A9c_t%C3%ACm_tr%E1%BB%8Dng_s%E1%BB%91_m%E1%BB%9Bi.png">
    + Thực hiện liên tục từ fit forward đến tìm trọng số mới đến khi Loss đạt giá trị tối ưu(có cách dừng)
    + Việc load nhiều ảnh một lúc đề thực hiện là bất khả thi, vì vậy ta sẽ có batch để chứa các ảnh, batch có 1 số lượng nhất định. Mỗi lần batch đưa bộ ảnh lên sẽ thực hiện cho ra 1 độ lỗi, sau khi thực hiện hết số lượng ảnh đầu vào ta sẽ tính tổng độ lỗi đó. Ta có 1 lần training sao cho mô hình đi qua hết các dữ liệu đầu vào là 1 epoch
  - Cấu tạo của 1 noron:
    + Kết quả từ phép tích chập(Convolution)
    + Activation funtion: Hàm lựa chọn các thông tin nào nên được giữ lại và quên đi
	* Sigmoid
	* Tank: giống sigmoid nhưng đi từ -1 đến 1
	* Relu (Các mạng CNN nay sài Relu rất nhiều)
	* Leaky relu: Giống relu nhưng sử dụng cho trường hợp không bị chết nơ ron
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/C%E1%BA%A5u_t%E1%BA%A1o_noron.png">
  - Assignment: [Shi-Tomasi Corner Detector](Week_3/Shi_Tomasi_Corner_Detector.ipynb).
### Week 4: Continue CNN
  - Padding: Kỹ thuật padding dùng để trích xuất đặc trưng các vùng xung quanh ảnh(vùng rìa) và giữ nguyên kích thước ảnh sau khi qua bộ lọc
    + Giả sử bộ lọc có kích thước FxF thì vùng padding cần đệm là (F - 1)/2
  - Pooling layer: Làm cho cách biểu diễn của mình nhỏ hơn và dễ quản lý hơn, thực hiện trên mỗi activation map một cách độc lập. Sau khi thực hiện thì đầu ra của depth không đổi, kích thước của chiều dài và rộng sẽ giảm đi 1 nửa(downsampling)
    + Max pooling: sẽ lấy con số lớn nhất trong 1 vùng mà pooling layer áp vào
    + Average pooling: sẽ lấy trung bình cộng trong 1 vùng mà pooling layer áp vào
  - Mô hình Alexnet:
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/8c823df6487937e52dc3869f83529a5879fb7b9d/Image/Alexnet.png">
<!-- Footer -->
<p align="center">© Copyright by Đỗ Trọng Khánh</p>
