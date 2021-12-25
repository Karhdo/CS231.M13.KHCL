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
* **Giảng viên**: TS.Lê Minh Hưng

## QUÁ TRÌNH
### Week 1: OpenCV Tutorial and Face Detection.
   1. [OpenCV Tutorial 1](Week_1/opencv_tutorial_01.ipynb) and [OpenCV Tutorial 2](Week_1/opencv_tutorial_02.ipynb) 
   2. [Face Detection](Week_1/Face_detection.ipynb)

### Week 2: Computer vision AI.
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

### Week 3: Overview about Convolutional neural network (CNN).
  - Khi có ảnh kích thước 7x7(thực tế là 7x7x3) và bộ lọc 3x3 thì kích thước ảnh sau khi sử dụng bộ lọc với stride = 1 là `(kích thước ảnh - kích thước bộ lọc)/stride + 1 = 5x5`.
  - Khi áp bộ lọc vào ảnh, 1 ô tại ảnh output 5x5 được tính nhờ vào phép tích chập (pixel wei multiplication). Ảnh có kích thước 7x7 có các giá trị cố định x1,...,x9 , bộ lọc kích thước 3x3 có các giá trị thay đổi w1,...,w9 . Vậy công thức tính tổng quát cho 1 ô của output 5x5 là: `(Tổng wi.xi) + bias (i = (1, 9)) (Phép này còn gọi là convolution)`.
  - Depth của kernel phải bằng với với depth của ảnh đầu vào.
  - Các bước thực hiện của bài toán CNN.
    + Đầu tiên thực hiện áp các bộ lọc tương ứng vào ảnh đầu vào, quá trình này gọi là CONVOLUTION LAYERS (+ MAXPOOLING). Kết quả cuối cùng của bước này sẽ cho ra 1 bức ảnh có kích thước nhỏ nhưng depth rất lớn (Ví dụ như trong ảnh).
    + Tiếp theo, thực hiện FLATTEN VECTOR cho bức ảnh kết quả từ bước trên sẽ thu được 1 vector ... chiều.
    + Sau đó thực hiện FULLY CONNECTED LAYERS (giảm kích thước của vector đến 1 mức tốt nhất).
    + Cuối cùng, phân loại để ra được kết quả mong muốn. Thiết kế các nơ ron ứng với các label, nơ ron nào cho tỉ lệ phần trăm cao hơn thì là kết quả dự đoán (Tổng xác suất của các nơ ron = 1).
 <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/Quy_tr%C3%ACnh_th%E1%BB%B1c_hi%E1%BB%87n_CNN.png">
 
  - FULLY CONNECTED là mỗi nơ ron ở mỗi layer kết nối đầy đủ với nơ ron ở layer cạnh nó.
  - Cách tính số lượng trọng số của 1 feature (trọng số là parameter: w) : `dài x rộng x depth + bias`.
  - Cách thực hiện bài toán CNN:
    + Khởi tạo ngẫu nhiên các trọng số cho F(Wi).
    + Đưa bức ảnh đầu vào qua F(Wi) sẽ cho ra kết quả dự đoán yi'.
    + Để đo đạc sự khác nhau giữa yi' với yi(Thực tế) ta dùng hàm Loss (Loss càng nhỏ kết quả càng tốt). `Loss = yi' - yi` mà yi cố định(hay là label) nên `Loss = f'(Wi)` hay có thể nói Loss phụ thuộc vào Wi, tăng giảm của Wi sẽ ảnh hưởng đến Loss.
    + Cách để tối ưu bài toán là giảm Loss. Tính đạo hàm riêng của Loss với từng Wi, sau đó thực hiện cập nhật lại trọng số Wi bằng công thức 
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/C%C3%B4ng_th%E1%BB%A9c_t%C3%ACm_tr%E1%BB%8Dng_s%E1%BB%91_m%E1%BB%9Bi.png">
    + Thực hiện liên tục từ fit forward đến tìm trọng số mới đến khi Loss đạt giá trị tối ưu(có cách dừng).
    + Việc load nhiều ảnh một lúc đề thực hiện là bất khả thi, vì vậy ta sẽ có batch để chứa các ảnh, batch có 1 số lượng nhất định. Mỗi lần batch đưa bộ ảnh lên sẽ thực hiện cho ra 1 độ lỗi, sau khi thực hiện hết số lượng ảnh đầu vào ta sẽ tính tổng độ lỗi đó. Ta có 1 lần training sao cho mô hình đi qua hết các dữ liệu đầu vào là 1 epoch.
  - Cấu tạo của 1 noron:
    + Kết quả từ phép tích chập(Convolution).
    + Activation funtion: Hàm lựa chọn các thông tin nào nên được giữ lại và quên đi.
	* Sigmoid.
	* Tank: giống sigmoid nhưng đi từ -1 đến 1.
	* Relu (Các mạng CNN nay sài Relu rất nhiều).
	* Leaky relu: Giống relu nhưng sử dụng cho trường hợp không bị chết nơ ron.
  <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/d34d1ecd8f8832baea45117cac04b036358715ce/Image/C%E1%BA%A5u_t%E1%BA%A1o_noron.png">
  
  - Assignment: [Shi-Tomasi Corner Detector](Week_3/Shi_Tomasi_Corner_Detector.ipynb).

