# classification
## Question 1:
Mục tiêu bài 1 là implement perceptron classifier theo mô tả của đề bài đó là: duyệt qua từng dữ liệu một. Khi đến một dữ liệu (f, ytrue), ta tìm label có điểm cao nhất đó là ypred = max(f * self.weights[y], y) trong đó f * self.weights[y] chính là điểm của label y với y thuộc legalLabels.
Sau đó so sánh ypred với ytrue, nếu bằng nhau, ta sẽ không làm gì. Còn nếu khác nhau thì weight[ytrue] tăng thêm f, còn weight[ypred] giảm đi f.
## Question 2:
Với Bài 2 ta cần tìm ra 100 features có weight lớn nhất trong một label nào đó. Cách làm là sắp xếp các features theo thứ tự weight giảm dần rồi lấy ra 100 phần tử đầu tiên. Sau khi chạy command, các feature hiện lên giống hình (a).
## Question 3:
Mục tiêu bài 3 là implement mira classifier theo mô tả của đề bài: tương tự như bài 1, ta duyệt qua các dữ liệu. Sau đó tìm ra label có score lớn nhất là ypred rồi so sánh nó với ytrue, nếu chúng bằng nhau, ta không làm gì. Còn nếu chúng khác nhau, lúc này weight[ytrue] tăng thêm f * tau, còn weight[ypred] giảm đi f * tau. Trong đó, tau là giá trị nhỏ nhất giữa C trong Cgrid và biểu thức ((weight[ypred] - weight[ytrue]) * f + 1)/(2*f*f)
## Question 4:
Tạo 1 features mới giúp tăng Performance 
feature dạng True false
Ý tưởng: kiểm tra lặp lại pixel 0 ,hoặc cụm pixel bằng cách kiểm tra bên cạnh pixel 0 còn có pixel khác(!=0) cạnh nó hay không


Sử dụng defth first seach để kiểm tra toàn bộ trạng thái pixel kế tiếp
	- Nếu vượt ra ngoài size  thì trả về false(từ lúc duyệt ban đầu đến khi tới rìa đều không xuất hiện pixel khác 0)
	- Xuất pixel(x,y) khác 0 thì trả về True
	- Nếu (x,y) đã duyệt trả về true 
	- Nếu không thì đưa (x,y) vào tệp đã duyệt và không duyệt lại nữa (đánh dấu đã duyệt cho  (x,y))
	- Trả về cụm logic and của  hàm defth first seach  cho các pixel xung quanh pixel đang duyệt:
	    return dfs(x - 1, y) and dfs(x + 1, y) and dfs(x, y - 1) and dfs(x, y + 1)
	- Nếu tất cả đều true thì mới trả về true, chỉ cần 1 chiều mà vượt ra khỏi biên thì sẽ là sai: 1 false-->tất cả đều false

Khởi tạo loop là false duyệt tất cả pixel nếu 1 cái thả mãn dfs tức là đã có lặp loop=true trả về giá trị loop sau cùng gọi tên feature đó ra
## Question 5:
Duyệt qua tất cả range( self.max_iterations)
Duyệt qua tất cả tệp trainingdata
Khởi tạo 1 max score với giá trị âm vô cùng
	Duyệt qua lable trong trainingdata
	Tính score += value * weights của các feature tương ứng:[lable][feature]
	Trả về score lớn nhất kèm lable đi kèm 
	Kiểm tra maxlable nếu đã có trong trainingtables thì bỏ qua tiếp tục vòng lặp ngược lại thì thêm nó vào training label 
## Question 6:
Yêu cầu: tạo cá feature cho con pacman
	Feature closestfood:
	- Duyệt tấy cả food, đưa ra khoảng cách giữa food và pacman lấy khoảng cách food gần nhất gán nó cho feature closestfood
	Feature closestghost:
	- Duyệt tất cả ghost đưa ra khoảng cách gost gần nhất 
	Đưa ra feature ghost gần nhất:
	- Đưa ra feature food còn lại dựa trên getnumfood
