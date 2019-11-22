# Array với numpy

Mặc định Python có nhiều kiểu dữ liệu \(data structure\), như List \(danh sách\), với List bạn có thể thực hiện việc tính toán trên dữ liệu mảng, tuy vậy Python list cũng gặp nhiều khó khăn và không tối ưu với các phép tính toán Toán học phức tạp hơn. 

Thư viện numpy ra đời khắc phục những điều đó, numpy được xem là công cụ mạnh và phổ biến hiện nay trên Python, với nhiều chức năng như tính toán trên mảng kích thước lớn đa chiều và xử lý ma trận. Numpy còn tối ưu giúp tính toán nhanh hơn, lưu trữ ít bộ nhớ hơn \(khi so sánh với Python list\).

### Tạo array

Tạo numpy array object bằng cách truyền vào danh sách các con số như ví dụ sau:

```python
>>> import numpy as np
>>> n_array = np.array([[0, 1, 2, 3],
                [4, 5, 6, 7],
                [8, 9, 10, 11]])
```

Một Numpy array object có thể có các thuộc tính, giúp mô tả thêm về array đó. Sau đây là một số thuộc tính quan trọng.

* `ndim`:  Cho biết số chiều của array. Ví dụ sau cho biết số chiều của array mà chúng ta đã định nghĩa là 2 chiều. 

  ```python
  >>> n_array.ndim
  2
  ```

  `n_array` có rank là 2, tức đây là mảng 2D.

* `shape` cho biết kích thước của từng chiều của array.

  ```python
  >>> n_array.shape
  (3, 4)
  ```

  Chiều thứ nhất có 3 phần tử, chiều thứ 2 có 4 phần tử, đây là một ma trận có 3 dòng 4 cột.

* `size` cho biết số phần tử của mảng

  ```python
  >>> n_array.size
  12
  ```

  Số phần tử của `n_array` là 12.

* dtype cho biết kiểu dữ liệu \(dtype = data type\) của các phần tử trong array.

  ```python
  >>> n_array.dtype.name
  int64
  ```

  Các phần tử có kiểu `int64`

### Toán tử toán học

#### Array subtraction

#### Squaring an array

#### A trigonometric function performed on the array

### Toán tử điều kiện

### Nhân ma trận

### Chỉ mục và Cắt ma trận \(Indexing và slicing\)

### Chuyển đổi hình dạng ma trận \(Shape manipulation\)