### Week 4: Mô hình mạng Neural Network AlexNet.
  - Padding: Kỹ thuật padding dùng để trích xuất đặc trưng các vùng xung quanh ảnh(vùng rìa) và giữ nguyên kích thước ảnh sau khi qua bộ lọc.
    + Giả sử bộ lọc có kích thước FxF thì vùng padding cần đệm là `(F - 1)/2`.
  - Pooling layer: Làm cho cách biểu diễn của mình nhỏ hơn và dễ quản lý hơn, thực hiện trên mỗi activation map một cách độc lập. Sau khi thực hiện thì đầu ra của depth không đổi, kích thước của chiều dài và rộng sẽ giảm đi 1 nửa(downsampling).
    + Max pooling: sẽ lấy con số lớn nhất trong 1 vùng mà pooling layer áp vào.
    + Average pooling: sẽ lấy trung bình cộng trong 1 vùng mà pooling layer áp vào.
  - Mô hình mạng Alexnet:
    <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/8c823df6487937e52dc3869f83529a5879fb7b9d/Image/Alexnet.png">
    + Số lượng trọng số ở FC layer chiếm số lượng rất lớn tổng số lượng trọng số của mô hình mạng (Nhược điểm 1).
    + Dùng kernel size lớn ảnh hưởng đến việc trích xuất đặc trưng (Nhược điểm 2).
  - Assignment: [Tính trọng số.](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/e5e953956eff2c196f935a02b2f9f0cf5d2e7a79/Image/Ti%CC%81nh_tro%CC%A3ng_so%CC%82%CC%81.png) and [Dùng mô hình để mạng AlexNet để lấy đặc trưng featuers sau đó dùng SVM model để huấn luyện và đánh giá.](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/1c5072777b0f01eda9c3a3f4cbfdb11b5b16ff68/Week_4/AlexNet_SVM.ipynb)

### Week 5: Mô hình mạng Neural Network VGGNet.
  - Nhược điểm của mô hình nạng AlexNet:
    + Dùng **kernel size** lớn (11x11) đấn đến số lượng trọng số nhiều và vùng quét thông tin rộng => Không lấy được nhiều thông tin chi tiết.
    + Số lượng trọng số ở lớp **Fully-connected Layer** quá lớn trên tổng số lượng trọng số của mô hình mạng.
  - Do đó  ZFNet ra đời để khắc phục nhược điểm **kernel size** lớn của AlexNet. Còn số lượng trọng số ở lớp **Fully-connected Layer** thì đến GoogleNet mới khắc phục.
  -  Về cơ bản AlexNet và ZFNet giống nhau về mặt kiến trúc, nó chỉ khác nhau ở kích thước **kernel size (7x7)**.
<table>
  <tr> 
    <td><img src='https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/9cb946d910646314c295918068c894436925746d/Image/Cac_mo_hinh_mang.png'></td>
    <td><img src='https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/9cb946d910646314c295918068c894436925746d/Image/VGGNet.png'></td>
  </tr>
