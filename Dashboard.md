# Các kịch bản trong Openstack
---------------------------------------
# Mục lục
- [I. Các hoạt động với quyền Admin](#1)
 - [1.1 Thao tác với Flavor](#11)
 - [1.2 Thao tác với Image](#12)
 - [1.3 Thao tác với Router](#13)
 - [1.4 Thao tác với Network](#14)
 - [1.5 Thao tác với key](#15)
 - [1.6 Thao tác với Port/Interface](#16)
 - [1.7 Thao tác với Floating Ip](#17)
 - [1.8 Thao tác với Project](#18)
 - [1.9 Thao tác với Group](#19)
 - [1.10 Thao tác với User](#110)
 - [1.11 Thao tác với Security Group](#111)
- [II. Các hoạt động với VM](#2)
 - [2.1 Tạo VM](#21)
 - [2.2 Attack/Detack Interface](#22)
 - [2.3 Thao tác với Snapshot](#23)
 - [2.4 Rebuild Instance](#24)
- [III. Các hoạt động với Cinder](#3)
 - [3.1 Tạo Volume](#31)
 - [3.2 Sizing Volume](#32)
 - [3.3 Snapshot Volume](#33)
 - [3.4 Volume Type](#34)
- [IV . Các hoạt động Monitoring](#4)
 - [4.1 Overview](#41)
 - [4.2 Tùy chỉnh Quocta](#42)
 - [4.3 Hypervisor](#43)

<a name=1></a>
# I . Các hoạt động với quyền Admin

<a name=11></a>
## 1.1 Thao tác với Flavor
Đầu tiên để thao tác với Flavor thì người dùng cần phải có quyền Admin trong Project đó.

Truy cập theo các trường `Admin`/`Compute`/`Flavors` để tiến hành quản lý các Flavor.

<img src=https://i.imgur.com/9sqAHU5.png></img>

Giao diện quản lý Flavor : tạo xóa, hiển thị thông tin các Flavor :

| Options | Định nghĩa |
|-----|-----|
|Name | Tên Flavor|
|VCPU| Số lượng Virtual CPU được thiết lập cho Flavor|
|RAM| Dung lượng RAM được thiết lập cho Flavor|
|Root Disk| Dung lượng ổ `/` cho Flavor|
|Emphermetal Disk| Dung lượng ổ đĩa lưu trữ tạm thời cho Flavor. Ổ này sẽ tự động xóa khi VM bị xóa. Mặc định là 0GB|
|Swap Disk| Dung lượng phân vùng Swap : RAM ảo cho Flavor|
|RX/TX factor| Tùy chọn tùy chỉnh lưu lượng băng thông so với RX/TX . mặc định là 1, nghĩa là băng thông sẽ giống như băng thông của mạng kết nối|
|ID| ID của Flavor |
|Public| Trạng thái chia sẻ của Flavor |
### Tạo Flavor

Để tạo một Flavor ta tiến hành như sau :

<img src=http://i.prntscr.com/yAINf4ZfS7CrwIyDfStUlQ.png></img>

Điền các thông số cho Flavor :

<img src=http://i.prntscr.com/BkLZSmq8Rlqd3ErzfpPlwg.png>

Thiết lập quyền truy cập và sử dụng Flavor

<img src=http://i.prntscr.com/Pe69AYkCToOZmfDdTUhtfA.png>

- `+` : Thêm cho phép Project đó sử dụng Flavor
- `-` : Loại bỏ, không cho Project đó sử dụng Flavor

### Xóa Flavor
Có thể chọn 1 trong 2 cách :
<img src=http://i.prntscr.com/hB2JozUhTiCQtQfQFYOXQQ.png>
- Tích vào Flavor cần xóa , chọn `Delete Flavor`
- Tại dòng Flavor cần xóa : `Actions`/`Delete Flavor`

<a name=12></a>
## 1.2 Thao tác với Image

Với quyền Admin thì có 2 lựa chọn để upload 1 image :
- Upload trên chỉ sử dụng cho Project đó : `Project`/`Compute`/`Images` :

<img src=http://i.prntscr.com/87fn6TZwR_OoGsAq7wI0xw.png>

- Upload có thể chia sẻ cho Project khác : `Admin`/`Compute`/`Images` :

<img src=http://i.prntscr.com/LC0Fu68rTD2aGyl62r-_GQ.png>

Giao diện quản lý các Images :

<img src=http://i.prntscr.com/WYpE4oDFTIWRiR1p75b5ug.png>

Ở giao diện này, người dùng có thể tạo, sửa , xóa , tìm kiếm các image có sẵn.

Các Images bao gồm các thông tin sau :

| Tên | Ý nghĩa |
|---|---|
| Owner | Chủ sở hữu Image |
| Name | Tên Image |
| Type | Loại Image |
| State| Trạng thái của Image |
| Visiblity | Khả năng hiển thị của Image |
| Protected | Image đang được protect hay không |
| Disk Format| Định dạng của Image |
| Size | Dung lượng của Image |
 - Type : có thể là Image từ Disk, từ Volume, hoặc từ 1 bản Snapshot.
 - Disk Format : ISO, OVA, PLOOP, QCOW2, Raw, VDI, VHD, VMDK, AKI, AMI, ARI hoặc Docker.

### Tìm kiếm Images :

<img src=http://i.prntscr.com/pLevObFvQP_RIFjrZYd2UQ.png>

| Tên | Ý nghĩa |
|----|----|
|Name | Tìm kiếm dựa theo tên Image|
|Status | Tìm kiếm dựa theo trạng thái của Image|
|Visiblity| Tìm kiếm dựa theo khả năng hiển thị của Image|
|Protected| Tìm kiếm dựa theo trạng thái Protected của Image|
|Format| Tìm kiếm dưa theo định dạng của Image|
|Min.Size| Tìm kiếm dựa theo mức dung lượng bé nhất của Image|
|Max.Size| Tìm kiến dựa theo mức dung lượng lớn nhất của Image|

Khi Click vào mỗi option, Openstack sẽ hiển thị thêm các lựa chọn ( đối với các option có tìm kiếm được cố định , hoặc điền vào nếu tìm kiếm  dựa theo mục đích của người dùng )

<img src=http://i.prntscr.com/XlG6zySOR2isE6WE97lvjQ.png>

### Upload Image

Tiến hành Click vào tùy chọn `Create Image `, một hộp thoại hiện ra :

<img src=http://i.prntscr.com/wU5128H7QoGaXO4Qt7CSag.png>

Các trường thông tin và ý nghĩa :

| Tên trường | Ý nghĩa |
|-----|-----|
|Image Name | Điền tên của Image |
|Image Description | Điền mô tả cho Image|
|Image Source | Chọn nguồn upload Image : `Image Location` hoặc `Image File`|
|Image Location hoặc Image File | Image location là Upload Image từ 1 URL nào đó. Image File là upload Image từ máy chủ nào đó. |
|Format | Lựa chọn định dạng của Image |
|Architecture | Cấu trúc của Image : i386 hoặc x86_64 |
|Minimum Disk | Dung lượng ổ đĩa cài tối thiểu cho Image |
|Minimum RAM | Dung lượng RAM tối thiểu cần cho Image |
|Image Sharing | Thiết lập chia sẻ Image :  Visibility và Protected |
| Visibility | Thiết lập quyền truy cập Image ở các Project : Public hoặc Private ( chia sẻ cho các project khác hoặc chỉ dc sử dụng ở Project đó) |
|Protected | Thiết lập User khác( ngoài Owner) có được quyền xóa  Image hay không |
| Image Metadata | Tùy chọn cho phép cập nhật Metadata của Image vào Glance |

Các trạng thái của Image khi upload:
- Queued : Định dạng Image đã dược lưu vào Registry.
- Saving : Image đang được upload vào Glance.
- Active : Image đã có sẵn trong Glace và sẵn sàng sử dụng.
- Deactive : Image đã có sẵn, nhưng chỉ admin mới được truy cập.
- Killed : Image upload lỗi, không sử dụng được.
- Deleted : Chỉ còn bản tóm lược của Image, image không sử dụng được.
- Pending_delete : Đang xóa Image và không phục hồi được.

### Xóa Image

Có thể xóa từng image hoặc xóa đồng loạt các image đã chọn :

<img src=http://i.prntscr.com/760acSnzTyC5rkQm4kPkww.png>

### Edit Imgae

Chỉnh sửa các thông số của Image :

- Chọn Image cần sửa, `Edit Image`. sau khi câp nhật, chọn `Update Image`

<img src=http://i.prntscr.com/7rMlUEucTnSFlm-Z2ZOqmg.png>

<a name=13></a>
## 1.3 Thao tác với Router

Router chỉ được tạo trên Tab Project : `Project`/`Network`/`Router`

<img src=http://i.prntscr.com/hPtH2a2CTliP_RDZhGdvAA.png>

Giao diện quản lý các Router sẽ như sau :

<img src=http://i.prntscr.com/rjY0U9sUSMSCL04kKh4aTA.png>

Thông tin các trường :

|Tên trường | Ý nghĩa |
|----|------|
|Project | Router được tạo ở Project nào |
|Name| Tên của Router|
|Status | Trạng thái hoạt động của Router|
|External Network| Provider Network nào được gán cho router để ra ngoài Internet|
| Admin State | Có thể xem như là trạng thái hoạt động, mặc định là true, nếu để failse thì router sẽ không hoạt động được|
|Actions| Các hành động thực hiện trên Router : Edit, Delete|

### Tạo 1 Router

Click vào tùy chọn : `Create Router`, hộp thoại tạo Router hiện ra, điền các thông tin về Router và ấn `Create Router` tiếp theo.

<img src=http://i.prntscr.com/Nyds7o-TRXSC4HZry80LHQ.png>

### Chỉnh sửa, cập nhật các Router

Để thiết lâp, chỉnh sửa cho Router nào thì Click vào tên Router đó :

<img src=http://i.prntscr.com/-AOgoL_eR2KEg-_-Jq6GKQ.png>

Mỗi Router sẽ có các thông tin sau :

- Overview : 1 :vùng hiển thị thông tin Router , 2 : hiển thị thông tin của External Network mà router gán vào :

<img src=http://i.prntscr.com/sDoY3VA7SKuZTT_GDlUSQg.png>

- Interfaces : Quản lý Network mà các Interface của Router đang gán :

<img src=http://i.prntscr.com/HNYKIgGxRpK7Rn2hv2s5xw.png>

Thông tin các Interface :

|Tên trường | Ý nghĩa |
|----|----|
|Name | Tên Interface|
|Fixed IPs| Địa chỉ Ip được gán cho Interface đó|
|Status| Trạng thái của Interface|
|Type| Loại Interface : Internal hoặc External|
|Admin Statate | Trạng thái Admin |
|Action | Hành động với Interface đó|

### Add Interface cho Router :

Click `Add Interface` điền các thông tin về  subnet,địa chỉ IP muốn gán, sau đó chọn `Submit`

<img src=http://i.prntscr.com/D40CVUktT0qjVbGQO80v5A.png>

### Xóa Interface

Có thể xóa nhiều Interface cùng 1 lúc bằng cách tích các Interface sau đó chọn `Delete Interface` hoặc xóa từng Interface bằng cách chọn `Delete Interface` ở mục `Action`.

<a name=14></a>
## 1.4 Thao tác với Network

Có 2 loại Network được sử dụng trong Openstack :
- Provoder Network : là network sử dụng dải IP chung với dải IP của máy chủ vật lý, thường được sử dụng là mạng external.
- Self-Service : Là network sử dụng dải IP khác với dải IP máy vật lý,chịu trách nhiệm kết nối nữa các VM với nhau. Còn gọi là Internal Network, dải mạng này không ra được Internet, trừ khi kết nối với router .

Để quản lý và hiển thị các thôn tin network chúng ta có thể truy cập theo 2 cách :
- `Project`/`Network`/`Networks` : hiển thị các Network có thể sử dụng được ở trong Project đó.
- `Admin`/`Network`/`Networks` : hiển thị các Network mà Admin quản lý.

Giao diện quản lý như sau :

<img src=http://i.prntscr.com/uaBwXgaIRO_HXN5Jr4BdcQ.png>

- Tìm kiếm Network :

 <img src=http://i.prntscr.com/pgP_sDHsSse9PRM89ydoxQ.png>

 Có thể tìm kiếm các Network theo tên Project, tên Network, shared ,External ,status , Admin State.

Các trường thông tin về Network như sau :

|Tên trường | Ý nghĩa |
|---------|---------|
|Project| Network ấy thuộc Project nào|
|Network Name| Tên Network|
|Subnet Associated| Tên các Subnet và dải địa chỉ Ip của các subnet|
|DHCP Agent |Số lượng Agent đang kết nối với Network|
|Share|Network đang chia sẻ dải mạng với Project khác hay không|
|External| Network có ra được Internet hay không|
|Status|Trạng thái của Network|
|Admin State| Trạng thái hoạt động kết nối|
|Actions|Các tùy chọn hành động với Network|


### Tạo Provider Network
Để tạo 1 dải mạng Provider : tiến hành chọn `Admin`/`Network`/`Networks` ,Sau đó chọn `Create Network` :

<img src=http://i.prntscr.com/XIwsrGIHS0Onwlhj5UnHGQ.png>

Hộp thoại Create Network xuất hiện :

<img src=http://i.prntscr.com/uJLHTssMRJyQGaJfBDpfzw.png>

Trong đó
- Provider network type hỗ trợ nhiều công nghệ : FLAT,VLAN,XVLAN,GRE,Geneve

 <img src=http://i.prntscr.com/O-IbNZlbSC_zs9c_xcd7Kw.png>

Tiếp theo ấn `Next` để thiết lập subnet :

<img src=http://i.prntscr.com/GJJn62GPQVGohD2abZNeag.png>

|Tên trường| Ý nghĩa |
|---|---|
|Subnet name|Tên của Subnet|
|Network Address| Địa chỉ mạng của Subnet|
|IP version|Công nghệ hỗ trợ IP của Subnet|
|Gateway| Địa chỉ IP của Subnet|
|Disable Gateway| Tắt chức năng IP Gateway subnet|

Tiếp tục ấn `Next` để thiết lập DHCP cho subnet :

<img src=http://i.prntscr.com/llp8SO6fRoO67eYVStXDPA.png>

|Tên trường | Ý nghĩa |
|---|---|
|Enable DHCP | Kích hoạt chức năng DHCP cho subnet |
|Allocation Pools | Cho phép cấp phát dải IP nào của subnet|
|DNS Name Server | Thiết lập DNS cho subnet|
|Host Router|Thông tin định tuyến cho subnet|

Chọn `Create` để  bắt đầu tạo 1 subnet provider.

### Tạo Self-Service Network

Để tạo 1 dải mạng Self-Service : tiến hành chọn `Project`/`Network`/`Networks` ,Sau đó chọn `Create Network` :

<img src=http://i.prntscr.com/nEz995uHSduBUwsoMJZ7Uw.png>

Hộp thoại Create Network xuất hiện :

<img src=http://i.prntscr.com/vQLcsiAcQ9_S1eynkrRCPA.png>

Điền và chọn các thông tin đã giải thích ở bảng trên, ấn `Next` để thiết lập Subnet :

<img src=http://i.prntscr.com/51l-1CSZQrOvD_ruBRf8-g.png>

Điền các thông tin và Click `Next` để thiết lập DHCP :

<img src=http://i.prntscr.com/dPPw9IZTScC689g2TqYkEg.png>

Tiếp tục điền các thông tin về DHCP và Click `Create` để tạo Selservice Network.

<a name=15></a>
## 1.5 Thao tác với Keypair
Key Pair giúp các máy chủ khác có thể ssh vào.

Để tạo và quản lý Keypair thì truy cập theo thứ tự như sau : `Project`/`Compute`/`Key Pairs` :

 <img src=http://i.prntscr.com/OSl35PphTCesY1NvSosWLA.png>

- Chọn 4 : Create Key Pair mới
- Chọn 5 : Import 1 Key Pair có sẵn.

### Tạo Key Pair

Nếu Create KeyPair mới chọn Create Key Pair :

<img src=http://i.prntscr.com/kDueb23sThqDOanV2dkMHQ.png>

Đặt tên cho keypair mới và chọn `Create Keypair`

 <img src=http://i.prntscr.com/fLsuvnRaQbW9Wt2g4XgfLg.png>

Hệ thống sẽ tạo private key , có thể lưu lại Private key này để Import cho máy chủ khác.

Chọn `Done` để  kết thúc quá trình tạo Keypair.

### Import keypair
### Delete keypair

Có thể xóa từng keypair hoặc tích vào các keypair muốn xóa và chọn `Delete Key Pair`.

 <img src=http://i.prntscr.com/DKYX266pT2uK1Jh7GCfrcA.png>

<a name=16></a>
## 1.6 Thao tác với Port

Việc tạo Port nhằm cố định địa chỉ IP hoặc 1 subnet cho một hoặc nhiều thiết bị mạng nào đó. Ví dụ như trong 1 network có 2 subnet thì việc xác định Port giúp quản trị có thể chủ động hơn trong việc chọn subnet mask.

Để thiết lập các Port cho 1 network nào đó, tiến hành chọn `Project`/`Network`/`Networks`/ chọn Network muốn tạo Port :

 <img src=http://i.prntscr.com/F_WSl1ZmSHOUcFz7L1ABJA.png>

Chuyển sang Tab Port :

 <img src=http://i.prntscr.com/DLzPZFRET0SxYxxDvjUKwg.png>

Có thể :
- Tạo Port mới : `Create Port`
- Xóa Port cũ : `Delete Port`
- Sửa Port : `Edit Port`

### Tạo Port mới

 <img src=http://i.prntscr.com/kCgzJLskTuKtNswB7yuEJA.png>

Các trường thông tin :

|Tên Trường | Ý nghĩa |
|----|----|
|Name| Điền tên cho Port|
|Enable Admin State | Cho phép port hoạt động |
|Device ID| Điền tên Device muốn gán Port vào|
|Device Owner| Điền tên của chủ sở hữu Device muốn gán Port|
| Specify IP address or Subnet | Thiết lập gán 1 fixed IP hoặc 1 subnet cho Port đó|
|Mac Address | Chỉ định địa chỉ MAC cho Port|
|Port Security | Bật chức năng chống Spoofing cho Port|


<a name=17></a>
## 1.7 Thao tác Floating IP

Floating Ip là thuật ngữ dùng để cấp phát 1 địa chỉ IP public nhằm mục đích asign cho 1 instance nào đó đang sử dụng IP private, giúp instance đó ra được internet.

Để Floating được IP cho 1 instance, đầu tiên phải allocate (Phân bổ) một địa chỉ IP public từ Pools(Kho lưu trữ các IP khả dụng), sau đó associate IP vừa đc allowcate đó cho 1 instance cụ thể.

### Allocate IP

Có 2 cách để allocate 1 địa chỉ IP từ Pools :
- `Project`/`Network`/`Floating IP` : cho phép allocate IP cho 1 Project hiện tại.Các IP ở mục này sẽ được cấp phát một cách ngẫu nhiên.

 <img src=http://i.prntscr.com/MBAuGzx_Q9CwyM7p3hOV5Q.png>

 Chọn nguồn Pools IP , sau đó chọn `Allocate IP` :

 <img src=http://i.prntscr.com/4nnIcIjtTmG1katQFRtm9Q.png>

- `Admin`/`Network`/`Floating IP` : cho phép allocate IP cho các Project khác nhau, và có thể chỉ định được IP muốn allocate, trường hợp Ip đó đã được sử dụng thì nó sẽ dùng IP tiếp theo, cứ thế đến khi nào có được IP chưa sử dụng thì IP đó sẽ được allocate.

  <img src=http://i.prntscr.com/0iFFrGttQF62dXcl_MmFZA.png>

  Allocate IP :

  <img src=http://i.prntscr.com/8O3ZJGmlSniUsZW0Rgxucg.png>

|Tùy chọn | Ý nghĩa |
|---|---|
|Pool| Nguồn cung cấp địa chỉ IP public|
|Project| Chọn Project muốn allocate IP|
|Floating IP Add| Địa chỉ IP muốn được allocate|

### Xóa Allocate IP

Có thể xóa từng Ip hoặc xóa nhiều IP cùng lúc :

<img src=http://i.prntscr.com/Ff2Di0gDTye0v73SbYoXxg.png>

### Associate IP cho Instance

Để associate IP cho instance cụ thể thì cần truy cập vào mục `Project`/`Network`/`Floating IP` :

Chọn địa chỉ IP muốn associate, tiếp theo chọn Associate:

<img src=http://i.prntscr.com/o-gKMANZTiK-qEO9lAyBrw.png>

Hộp thoại mới hiện ra :

 <img src=http://i.prntscr.com/8_oNvBggTqeGqfIzQtGDZg.png>

Chọn IP , chọn `Port`/`Instance` muốn Associate , sau đó click `Associate`

Cách khác : có thể  Associate Floating Ip ngay ở Instance :

  <img src=http://i.prntscr.com/RYRBGSCiQEOcwwegYYsXOw.png>

<a name=18></a>
## 1.8 Thao tác với Project

Để quản lý các Project : thêm,sửa ,xóa,... cần phải có quyền Admin.

<img src=http://i.prntscr.com/qfgnRyH8QhKJKHBPCyA85w.png>

Chi tiết thôn tin các Project như sau :

|Tên trường|Ý nghĩa|
|---|---|
|Name| Tên project|
|Description| Mô tả Project |
|Project ID | ID của Project|
|Domain Name| Project thuộc Domain nào|
|Enable| Trạng thái hoạt động của Domain|
|Actions|Các hoạt động sửa,quản lý thành viên,....|

### Tạo project

Để tạo Project tiến hành Click vào `Create Project `, hộp thoại tạo project mở ra :

<img src=http://i.prntscr.com/tfC94x-xSvKoeccZZBNYvQ.png>

Có 4 tab cần quản lý khi tạo Project :
- `Project Information` : Thông tin cơ bản của project
- `Project Members` : Quản lý các thành viên và role trên Project
- `Project Groups` : Quản lý nhóm thành viên và role trên Project
- `Quotas` : Quản lý giới hạn nguồn tài nguyên trên Project

`Project Information` :

|Tên trường | Ý nghĩa |
|---|---|
|Domain ID | ID của Domain nơi tạo Project |
|Domain name| Tên của Domain nơi tạo Project|
|Name| Tên Project|
|Description| Mô tả Project|
|Enable| Kích hoạt Project sau khi tạo hay không|

`Project Members` :

<img src=http://i.prntscr.com/dJU7LI7JRiWc4KoONn3uQQ.png>

- `+` : Thêm User vào Project
- `-` : Loại bỏ user khỏi Project
- `admin,user,member` : các role được gán cho mỗi user.

`Project Groups` :

 <img src=http://i.prntscr.com/tfvoPS2HQvKYTBhmUm56_Q.png>

 Thêm 1 nhóm người dùng vào project và phân quyền cho nhóm người dùng đó.

`Quotas` :

<img src=http://i.prntscr.com/RRHrT29ITm2HHPKECXSisA.png>

Tinh chỉnh, thiết lập giới hạn các tài nguyên được phép sử dụng trong Project : VCPUs, Instances,Key pair,Volume ,...

Click `Create Project ` để kết thúc quá trình tạo Project

### Sửa Project

Sau khi Project tạo ra, trong quá trình hoạt động hoặc nhầm lẫn lúc tạo, Admin hoàn toàn có thể tinh chỉnh lại Project bất kỳ.

<img src=http://i.prntscr.com/xYBho8HySB_-TIDkmeEtdw.png>

### Xóa Project

Có thể xóa 1 (`Delete Project` trong `Action`)hoặc nhiều project cùng lúc(Chọn các Project muốn xóa ,sau đó `Delete Project`).

<a name=19></a>
## 1.9 Thao tác với Group

Mục đích của Group là nhóm các thành viên có điểm tương đồng nào đó thành 1 nhóm để dễ dàng quản lý.

<img src=http://i.prntscr.com/BwIXX89iSS_9scNw1z0sLQ.png>

|Tên trường | Ý nghĩa |
|---|--|
|Name| Tên Group|
|Descriptions| Mô tả cho Group|
|Group ID| ID của Group|
|Actions| Các hoạt động như : quản lý thành viên,chỉnh sửa thông tin Group|

### Tạo Group mới

Chọn `Create Group` , hộp thoại Tạo Group mới xuất hiện

<img src=http://i.prntscr.com/S589BgV1SVmzYOuaKzRWEA.png>

 Điền các thông tin cho Group mới và chon `Create Group`.

### Quản lý Members trong Group

Tại Group muốn Quản lý, chọn `Manager Members`

<img src=http://i.prntscr.com/UtyDNmcRTeqE7V209fUfwA.png>

Cửa sổ mới mở ra, hiển thị danh sách các user có trong Group

Click vào `Add Users` sẽ hiện ra hộp thoại chứa các User trong Project, muốn thêm user nào thì tích vào user đó , sau đó chọn `Add User`

<img src=http://i.prntscr.com/XyVx2y96TFeWWYEjvh4gCw.png>



<a name=110></a>
## 1.10 Thao tác với User

Để quản lý các User, vào `Identity`/`Users`

<img src=http://i.prntscr.com/ZKI5ItFSQVqz0c1LPbFIvg.png>

Các trường thông tin :

|Tên Trường|Ý nghĩa|
|---|---|
|User Name| Tên đăng nhập của User|
|Description| Mô tả user|
|Email| Địa chỉ Email của User|
|User ID| ID của User|
|Enable| Trạng thái kích hoạt của User|
|Domain Name| Tên Domain quản lý User|
|Actions| Các hành động quản lý user : Thay đổi thông tin, thay đổi mật khẩu, disable, xóa user|

### Tạo User mới

Click `Create User` , hộp thoại tạo user xuất hiện

<img src=http://i.prntscr.com/75MbMukRRhi_ApySWkQ9Bw.png>

- Primary Project : Chọn Project chính cho user khi đăng nhập.
- Role : xét Role cho user tại Project vừa add.

### Thêm User vào Project

Tại tab `Identity`/`Projects`

<img src=http://i.prntscr.com/aIdvKTq4S3S0RjV1sqZ7og.png>

- Chọn project muốn thêm User
- Tại mục `Actions`, chọn `Manager Members`
- `+` : Thêm User vào Project
- `-` : Bỏ User ra khỏi Projet

Chọn `Save` Sau khi thiết lập xong.

<a name=111></a>
## 1.11 Thao tác với Security Group

Security Group giúp quản lý tất cả các kết nối giữa các Security group với nhau và với một dải mạng hay một IP bất kì nào đó. Việc quản lý này dựa trên các Rule được thiếp lập ở trong Security Group.

Để quản lý, tạo, sửa Security Group và các Rule của nó thì thực hiện như sau :

- Truy cập : `Project`/`Network`/`Security Group` :

<img src=http://i.prntscr.com/K4ualgDyRQK_zbGTExIMZQ.png>

Các thông tin hiển thị trong Security Group :

| Tên trường |Ý nghĩa|
|----|----|
|Name| Tên của Security Group|
|Security Group ID | ID của Security Group|
|Description| Mô tả về  Security Group|
|Actions | Các động như quản lý Rule, sửa, xóa Security Group|

### Tạo Security Group
Để tạo thêm mới 1 Security Group tiến hành như sau :

- Click vào `Create Securuty Group`, Hộp thoại tạo Security mới hiện ra :

<img src=http://i.prntscr.com/N0gPhXukSBGuY--9UUkxvQ.png>

Điền `Name` và `Description`  của Security Group sau đó chọn `Create Security Group` để kết thúc quá trình tạo mới.

### Quản lý Rule trong Security Group

Có thể thêm các rule mới hoặc xóa các rule không cần thiết : `Add Rule`, `Delete Rule`.

<img src=http://i.prntscr.com/_-R3R9dXRgix3CCylwe0wQ.png>

Thông tin các trường :

|Tên trường| Ý nghĩa |
|---|---|
|Direction| Hướng đi của dữ liệu : Ingress : đi vào, Egress : đi ra|
|Ether Type| Loại IP muốn quản lý : IPv4 và Ipv6|
|Ip Protocol | Các giao thức IP : TCP,UDP,ICMP,DNS,HTTP,HTTPS,IMAP,POP3,SNMP,SSH,LDAP,MS SQL,MYSQL,POP3,POP3s,RDP,SNMTPs.|
|Port Range | Rule này áp dụng trên Port nào, có thể là 1 hoặc nhiều Port |
|Remote IP Prefix| Rule này áp dụng cho địa chỉ hay dải địa chỉ IP nào|
|Remote Security Group| Rule này áp dụng cho nhóm Security nào|

Để thêm 1 Rule Click vào `Add Rule` , hộp thoại tạo rule xuất hiện :

<img src=http://i.prntscr.com/AW2MwEIrRSC4DlJ8ZJ_wMQ.png>

Điền các thông số như bảng trên, click `Add` để kết thúc quá trình tạo rule.

<a name=2></a>
# 2. Các hoạt động với VM

<a name=21></a>
## 2.1 Tạo VM

Để quản lý các VM tiến hành như sau : chọn `Project`/`Compute`/`Instances` :

<img src=http://i.prntscr.com/hNsYigO9T1qETCx5IUG_JQ.png>

Các thông tin hiển thị :

|Tên trường | Ý nghĩa |
|---|---|
|Instance Name | Tên Instance|
|Image Name| Tên Image mà Instance sử dụng|
|IP Address | Địa chỉ IP Fixed của Instance|
|Flavor| Tên Flavor mà Instance sử dụng|
|Key Pair| Tên Key Pair mà Instance sử dụng|
|Status | Trạng thái của Instance |
|Availablity Zone| Tên Zone quản lý Instance|
|Task| |
|Power State| Trạng trái hoạt động của Instance |
|Time Since created| Thời gian tính từ lúc tạo|
|Actions| Danh mục các hành động đối với Instance |

Để tạo mới 1 Instance click vào `Launch Instance` , Hộp thoại Create Instance xuất hiện :

<img src= http://i.prntscr.com/zYXTP0PtRbiZr6rQOmmGRQ.png>

|Tên trường | Ý nghĩa |
|---|---|
|Instance Name| Điền tên Instance|
|Availablity Zone| Zone quản lý Instance|
|Count | Số lượng Instance muốn tạo|

**Source** :

<img src=http://i.prntscr.com/V3EZWX-WSIeQ6o2oJILSPQ.png>

|Tên Trường| Ý nghĩa |
|---|--|
|Select Boot Source| Chọn Nguồn Boot instance : `Image`, `Volume`,`Volume Snapshot`,`Instance Snapshot`|
|Volume Size| Thiết lập kích cỡ Volume cho Instance|
|1 | Cho phép tạo Volume khi cài đặt Instance|
|2 | Không cho phép tạo volume khi cài đặt Instance |
|3 | Volume khi Instance bị xóa |
|4 | Volume không bị xóa khi Instance bị xóa|
|5 | Loại bỏ Image/Volume/Volume Snapshoot/Instance Snapshoot vừa thêm |
|6 |Thêm Image/Volume/Volume Snapshoot/Instance Snapshoot|

**Flavor** :

<img src=http://i.prntscr.com/E05MhMUASb_7sCEx6AXteA.png>

- 1 : Loại bỏ Flavor vừa thêm
- 2 : Đẩy Flavor lên để thiết lập cho Instance.

**Network** :

Tạo Network để giao tiếp Instance với các thiết bị mạng trên Cloud.



<img src=http://i.prntscr.com/XnzwsSvcRre_KV0poPwwvA.png>

Chọn hoặc bỏ chọn 1 Network.

**Network Port**

Có thể dùng thay thế cho `Network` hoặc có thể kết hợp cả 2.

<img src=http://i.prntscr.com/C66JuivWSVWZDXKH1dQDOA.png>

**Security Group**

Chọn Security group để quản lý kết nối với Instance

<img src=http://i.prntscr.com/lrlmXF3hTJ_CyeraFVD4yg.png>

**Key Pair**

Thiết lập keypair để các máy khác có thể remote qua màn hình console

Có thể :
- Create Key Pair : Tạo 1 Key Pair mới.
- Import Key Pair : Import Key pair có sẵn.
- 3 : hủy sử dụng Keypair vừa thêm.
- 4 : Sử dụng Key Pair muốn dùng.


<img src=http://i.prntscr.com/KAye5qdaRxG0Arco1xzKBw.png>


Click `Launch Instance` kết thúc quá trình tạo Instance.

<a name=22></a>
## 2.2 Attack/Detack Interface

Một Instance lúc tạo đã được gán 1 Network, trong trường hợp người dùng muốn thay thế hoặc muốn gán thêm hay loại bỏ 1 card mạng nào trên Instance thì sử dụng tính năng này.

### Attack Interface

Tại Instance muốn thêm Interface : `Actions`/`Attach Interface`

<img src=http://i.prntscr.com/1nHkXP8ESJG9etOpa5GLxA.png>

Chọn Network muốn Attack vào , sau đó chọn `Attach Interface`

<img src=http://i.prntscr.com/yKKuMO8IQUuJsBcWTgTDUA.png>

### Detack Interface

Tại Instance muốn thêm Interface : `Actions`/`Detach Interface`

<img src=http://i.prntscr.com/WhOrOsYNRECkGuQCsxNDKA.png>

<a name=23></a>
## 2.3 Snapshot Instance


Snapshot sẽ lưu trạng thái, dữ liệu của Instance tại thời điểm Snapshot, Instance sau khi Snapshot sẽ được lưu dưới dạng 1 image instance snapshot

Để Snapshot tiến hành như sau : tại Instance muốn Snapshot , chọn `Create Snapshot`

<img src=http://i.prntscr.com/oYKLTZ3UQSK85RymvaIuhw.png>

Hộp thoại tạo Create Snapshot tạo ra,Điền tên muốn đặt cho Snapshot, click `Create Snapshot` để tạo.

<img src=http://i.prntscr.com/D8drGGizRZGRQJ1ofwmF8A.png>


<a name=24></a>
## 2.4 Rebuild Instance

Rebuild Instance là thuật ngữ dùng thay đổi image của Instance mà sau khi thay đổi vẫn được cấu hình IP,volume,.. đã được cấp phát trước đó.

Để Rebuild 1 Instance thực hiện như sau : `Actions`/`Rebuild Instance` :

<img src=http://i.prntscr.com/GHuYH_vWQYSFIYLMPuRVXA.png>

Chọn image muốn cài lên vm , sau đó click `Rebuild Instacne `

<img src=http://i.prntscr.com/MlirOqTBRHmPmXCmupU1pw.png>

<a name=3></a>
# 3. Các hoạt động với Cinder

Để quản lý, sửa, tạo ,xóa các Volume truy cập theo đường dẫn sau : `Project`/`Volume` :

<img src=http://i.prntscr.com/yy0FWNYhQYOMckodYzw8pg.png>

Thông tin các trường :

|tên trường | Ý nghĩa |
|---|---|
|Name| Tên volume |
|Descriptions| Mô tả về Volume|
|Size| Kích thước Volume|
|Status| Trạng thái sử dụng của Volume|
|Type| Loại Volume được sử dụng|
|Attached To| Volume đang được gán cho thiết bị nào|
|Availability Zone| Zone quản lý Volume|
|Bootable| Volume này có phải là Boot Volume ha không|
|Encrypted| Volume này đươc mã hóa hay không|
|Actions| Các hoạt động có thể áp đặt lên Volume|

<a name=31></a>
## 3.1 Tạo Volume

Để tạo một volume, tiến hành Click vào `Create Volume `, hộp thoại Create Volume hiện ra :

<img src=http://i.prntscr.com/byDtdQuJSVuYqZO5DNSCxA.png>

- `Volume Source` : Nguồn tạo Volume, có thể là Volume trống, hoặc chứa image,Snapshot .

Điền các thông tin tạo Volume sau đó click vào `Click Volume` để tạo volume mới.

<a name=32></a>
## 3.2 Sizing Volume

Tính năng này cho phép mở rộng kích thước của Volume. Volume muốn resize phải trong trạng thái Available và không được gán cho Instance nào.

Tại volume muốn resize :  Actions

<img src=http://i.prntscr.com/2SDnDqSWSxqVPnKNLs_0zw.png>

Hộp thoại Extend Volume xuất hiện, điền kích cỡ muốn thay đổi (Lớn hơn kích cỡ cũ), sau đó chọn `Extend Volume`.

<img src=http://i.prntscr.com/-3neF528S32Hs62BUBklLg.png>

<a name=33></a>
## Snapshot Volume

Tính năng Snapshot Volume cho phép sao lưu lại các trạng thái của Volume tại thời điểm Snapshot. Chức năng này có thể thực hiện kể cả khi Volume đang được attack vào thiết bị khác.

Các Volume có bootable có thể được dùng để Launch Instance mới.

Để Snapshot Volume tiến hành như sau . Tại Volume cần Snapshot : `Actions`/`Create Snapshot`

<img src=http://i.prntscr.com/5HWz0a2rSY2t0wLRXbPtPw.png>

Hộp thoại Snapshot hiện ra. Điền các thông tin cho bản Snapshot, sau đó `Create Volume Snapshot` :

<img src=http://i.prntscr.com/QRjK8dwwSJOUzgFErXVU9Q.png>

<a name=34</a>
## Volume Type

<a name=4></a>
# 4. Monitor

<a name=41></a>
## 4.1 Overview

Phần này cho cách nhìn tổng quan về tài nguyên trong các Project :

<img src=http://i.prntscr.com/SlDnnW2BT-uQLVpH8Fjxeg.png>

List Summary : hiển thị lượng nguồn tài nguyên đã được sử dụng trên tổng các nguồn tài nguyên có thể sử dụng trên Project :
- Instance : số lượng Instance đang có sẵn : 3 trên tổng số Instance giới hạn của Project : 10.
- VCPUs : số lượng virtual CPU đang được sử dụng.
- RAM : số lượng RAM đang được sử dụng .
- Floating ÍP : Số lượng IP Floadting đang được Allocate.
- Security Groups : số lượng Secrurity Group đang có trong Project.
- Volumes : Số lượng Volume hiện có trong Project.
- Volume Storage : Tổng dung lượng volume đang được sử dụng ở Project.

**Usage Summary**

Hiển thị và tải xuống báo cáo tổng quan về lượng tài nguyên được sử dụng trong khoảng thời gian nhất định, giúp cho quản trị viên nắm được việc sử dụng các tài nguyên trong quá khứ.


<img src=http://i.prntscr.com/PLI6G5UcQcmjwllOi3fU9g.png>
- 1 : Ngày bắt đầu khảo sát.
- 2 : Ngày kết thúc khảo sát.
- 3 : số lượng tài nguyên sử dụng tính từ thời điểm bắt đầu tới thời điểm kết thúc.
- 4 : Download bản báo cáo tài nguyên dưới dạng excel.
- 5 : Download bản báo cáo tài nguyên dưới dạng Juju Enviroment file.

**Usage**

Hiển thị các Instance cùng các thông tin sử dụng tài nguyên chi tiết của mỗi Instace.

<img src=http://i.prntscr.com/LgU5_IM3R4G8DgCqpxJO6Q.png>

- Instance Name : tên Instance
- VCPUs : số lượng CPU cấp trên Instance đó.
- Disk : dung lượng ổ đĩa trên Instance đó.
- RAM : dung lượng RAM trên Instance.
- Time since created : Thời gian từ lúc cấp phát đến thời điêm hiện tại.

<a name=42></a>

## 4.2 Tùy chỉnh Quota (Giới hạn nguồn tài nguyên)

Để giới hạn nguồn tài nguyên được sử dụng trong mỗi Project : RAM,vCPU,Instance ,Disk,.. tiến hành như sau : `Identity`/`Project`/`Actions`/`Modify Qoutas`

<img src=http://i.prntscr.com/9Jqi5GkfQOOrJFDPaHz2BQ.png>

Hộp thoại Edit Group hiển thị

<img src=http://i.prntscr.com/AMykcc9pTJ_GhheB8yj8lA.png>

Sau khi chỉnh sửa các thông số giới hạn nguồn tài nguyên chọn `Save` để lưu lại.

<a name=43></a>
## 4.3 Hypervisor

Quản lý, theo dõi các hypervisor, các nguồn tài nguyên đang được cấp phát và sử dụng các tài nguyên trên Hypervosor.

Để quản lý Hypervisor : `Admin`/`Hypervisor` :

<img src=http://i.prntscr.com/jJ-YceA3ShexAcLXrHk33g.png>

- Hypervisor Summary : Hiển thị tổng quan các nguồn tài nguyên đang được sử dụng trên hypervisor .

<img arc=http://i.prntscr.com/wk-V0BuFTzqvxoGjpe8qwg.png>

Thông tin các trường :

|Tên trường| Ý nghĩa|
|---|---|
|Hostname| Tên máy chủ quản lý Hypervisor|
|QEMU| Hypervisor đang được sử dụng|
|VCPUs used| Số lượng vCPU đã được sử dụng|
|VCPU total| Tổng số lượng vCPU |
|RAM used| Dung lượng RAM đã được sử dụng|
|RAM total| Tổng dung lượn RAM|
|Local Storage used| Dung lượng ổ cứng đã sử dụng|
|Local Storage total| Tổng dung lượng ổ cứng|
|Instacnes| Số lượng Instance đang sử dụng trên hypervisor|

Khi click vào mỗi `Hostname` sẽ hiển thị các Instance và id của nó có trong Hostname đó :

<img src=http://i.prntscr.com/FBAA5LFrSwCBLkbCmhWnBw.png>

Click vào mỗi Instance sẽ hiển thị các thông tin, log, console , Action log... của các Instance :

<img src=http://i.prntscr.com/FWF0IWJvSXaPWQBcg0ONig.png>

Phần này giúp quản lý, điều khiển các Instance.

**Compute Host**

Hiển thị các Host Compute  trong hệ thống Openstack

<img src=http://i.prntscr.com/6qGFYFI4TnCbHRMXmJIhVQ.png>

|Tên trường | Ý nghĩa |
|---|---|
|Host | Tên Host chứa Node Compute |
| Availability zone | Zone node Compute |
|Status| Trạng thái Node Compute|
|State| |
|Time since update| Thời gian kể từ lúc update mới nhất|
|Actions| Các hoạt động với node Compute|
