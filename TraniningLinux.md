# SSL

## 	SSL là gì ?

​	SSL là viết tắt của từ Secure Sockets Layer. SSL là tiêu chuẩn của công nghệ bảo mật, truyền thông mã hoá giữa máy chủ Web server và trình duyệt. Tiêu chuẩn này hoạt động và đảm bảo rằng các dữ liệu truyền tải giữa máy chủ và trình duyệt của người dùng đều riêng tư và toàn vẹn. SSL hiện tại cũng là tiêu chuẩn bảo mật cho hàng triệu website trên toàn thế giới, nó bảo vệ dữ liệu truyền đi trên môi trường internet được an toàn. Tuy nhiên SSL đã được thay thế thành TLS nhưng dùng từ "SSL" gọi chung cho cả SSL và TLS

## 	Có bao nhiêu cách chứng thực SSL ?

​	Trong giao thức SSL/TLS, việc chứng thực (hoặc xác thực) là quá trình xác minh danh tính của các bên liên quan trong một kết nối bảo mật. Có một số cách chứng thực khác nhau, tùy thuộc vào cấu hình và yêu cầu của hệ thống.

​	Domain Validated SSL (DV SSL): Đây là loại chứng chỉ SSL cơ bản nhất và chứng thực dựa vào tên miền, nghĩa là tổ chức chứng thực (CA) sẽ kiểm tra xem mình có phải là người sở hữu tên miền đó hay không bằng cách chứng thực qua DNS hoặc gửi mã vào email của người đăng ký. Vì chỉ xác minh quyền sở hữu tên miền nên độ tin cậy thấp.

​	Organization Validation (OV SSL): Chứng chỉ này không chỉ xác minh quyền sở hữu tên miền mà còn xác thực danh tính của tổ chức.CA sẽ kiểm tra các tài liệu và thông tin pháp lý của tổ chức, có độ tin cậy cao.

​	Extended Validation SSL (EV): Chứng chỉ này cung cấp mức độ xác thực cao nhất, với quy trình xác thực nghiêm ngặt hơn. CA thực hiện kiểm tra kỹ lưỡng hơn đối với tổ chức, bao gồm xác thực pháp lý, kiểm tra hoạt động của tổ chức và các tài liệu liên quan, đặc biệt để nhận biết nó sẽ hiện tên tổ chức/doanh nghiệp đăng ký, tăng độ uy tín.

## 	CSR file dùng làm gì trong quá trình tạo SSL


* CSR (Certificate Signing Request) là một file quan trọng trong quá trình tạo chứng chỉ SSL/TLS. Trong file CSR chứa thông tin quan trọng như tên miền, tổ chức, địa chỉ email, thông tin liên lạc, Khóa công khai (Public key) mà chứng chỉ sẽ sử dụng, CSR là một yêu cầu chính thức để cấp chứng chỉ SSL/TLS.

  ## 	Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech

  mkdir tech.training.vietnix.tech > tạo thư mục

  cd tech.training.vietnix.tech > vào thư mục

  openssl genrsa -out ca.key 2048 > tạo file private key

  openssl req -new -key ca.key -out ca.csr > tạo file csr

![image-20240911173233268](/home/thinhluc/snap/typora/90/.config/Typora/typora-user-images/image-20240911173233268.png)
  Hệ thống hỏi thì điền thông tin tương tự, phần email và challenge password nhấn Enter để bỏ qua.

## Pem file là gì ?

​	File PEM (Privacy Enhanced Mail) là một định dạng tệp tin được sử dụng để lưu trữ chứng chỉ và khóa mã hóa trong các ứng dụng bảo mật. Định dạng này rất phổ biến trong các ứng dụng và dịch vụ bảo mật, như chứng chỉ SSL/TLS, khóa riêng (private key), và chứng chỉ CA (Certificate Authority). Nó thường có đuôi .pem  hoặc các phần mở rộng khác .crt, .cer, .key, .csr, v.v.

​	Ta thường thấy tệp PEM có chứa dữ liệu phần đầu và phần cuối để xác định loại dữ liệu bên trong:

-------BEGIN CERTIFICATE-------

(DỮ LIỆU ĐÃ MÃ HÓA)

-------END CERTIFICATE------

HAY

--------BEGIN PRIVATE KEY--------

(DỮ LIỆU MÃ HÓA)

--------END PRIVATE KEY--------

## Private key ssl là gì ?

​	Khóa riêng SSL là một khóa mã hóa bí mật được sử dụng trong hệ thống mã hóa SSL/TLS, được sử dụng để ký chứng chỉ và yêu cầu ký chứng chỉ (CSR). Nó là một phần của cặp khóa mã hóa khóa công khai (Public Key) và khóa riêng (Private Key). Khóa riêng chỉ nên được biết đến và sử dụng bởi chủ sở hữu của chứng chỉ SSL và không nên được chia sẻ.

## PFX file là gì ? Cách chuyển từ file crt file sang PFX file.

​	File PFX lưu trữ dữ liệu được mã hóa, bảo vệ bằng mật khẩu để đảm bảo tính bảo mật của khóa riêng và các chứng chỉ.

​	Trong file PFX có chứa Private Key, Crt (Certificate). Được dùng trong việc input và output. Input: Tệp PFX thường được sử dụng để nhập khẩu chứng chỉ và khóa riêng vào các máy chủ, trình duyệt web, hoặc ứng dụng bảo mật



# Domain

## 	Domain là gì ?

​	Domain hay tên miền là địa chỉ trang web hoạt động trên Internet. Người dùng gõ Domain vào trình duyệt sẽ truy cập được một website bất kỳ

​	Ví dụ: google.com, youtube.com, ...

