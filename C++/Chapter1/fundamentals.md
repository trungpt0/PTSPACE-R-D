# Cơ bản về ngôn ngữ C++

## Lịch sử

Ngôn ngữ lập trình C++ được phát triển bởi Bjarne Stroustrup và nhóm của ông tại Bell Laboratories. Vào năm 1980, phiên bản đầu tiên của C++ ra đời được gọi là "C with classes". Như tên gọi C++, ngụ ý rằng ngôn ngữ lập trình này bắt nguồn từ C và ++ biểu thị sự cải tiến và phát triển hơn so với ngôn ngữ C ban đầu.

## Đặc điểm của C++

C++ không phải là một ngôn ngữ hướng đối tượng thuần túy mà là một ngôn ngữ lai chứa chức năng của ngôn ngữ lập trình C. Điều này có nghĩa là C++ có tất cả các tính năng có sẵn trong C. Ngoài ra nó còn hỗ trợ các đặc tính của lập trình hướng đối tượng (hay viết tắt là OOP) đó là:

- Tính trừu tượng hóa dữ liệu
- Tính đóng gói dữ liệu
- Tính kế thừa
- Tính đa hình

Những bài sau thì mình sẽ nói chi tiết hơn về 4 đặc tính này.

## Đối tượng

Lập trình hướng đối tượng (OOP) chuyển trọng tâm chú ý sang các đối tượng. Ví dụ, một chương trình quản lý tài khoản ngân hàng sẽ làm việc với các dữ liệu và hành vi như số dư, rút tiền, gửi tiền, kiểm tra số dư. Một đối tượng đại diện cho tài khoản trong chương trình sẽ có các thuộc tính và chức năng quan trọng để quản lý tài khoản.

```cpp
#include <iostream>
using namespace std;

// Định nghĩa lớp (Class)
class BankAccount {
private:
    double balance; // Thuộc tính: Số dư

public:
    // Constructor: Khởi tạo đối tượng
    BankAccount(double initialBalance) {
        balance = initialBalance;
    }

    // Phương thức: Gửi tiền
    void deposit(double amount) {
        balance += amount;
    }

    // Phương thức: Rút tiền
    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds!" << endl;
        }
    }

    // Phương thức: Kiểm tra số dư
    double getBalance() {
        return balance;
    }
};

int main() {
    // Tạo đối tượng từ lớp
    BankAccount account(1000); // Tài khoản với số dư ban đầu là 1000

    // Sử dụng các phương thức của đối tượng
    account.deposit(500);    // Nạp thêm 500
    account.withdraw(300);   // Rút 300
    cout << "Balance: " << account.getBalance() << endl; // In số dư

    return 0;
}
```

Trong OOP, một đối tượng sẽ có dữ liệu hay thuộc tính (properties) và chức năng (capacities). Một lớp (class) định nghĩa kiểu đối tượng cụ thể bằng cách xác định cả properties và capacities của các đối tượng thuộc kiểu đó.

## Ưu điểm của OOP

Lập trình hướng đối tượng cung cấp một số lợi thế chính cho phát triển phần mềm:

- Giảm tính nhạy cảm với lỗi bằng cách tổ chức mã nguồn thành các đối tượng độc lập. Điều này làm cho lỗi dễ dàng được cô lập và xử lý.
- Dễ dàng tái sử dụng thông qua các cơ chế như kế thừa và thư viện lớp. Khi một lớp hoặc đối tượng đã được thiết kế và kiểm thử, nó có thể được sử dụng trong các dự án khác mà không cần viết lại.
- Yêu cầu bảo trì thấp bằng cách tổ chức mã rõ ràng và có cấu trúc. Các lỗi hoặc thay đổi có thể được thực hiện mà không ảnh hưởng lớn đến toàn bộ hệ thống.