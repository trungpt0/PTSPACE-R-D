# **CHAPTER2: FUNDAMENTAL CONCEPTS**

## 2.1 The Core Operating System: The Kernel
_Kernel_ giúp quản lý tài nguyên và hỗ trợ lập trình. Trên Linux, tệp kernel thường nằm ở `/boot/vmlinuz`. kiến trúc bộ xử lý hoạt động ở 2 mode cơ bản: _user mode_ và _kernel mode_.  

Tiến trình không rõ trạng thái hệ thống hay tài nguyên toàn cục. Ngược lại, Kernel quản lý toàn bộ hệ thống, điều phối tài nguyên, và đảm bảo các tiến trình hoạt động hiệu quả.

## 2.2 The Shell
_`Shell` là trình thông dịch lệnh_, hoạt động như một tiến trình người dùng trên UNIX, không thuộc kernel, nó được khởi tạo khi người dùng đăng nhập lần đầu vào hệ thống. Các loại Shell phổ biến: sh, csh, ksh, bash (phổ biến nhất),...

`Shell Script` là tệp văn bản chứa lệnh shell, hỗ trợ biến, vòng lặp, điều kiện, I/O và hàm, với cú pháp tùy thuộc vào từng loại shell.

## 2.3 Users and Groups
Trên hệ thống UNIX/Linux, mỗi người dùng có một _tên đăng nhập duy nhất_ và _user ID_(UID), cùng thông tin trong tệp `/etc/passwd` như _group ID_, _home directory_, và _login shell_. Mật khẩu của người dùng được mã hóa trong tệp `/etc/shadow` để bảo mật. 

Groups giúp quản lý quyền truy cập vào tệp và tài nguyên, với thông tin trong tệp `/etc/group` bao gồm tên nhóm, _group ID_(GID) và danh sách thành viên. Người dùng có thể thuộc một hoặc nhiều nhóm, tùy thuộc vào hệ thống. 

_Superuser_(root) có quyền truy cập toàn bộ tài nguyên hệ thống, với ID người dùng là 0, và được dùng bởi quản trị viên để thực hiện các tác vụ quản trị.

## 2.4 Single Directory Hierarchy, Directories, Links, and Files
Hệ điều hành UNIX/Linux sử dụng cấu trúc thư mục phân cấp duy nhất, bắt đầu từ thư mục gốc(root) `/`.
![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEihAiKjvpZWCGO48NlU59J0-z6AkFGensRGZxw3fTVm9xyr8jzv0KPKNvOa-IywbgE0J19VSkbaRYT5qAFl-3QboamnSmsUUwbcl5bTal1o0n16gsTT4uFGhIyHGR9fNQzFtDNBrBlpgdM/s400/figure+2-1.PNG)

liên kết trong UNIX/LINUX được chia làm 2 loại: 
- _hard link_ 
- _symbolic link_(còn gọi là soft link ,tương tự shortcut trên windowns) 
![](https://static.vietnix.vn/wp-content/uploads/2024/04/cac-loai-lien-ket-trong-linux.webp)

Quyền truy cập file được phân chia cho ba loại người dùng: _`owner`_, _`group`_, và _`other`_. Với các quyền truy cập bao gồm: _`read`_, _`write`_ và _`execute`_.
![](https://cdn.hashnode.com/res/hashnode/image/upload/v1670002037392/7be8376a-b818-4054-a07e-ee42a5a92884.jpeg)

## 2.5 Programs
Chương trình tồn tại dưới hai dạng: mã nguồn và mã máy nhị phân. Mã nguồn phải được biên dịch và liên kết để chuyển thành mã máy. Khác với script các lệnh được xử lý trực tiếp bởi chương trình như shell.

Trong C, các chương trình có thể truy cập các tham số dòng lệnh, tức là các từ được cung cấp trên dòng lệnh khi chương trình được chạy. Ví dụ:
```C
int main(int argc, char *argv[])
```
với tham số `argc`(số lượng tham số) và `argv`(mảng các tham số). Tham số đầu tiên, _`argv[0]`(tên của chương trình)_.

## 2.6 Processes
Quá trình là một thể hiện của chương trình đang thực thi. Một quá trình được chia thành các phần logic sau, được gọi là các segments:
![](https://embeddedwala.com/uploads/images/202307/img_temp_64adb4df98f352-39966501-57144235.png)