## 	Các trạng thái của domain

	1. Đăng Ký (Registered): Tên miền đã được đăng ký thành công và đang hoạt động. Chủ sở hữu tên miền có quyền kiểm soát và quản lý tên miền.
	1. Chờ Kích Hoạt (Pending Activation):  Tên miền vừa mới được đăng ký hoặc thay đổi và đang chờ kích hoạt hoàn toàn.
	1. Đang Xác Thực (Pending Verification): Tên miền đang chờ xác thực từ chủ sở hữu hoặc quản trị viên. Điều này thường xảy ra khi có thay đổi quan trọng như chuyển tên miền hoặc thay đổi thông tin liên hệ.
	1. Đã Đăng Ký (Active): Tên miền đã được đăng ký và kích hoạt, có thể sử dụng bình thường.
	1.  Đang Đợi Gia Hạn (Pending Renewal): Tên miền sắp hết hạn và đang chờ gia hạn.
	1. Hết Hạn (Expired): Tên miền đã hết hạn và không được gia hạn trong thời gian quy định.
	1. Đang Trong Thời Gian Gia Hạn (Grace Period): Tên miền đã hết hạn nhưng đang trong thời gian gia hạn. Chủ sở hữu có thể gia hạn tên miền trong khoảng thời gian này mà không bị mất quyền sở hữu.
	1. Đang Trong Thời Gian Chờ Xóa (Redemption Period): Tên miền đã hết hạn và đang trong thời gian chờ xóa, thường là khoảng 30 ngày sau thời gian gia hạn. Trong giai đoạn này, tên miền có thể phục hồi nhưng sẽ phải trả thêm phí phục hồi.

## Subdomain là gì?

​	Subdomain cho phép tổ chức và quản lý các phần khác nhau của trang web hoặc ứng dụng web dưới cùng một TÊN MIỀN CHÍNH.

​	Nếu bạn có tên miền chính là vietnix.vn, bạn có thể tạo các sub-domain như blog.vietnix.vn hoặc support.vietnix.vn

​	Mỗi sub-domain có thể trỏ đến một trang web hoặc phần cụ thể của trang

## Virtual Hosts là gì?

​	Virtual Hosts (máy chủ ảo) là một kỹ thuật được sử dụng trong quản lý web hosting để cho phép một máy chủ web duy nhất phục vụ nhiều trang web hoặc tên miền khác nhau. Điều này giúp tiết kiệm tài nguyên và quản lý dễ dàng hơn cho các trang web, đặc biệt khi chạy trên cùng một máy chủ vật lý.



# Mail Server

## Tìm hiểu MX Record

​	Khi ai đó gửi email đến địa chỉ này, máy chủ email cần biết gửi email đó đến đâu. Đây là nơi mà bản ghi **MX (Mail Exchange Record)** vào cuộc.

​	**MX Record** là một "dấu chỉ đường" trong hệ thống DNS (Domain Name System) cho biết máy chủ nào sẽ nhận email cho tên miền của bạn. Nó như là một danh bạ cho các máy chủ email, giúp các máy chủ gửi email biết gửi thư đến đâu.

​	***Vai Trò của MX Record:** 

​	**Địa chỉ Email:** Khi bạn gửi email đến `info@vietnix.vn`, máy chủ email sẽ tra cứu bản ghi MX của `vietnix.vn` để biết máy chủ nào nhận email cho tên miền này.

​	**Ưu Tiên:** Nếu có nhiều máy chủ nhận email, MX Record cho biết thứ tự ưu tiên để thử gửi email. Máy chủ có ưu tiên thấp hơn (số nhỏ hơn) sẽ được thử trước.

​	*** Cấu Hình MX Record**

​		**Tạo MX Record:**

​	Bạn cần tạo bản ghi MX trong hệ thống DNS của tên miền. Đây là nơi bạn chỉ định máy chủ email nào sẽ nhận email cho tên miền của bạn.

​		**Ví Dụ Cấu Hình:**

​	Giả sử bạn có tên miền `vietnix.vn` và muốn thiết lập hai máy chủ email. Bạn sẽ cấu hình bản ghi MX như sau: 

​		**Máy chủ chính:** `mail1.vietnix.vn` với ưu tiên 10.

​		**Máy chủ phụ:** `mail2.vietnix.vn` với ưu tiên 20.	

​	Điều này có nghĩa là email sẽ được gửi đến `mail1.vietnix.vn` trước. Nếu `mail1.vietnix.vn` không hoạt động, email sẽ được gửi đến `mail2.vietnix.vn`.

​	`vietnix.vn    3600    IN    MX    10    mail1.example.com.`

​	`vietnix.vn   3600    IN    MX    20   mail2.example.com.`

### **Tóm Tắt**

- **Bản Ghi MX** là như một chỉ dẫn cho các máy chủ email khác biết nơi gửi email đến khi bạn gửi email đến một địa chỉ thuộc tên miền của bạn.
- **Ưu Tiên** giúp xác định thứ tự máy chủ email nên được thử liên lạc.
- **Cấu Hình và Kiểm Tra** giúp đảm bảo email của bạn được gửi đến đúng nơi và hoạt động hiệu quả.

## Tìm hiểu DKIM, SPF, PTR

​	**1. DKIM (DomainKeys Identified Mail)**

​	**DKIM** là một phương pháp xác thực email giúp bảo vệ email khỏi việc bị giả mạo. Nó đảm bảo rằng email chưa bị thay đổi trong quá trình truyền tải và xác nhận rằng email thực sự đến từ miền mà nó tuyên bố.

​	**Cách Hoạt Động:**

​		**Ký Email:** Khi email được gửi đi từ máy chủ email của bạn, nó sẽ được ký bằng một chữ ký số mà máy chủ sử dụng khóa riêng (private key).

​		**Đăng Bản Ghi DKIM:** Bản ghi DKIM được đăng trên hệ thống DNS của tên miền bạn, chứa khóa công khai (public key).

​		**Xác Thực:** Khi email đến máy chủ nhận, máy chủ này sẽ tra cứu bản ghi DKIM trong DNS để lấy khóa công khai và kiểm tra chữ ký số. Nếu chữ ký hợp lệ và khớp với nội dung email, email được xác thực là từ miền đúng và không bị thay đổi.

#### **Cấu Hình DKIM:**

