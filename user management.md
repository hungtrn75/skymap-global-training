## Xây dựng trang User Management
### 1. Nguồn dữ liệu
[https://demobayer.eofactory.ai/core/api/users?page=1&per_page=15&active=true&sort=name&search=Sahdeo](https://demobayer.eofactory.ai/core/api/users?page=1&per_page=15&active=true&sort=name&search=Sahdeo)

> Các params trên phương thức GET 
- search(không bắt buộc): Từ khóa để tìm kiếm trong thuộc tính name
- page(bắt buộc): Page hiện tại cần lấy danh sách
- per_page(không bắt buộc/mặc định: 5): Số phần tử trong một page
- active(không bắt buộc/mặc định: true): Trạng thái đang được active hoặc không trên hệ thống
- sort(không bắt buộc): Cần sắp xếp theo thứ tự của thuộc tính nào. Mặc định không có dấu trừ là A->Z và ngược lại là Z->A với dấu trừ

>Ví dụ:

![img](assets/3.png)

### 2. Xây dựng giao diện
>Hiện tại chỉ cần giao diện quản lý với dạng bảng và chưa cần lọc theo search và orginazation


- Giao diện ở phía web để tham khảo các cột cần xây dựng

![img](assets/4.png)
