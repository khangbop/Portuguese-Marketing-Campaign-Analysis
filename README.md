# Project3
Machine Learning

Chiến dịch Tiếp thị qua điện thoại của 1 tổ chức ngân hàng Bồ Đào Nha

Giải thích dữ liệu:

**DỮ LIỆU KHÁCH HÀNG
{
- Age (Dữ liệu số): Tuổi
- Job (Dữ liệu phân loại): Các loại nghề bao gồm:
	+ admin		: quản trị viên
	+ blue-collar	: nhân viên lao động tay chân
	+ entrepreneur	: doanh nhân
	+ housemaid	: giúp việc
	+ management	: công việc liên quan đến quản trị, quản lý
	+ retired	: nghỉ hưu
	+ self-employed	: những công việc do cá nhân tự chủ
	+ services	: nghề dịch vụ
	+ student	: học sinh/sinh viên
	+ technician	: kỹ thuật viên
	+ unemployed	: thất nghiệp
	+ unknown	: không rõ
- Marital (Dữ liệu phân loại): tình trạng hôn nhân:
	+ divorced	: bao gồm cả góa phụ và cả ly hôn
	+ married	: đã kết hôn
	+ single	: còn độc thân
	+ unknown	: không rõ
- Education (Dữ liệu phân loại): Trình độ học vấn (Trình độ học vấn ở Bồ Đào Nha)
	+ basic.4y		: 4 năm trong mức Giáo dục cơ bản (từ lớp 1-4)
	+ basic.6y		: 6 năm trong mức Giáo dục cơ bản (từ lớp 1-6)
	+ basic.9y		: Giáo dục cơ bản (Từ lớp 1-9)
	+ high.school		: Giáo dục nâng cao (từ lớp 10-12)
	+ illiterate		: Mù chữ
	+ professional.course	: Khóa chuyên nghiệp (hình như trên đại học)
	+ university.degree	: tốt nghiệp đại học
	+ unknown		: không rõ
- Default (Dữ liệu phân loại): Có đăng ký thẻ tín dụng mặc định
	+ yes
	+ no
	+ unknown
- Housing (Dữ liệu phân loại): Có khoản vay nhà ở không
	+ yes
	+ no
	+ unknown
- Loan (Dữ liệu phân loại): Có khoản vay cá nhân không
	+ yes
	+ no
	+ unknown
} 

**DỮ LIỆU LIÊN QUAN ĐẾN CHIẾN DỊCH TIẾP THỊ HIỆN TẠI CỦA NHỮNG CUỘC ĐT GẦN ĐÂY NHẤT
{
- Contact (Dữ liệu phân loại): phương thức liên lạc/liên hệ
	+ cellular	: điện thoại di động
	+ telephone	: điện thoại có dây/điện thoại bàn
- Month (Dữ liệu phân loại): tháng diễn ra cuộc đt (jan, feb, mar, ...)
- Day_of_week (Dữ liệu phân loại): thứ diễn ra cuộc đt (thứ 2,3,4,...)
- Duration (Dữ liệu số): Thời lượng liên lạc trên đt
	+ Lưu ý: Thuộc tính này ảnh hưởng lớn đến mục tiêu đầu ra (output)
	ví dụ nếu thời lượng = 0 thì y ='no'.
	Tuy nhiên, không biết được thời lượng trước khi cuộc gọi xảy ra.
	Mà khi kết thúc cuộc gọi thì sẽ biết y.
	==> nên như vậy chỉ cần dựa vào thời lượng là sẽ biết được output vì nó ảnh hưởng
	trực tiếp tới y
	==> nên ta sẽ xóa cột này đi khi dự đoán mô hình
}

**DỮ LIỆU KHÁC
{
- Campaign (Dữ liệu số): số cuộc điện thoại diễn ra suốt chiến dịch của khách hàng này
- Pdays (Dữ liệu số): số ngày đã trôi qua kể từ lần cuối cùng của khách hàng được liên 
hệ từ chiến dịch trước đó (999 nghĩa là khách hàng không dc liên hệ trước đó)
- Previous (Dữ liệu số): số cuộc điện thoại diễn ra trong chiến dịch trước với khách hàng này
- Poutcome (Dữ liệu phân loại): Kết quả của chiến dịch trước
	+ failure	: thất bại
	+ nonexistent	: không tồn tại
	+ success	: thành công
}

**DỮ LIỆU VỀ BỐI CẢNH KINH TẾ VÀ XÃ HỘI
{
- Emp.var.rate (Dữ liệu số): Tỷ lệ thay đổi việc làm (Tính theo quý)
- Cons.price.idx (Dữ liệu số): Chỉ số giá tiêu dùng (Tính theo tháng)
- Cons.conf.idx (Dữ liệu số): Chỉ số niềm tin người tiêu dùng
- Euribor3m (Dữ liệu số): Lãi suất Euribor kỳ hạn 3 tháng
	+ Euribor (Euro Interbank Offered Rate) hay Tỉ lệ chào bán liên ngân hàng Euro,
	là tỉ lệ tham chiếu được xây dựng từ lãi suất trung bình mà các ngân hàng Châu 
	Âu cung cấp cho vay ngắn hạn không có tài sản bảo đảm trên thị trường liên ngân
	hàng. Thời gian đáo hạn của các khoản vay được sử dụng để tính Euribor thường 
	dao động từ một tuần đến một năm.
- Nr.employed (Dữ liệu số): chỉ số số lượng nhân viên theo quý
}

