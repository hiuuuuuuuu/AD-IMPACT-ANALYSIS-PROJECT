# AD IMPACT ANALYSIS PROJECT

![image](https://github.com/user-attachments/assets/9d75a586-0032-46e1-b397-1077fe72705d)

### Data Source: 
  [marketing_AB.csv](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing)

### Tool:
- Python : JupyterLab

### Data Dictionary:
  **Index**: Chỉ số dòng

  **user id**: Mã người dùng (duy nhất)

  **test group**: Nếu là **"ad"** thì người đó **đã xem quảng cáo**, nếu là **"psa"** (public service announcement) thì họ **chỉ xem thông báo dịch vụ cộng đồng**

  **converted**: Nếu người đó mua sản phẩm thì là True, ngược lại là False

  **total ads**: Số lượng quảng cáo mà người đó **đã xem**

  **most ads day**: Ngày mà người đó xem số lượng quảng cáo lớn nhất

  **most ads hour**: Giờ trong ngày mà người đó xem số lượng quảng cáo lớn nhất
  
  ### Introduce:
- Các công ty tiếp thị muốn thực hiện các chiến dịch thành công, nhưng thị trường rất phức tạp và có nhiều lựa chọn có thể hiệu quả. Vì vậy, thông thường họ điều chỉnh các thử nghiệm A/B, đó là một quy trình thử nghiệm ngẫu nhiên trong đó hai hoặc nhiều phiên bản của một biến (trang web, thành phần trang, biểu ngữ, v.v.) được hiển thị cho các phân khúc người khác nhau cùng một lúc để xác định phiên bản nào để lại tác động tối đa và thúc đẩy các số liệu kinh doanh.

### Goal:
  - **Phân tích các nhóm, xác định xem quảng cáo có thành công hay không?**
  
  - **Việc hiển thị quảng cáo cho người dùng có dẫn đến việc mua sắm nhiều hơn không?**

### 1. Import and clean data
### 2. Cân bằng dữ liệu
- Mục đích của việc cân bằng dữ liệu giữa hai nhóm (trong trường hợp này là nhóm "ad" và nhóm "psa") bằng cách thực hiện undersampling nhóm lớn hơn là để giải quyết vấn đề mất cân bằng dữ liệu. Việc có số lượng mẫu tương đương từ cả hai nhóm sẽ giúp đảm bảo rằng các kết quả phân tích hoặc mô hình hóa không bị thiên lệch bởi nhóm có nhiều mẫu hơn.
- undersampling nhóm ad để cân bằng số lượng với nhóm psa 

### 3.EDA (Exploratory Data Analysis)

![image](https://github.com/user-attachments/assets/9229f0c9-a744-4b54-9eb2-38225f4f956f)

![image](https://github.com/user-attachments/assets/5b8629fb-6f5a-49f6-a90c-61d1a9385877)

![image](https://github.com/user-attachments/assets/054b8836-27a4-4c3a-8384-b2d33b475412)

![image](https://github.com/user-attachments/assets/ea0d7554-feb2-4e79-bdd2-b1848112b533)

![image](https://github.com/user-attachments/assets/8d7d7ba8-a37e-4879-be86-a201e58420da)






### 4. A/B Test:

   **Phân tích các nhóm, xác định xem quảng cáo có thành công hay không?**
   
**Treatment Group:** (nhóm can thiệp) nhóm người (_ad_) thí nghiệm được tiếp xúc với yếu tố thử nghiệm hoặc thay đổi mới hiện thị quảng cáo. Mục tiêu là để xem liệu việc hiển thị quảng cáo có tăng tỷ lệ chuyển đổi hay không.

**Control Group:** (nhóm kiểm soát) nhóm người (_psa_) không tiếp xúc với yếu tố thử nghiệm hoặc thay đổi mới hiển thị quảng cáo dịch vụ công. Mục tiêu là để so sánh với nhóm "treatment" và đánh giá hiệu quả thực sự của quảng cáo.

![image](https://github.com/user-attachments/assets/1e8a7e8c-55b4-4c89-bac5-cbaa5c086910)


**Sau phân tích có quan sát đáng chú ý:**
- Sự tăng nhẹ trong tỷ lệ chuyển đổi của nhóm Treatment khi cân bằng dữ liệu có thể cho thấy quảng cáo có tác động tích cực hơn trong điều kiện cân bằng. => **quảng cáo có thể thực sự đang ảnh hưởng lên hành vi người tiêu dùng.**
- Tỷ lệ chuyển đổi của nhóm Control không thay đổi, điều này cho thấy rằng sự thay đổi trong nhóm Treatment có thể do quảng cáo chứ không phải do yếu tố bên ngoài.


### 5.Hypothesis_testing :

**Việc hiển thị quảng cáo cho người dùng có dẫn đến việc mua sắm nhiều hơn không?**

* (H0): Việc hiển thị quảng cáo không có ảnh hưởng đáng kể đến số lượng mua sắm.
* (H1): Việc hiển thị quảng cáo có ảnh hưởng đáng kể đến số lượng mua sắm.

- Sử dụng phương pháp t-test so sánh hai mẫu độc lập giữa nhóm Treatment và nhóm Control thông qua tỷ lệ chuyển đổi:

![image](https://github.com/user-attachments/assets/3bf8b622-5f79-478b-9a30-0e2507dae8db)


**Kết luận rằng**: 
- Mặc dù p-value trong dữ liệu cân bằng cao hơn so với dữ liệu gốc, nhưng vẫn rất nhỏ, cho thấy rằng sự khác biệt đáng kể vẫn tồn tại trong dữ liệu đã cân bằng. Điều này cho thấy rằng cân bằng dữ liệu không làm mất đi sự khác biệt quan trọng giữa các nhóm.
- T-statistic: Giá trị t-statistic giảm nhẹ trong dữ liệu cân bằng, nhưng vẫn đủ lớn để chứng tỏ sự khác biệt đáng kể.

**=> Việc hiển thị quảng cáo có ảnh hưởng đáng kể đến số lượng mua sắm, và kết quả này được xác nhận qua cả dữ liệu gốc và dữ liệu đã cân bằng. Điều này có thể hỗ trợ quyết định tiếp tục hoặc tăng cường các chiến dịch quảng cáo dựa trên hiệu quả được chứng minh.**

### 6. Summary:
- Quan sát từ dữ liệu cho thấy tỷ lệ chuyển đổi trung bình trong nhóm Treatment cao hơn nhóm Control. Điều này cho thấy **quảng cáo ảnh hưởng tích cực đến tỷ lệ chuyển đổi**. Kết quả này vẫn nhất quán ngay cả khi cân bằng dữ liệu, gợi ý mối liên hệ giữa việc tiếp xúc với quảng cáo và khả năng chuyển đổi cao.
- Qua kiểm tra giả thuyết xác định liệu việc hiện thị quảng cáo có dẫn đến việc mua sắm nhiều hơn. Giả thuyết không (H0) cho rằng việc hiển thị quảng cáo không có ảnh hưởng đáng kể đến số lượng mua hàng, trong khi giả thuyết khác (H1) cho rằng có ảnh hưởng. => Việc **hiển thị quảng cáo có ảnh hưởng đáng kể đến số lượng mua sắm**, và kết quả này được xác nhận qua cả dữ liệu gốc và dữ liệu đã cân bằng. **Điều này có thể hỗ trợ quyết định tiếp tục hoặc tăng cường các chiến dịch quảng cáo dựa trên hiệu quả được chứng minh.**
