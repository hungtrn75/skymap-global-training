### Xây dựng màn hình tạo mới/cập nhật một TSP Branch

> Giao diện đề xuất

<img src="../assets/17.png" alt="17" width="400"/>

> Giao diện khi xác thực dữ liệu khi người dùng nhập liệu chưa đúng

<img src="../assets/18.png" alt="18" width="400"/>

> API để tạo mới TSP Branch: `/tsps`

dữ liệu cần gửi lên dưới dạng json
```
{
  "town": "Hung TSP Branch Test",
  "organization": "Acres Rural Supplies Pty Ltd"
}
```
trong đó
- `town`: string
- `organization`: string|tên của organization đã chọn

> API để cập nhật TSP  Branch: `/tsps/{id}`
trong đó
- `id`: là định danh của tsp branch cần cập nhật thông tin