**DỮ LIỆU ĐẦU RA
- y (Dữ liệu phân loại): Khách hàng có đăng ký khoản tiền gửi có kỳ hạn không
	+ yes
	+ no

**Note: Có những dữ liệu ghi là Unknown. Điều này có nghĩa là họ không biết.
nên ta sẽ đổi thành NaN (Missing Value). Tùy vào kiểu dữ liệu và tỷ lệ % so với
toàn dữ liệu ta sẽ xử lý chúng.

--------------------------------------------------------------------------------------------
DỰ ĐOÁN PHÂN LOẠI
Predict Classification

Sử dụng các mô hình sau:
- Logistic Regression
- KNN/K-Nearest Neighbors
- SVM/Support Vector Machine
- Decision Tree
- Random Forest
- Boosting

--------------------------------------------------------------------------------------------
Các bước phân tích trong Machine Learning

1. Data Preprocessing
2. EDA
3. Feature Scaling
4. Split Train/Test
5. Predicting Test Results
6. Evaluating Model Performance

--------------------------------------------------------------------------------------------
Đầu tiên ta sẽ xét về những dữ liệu khách hàng (Tuổi, nghề nghiệp, tình trạng hôn nhân,...)
liệu những chỉ số này có ảnh hưởng tới khả năng khách hàng sẽ đăng ký (y)

TUỔI:
- Tổng số lượng khách hàng là 41.18k với 4639 người đăng ký tức chỉ chiếm khoảng 11%.
- Ta nhìn biểu đồ biểu thị, độ tuổi kh đăng ký tập trung vào khoảng từ 30 đến 60 tuổi.
Đây là chỉ tính những người đã đăng ký
- Còn khi nhìn tổng quan toàn bộ thì độ tuổi kh hầu là trong khoảng từ 20 đến 70 tuổi.
toàn bộ từ 70 tuổi trở lên là trường hợp ngoại lai.
- Những điểm ngoại lai này rất ít chỉ chiếm 1.14%
- Nhưng ta nên xét có bỏ không: Khi xét cả 2 TH đối vs khách hàng có đk và ko đk thì
Những kh có đk có thể phân tán trên những điểm ngoại lai này. Nên mình nghĩ không nên bỏ.
Vì mặc dù hiếm nhưng vẫn có thể xảy ra.
=> Kết luận: Tuổi có ảnh hưởng đến y không? Có thể có vì mặc dù ta thấy có phân tán trên
toàn bộ độ tuổi nhưng vẫn chủ tập trung từ 30-60 tuổi.

NGHỀ NGHIỆP, TÌNH TRẠNG HÔN NHÂN, HỌC VẤN:
- Đối với học vấn thì tốt nghiệp đại học chiếm tỷ lệ cao nhất, tình trạng hôn nhân là đã
kết hôn, nghề nghiệp thì là admin (quản trị viên)
- So sánh đầu ra (y) thì hầu như các biểu đồ không thay đổi mấy. Tức là kh đã đăng ký định
mức vẫn chủ yếu là tốt nghiệp đại học, đã kết hôn và thuộc nghề quản trị viên.
=> Kết luận: 3 chỉ số này vẫn có ảnh hưởng đến khả năng kh đăng ký định mức.

VAY CÁ NHÂN, VAY NHÀ Ở, TÍN DỤNG MẶC ĐỊNH:
- Đối vs 3 chỉ số này thì hầu như tất cả khách hàng đều không có đk khoản vay cá nhân và thẻ
tín dụng mặc định. Khoản vay nhà ở thì phân bổ ở cả 2 vừa có vừa không, dù số lượng kh đk nhiều
hơn 1 chút.
- Khi ta đưa vào đầu ra ta thấy có sự thay đổi ở cả 3 biểu đồ mặc dù không nhiều.
- Ở biểu đồ 2 (tín dụng) thì mất luôn cột yes. Tức là những khách hàng đã đăng ký tiền gửi sẽ
không đăng ký tín dụng mặc định
=> Kết luận: Ở cả 3 chỉ số này đều có ảnh hưởng đến khả năng kh đăng ký tiền gửi.


Tiếp theo ta sẽ xem 3 yếu tố liên quan đến chiến dịch tiếp thị (CONTACT, DAY_OF_WEEK, MONTHS)