1. **Tạo Cặp Khóa:** Tạo khóa công khai và khóa riêng.
2. **Đăng Bản Ghi DKIM:** Đăng bản ghi TXT trong DNS của bạn, chứa khóa công khai và thông tin ký.
3. **Cấu Hình Máy Chủ:** Cấu hình máy chủ email của bạn để ký email bằng khóa riêng.

`selector._domainkey.example.com. IN TXT "v=DKIM1; k=rsa; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA7...bQIDAQAB"`

​	**`selector`** là tên mà bạn chọn để phân biệt các bản ghi DKIM khác nhau.

**`v=DKIM1`** chỉ phiên bản DKIM.

**`k=rsa`** chỉ loại khóa.

**`p=`** chứa khóa công khai.

​	**2. SPF (Sender Policy Framework)**

​	**SPF** là một phương pháp xác thực email giúp ngăn chặn giả mạo email bằng cách xác nhận rằng email gửi từ một máy chủ hợp lệ cho miền mà nó tuyên bố.

​	**Cách Hoạt Động:**

 - **Đăng Bản Ghi SPF:** Bạn đăng một bản ghi TXT trong DNS của miền bạn, chỉ định các máy chủ hợp lệ có quyền gửi email cho miền đó

 - **Xác Thực:** Khi một email đến, máy chủ nhận sẽ kiểm tra bản ghi SPF để xác nhận xem địa chỉ IP của máy chủ gửi có được phép gửi email cho miền không.

   **Cấu Hình SPF:**

   - **Tạo bản ghi SPF**: Xác định các máy chủ hợp lệ và tạo bản ghi SPF

   - **Đăng bản ghi SPF:** Đăng bản ghi TXT trong DNS của bạn

   **Ví dụ bản ghi SPF:**

   example.com. IN TXT "v=spf1 ip4:192.168.0.1 include:spf.example.net -all"

   - **`v=spf1`** chỉ phiên bản SPF.
   - **`include:spf.example.net`** cho phép các máy chủ trong bản ghi SPF của `example.net`
   - **`-all`** cho biết tất cả các máy chủ khác không được phép gửi email.

​	**3. PTR (Pointer Record)**

​	**PTR Record** là một loại bản ghi DNS được sử dụng để ánh xạ địa chỉ IP trở lại tên miền. Nó thường được sử dụng trong xác thực email để đảm bảo rằng địa chỉ IP của máy chủ gửi email có một tên miền hợp lệ.

​	**Cách Hoạt Động:** 

 	1. **Yêu Cầu Đăng Ký**: Liên hệ với nhà cung cấp dịch vụ internet (ISP) hoặc quản trị viên DNS để yêu cầu cấu hình bản ghi PTR cho địa chỉ IP của bạn.
 	2. **Đăng bản ghi PTR**: Cung cấp thông tin để ánh xạ địa chỉ IP đến tên miền.

**Ví dụ bản ghi PTR**

Nếu địa chỉ IP `192.168.0.1` của bạn trỏ tên miền `mail.vietnix.vn`, bản ghi PTR có thể trông như sau:

​	`1.0.168.192.in-addr.arpa. IN PTR mail.example.com.`

### **Tóm Tắt**

- **DKIM**: Xác thực rằng email không bị thay đổi và đến từ tên miền đúng.
- **SPF**: Xác thực rằng email được gửi từ một máy chủ hợp lệ cho tên miền.
- **PTR**: Xác minh rằng địa chỉ IP của máy chủ gửi có tên miền hợp lệ.



# DNS



## DNS là gì ?

​	DNS là viết tắt của cụm từ Domain Name System, mang ý nghĩa đầy đủ là hệ thống phân giải tên miền. Hiểu một cách ngắn gọn nhất, DNS cơ bản là một hệ thống chuyển đổi các tên miền website mà chúng ta đang sử dụng, ở dạng www.tenmien.com sang một địa chỉ IP dạng số tương ứng với tên miền đó và ngược lại.

## Các loại recored DNS

Trong hệ thống DNS (Domain Name System), có nhiều loại bản ghi (record) khác nhau, mỗi loại phục vụ một mục đích cụ thể:

1. **A Record (Address Record)**

   - **Chức Năng:** Liên kết một tên miền với địa chỉ IPv4.
   - **Ví Dụ:** `vietnix.vn` `192.0.2.1`.
   - **Công Dụng:** Tương tự như bản ghi A, nhưng dành cho địa chỉ IPv6, giúp các thiết bị kết nối với địa chỉ IPv6

2.  **AAAA Record (IPv6 Address Record)**

   - **Chức Năng:** Chỉ định một tên miền là bí danh (alias) cho một tên miền khác.
   - **Ví Dụ:** `example.com` → `2001:db8::1`
   - **Công Dụng:** Tương tự như bản ghi A, nhưng dành cho địa chỉ IPv6, giúp các thiết bị kết nối với địa chỉ IPv6.

3. **CNAME Record (Canonical Name Record)**

   - **Chức Năng:** Chỉ định một tên miền là bí danh (alias) cho một tên miền khác.
   - **Ví Dụ:** `www.example.com` → `example.com`.
   - **Công Dụng:** Khi truy cập `www.example.com`, bản ghi CNAME sẽ chuyển hướng yêu cầu đến `example.com`, giúp quản lý các tên miền phụ dễ dàng hơn.

4. **MX Record (Mail Exchange Record)**

   - **Chức Năng:** Xác định máy chủ email chịu trách nhiệm nhận email cho miền.
   - **Ví Dụ:** `example.com` → `mail.example.com` với ưu tiên `10`.
   - **Công Dụng:** Hướng dẫn email đến máy chủ email cụ thể. Ưu tiên giúp xác định thứ tự mà các máy chủ email sẽ được thử nghiệm.

5. **PTR Record (Pointer Record)**

   - **Chức Năng:** Ánh xạ địa chỉ IP trở lại tên miền, thực hiện tra cứu ngược (reverse lookup).
   - **Ví Dụ:** `192.0.2.1` → `mail.vietnix.vn`
   - **Công Dụng:** Dùng trong tra cứu ngược để xác thực rằng địa chỉ IP có liên kết với một tên miền cụ thể, thường được sử dụng trong các hệ thống bảo mật email.