</table>

  - VGG có 2 phiên bản **VGG16 (16 layer)** và **VGG19 (19 layer)**, sử dụng **filters size 3x3**.
  - Thay vì sử dụng kernel 7x7 ở mô hình ZFNet, thì ở VGG sử dụng 3 lớp **conv layer 3x3** thì nó có effcitive receptive field so với lớp 7x7. Ngoài ra nó sẽ giúp tăng tính **non-linearities**
  - Trong VGG ở lớp FC7 featuers thì có tính tổng quát hoá cho nhiều đặc vụ khác (FC7 featuers generalize well to other tasks).
  - Assignment: [Dùng mô hình để mạng VGG16 để lấy đặc trưng ở lớp FC7 featuers sau đó dùng SVM model để huấn luyện và đánh giá.](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/e8af5de147a49b5cda346488ad89f49fabb2ae8b/Week_5/VGG16_SVM.ipynb)
 
 ### Week 6: SIFT trong Open CV (Scale-Invariant Feature Transform).
  - SIFT là một thuật toán tiêu biểu và có hiệu quả khá cao vì dựa theo các cục bộ bất biến trong ảnh. Đặc trưng được trích chọn trong SIFT là các điểm đặc biệt keypoints.
Các điểm này kèm theo các mô tả về nó và kèm theo một vecto lấy keypoint làm điểm gốc
  - Phương pháp trích chọn điểm đặc trưng cục bộ bất biến SIFT gồm các bước:
    + Dò tìm các điểm cực trị (Scale-space Extrema Detection): Bước đầu tiên sẽ áp dụng hàm DOG(Difference of Guassian) để tìm ra các điểm có khả năng làm điểm đặc trưng tiềm năng. Điểm đặc trưng tiềm năng là điểm có tính chất không thay đổi dưới các phép phóng và xoay ảnh. Ví dụ: một pixel trong ảnh được so sánh với 8 lân cận điểm cũng như 9 pixel ở các tỷ lệ tiếp theo và 9 pixel ở các tỷ lệ trước. Nếu nó là một giá trị cực trị thì nó là một Keypoint. Về cơ bản nó có nghĩa là điểm được thể hiện tốt nhất trong thang đo đó. Được hiển thị trong hình dưới đây:
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/44cd72ff4af0f915e1f903cb090b2fca24c56572/Image/KeyPoint.png">
    + Lọc và trích xuất các điểm đặc biệt (Keypoint Localization): Khi tìm được vị trí các Keypoint, chúng phải được tinh chỉnh để có kết quả chính xác hơn. Ta sử dụng chuỗi Taylor mở rộng không gian tỷ lệ để có được vị trí Keypoint chính xác hơn và nếu cường độ tại điểm cực này nhỏ hơn giá trị ngưỡng 0,03 , nó sẽ bị loại bỏ. Ngưỡng này được gọi là tương phản (ngưỡng trong OpenCV). Vì vậy, nó giúp loại bỏ bất kỳ điểm chính có độ tương phản thấp, điểm cạnh và những gì còn lại là điểm ta cần quan tâm.
    + Xác định hướng cho các điểm nổi bật: Mỗi điểm nổi bật sẽ được gán cho một hoặc nhiều hướng dựa trên hướng gradient của ảnh. Mọi phép toán xử lý ở các bước sau này sẽ được thực hiện trên những dữ liệu ảnh mà đã được biến đổi tương đối so với hướng đã gán, kích cỡ và vị trí của mỗi điểm đặc trưng. Nhờ đó, tạo ra một sự bất biến trong các phép xử lý này
    + Mô tả các điểm nổi bật: Các hướng gradient cục bộ được đo trong ảnh có kích cỡ cụ thể nào đó trong vùng lân cận với mỗi điểm đặc trưng. Sau đó, chúng sẽ được biễu diễn thành một dạng mà cho phép mô tả các tầng quan trọng của quá trình bóp méo hình dạng cục bộ và sự thay đổi về độ sáng
  - SIFT trong openCV: 
    ```
    img = cv2.imread('/content/drive/MyDrive/Học kỳ 5/Nhập môn thị giác máy tính/Image/jurassic.jpg')
    gray= cv2.cvtColor(img,cv2.COLOR_BGR2GRAY) # Đưa về ảnh xám trước khi dùng SIFT

    sift = cv2.SIFT() # Khởi tạo đối tượng SIFT, ta có thể truyền các tham số cho nó
    kp = sift.detect(gray,None) # tìm Keypoint trong ảnh

    img_1=cv2.drawKeypoints(gray,kp) # vẽ các vòng tròn nhỏ trên các vị trí của các Keypoint

    img_2=cv2.drawKeypoints(gray,kp,flags=cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS) # Nếu bạn truyền cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS 
                                                                         # cho nó, nó sẽ vẽ một vòng tròn có kích thước của Keypoint và thậm chí nó sẽ hiển thị hướng của nó	
    ```
    + <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/b8949baaf30524080640a46fee6281cd4bc9a0c5/Image/SIFT_detect.png">
    + Để tính mô tả sử dụng hàm **kp, des = sift.detectAndCompute(gray,None)** . Hàm này sẽ trực tiếp tìm các keypoint mà không cần các bước trên. Hàm sẽ trả về 2 thông số: kp sẽ là một danh sách các Keypoint và des là một mảng dạng Number_of_keypoints * 128
  - Assignment: [Classification MNIST](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/edf620eaa59576637201e2eb91f73112d5834475/Week_6/Image-Classification-using-SIFT.ipynb) and [Classification Animal Faces.](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/68f512693039bfd774fb10e271fd2b42b584f4f1/Week_6/SIFT_SVM.ipynb)