CONTACT:
- Nhìn tổng quan thì ở cả 2 phương thức, đtdd chiếm tỷ lệ cao hơn so vs đt bàn 63% tổng số
- Giải thích vì sao: Đơn giản là đtdd đc ưa chuộng hơn vì tiện lợi và đt bàn trở nên lỗi thời
nên có sự chênh lệch như vậy
- Khi đưa vào biến đầu ra thì tỷ lệ kh sử dụng đtdd tăng lên 83%
- Nên nhớ hầu như những kh thuộc biến y (kh đăng ký) là người đã kết hôn, tốt ngiệp đh, thuộc
độ tuổi trẻ và trung niên -> ta có thể dễ suy ra nhu cầu về đtdd cũng tăng.
=> Kết luận: Đầu ra cũng dc ảnh hưởng bởi tỷ lệ người sử dụng đtdd.

MONTH:
- Đây là những tháng mà cuộc điện thoại diễn ra.
- Ta thấy từ tháng 3-5 có sự tăng vọt về số lượng khách hàng, đến t6 thì lại giảm mạnh, từ t6
t7 t8 tăng nhẹ, tiếp tục giảm mạnh tới t9, tăng nhẹ tới tháng 11, và tuột mức thấp nhất vào t12
- Khi ta lọc ra những khách hàng đã đk gửi tiết kiệm (y), ta thấy có sự đổi mặc dù không quá rõ
ràng
=> Kết luận: có ảnh hưởng

DAY_OF_WEEK:
- Những thứ mà cuộc điện thoại của chiến dịch diễn ra.
- Nhìn chung thì có sự phân bổ đồng đều ở các ngày trong tuần và cao nhất vào t5
- Khi đưa vào biến y để xét sự tương quan: Ta thấy t5 vẫn cao nhất, t2 và t6 đặc biệt thấp hơn các
thứ khác.
- T5 là ngày gì? Tại sao t2 t6 lại hiệu suất thấp. Có thể hiểu t2 là ngày đầu tuần, kh sẽ không
thích tiếp nhận các cuộc gọi tiếp thị, cũng như t6 ngày cuối tuần, -> ảnh hưởng hiệu suất của
chiến dịch
=> Kết luận: có ảnh hưởng


Và thứ 3, những thông tin liên quan khác về chiến dịch

CAMPAIGN: đây là chỉ số cuộc điện thoại diễn ra trong suốt chiến dịch
- Phần lớn khách hàng đều nhận 1 cuộc
- Đối với khách hàng đã đăng ký thì hầu nhưng cũng nhận 1 cuộc đt
- So sánh 2 biểu đồ thì ta thấy có sự tương đồng trên cả 2 biểu đồ
Nhiều nhất 1 cuộc sau đó giảm dần
=> Có ảnh hưởng

PDAYS: Đây là chỉ số số ngày đã trôi qua kể từ lần cuối cùng của khách hàng được liên 
hệ từ chiến dịch trước đó (999 nghĩa là khách hàng không dc liên hệ trước đó)
- Hơn 95% khách hàng đều không đc liên hệ trước đó
- Chỉ 1 số ít kh dc liên hệ
- Thêm y
=> Biểu đồ cũng tương tự (thay đổi ít)

PREVIOUS: số cuộc điện thoại diễn ra trong chiến dịch trước với khách hàng này
- Hơn 85% khách hàng không tham gia chiến dịch trước đó
- Điều này cũng tương tự đối vs khách hàng đăng ký gửi tiết kiệm, đa số khách hàng cũng ko
tham gia chiến dịch trc đó
=> có ảnh hưởng

POUTCOME: Đây là kết quả chiến dịch trc
- nonexistence biểu thị số người ko tham gia chiến dịch trc
- tỷ lệ thành công chỉ có 3% và thất bại 10%
- Đưa vào biến y tỷ lệ thành công lên 19% thất bại 13%
=> có nghĩa là trong số những người đăng ký gửi tiết kiệm có khoảng 32% người tham gia chiến dịch
trước đó


Cuối cùng phải kể đến: Những chỉ số liên quan đến kinh tế xã hội.

Emp.var.rate (Dữ liệu số): Tỷ lệ thay đổi việc làm (Tính theo quý)
- 1.40 tức là khách hàng đó có tỷ lệ 1.4% thay đổi việc làm <-- đa số khách hàng nằm trong mốc này
- Những khách hàng đăng ký gửi có kỳ hạn có tỷ lệ thay đổi việc làm thấp hơn -1.80

Cons.price.idx (Dữ liệu số): Chỉ số giá tiêu dùng (Tính theo tháng) CPI
- là chỉ số tính theo phần trăm để phản ánh mức thay đổi tương đối của giá hàng tiêu dùng theo 
thời gian -> theo tháng tức là tỉ số% giá thay đổi theo tháng
vd: 93.994 là từng tháng sẽ thay đổi 94%
- so sánh 2 biểu đồ giữa chỉ số giá tiêu dùng của tổng khách hàng vs của khách hàng đã đk gửi
có kỳ hạn -> có đk phân bố đều hơn so vs tổng 
