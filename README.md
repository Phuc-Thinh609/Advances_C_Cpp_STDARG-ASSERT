# STDARG 
 - Thư viện __stdarg__ xử lý hàm có số tham số không cố định
 - Công dụng: cho phép viết các hàm nhận số lượng đối số khác nhau tại mỗi lần gọi, các hàm như __printf__, __scanf__
 - Các thành phần chính:

   | Thành phần | Công dụng |
   |------------|-----------|
   | __va_list__ | Khai báo danh sách các đối số biến đổi |
   | __va_start__ | Bắt đầu truy cập danh sách |
   | __va_arg__ | Lấy từng đối số trong danh sách |
   | __va_end__ | Kết thúc truy cập danh sách |
- Ví dụ - in giá trị
  ```Cpp
  void display(int count, ...) {
    va_list args;
    va_start(args, count);
    for (int i = 0; i < count; i++) {
        printf("Value at %d: %d\n", i, va_arg(args,int)); 
    }
    va_end(args);
  }
  ```
# ASSERT 
 - Thư viện __assert__ kiểm tra điều kiện khi chạy (Debug)
 - Công dụng:
   * Kiểm tra điều kiện logic trong chương trình
   * Nếu điều kiện sai -> in lỗi và dừng chương trình
   * Chỉ dừng khi debug, có thể tắt bằng __#define NDEBUG__
 - Ví dụ điển hình
   ```Cpp
     int x = 5;
     assert (x == 5);
     //Chương trình sẽ tiếp tục thực thi nếu điều kiện là đúng
     printf ("X is: %d", X)
   ```
- Ứng dụng thư viện assert
  | Macro tự định nghĩa | Chức năng |
  |---------------------|-----------|
  | __assert_in_range__(val, min, max) | Kiểm tra giá trị trong khoảng |
  | __assert_size(type, size)__ | Kiểm tra kích thước kiểu dữ liệu |
  - Ví dụ kiểm tra giá trị trong khoảng
    ```Cpp
      #define ASSERT_IN_RANGE(val, min, max) assert((val) >= (min) && (val) <= (max))
    
      void setLevel(int level) {
          ASSERT_IN_RANGE(level, 1, 10);
          // Thiết lập cấp độ
      }
    ```
  - Ví dụ kiểm tra kích thước kiểu dữ liệu
    ```Cpp
      #define ASSERT_SIZE(type, size) assert(sizeof(type) == (size))
    
      void checkTypeSizes() {
          ASSERT_SIZE(uint32_t, 4);
          ASSERT_SIZE(uint16_t, 2);
          // Kiểm tra các kích thước kiểu dữ liệu khác
      }
    ```
