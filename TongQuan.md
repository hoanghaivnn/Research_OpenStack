# Tìm hiểu và so sánh các giải pháp điện toán đám mây.
-----------------------------------------------------------------

## I. Ảo hóa ( Virtualization) :
- Hiểu nôm na thì nó là một kỹ thuật tạo ra các phần cứng, thiết bị mạng, thiết bị lưu trữ,... trên các thiết bi vật lý một cách mô phỏng.
- Đi kèm với Ảo hóa là các cụm từ như : Hardware Viturelization, Platform Virtualization : các cụm từ này chỉ việc tạo ra các thành phần cứng để tạo ra các máy ảo ( Virtual Machine ) , chúng có gần như đầy đủ các thành phần như máy thật ( Physical Machine ) và có thể cài đặt trên hệ điều hành Linux, Windows,... Trong Network thì có các Router Switch ảo,... và tất nhiên người sử dụng có thể sử dụng và khai thác chúng như các thiết bị thật.

## II. Cloud Computing
- Đa số nó được hiểu là Điện toán đám mây. Theo NIST , điện toán đám mây được định nghĩa :
- Cloud Computing là một mô hình cho phép truy cập qua mạng để lựa chọn và sư dụng tài nguyên có thể dược tính toán. Ví dụ như mạng, máy chủ, lưu trữ, ứng dụng và dịch vụ ) theo nhu cầu một cách thuận tiện và nhanh chóng, đồng thời cho phép kết thúc sử dụng dịch vụ, giải phóng tài nhuyên dễ  dàng , giảm thiểu các giao tiếp với các nhà cung cấp.
- Cloud Computing có 5 đặc tính, 4 mô hình dịch vụ và 3 mô hình triển khai.
### 2.1 Các đặc tính của Cloudcomputing
Khi nhắc đến điện toán đám mây , người ta thường nghĩ đến con số 5-4-3 : 
#### 5 đặc điểm :
- Tính tự phục vụ theo như cầu : cho phép khách hàng đơn phương thiết lập yêu cầu nguồn lực nhằm đáp ứng các yêu cầu của hệ thống như thời gian sử dụng Server, dung lượng lưu trữ, khả năng đáp ứng các tương tác của hệ thống ra bên ngoài.
- Truy cập diện rộng : Khách hàng có thể đứng ở bất cứ vị trí nào, miễn có Internet là có thể truy cập, sử dụng được dịch vụ .
- Dùng chung tài nguyên và độc lập vị trí : Tài nguyên của nhà cung cấp dịch vụ được dùng chung, phục vụ cho nhiều người dùng dựa trên mô hình " multi-tenant" , cho phép tài nguyên phần cứng và tài nguyên ảo hóa được cấ phát tự động dựa trên nhu cầu của người dùng. Người sử dụng không cần quan tâm đến vị trí của các tài nguyên được cung cấp.
- Khả năng co giãn : Cho phép có thể mở rộng, hoặc thu nhỏ các tài nguyên được cấp phát theo nhu cầu hay yêu cầu của người dùng.
- Chi trả theo thực dùng : Người dùng sẽ chỉ phải trả phí những gì mình sử dụng.

#### 4 mô hinh dịch vụ
- Public Cloud ( Đám mây công cộng ) : Là các dịch vụ trên nền tảng Cloud Computing để cho các cá nhân, tổ chức thuê và dùng chung tài nguyên.
- Private Cloud ( Đám mây riêng ) : Dùng chung cho một doanh nghiệp và không chia sẻ với người dùng ngoài doanh nghiệp đó.
- Community Cloud ( Đám mây cộng đồng ) : là các dịch vụ trên nền tảng Cloud Computing do các công ty cùng hợp tác xây dựng và cung cấp dịch vụ cho một cộng đồng nào đó.
- Hybrid Cloud ( Đám mây lai ) : là sự kết hợp giữa mô hình Pubic Cloud và Private Cloud.

#### 3 mô hình triển khai
- Infrastructure as a Service ( Dịch vụ hạ tầng ) : khách hàng quản lý các tài nguyên như là dịch vụ : bao gồm máy chủ, thiết bị mạng, bộ nhớ, CPU, không gian đĩa cứng, trang thiết bị trung tâm dữ liệu.
- Platform as a Servive (Dịch vụ nền tảng ) : Khách hàng quản lý việc phát triển, triển khai và vận hành các ứng dụng trên nền tảng Cloud Computing.
- Software as a Service ( dịch vụ phần mềm ) : Khách hàng sử dụng các ứng dụng của nhà phát triển mà không cần quan tâm nó được tạo ra như thế nào.
### 2.2 Mô hình Public Cloud
Mô hình public cloud là 1 trong 4 mô hình của điện toán đám mây, trong đó, nhà cung cấp dịch vụ sẽ tạo ra các nguồn tài nguyên như : máy ảo , ứng dụng,bộ nhớ lưu trữ có sẵn trên môi trường internet. Nó có thể được sử dụng miễn phí hoặc trả phí sau mỗi lần sử dụng dịch vụ.

#### Lợi ích của việc sử dụng Public Cloud

Những lợi ích của việc sử dụng Public Cloud là : 
- Nó làm giảm chi phí đầu tư cơ sở vật chất cũng như nguồn lực so với việc tự triển khai tại mỗi doang nghiệp.
- Cho phép mở rộng nhu cầu và đáp ứng được khối lượng công việc lớn của người dùng.
- Hạn chế được việc lãng phí sử dụng tài nguyên, do người dùng sẽ trả tiền sử dụng dịch vụ khi họ sử dụng tài nguyên.
#### Kiến trúc Public Cloud

Public Cloud là một môi trường ảo hóa đầy đủ , 

## OpenStack là gì ?
- OpenStack là một phần mềm mã nguồn mở , dùng để triển khai Cloud Computing , bao gồm Private Cloud và Public Cloud.

<img src="https://i.imgur.com/1QPvTGM.png">

Hình minh họa vị trí của OpenStack trong thực tế
- Phía dưới là phần cứng đã được ảo hóa để chia sẻ cho ứng dụng, người dùng.
- Trên cùng là các ứng dụng của người dùng.
- OpenStack là phần ở giữa 2 phần tren, trong OpenStack có nhiều thành phần , module khác nhau.

<img src="https://i.imgur.com/IuAdtJQ.png">

Các thành phần ( Project con) trong OpenStack :

- Compute ( code-name Nova) : 
- Networking (code-name Neutron)
- Object Storage (code-name Swift)
- Block Storage (code-name Cinder)
- Identity (code-name Keystone)
- Image Service (code-name Glance)
- Dashboard (code-name Horizon)
- Telemetry (code-name Ceilometer)
- Orchestration (code-name Heat)