6. **NS Record (Name Server Record)**

   - **Chức Năng:** Xác định các máy chủ DNS chịu trách nhiệm cho một tên miền.
   - **Ví DỤ:**`vietnix.vn` → `ns1.vietnix.vn` và `ns2.vietnix.vn`.

7. **TXT Record (Text Record)**

   - **Chức Năng:** Chứa thông tin văn bản cho các mục đích khác nhau.
   - **Ví DỤ:** `vietnix.vn` → `"v=spf1 ip4:192.0.2.1 -all"`.

8. **SRV Record (Service Record)**

   - **Chức Năng:** Cung cấp thông tin về các dịch vụ cung cấp bởi tên miền, chẳng hạn như dịch vụ VoIP hoặc dịch vụ chat.
   - **Ví DỤ:** `_sip._tcp.example.com` → `sipserver.example.com` với ưu tiên `10` và cổng `5060`.
   - **Công Dụng:** Xác định máy chủ và cổng cho các dịch vụ mạng cụ thể, giúp ứng dụng và dịch vụ tìm các máy chủ cung cấp dịch vụ.

9. **SOA Record (Start of Authority Record)**

   - **Chức Năng:** Cung cấp thông tin về miền, bao gồm máy chủ DNS chính, email của quản trị viên và thông tin về phiên bản của bản ghi.
   - **Ví DỤ:** `vietnix.vn` → `ns1.vietnix.vn` (master server), `admin.vietnix.vn` (contact email).
   - **Công Dụng:** Đóng vai trò quan trọng trong việc quản lý thông tin về miền, như thời gian cập nhật, số phiên bản của bản ghi, và thời gian sống của bản ghi.

10. **DNSKEY Record**

    - **Chức Năng:** Cung cấp khóa công khai cho DNSSEC (DNS Security Extensions).
    - **Ví DỤ:** Cung cấp khóa công khai để xác thực các bản ghi DNS đã ký.
    - **Công Dụng:** Được sử dụng trong DNSSEC để cung cấp một phương pháp bảo mật cho DNS, đảm bảo tính toàn vẹn và xác thực của các bản ghi DNS.

11. **DS Record (Delegation Signer Record)**

    - **Chức Năng:** Liên kết giữa các bản ghi DNSSEC của miền chính và miền phụ.
    - **Ví DỤ:** Liên kết bản ghi DNSSEC từ một miền cấp cao đến miền cấp dưới.
    - **Công Dụng:** Được sử dụng trong DNSSEC để đảm bảo rằng các bản ghi DNS của miền con được xác thực bởi miền cha.

12.  **NAPTR Record (Naming Authority Pointer Record)**

    - **Chức Năng:** Cung cấp thông tin cho các dịch vụ mạng như SIP (Session Initiation Protocol) và ENUM (Telephone Number Mapping).

    - **Ví DỤ:** `_sip._tcp.example.com` → `1 1 "u" "sip" "sip:service@example.com"`

    - **Công dụng**: Hỗ trợ các dịch vụ và ứng dụng cần ánh xạ số điện thoại hoặc thông tin dịch vụ sang các địa chỉ mạng

      

## Nguyên tắc làm việc của DNS

1. **Nhập tên miền**
2. **Kiểm tra Cache**: Máy chủ DNS kiểm tra địa chỉ IP đã được lưu trữ chưa
3. **Tra cứu**: Nếu không có trong cache, yêu cầu được gửi đến máy chủ DNS cấp cao hơn để tìm máy chủ chính (authoritative DNS server).
4. **Nhận Địa Chỉ IP**: Máy chủ chính trả về địa chỉ IP cho tên miền.
5. **Kết Nối Web:** Trình duyệt sử dụng địa chỉ IP để kết nối đến máy chủ web và tải trang.

**DNS chuyển tên miền thành địa chỉ IP qua kiểm tra cache và tra cứu các máy chủ DNS.**

## Cách phân giải địa chỉ DNS