### Week 7: Báo Cáo Giữa Kì - Classification Of Face Animal
<img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/996e14111f2bfb8ab095d1b3657a6f60b5a7f610/Image/report_cv.png">

### Week 8: Mô hình mạng Neural Network GoogleNet.
  - GoogleNet được tạo thành từ các inception module rất hiệu quả.
  - “Inception module”: thiết kế 1 cấu trúc liên kết mạng cục bộ đủ tốt và sau đó stack các modules lại để tạo thành các mạng lớn hơn(network within a network) tức đầu ra của module này là đầu vào module kia
  - Ý tưởng của GoogleNet là kết hợp các kernel khác nhau trong cùng một module tăng số lượng thông tin từ vùng ảnh trong ảnh.
  - Với kiểu thiết kế naïve version: Gồm có 4 kernel để trích xuất đặc trưng ảnh: 1x1, 3x3, 5x5 và một 3x3 maxpooling. Mỗi kernel đều thêm padding để đảm bảo đầu ra feature map có cùng kích thước để concatenate lại với nhau.
  - Kiểu thiết kế thứ 2: Thêm các bottleneck (kernel size 1x1) trước khi đi qua các kernel size khác để giảm chiều sâu → giảm số lượng phép nhân xuống rất nhiều.
  - <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/c4b9e20d5485454b3da47fc0293d69c5b4f63980/Image/InceptionModule.png">
  - Vùng đầu được thiết kế kiểu stem network: conv-maxpooling
  - Khi tính gradient từ đầu ra đến weight đầu, ta tính loss function sẽ đi qua nhiều change rules khác nhau, việc dùng nhiều change rules sẽ dẫn đến hiện tượng gradient vanishing(mất mát đạo hàm) vì thế cần bổ sung thêm các đầu ra. Khi thiết kế các loss function ngay chỗ đó, thì tại thời điểm nào đó vẫn có cập nhật đạo hàm về từ hướng này xuống, nó bổ sung đạo hàm từ các hướng kia lại với nhau thì sẽ giảm hiện tượng gradient vanishing(mất mát đạo hàm)
  - Gradient vanishing: Là vấn đề xảy ra khi huấn luyện các mạng nơ ron nhiều lớp. Khi huấn luyện, giá trị đạo hàm là thông tin phản hồi của quá trình lan truyền ngược. Giá trị này trở nên vô cùng nhỏ tại các lớp nơ ron đầu tiên khiến cho việc cập nhật trọng số mạng không thể xảy ra
  - <img src = "https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/2891b3a00410d5908bbb851bc091498dbb580b07/Image/GoogleNet.png">
 
 ## ĐỒ ÁN CUỐI KÌ
 ### Giới thiệu đề tài
 - Tên đề tài: Garbage Classification
 - File báo cáo: [Final Report](https://github.com/trong-khanh-1109/CS231.M13.KHCL/blob/f184d613576f724c47bb1ffc13e03652a401320b/Final%20Project/Report_CV.pdf)
 ### Thực nghiệm
 - Folder: [Code](Final%20Project/Code)
<!-- Footer -->
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;`Copyright © 2021 - Đỗ Trọng Khánh`
