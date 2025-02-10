
🚦 Hệ Thống Đèn Giao Thông với PIC16F877A

## 📌 Giới Thiệu
Dự án này triển khai **hệ thống đèn giao thông** sử dụng **vi điều khiển PIC16F877A**. Hệ thống điều khiển **đèn đỏ, vàng, xanh** theo thời gian định sẵn, hiển thị số đếm ngược trên **LED 7 đoạn**, và hỗ trợ chế độ điều khiển bằng nút bấm.

---


## 🛠 Tính Năng Chính
✅ **Điều khiển đèn giao thông** với các trạng thái **Xanh - Vàng - Đỏ**  
✅ **Hiển thị thời gian đếm ngược** trên LED 7 đoạn  
✅ **Chế độ tự động và điều khiển bằng tay** thông qua nút bấm  
✅ **Hỗ trợ mô phỏng giao thông thực tế** với nhiều thời gian chu kỳ khác nhau  

---

## ⚙️ Phần Cứng Cần Thiết
- **Vi điều khiển**: PIC16F877A  
- **LED 7 đoạn**: 2 hoặc 4 module LED 7 đoạn  
- **Đèn LED**: Mô phỏng **đèn đỏ, đèn vàng, đèn xanh**  
- **Nút nhấn**: Chế độ điều khiển bằng tay  
- **Điện trở, tụ điện**: Tùy chỉnh mạch điện  
- **Thạch anh**: 20MHz  
- **Nguồn điện**: 5V DC  

---

## 💻 Cách Hoạt Động
1️⃣ **Hệ thống khởi động**, Timer1 bắt đầu đếm thời gian.  
2️⃣ **Chuyển trạng thái đèn** theo chu kỳ:  
   - Đèn **Xanh**: 20s  
   - Đèn **Vàng**: 3s  
   - Đèn **Đỏ**: 20s  
3️⃣ **Hiển thị thời gian còn lại** trên LED 7 đoạn.  
4️⃣ **Nếu có nút bấm điều khiển bằng tay**, hệ thống có thể thay đổi trạng thái đèn.  

---

## 📜 Code Mẫu
### **1. Khởi tạo hệ thống**
```c
void initialize_system() {
    setup_timer_1(T1_INTERNAL | T1_DIV_BY_8);
    set_timer1(3036);
    clear_interrupt(INT_TIMER1);
    enable_interrupts(INT_TIMER1);
    enable_interrupts(GLOBAL);
}
