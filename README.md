# Chương 4: QUẢN LÝ TÀI NGUYÊN VÀ BẢO MẬT

## 1. Thiết lập tài khoản người dùng, tạo nhóm, những tập lệnh quản trị nhóm	

Trong hệ điều hành Ubuntu, quản lý tài khoản người dùng và tạo nhóm là một phần quan trọng của việc quản lý hệ thống. Điều này cho phép bạn tạo, quản lý và kiểm soát quyền truy cập của người dùng vào các tài nguyên trên máy chủ hoặc máy tính cá nhân. Dưới đây, chúng ta sẽ tìm hiểu về cách thiết lập tài khoản người dùng, tạo nhóm và sử dụng một số tập lệnh quản trị nhóm trong Ubuntu.

Trong quá trình cài đặt một hệ thống Linux, một số tài khoản người dùng đặc biệt sẽ tự động được tạo ra. Các tài khoản người dùng này được sử dụng với một số chức năng đặc biệt trên hệ thống. 

Có 3 tài khoản người dùng đặc biệt : root, nobody và bin. 

#### 1.1 Tài khoản root 

Tài khoản root còn được gọi là tài khoản siêu người dùng là tài khoản có quyền cao nhất trên hệ thống Linux. Người dùng sử dụng tài khoản root để thực hiện một số công việc quản trị hệ thống bao gồm : thêm các tài khoản người dùng mới, thay đổi mật khẩu của người dùng, xem các file log của hệ thống, cài đặt phần mềm, gỡ bỏ phần mềm, thay đổi quyền của file trên hệ thống … 

Khi sử dụng tài khoản root, người dùng phải rất cẩn thận vì mọi thao sẽ ảnh hưởng trực tiếp đến hệ thống. Tuy nhiên trong quá trình người dùng sử dụng tài khoản root để thực hiện một số công việc quản trị, hệ thống luôn có cảnh báo các thao tác mà người dùng đang thực hiện để tránh trường hợp người dùng làm sai ảnh hưởng đến hệ thống.

Khi cài đặt Ubuntu. Bạn chính là người cài đặt, lúc đó bạn sẽ tạo 1 user và password để truy cập hệ thống. Và user này thuộc nhóm Admin. Quyền lực của nhóm này tuy mạnh nhưng không liên tục, nói cách khác thì quyền mặc định của bạn sử dụng không phải là quyền lớn nhất đối với hệ thống.

