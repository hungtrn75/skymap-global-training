> 1. Tạo usecase cho phần lấy dữ liệu từ API với cái params cần thiết

> 2. Để xây dựng giao diện dạng bảng với phần phân trang trên mobile với thư viện [data_table_2](https://pub.dev/packages/data_table_2) thì cần phải xác định được các thuộc tính bắt buộc phải có
>    VD:

```
  AsyncPaginatedDataTable2(
    controller: _controller,
    columns: _columns,
    source: _dataSourceAsync!,
    horizontalMargin: 20,
    columnSpacing: 5,
    wrapInCard: false,
    rowsPerPage: 15,
    fit: FlexFit.tight,
    autoRowsToHeight: false,
    sortColumnIndex: _sortColumnIndex,
    sortAscending: _sortAscending,
    minWidth: 900,
    loading: const SizedBox(),
    errorBuilder: (e) => ErrorAndRetry(e.toString(), () {
      _dataSourceAsync!.refreshDatasource();
    }),
  )
```
- controller: Controller bắt buộc phải có khởi tạo của nó giúp kiểm soát các chức năng của table thông qua controller như: Thay đổi chỉ số page hiện tại cần lấy dữ liệu, chuyển sang page tiếp theo,...
```
final PaginatorController _controller = PaginatorController()
```
- columns: Khai báo bảng của mình gồm những cột nào và thuộc tính gì
```
List<DataColumn> get _columns {
    return [
      DataColumn(
        label: const Text('Organization'),
        onSort: (columnIndex, ascending) => sort(columnIndex, ascending),
      ),
      DataColumn(
        label: const Text('Town'),
        onSort: (columnIndex, ascending) => sort(columnIndex, ascending),
      ),
      DataColumn(
        label: const AutoSizeText(
          'Farm units Count',
          maxLines: 1,
        ),
        numeric: true,
        onSort: (columnIndex, ascending) => sort(columnIndex, ascending),
      ),
      DataColumn(
        label: const Text('Fields count'),
        numeric: true,
        onSort: (columnIndex, ascending) => sort(columnIndex, ascending),
      ),
      DataColumn(
        label: const Text('Staffs count'),
        numeric: true,
        onSort: (columnIndex, ascending) => sort(columnIndex, ascending),
      ),
      const DataColumn(label: Text('Actions'), numeric: true),
    ];
  }
```
VD ở trên có 6 cột. 
>> Những cột nào có thêm chức năng click để sắp xếp thì cần thêm thuộc tính onSort. Hàm này sẽ trả về các đối số trong callback của nó là chỉ số cột đã click và cột đó nên sắp xếp theo thứ tự tăng(true) hay giảm dần(false)

>> Mặc định thì layout của các cột sẽ bắt đầu từ trái sang phải. Nếu muốn sắp xếp từ phải sang để giao diện được đẹp hơn thì có thể thêm thuộc tính numeric(true)

- Thuộc tính sortColumnIndex giúp xác định dấu mũi tên sắp xếp sẽ nằm ở cột nào
- Thuộc tính sortAscending giúp xác định đang sắp xếp theo thứ tự tăng(mũi tên lên) hay giảm dần(mũi tên xuống)