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
  - Assignment: [Shi-Tomasi Corner Detector](Week_3/Shi_Tomasi_Corner_Detector.ipynb).
  - Khi có ảnh kích thước 7x7(thực tế là 7x7x3) và bộ lọc 3x3 thì kích thước ảnh sau khi sử dụng bộ lọc với stride = 1 là (kích thước ảnh - kích thước bộ lọc)/stride + 1 = 5x5
  - Khi áp bộ lọc vào ảnh, 1 ô tại ảnh output 5x5 được tính nhờ vào phép tích chập (pixel wei multiplication). Ảnh có kích thước 7x7 có các giá trị cố định x1,...,x9 , bộ lọc kích thước 3x3 có các giá trị thay đổi w1,...,w9 . Vậy công thức tính tổng quát cho 1 ô của output 5x5 là: (Tổng wi . xi) + bias (i = (1, 9)) (Phép này còn gọi là convolution)
  - Depth của kernel phải bằng với với depth của ảnh đầu vào
  - Các bước thực hiện của bài toán CNN
    + Đầu tiên thực hiện áp các bộ lọc tương ứng vào ảnh đầu vào, quá trình này gọi là CONVOLUTION LAYERS (+ MAXPOOLING). Kết quả cuối cùng của bước này sẽ cho ra 1 bức ảnh có kích thước nhỏ nhưng depth rất lớn (Ví dụ như trong ảnh)
    + Tiếp theo, thực hiện FLATTEN VECTOR cho bức ảnh kết quả từ bước trên sẽ thu được 1 vector ... chiều
    + Sau đó thực hiện FULLY CONNECTED LAYERS (giảm kích thước của vector đến 1 mức tốt nhất)
    + Cuối cùng, phân loại để ra được kết quả mong muốn. Thiết kế các nơ ron ứng với các label, nơ ron nào cho tỉ lệ phần trăm cao hơn thì là kết quả dự đoán (Tổng xác suất của các nơ ron = 1)
      *
<!-- Footer -->
<p align="center">© Copyright by Đỗ Trọng Khánh</p>