1. **Sử dụng Công Cụ Trực Tuyến**
   - Có nhiều công cụ trực tuyến giúp bạn phân giải tên miền thành địa chỉ IP, chẳng hạn như:
     - **MXToolbox** (https://mxtoolbox.com)
     - **What's My DNS** (https://www.whatsmydns.net)
     - **DNS Checker** (https://dnschecker.org)
2. **Sử Dụng Lệnh Trên Terminal/CMD**

- Trên Windows:

  Mở command Prompt (CMD) và gõ lệnh:

  `nslookup <tên-miền>`

- Trên Linux và MacOS

  - Mở Terminal và gõ lệnh: `dig <tên-miền>`
  - Hoặc dùng lệnh `host <tên miền>` (sẽ hiển thị đơn giản hơn)

===========================================================

# ping/hping3 ping đến domain vietnix.vn 

### ttl= là gì

​	Khi bạn gửi một gói tin trên mạng, gói tin đó có một "hạn sử dụng" được gọi là TTL. Mỗi lần gói tin đi qua một thiết bị mạng (như router),  giá trị TTL giảm đi một đơn vị, Nếu TTL giảm về 0 trước khi gói tin đến đích, gói tin sẽ bị loại bỏ, và một thông báo lỗi sẽ được gửi lại cho nơi gửi gói tin để cho biết gói tin không thể đến đích. TTL thường được đặt giá trị mặc định khi gói tin được gửi, ví dụ 64 hoặc 128.

![image-20240911095239665](/home/thinhluc/snap/typora/90/.config/Typora/typora-user-images/image-20240911095239665.png)

​	Trong hình trên ta thấy ttl= 53 có nghĩa là gói tin đã đi qua một số router và còn lại 53 bước nhảy có thể thực hiện được, nếu TTL được đặt mặc định là 64 thì gói tin đã đi qua 11 router (64-53)

* TTL là số bước nhảy mà gói tin có thể thực hiện trên mạng trước khi bị loại bỏ.
* TTL giảm dần mỗi khi gói tin đi qua một router
* TTL giúp ngăn gói tin bị lặp vô tận trong mạng

### time= là gì

​	Đại diện cho thời gian trễ (lantency) hoặc thời gian gói tin được gửi và nhận giữa Điểm gửi và điểm nhận, rồi quay lại

- Thời gian trễ thấp thì kết nối mạng nhanh và ổn định, lantency dưới 50ms được xem là tốt cho kết nối mạng
- Thời gian trễ cao có thể chỉ ra sự cố về kết nối, tốc độ mạng sẽ bị chậm dẫn đến rớt mạng

### ssh command

- Dùng password
  - ssh <tên người dùng>@<địa chỉ máy chủ>. Ví dụ user@192.168.1.10

- Dùng key

  1. Tạo cặp khóa SSH

     `ssh-keygen -t rsa -b 4096 -C "email@vietnix.vn"`

     - `-t rsa`: Chỉ định loại khóa (RSA)
     - `-b 4096`: Độ dài của khóa (4096 bit).
     - `-C "email@vietnix.vn"`: Thêm chú thích cho khóa

  2. Sao chép khóa công khai (Public Key) đến máy chủ (server)

  3. Sao chép nội dung của tệp khóa công (thường là `~/.ssh/id_rsa.pub`) và thêm nó vào tệp `~/.ssh/authorized_keys` trên máy chủ từ xa. Mở nội dung file bằng lệnh cat:

     ​				`cat ~/.ssh/id_rsa.pub`

     Sao chép nội dung và dán vào tệp `~/ssh/authorized_keys` trên máy chủ từ xa. Có thể dùng lệnh:

     `cat ~/.ssh/id_rsa.pub | ssh user@192.168.1.10 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"`

     Chú thích:

     - `ssh user@192.168.1.10`: `tên người dùng`@`địa chỉ máy chủ` của máy chủ từ xa

     - Đọc khóa công SSH từ tệp `id_rsa.pub` trên máy tính của bạn.

     - Kết nối đến máy chủ từ xa qua SSH.

     - Tạo thư mục `.ssh` trên máy chủ từ xa nếu chưa tồn tại.

     - Thêm khóa công vào tệp `authorized_keys` trên máy chủ từ xa, cho phép máy tính của bạn kết nối tới máy chủ từ xa mà không cần mật khẩu trong tương lai.

  Hoàn tất sẽ kết nối được đến máy chủ từ xa mà không dùng password

​						`ssh user@192.168.1.10`

**Chú ý: Nếu khóa riêng không nằm ở vị trí mặc định (ví dụ: `~/.ssh/id_rsa`), thì chỉ định nó bằng tùy chọn `-i`: ví dụ**

​			`ssh -i /path/to/private_key user@192.168.1.10`

/path/to/private_key: đường dẫn đến khóa riêng (tùy vào đường dẫn chứa khóa riêng của bạn)

- Dùng port custom

`ssh -p 2200 user@192.168.1.10`

​	> -p <cổng> port custom đã cấu hình cho ssh

### scp command

**`scp`**: Lệnh dùng để sao chép tệp và thư mục qua kết nối SSH.

- **scp 1 file**

  - **Sao chép file từ máy cục bộ đến máy chủ từ xa**

    `scp file.txt user@remote_host:/path/to/remote/directory`

    - file.txt: tệp bạn muốn sao chép.

    - user@remote_host: Tên người dùng và địa chỉ IP hoặc tên miền của máy chủ từ xa.

    - /path/to/remote/directory: Đường dẫn đến thư mục đích trên máy chủ từ xa

  - Sao Chép Tệp Từ Máy Chủ Từ Xa Về Máy Cục Bộ

    `scp user@remote_host:/path/to/remote/file.txt`

    - `user@remote_host:/path/to/remote/file.txt`: Đường dẫn đầy đủ đến tệp trên máy chủ từ xa.

    - Thư mục hiện tại trên máy tính cục bộ nơi tệp sẽ được sao chép đến.

- **scp 1 foler**

  - scp -r folder user@remote_host:/path/to/remote/directory
    - -r folder là thư mục cần tải 

### rsync command

​			`rsync [tùy chọn] <nguồn> <đích>`

- **rsync file**
  - **Sao Chép Tệp Từ Máy Cục Bộ Đến Máy Chủ Từ Xa**

`rsync -avz file.txt user@remote_host:/path/to/remote/directory`

***`-a`** (archive mode): Sao chép tệp và thư mục, giữ nguyên các thuộc tính (như quyền, thời gian sửa đổi, và cấu trúc thư mục).*

***`-v`** (verbose): Hiển thị chi tiết quá trình sao chép.*

***`-z`** (compression): Nén dữ liệu trong khi truyền để giảm băng thông.*

​	***Sao Chép Tệp Từ Máy Chủ Từ Xa Về Máy Cục Bộ**

`rsync -avz user@remote_host:/path/to/remote/file.txt /local/path/`

**`/local/path/`**: Thư mục trên máy tính cục bộ nơi bạn muốn sao chép tệp đến.

- **rsync folder**
  - **Sao Chép Thư Mục Từ Máy Cục Bộ Đến Máy Chủ Từ Xa**

`rsync -avz folder/ user@remote_host:/path/to/remote/directory/`

*Lưu ý rằng có dấu `/` ở cuối `folder/` để chỉ sao chép nội dung của thư mục, không phải chính thư mục đó. Nếu bạn không có dấu `/`, thư mục `folder` sẽ được sao chép vào thư mục đích.*

​		**Sao Chép Thư Mục Từ Máy Chủ Từ Xa Về Máy Cục Bộ**		

`rsync -avz user@remote_host:/path/to/remote/folder/ /local/path/`

**`rsync`**: Công cụ sao chép và đồng bộ hóa tệp và thư mục.

**`-a`**: Chế độ lưu trữ, sao chép toàn bộ thuộc tính.

**`-v`**: Hiển thị chi tiết.

**`-z`**: Nén dữ liệu khi truyền.

- **rsync increamental**

  Sao chép gia tăng (incremental)**: Chỉ sao chép các phần đã thay đổi hoặc các tệp mới từ lần sao chép trước.

  `rsync -avz --update source_dir/ user@remote_host:/path/to/destination_dir/`

  **`-a`**: Chế độ lưu trữ, giữ nguyên thuộc tính tệp.

  **`-v`**: Hiển thị chi tiết về quá trình sao chép.

  **`-z`**: Nén dữ liệu khi truyền.

  **`--update`**: Chỉ sao chép các tệp mới hơn hoặc đã thay đổi.

  **`source_dir/`**: Đây là thư mục nguồn trên máy tính cục bộ mà bạn muốn sao chép. 

  **`/path/to/destination_dir/`**: Đường dẫn đến thư mục đích trên máy chủ từ xa.

  

  # cat command

- **cat nội dung 1 file**

  `cat file.txt`

- cat dòng thứ <n> trong file

  `cat <tên_tệp> | head -n <n> | tail -n 1`

  > Chú thích

  **`cat <tên_tệp>`**: Hiển thị toàn bộ nội dung của tệp.

  **`head -n <n>`**: Lấy các dòng từ đầu tệp đến dòng thứ `<n>`.

  **`tail -n 1`**: Lấy dòng cuối cùng của kết quả từ `head`, tức là dòng thứ `<n>`

- cat nhiều dòng vào 1 file bằng EOF

  `cat <<EOF > file.txt`

### echo command

- Dùng echo để chèn thêm 1 dòng vào cuối file

  `echo "Dòng mới" >> file.txt`

- Dùng echo để overwirte nội dung của file

​	`echo "Nội dung mới" > tên_tệp`

### tail/head command

Lệnh xem các dòng đầu và cuối của tệp

- tail và tailf
  - **`tail`**: Hiển thị và theo dõi các dòng cuối cùng của tệp. Sử dụng `-f` để theo dõi sự thay đổi.
  - **`tailf`**: Một phiên bản tối ưu của `tail -f`, được thiết kế đặc biệt để theo dõi các tệp log và thường hiệu quả hơn cho các tệp lớn.

### sed command

**Cú pháp cơ bản **

`sed [tùy chọn] 'lệnh' [tệp]`

- Dùng sed để find and replace một string trong file

`sed 's/pattern/replacement/' [tệp]`

**`s`**: Lệnh thay thế.

**`pattern`**: Mẫu (chuỗi) cần tìm.

**`replacement`**: Chuỗi thay thế.

**`[tệp]`**: Tên tệp chứa văn bản.

- traceroute/tracert command

  `traceroute/tracert 'tên miền'`

- Sau khi traceroute xong giải thích chi tiết kết quả trả về

![image-20240911134012679](/home/thinhluc/snap/typora/90/.config/Typora/typora-user-images/image-20240911134012679.png)

​	Có 11 điểm trung gian mà gói tin phải đi qua, điểm 4 không phản hồi cho máy chủ đã ping

​	64 hops max giới hạn số lượng hop (điểm trung gian) tối đa mà lệnh sẽ theo dõi

### netstat command

- **hiển thị các socket đang listen**

  `netstat -a`

- **don't resolve hostname**

  `netstat -an`

- don't resolve portname

  `netstat -n`

- display process name/PID

  `netstat -p`

- only show tcp socket

  `netstat -at`

- only show udp socket

  `netstat -au`

### sort command

- sort theo thứ tự tăng dần

  `sort file.txt`

- sort theo thứ tự giảm dần

  `sort -r file.txt`

- sort theo column

  `sort -k <cột> [tập tin]`

### uniq command

- lọc ra các dòng lặp lại trong một file

  `uniq -d [tập tin]`

- lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại

  `sort file.txt | uniq -c`

### wc command

- Đếm số dòng trong file

  `wc -l [tập tin]`

- Đếm số kí tự trong file

  `wc -c [tập tin]`

### chmod, chown, chattr command

- Phân quyền bằng số, phân quyền bằng chữ

  - Phân quyền bằng số

  **Quy Tắc Cơ Bản**

  **0**: Không có quyền (---)

  **1**: Quyền thực thi (--x)

  **2**: Quyền ghi (-w-)

  **3**: Quyền ghi và thực thi (-wx)

  **4**: Quyền đọc (r--)

  **5**: Quyền đọc và thực thi (r-x)

  **6**: Quyền đọc và ghi (rw-)

  **7**: Quyền đọc, ghi, và thực thi (rwx)

  `chmod 755 file.txt`

  Chú thích: 

  **7** (rwx) cho chủ sở hữu.

  **5** (r-x) cho nhóm.

  **5** (r-x) cho những người khác.

  - **Phân quyền bằng chữ**

  **Quyền Truy Cập**

  - **`r`**: Quyền đọc (read)
  - **`w`**: Quyền ghi (write)
  - **`x`**: Quyền thực thi (execute)

  **Quyền Sở Hữu**

  - **`u`**: Chủ sở hữu (user)
  - **`g`**: Nhóm (group)
  - **`o`**: Khác (others)
  - **`a`**: Tất cả (all)

  *Ví dụ:* *Cấp Quyền Đọc, Ghi, và Thực Thi Cho Chủ Sở Hữu, Chỉ Quyền Đọc và Thực Thi Cho Nhóm và Khác*

  `chmod u=rwx,go=rx file.txt`

- Đổi owner user/group

  `chown user:group file.txt`

  Chú thích: Thay đổi chủ sở hữu của `file.txt` thành `user` và nhóm thành `group`.

- Set Immutable Attribute

  `sudo chattr +i file.txt`

  Chú thích: Lệnh này đặt thuộc tính không thay đổi cho `file.txt`, ngăn không cho bất kỳ ai thay đổi, xóa, hoặc di chuyển tập tin này, ngoại trừ người dùng root.

### find command

- find các file có đuôi .log

- find các folder có tên abc

- find các file có tên abc

- find các file có tên abc và thực hiện phần quyền read only cho file

### cp command

- cp file

  `cp [tùy chọn] [nguồn] [đích]`

  `cp file1.txt file2.txt`

- cp folder

  `cp -r dir1 dir2`

### mv command

- mv file, folder

  **Đổi tên tập tin từ `oldname.txt` thành `newname.txt` trong cùng thư mục:**

  `mv oldname.txt newname.txt`

  **Di Chuyển Tập Tin Đến Thư Mục Khác**

  mv file.txt /path/to/destination/

### cut command

- cut kí tự thứ <n> trong string

`echo "chuỗi_văn_bản" | cut -c <n>`

- cut từ kí tự thứ <n> trở về sau

`echo "chuỗi_văn_bản" | cut -c <n>-`

- cut từ kí tự thứ <n> trở về trước

`echo "chuỗi_văn_bản" | cut -c -<n>`

### dig command

- Dùng Dig command để kiểm tra resolv record A, MX, NS

​	`dig +short <tên_miền> A`

​	`dig +short <tên_miền> MX`

​	`dig +short <tên_miền> NS`

- Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS
- `dig @<máy_chủ_DNS> <tên_miền> <loại_bản_ghi>`

# tar/zip/unzip command

**Nén/Giải nén file tar.gz - Nén/Giải nén file .zip**

- **Nén và giải nén file tar.gz**

  `tar -czf <tên_file.tar.gz> <đường_dẫn_tới_file_hoặc_thư_mục>`

  *Chú thích:*

   ***`-c`**: Tạo file archive.*

  ***`-z`**: Nén bằng gzip.*

  ***`-f`**: Xác định tên file archive.*

  *Ví dụ*:  `tar -czf archive.tar.gz /path/to/directory` . 

  > Nén file `/path/to/file` thành file `file.tar.gz`.

- **Giải Nén File `.tar.gz`**

  `tar -xzf <tên_file.tar.gz>`

  *Chú thích:*

  **Giải thích:**

  - **`-x`**: Giải nén file archive.
  - **`-z`**: Giải nén gzip.
  - **`-f`**: Xác định tên file archive.

- **Giải Nén Đến Thư Mục Cụ Thể**

  `tar -xzf archive.tar.gz -C /path/to/destination`

### mount/umount command

- Add thêm một ổ cứng sdb ~ 5gb

1. **Kiểm Tra Thiết Bị**

   `lsblk`

2. **Tạo Phân Vùng**

   `sudo fdisk /dev/sdb`

   Trong `fdisk`, thực hiện các bước sau:

   Nhấn **`n`** để tạo phân vùng mới.

   Nhấn **`p`** để chọn phân vùng chính.

   Chọn **`1`** để phân vùng đầu tiên (hoặc chọn số phân vùng khác nếu cần).

   Chọn các giá trị mặc định hoặc nhập thông số cụ thể.

   Nhấn **`w`** để lưu và thoát.

3. **Định dạng phân vùng**

   Sau khi tạo phân vùng, bạn cần định dạng nó với hệ tập tin. Ví dụ, để định dạng phân vùng `/dev/sdb1` với hệ tập tin ext4:

   `sudo mkfs.ext4 /dev/sdb1`

4. **Tạo thư mục gắn kết**

   `sudo mkdir /mnt/test`

5. **Gắn Kết Phân Vùng**

   Gắn kết phân vùng `/dev/sdb1` vào thư mục `/mnt/test`:

   `sudo mount /dev/sdb1 /mnt/test`

6. **Kiểm tra**

   Xác nhận rằng phân vùng đã được gắn kết thành công:

   `df -h` hoặc `lsblk`

7. **Umount /mnt/test**

   `sudo umount /mnt/test /dev/sdb1`

### Symbolic Links, Hard Links command

- **Định nghĩ Sym Link**

  **Symbolic Link** (hay còn gọi là **symlink**) là một cách để tạo một liên kết giống như shortcut tới một tập tin hoặc thư mục khác trên hệ thống. Đây là cách giúp truy cập tập tin hoặc thư mục từ một vị trí khác mà không cần phải sao chép nó. Tóm lại, Symlink chỉ đơn giản là một liên kết tới một tập tin hoặc thư mục khác, Nếu mở symlink, sẽ thấy nội dung của tập tin hoặc thư mục mục tiêu đã liên kết

  **Đặc điểm chính:**

  - Là một liên kết đến đường dẫn của tập tin hoặc thư mục.

  - Có thể liên kết đến các hệ thống tập tin khác nhau.

  - Nếu tập tin gốc bị xóa, symlink trở thành "dangling" (liên kết bị gãy) và không còn hữu ích.

  ***Ví dụ*:** 

  1. **Tạo Symlink Đến Tập Tin**

     Giả sử có tập tin `file.txt` trong thư mục `/home/user/`, và bạn muốn tạo một symlink đến nó trong thư mục `/home/user/links`

     `ln -s /home/user/file.txt /home/user/links/link_to_file.txt`

     Chú thích: `link_to_file.txt` sẽ là một symlink trong thư mục `/home/user/links` và liên kết đến `file.txt`.

  2. **Tạo Symlink Đến Thư Mục**

     Nếu có một thư mục `docs` trong `/home/user/` và muốn tạo một symlink đến nó trong thư mục `/home/user/links`:

     `ln -s /home/user/docs /home/user/links/link_to_docs`

     **Giải thích**: `link_to_docs` sẽ là một symlink trong thư mục `/home/user/links` và liên kết đến thư mục `docs`.

- **Định nghĩa Hard Link**

  **Hard Link** là một tính năng trong hệ thống tập tin Unix/Linux cho phép bạn tạo một liên kết trực tiếp đến cùng một tập tin trên đĩa cứng. Một hard link có thể xem như là một cách để có nhiều tên cho cùng một tập tin thực sự, và tất cả các tên này đều trỏ đến cùng một dữ liệu trên đĩa.

  **Đặc điểm chính:**

  - Là một liên kết trực tiếp đến cùng một dữ liệu trên đĩa.

  - Không thể liên kết đến các hệ thống tập tin khác nhau.

  - Nếu tập tin gốc bị xóa, các hard link khác vẫn có thể truy cập dữ liệu.

  ***Ví dụ:*** Giả sử bạn có tập tin gốc `file.txt` trong thư mục `/home/user/`

  `ln /home/user/file.txt /home/user/hardlink_file.txt`

### ls command

- Liệt kê danh sách file/thư mục

  `ls`

- Liệt kê danh sách file/thư mục và thuộc tính

  `ls -l`

- Show file ẩn

- ls -la`

### ps command

- **show tiến trình**

  `ps` - Hiển thị các tiến trình thuộc về phiên làm việc hiện tại.

  `ps -e` - Hiển thị tất cả các tiến trình trong hệ thống.

  `ps aux` - Hiển thị tất cả các tiến trình, bao gồm thông tin chi tiết như người dùng, %CPU, %MEM, thời gian chạy, và lệnh.

- **kill tiến trình**

  Cú pháp: `kill [tùy_chọn] [PID]`

  **`[tùy_chọn]`**: Tín hiệu bạn muốn gửi (mặc định là `SIGTERM`).

  **`[PID]`**: ID của tiến trình bạn muốn gửi tín hiệu.

  **Các Tín Hiệu Thông Dụng**

  - **`SIGTERM` (15)**: Tín hiệu kết thúc (terminate) tiến trình một cách lịch sự, yêu cầu tiến trình dừng lại và dọn dẹp tài nguyên. Đây là tín hiệu mặc định khi sử dụng lệnh `kill`.
  - **`SIGKILL` (9)**: Tín hiệu kết thúc ngay lập tức, buộc tiến trình dừng lại mà không cho cơ hội dọn dẹp tài nguyên. Được sử dụng khi `SIGTERM` không có tác dụng.
  - **`SIGINT` (2)**: Tín hiệu ngắt, thường được gửi khi nhấn `Ctrl+C` trong terminal.
  - **`SIGHUP` (1)**: Tín hiệu treo (hang up), thường dùng để yêu cầu tiến trình tái cấu hình hoặc khởi động lại.

### top command

**Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy**

- **Giải thích về Load average, us, sy, ni, id, wa, hi, si, st, zombie process, sleeping process**
  - **Load average**: là một chỉ số cho biết trung bình số lượng công việc đang chờ đợi hoặc đang sử dụng tài nguyên của CPU trong một khoảng thời gian cụ thể. Nếu CPU có 4 core thì giá trị của LA nhỏ hơn 4 thì hệ thống đang chạy rất nhẹ nhàng, không có công việc chờ đợi.
  - **us**: Phần trăm CPU đang sử dụng cho các tiến trình của người dùng
  - **sy**: Phần trăm CPU đang sử dụng cho các tác vụ của hệ thống, tức là các nhiệm vụ của kernel (nhân hệ điều hành) hoặc các chức năng hệ thống khác.
  - **ni**:  Phần trăm CPU dành cho các tiến trình có độ ưu tiên "nice" (được điều chỉnh bởi lệnh `nice`). Đây là thời gian CPU được phân bổ cho các tiến trình có mức độ ưu tiên thấp hơn (như được chỉ định bởi người dùng).
  - **id**: Phần trăm thời gian CPU không hoạt động, tức là CPU đang rảnh và không làm việc.
  - **wa**: Phần trăm thời gian CPU đang chờ đợi các I/O (đầu vào/đầu ra) hoàn tất. Đây là thời gian CPU không thể tiếp tục làm việc vì nó đang chờ dữ liệu từ các thiết bị I/O.
  - **hi**: Phần trăm thời gian CPU đang xử lý các ngắt phần cứng. Ngắt phần cứng là các tín hiệu từ phần cứng yêu cầu CPU dừng lại công việc hiện tại để xử lý một sự kiện từ phần cứng.
  - **si**: Phần trăm thời gian CPU đang xử lý các ngắt phần mềm. Ngắt phần mềm là các yêu cầu từ hệ điều hành hoặc ứng dụng yêu cầu CPU dừng lại công việc hiện tại để thực hiện một tác vụ khác.
  - **st**: Phần trăm thời gian CPU bị "cướp" bởi các máy ảo khác (trong trường hợp bạn đang chạy máy ảo). Đây là thời gian mà CPU đã được yêu cầu bởi một máy ảo khác nhưng vẫn chưa được phân bổ cho máy ảo của bạn.cac
  - **zombie process**: là một tiến trình đã hoàn tất công việc của nó và kết thúc, nhưng vẫn còn "hiện diện" trong hệ thống vì thông tin về nó chưa được dọn dẹp hoàn toàn. Điều này xảy ra vì tiến trình cha của nó chưa thu thập thông tin về trạng thái kết thúc của tiến trình con.
  - **sleeping process**: Số lượng tiến trình đang ở trạng thái "sleeping". Đây là các tiến trình đang chờ đợi một sự kiện hoặc tài nguyên, không sử dụng CPU trong thời gian này.

### free command

- Giải thích ram used, free, shared, buff/cache, free:
  - used: dung lượng đã được sử dụng
  - free: dung lượng trống
  - shared: dung lượng mà được chia sẻ giữa các tiến trình
  - buff/cache: Bộ nhớ đang được sử dụng cho các bộ đệm (buffers) và cache. Bộ nhớ này được sử dụng để cải thiện hiệu suất của hệ thống bằng cách lưu trữ dữ liệu thường xuyên truy cập.

### df command

- Xem dung lượng disk

  `lsblk`

- Phân vùng / là gì

  Phân vùng (partition) là quá trình chia một ổ đĩa cứng hoặc thiết bị lưu trữ thành nhiều khu vực độc lập, mỗi khu vực hoạt động như một ổ đĩa riêng biệt. Việc phân vùng giúp tổ chức và quản lý dữ liệu hiệu quả hơn, đồng thời có thể cải thiện hiệu suất và bảo mật của hệ thống, tức là một đĩa vật lý, có thể chia ra nhiều ổ đĩa luận lý riêng biệt