Thay đổi password cho root 
- Lưu ý: Khi thực hiện lệnh với đặc quyền của root, cần thêm sudo trước lệnh `sudo passwd root`

  ![image](https://github.com/HaiiND/t/assets/120678965/a7ff3e3a-0944-4e51-ac7d-260b08b0019d)

Sau bước này bạn nhập password của bạn vào và sẽ được hỏi :
- Enter new UNIX password: Nhập password mới cho root 
- Retype new UNIX password: Nhập lại password lần nữa

Thông báo sau cùng : passwd: password updated successfully là thành công

Để chuyển sang tài khoản của root, dùng lệnh: `su`

Sau đó nhập password vừa tạo cho Root, và sẽ thành thế này:
root@xxx:/home/username#

Mặc định, mật khẩu của tài khoản root bị khóa trong Ubuntu. Điều này có nghĩa là bạn không thể đăng nhập trực tiếp với tài khoản root hoặc sử dụng lệnh `su` để trở thành người dùng root. Nhưng bạn vẫn có thể chạy các chương trình với đặc quyền của root với sudo, nó cho phép người dùng chạy chương trình nào đó với quyền root mà không phải biết mật khẩu của root.


Điều này có nghĩa là trong thiết bị cuối (terminal) bạn nên sử dụng sudo cho những lệnh cần đặc quyền của root; đơn giản chỉ việc thêm “sudo” vào đầu tất cả các lệnh bạn sẽ chạy với quyền root. Nên nhớ rằng, khi ” sudo” yêu cầu nhập mật khẩu, nó cần mật khẩu người dùng chứ không phải mật khẩu của tài khoản root.

Mặc định không cho đăng nhập trực tiếp với tài khoản root có những lợi ích sau:
- Trình cài đặt sẽ phải hỏi một vài câu hỏi.
- Người dùng không cần phải nhớ mật khẩu root, cái mà họ rất hay quên.
- Tránh xa quyền “Tôi có thể làm mọi thứ” khi đăng nhập, bạn sẽ được nhắc khi làm bất kỳ điều gì thay đổi đến hệ thống.
- Sudo thêm một lịch sử các lệnh đã chạy trong /var/log/auth.log. Nếu bạn gặp vấn để, bạn luôn luôn có thể quay lại và xem những lệnh nào đã được thực hiện. Nó cũng tốt để quản lý, kiểm tra.
- Mật khẩu tài khoản root bị khóa làm máy tính bạn an toàn hơn rất nhiều. Mọi cracker sẽ thử tấn công vào tài khoản root trước tiên, mật khẩu root bị khóa đồng nghĩa với việc loại bỏ được 1 lần nguy hiểm.

Chú ý:
- Để sử dụng lệnh với quyền root, thêm sudo vào đầu mỗi lệnh.
- Mật khẩu sẽ được lưu lại mặc định là 15 phút. Sau khoảng thời gian này, bạn cần nhập lại mật khẩu khi sử dụng sudo
- Mật khẩu sẽ không hiện lên màn hình khi bạn đánh, không hiện một hàng dấu '*'. Nó bắt đầu được nhập vào với mỗi lần gõ phím.
- sudo !! sẽ lặp lại lệnh cuối cùng nhưng với quyền root, nghĩa là thêm vào sudo ở đầu lệnh đó.
- Bạn không nên sử dụng sudo cho những chương trình có giao diện đồ họa, bạn nên sử dụng gksudo, ví dụ: ALT + F2 gksudo gedit

Đăng nhập với quyền root:
- Bạn có thể sử dụng sudo hoặc gksudo để thực thi với đặc quyền của root, nhưng nếu bạn vẫn muốn đăng nhập với người dùng root thì có thể dùng lệnh:
 Mã: sudo –i 
Có 1 chú ý nhỏ về sự khác nhau giữa sudo và gksudo: Khi sử dụng câu lệnh sudo, thì chúng ta sẽ thực thi một câu lệnh với quyền root nhưng với các thiết đặt (configuration) là của user đang sử dụng. Trong khi đó gksudo thì ngược lại. gksudo sẽ thực thi một câu lệnh với quyền root và với các thiết đặt cũng của root luôn. Chính vì thế, khi dùng sudo cho các chương trình có giao diện đồ họa nhiều lúc có thể dẫn tới lỗi.

#### 1.2 Tài khoản nobody 

Tài khoản người dùng nobody được sử dụng để chạy các dịch vụ trên hệ thống. Tài khoản này không có thư mục home hoặc môi trường làm việc shell. Nếu tài khoản này bị lỗi, các dịch vụ đang chạy sử dụng tài khoản này sẽ bị ảnh hưởng nhưng hệ thống vẫn được bảo mật. 

#### 1.3 Tài khoản bin 

Tài khoản bin được sử dụng trên hệ thống với thư mục home là /bin. Tài khoản này được sử dụng để bảo mật các file nhị phân cơ bản trên hệ thống. Tài khoản bin không có môi trường làm việc shell. Tài khoản này được tạo mặc định trong quá trình cài đặt hệ thống.

#### 1.4 Quản lý tài khoản người dùng

Trong Ubuntu, tài khoản người dùng là các thực thể được tạo ra để cho phép người dùng truy cập và sử dụng hệ thống. Dưới đây là một số tập lệnh quan trọng để quản lý tài khoản người dùng:

- sudo adduser <username>: Sử dụng lệnh này để tạo một tài khoản người dùng mới với tên người dùng <username>.
- sudo deluser <username>: Sử dụng để xóa một tài khoản người dùng. Hãy cẩn thận khi sử dụng lệnh này vì nó có thể xóa tài khoản và dữ liệu của người dùng mà không thể khôi phục.

Thay đổi mật khẩu người dùng: Sử dụng lệnh sudo passwd <username> để đặt lại mật khẩu cho một người dùng cụ thể.
Xem các user trên hệ thống sử dụng lệnh getent passwd

  ![image](https://github.com/HaiiND/t/assets/120678965/c3964ecb-bf09-48b5-a783-ae82ad2fc2dc)

Khóa và mở khóa tài khoản: Dùng lệnh sudo passwd -l <username> để khóa một tài khoản người dùng. Để mở khóa, bạn sử dụng lệnh sudo passwd -u <username>.

  ![image](https://github.com/HaiiND/t/assets/120678965/29b41c33-fe9a-428d-bbbe-c2ba002a58da)

- hdh1: Đây là tên người dùng (username) của tài khoản người dùng. Khi người dùng đăng nhập vào hệ thống, họ sẽ sử dụng tên người dùng này.
- x: Phần này thường được sử dụng để lưu trữ mật khẩu được băm (hashed password). Trong trường hợp này, "x" chỉ ra rằng mật khẩu đã được lưu trữ trong tệp /etc/shadow và không thể đọc trực tiếp từ tệp /etc/passwd. Thông tin mật khẩu được lưu trữ an toàn hơn trong /etc/shadow.
- 1001: Đây là User ID (UID) của tài khoản người dùng. UID là một số duy nhất dùng để xác định tài khoản người dùng trong hệ thống. Mỗi tài khoản người dùng có một UID riêng. Trong trường hợp này, UID là 1001.
- 1001: Đây là Group ID (GID) của tài khoản người dùng. GID xác định tài khoản thuộc về nhóm nào. Trong trường hợp này, GID cũng là 1001, có thể người dùng này thuộc vào một nhóm có cùng GID.
- ,,,: Những phần này thường liên quan đến thông tin về người dùng như tên đầy đủ, số điện thoại, địa chỉ, v.v. Trong trường hợp này, thông tin này đã được bỏ trống, vì vậy bạn thấy dấu phẩy liền kề.
- /home/hdh1: Đây là đường dẫn đến thư mục chủ (home directory) của tài khoản người dùng. Đây là nơi người dùng lưu trữ các tệp và thư mục cá nhân của họ.
- /bin/bash: Đây là đường dẫn đến shell mặc định mà tài khoản người dùng sẽ sử dụng khi đăng nhập vào hệ thống. Trong trường hợp này, tài khoản người dùng sẽ sử dụng shell Bash (/bin/bash) khi đăng nhập.


Một số UID đặc biệt: 
- UID = 0: được gán cho tài khoản Root. 
- UID = 65534: được gán cho tài khoản Nobody. 
- UID = 1 – 99: được gán riêng cho các tài khoản dịch vụ. 

#### 1.5 Tạo nhóm:

Trong Ubuntu, bạn có thể tạo các nhóm để quản lý quyền truy cập và chia sẻ tài nguyên giữa các người dùng. Dưới đây là các bước để tạo một nhóm:

- sudo groupadd <groupname>: Lệnh này tạo một nhóm mới với tên <groupname>.

  ![image](https://github.com/HaiiND/t/assets/120678965/cf89fec5-cc3c-46dd-a40c-3a2be40fb5df)

- sudo usermod -aG <groupname> <username>: Sử dụng để thêm một tài khoản người dùng vào một nhóm cụ thể.

Quyền sudo: Một phần quan trọng trong việc quản lý tài khoản người dùng là xác định ai có quyền thực hiện các tác vụ cấp cao như cài đặt phần mềm hay quản lý hệ thống. Người dùng được thêm vào nhóm sudoers có thể sử dụng lệnh sudo để thực hiện các tác vụ có quyền.

Quyền truy cập vào tệp và thư mục: Sử dụng lệnh chmod để thay đổi quyền truy cập của tệp và thư mục. Bạn có thể sử dụng lệnh chown để thay đổi chủ sở hữu của tệp và thư mục.

#### 1.6 Tập lệnh quản trị nhóm:

Khi bạn đã tạo các nhóm, có một số tập lệnh quản trị nhóm quan trọng:

- groups <username>: Hiển thị danh sách các nhóm mà một tài khoản người dùng cụ thể thuộc vào.
- sudo deluser <username> <groupname>: Sử dụng để loại bỏ một tài khoản người dùng khỏi một nhóm.
- sudo gpasswd -a <username> <groupname>: Để thêm một tài khoản người dùng vào một nhóm.
- Phân quyền dựa trên nhóm: Bạn có thể cấp quyền truy cập cho một tệp hoặc thư mục dựa trên các nhóm sử dụng chown và chmod.
- Xem danh sách nhóm: Sử dụng lệnh cat /etc/group để xem danh sách tất cả các nhóm trên hệ thống.
- Xóa nhóm: Để xóa một nhóm, bạn có thể sử dụng lệnh sudo groupdel <groupname>.

Quản lý tài khoản người dùng và nhóm là một phần quan trọng của việc bảo mật và quản lý hệ thống Ubuntu. Nó cho phép bạn kiểm soát quyền truy cập vào tài nguyên và dữ liệu, đồng thời cũng giúp bạn tổ chức và quản lý người dùng dễ dàng hơn. Hãy luôn thực hiện các thao tác quản lý này cẩn thận và có lập kế hoạch trước để đảm bảo tính an toàn và hiệu quả của hệ thống.


## 2. QUẢN LÝ TÀI NGUYÊN TRONG UBUNTU

Ubuntu là hệ điều hảnh mở dựa trên Linux. Ubuntu tạo ra môi trường nhiều người dùng chung tài nguyên. Chính vì vậy việc bảo mật các tài nguyên này rất quan trọng. Người quản trị cần phải thiết lập quyền hạn cho tập tin, thư mục sao cho không bị thay đổi nội dung, không bị xóa. Để nắm rõ vấn đề này, bạn cần tìm hiểu quyền hạn của người dùng trên FileSystem. Đây cũng là một trong số những ly do người sử dụng đánh giá rất cao khả năng bảo mật, an toàn. Ngoài ra việc phân quyền tốt sẽ tránh việc hệ thống file system của Ubuntu bị phá hỏng nhờ đó hệ thống vận hành một cách ổn định hơn.

#### 2.1 Quyền truy cập trên file system 

Trong Linux mọi đối tượng đều có dạng là tập tin. Tất cả tập tin đều có  người sở hữu và quyền truy cập. 

-Linux cho phép người dùng xác định các quyền đọc (read), ghi (write) và thự thi 

(execute) cho từng đối tượng. Có ba loại đối tượng : 
 + Người sở hữu (owner) : 3 ký tự đầu tiên (rw-) 
 + Nhóm sở hữu (group) : 3 ký tự tiếp theo (r--) 
 + Người khác (others) : 3 ký tự cuối cùng (r--) 
 
- Quyền đọc : cho phép bạn đọc nội dung của tập tin. Đối với thư mực, quyền đọc cho phép bạn di chuyển vào thư mục bằng lệnh cd và xem nội dung của thư mục. 
- Quyền ghi : cho phép bạn thay đổi nội dung hay xóa tập tin. Đối với thư mục, quyền ghi cho phép bạn tạo ra, xóa hay thay đổi tên các tập tin, thư mục con trong thư mục cha, nhưng không phụ thuộc vào quyền cụ thể của tập tin trong thư mục. Như vậy, quyền ghi của thư 
mục sẽ vô hiệu hóa các quyền truy cập của tập tin trong thư mục. 
- Quyền thực thi : cho phép bạn gọi chương trình lên bộ nhớ cách cách nhập tên tập tin từ bàn phím hay bằng chuột. Đối với thư mục, bạn chỉ có thể chuyển vào (cd) thư mục nếu bạn có quyền thực thi với thư mục. 

Owner Group Others 
read write execute read write execute read write execute 
Theo cách tính số nhị phân, ta có thể xác định số quyền hạn của một đối 
tượng bằng cách tính tổng giá trị các quyền. 
-Theo cách tính số nhị phân, ta có thể xác định số quyền hạn của một đối 
tượng bằng cách tính tổng giá trị các quyền. 
Quyền Giá trị hệ 2 Giá trị hệ 10 
Read 100 4 
Write 010 2 
Excute 001 1 
None 000 0
  ![image](https://github.com/HaiiND/t/assets/120678965/020073ee-98d0-4396-8e76-afe86395f4b1)

#### 2.2. Quản lý tiến trình:

Tiến trình là các chương trình hoặc nhiệm vụ đang chạy trên hệ thống. Dưới đây là một số tập lệnh quản lý tiến trình quan trọng:

  ![image](https://github.com/HaiiND/t/assets/120678965/fa6c8711-dd42-4d36-b459-86a097047c1e)

- ps: Sử dụng để liệt kê tất cả các tiến trình đang chạy trên hệ thống.

- top hoặc htop: Hiển thị danh sách tiến trình đang chạy theo thời gian thực, bao gồm thông tin về sử dụng CPU và bộ nhớ.

- kill: Sử dụng để dừng tiến trình. Cú pháp cơ bản là kill <PID>, trong đó <PID> là số xác định tiến trình.

#### 2.3. Quản lý bộ nhớ:

Bộ nhớ là một phần quan trọng của hệ thống và việc quản lý nó đảm bảo rằng hệ thống hoạt động một cách hiệu quả. Dưới đây là một số tập lệnh liên quan đến quản lý bộ nhớ:

  ![image](https://github.com/HaiiND/t/assets/120678965/7a4218bb-94bf-4460-b1d4-022c6467b066)

- free: Hiển thị thông tin về bộ nhớ hệ thống, bao gồm bộ nhớ đã sử dụng và còn trống.

- top hoặc htop: Bên cạnh việc quản lý tiến trình, chúng cũng hiển thị thông tin về việc sử dụng bộ nhớ, giúp bạn xác định các tiến trình tiêu tốn nhiều bộ nhớ.

- vmstat: Hiển thị thông tin về việc sử dụng bộ nhớ ở cấp hệ thống.

#### 2.4. Quản lý thư mục:

Quản lý thư mục là việc sắp xếp, tạo ra, di chuyển và xóa thư mục và tệp trong hệ thống tệp của bạn. Dưới đây là một số tập lệnh quản lý thư mục quan trọng:

  ![image](https://github.com/HaiiND/t/assets/120678965/46f3cc24-63fc-4d20-992a-b40e5c000a8f)

- ls: Dùng để liệt kê các tệp và thư mục trong thư mục hiện tại.

- mkdir: Sử dụng để tạo mới một thư mục. Cú pháp là mkdir <tên_thư_mục>.

- cd: Sử dụng để di chuyển giữa các thư mục. Cú pháp là cd <đường_dẫn>.

- rm: Dùng để xóa tệp hoặc thư mục. Cú pháp là rm <tên_tệp_đã_xóa> hoặc rm -r <tên_thư_mục_đã_xóa> để xóa thư mục và nội dung bên trong.

#### 2.5. Quản lý vào/ra:

Trong Linux, mọi thứ được xem là một tệp, bao gồm cả các thiết bị và cổng giao tiếp. Dưới đây là một số tập lệnh liên quan đến quản lý vào/ra:
  
- ls /dev: Liệt kê các thiết bị có sẵn trong hệ thống.

- dmesg: Hiển thị thông tin hệ thống và lịch sử lỗi của hệ thống.

- lsof: Liệt kê các tệp và thư mục đang được mở bởi các tiến trình.

- strace: Sử dụng để theo dõi các cuộc gọi hệ thống và thao tác vào/ra của một tiến trình cụ thể.

Quản lý tiến trình, bộ nhớ, thư mục, và vào/ra là một phần quan trọng của việc quản lý hệ thống Ubuntu và các hệ thống Linux khác. Nắm vững các tập lệnh này giúp bạn kiểm soát hiệu suất hệ thống, tìm hiểu và khắc phục sự cố, cũng như quản lý tệp và thư mục một cách hiệu quả. Hãy thực hành và nghiên cứu để trở thành một quản trị viên hệ thống thành thạo.


## 3.Gói cài đặt (package management)

Gói cài đặt là cách tiện lợi để cài đặt, cập nhật và quản lý phần mềm trên hệ thống. Ubuntu sử dụng hệ thống quản lý gói cài đặt dpkg cùng với apt hoặc apt-get để tạo một môi trường quản lý gói mạnh mẽ và dễ sử dụng. Trong bài viết này, chúng ta sẽ tìm hiểu về gói cài đặt dpkg và cách sử dụng nó trong Ubuntu.

Gói cài đặt dpkg:

- dpkg là hệ thống quản lý gói cơ bản trong Ubuntu. Nó cho phép bạn cài đặt, cập nhật, xóa và quản lý các gói phần mềm.

Các tập lệnh quản lý gói cài đặt dpkg quan trọng:

- Cài đặt gói từ tệp .deb:
  - Sử dụng lệnh dpkg -i <tên_gói.deb> để cài đặt một gói từ một tệp .deb. Ví dụ: dpkg -i package.deb.
- Cập nhật gói cài đặt:
  - Để cập nhật một gói đã được cài đặt, sử dụng lệnh dpkg -i --force-confnew <tên_gói.deb>. Điều này đảm bảo rằng các tệp cấu hình sẽ được cập nhật mà không ghi đè lên các tùy chọn cấu hình hiện có.
Xem trạng thái gói cài đặt:
  - Sử dụng lệnh dpkg -l để liệt kê tất cả các gói đã cài đặt và trạng thái của chúng.
- Xóa gói cài đặt:
  - Sử dụng lệnh dpkg -r <tên_gói> để xóa một gói đã cài đặt nhưng giữ lại các tệp cấu hình. Để xóa một gói cùng với tệp cấu hình, sử dụng lệnh dpkg -P <tên_gói>.
- Kiểm tra phụ thuộc gói:
  - Để kiểm tra phụ thuộc của một gói, sử dụng lệnh dpkg -I <tên_gói.deb>. Nó sẽ hiển thị thông tin chi tiết về gói và các phụ thuộc của nó.

Lợi ích của dpkg trong Ubuntu:
- dpkg là một công cụ quản lý gói mạnh mẽ và linh hoạt, cho phép bạn thực hiện nhiều tác vụ quản lý gói cài đặt mà không cần kết nối internet.
- dpkg là một phần của cơ sở hệ thống quản lý gói Debian, điều này có nghĩa là các gói cài đặt .deb có thể được sử dụng trên nhiều hệ thống dựa trên Debian như Ubuntu và Debian chính thống.
- Dựa vào dpkg, Ubuntu sử dụng các công cụ quản lý gói mở rộng như apt và apt-get, giúp quản lý gói cài đặt và giải quyết các phụ thuộc một cách dễ dàng hơn.

Kết luận, dpkg là một công cụ quản lý gói cài đặt quan trọng trong Ubuntu, cho phép bạn cài đặt, cập nhật và quản lý phần mềm trên hệ thống một cách hiệu quả. Sử dụng dpkg cùng với các công cụ quản lý gói mở rộng giúp tạo ra một môi trường quản lý gói đáng tin cậy trên hệ thống của bạn.

