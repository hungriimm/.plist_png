# Sprite Cutting Tool
Tools hỗ trợ cắt PNG từ file Plist có hỗ trợ chỉnh sửa update toạ độ trực tiếp cho file Plist
## Giới thiệu

Sprite Cutting Tool là một công cụ GUI (giao diện người dùng) được viết bằng Python, giúp bạn xử lý các file sprite sheet (`.png`) và file định nghĩa sprite (`.plist`). Công cụ này hỗ trợ:

- **Cắt tất cả sprite**: Cắt tất cả các sprite từ sprite sheet và lưu vào thư mục.
- **Cắt sprite theo lựa chọn**: Cắt các sprite được chọn từ danh sách.
- **Xem trước và chỉnh sửa tọa độ**: Xem trước khung tọa độ của một sprite, chỉnh sửa các thuộc tính như `frame`, `sourceColorRect`, `sourceSize`, và lưu lại file `.plist`.

Công cụ sử dụng `tkinter` để tạo giao diện người dùng và `Pillow` để xử lý hình ảnh.

## Yêu cầu cài đặt

### 1. Cài đặt Python

- Đảm bảo bạn đã cài đặt **Python 3.12** hoặc phiên bản mới hơn. Tải Python tại python.org.

### 2. Cài đặt các thư viện cần thiết

Công cụ yêu cầu các thư viện sau:

- `Pillow`: Để xử lý hình ảnh.
- `tkinter`: Để tạo giao diện GUI (thường đã có sẵn trong Python).

Cài đặt `Pillow` bằng lệnh sau:

```bash
pip install Pillow
```

### 3. Tải mã nguồn

- Tải mã nguồn từ repository hoặc sao chép file `tool_plist_png_new.py` vào máy của bạn.

## Cách sử dụng

### 1. Chạy công cụ

1. Mở terminal/command prompt và điều hướng đến thư mục chứa file `tool_plist_png_new.py`:

   ```bash
   cd C:\Users\Admin
   ```
2. Chạy file bằng Python:

   ```bash
   python tool_plist_png_new.py
   ```

### 2. Chọn file `.plist` và `.png`

- Khi khởi động, công cụ sẽ hiển thị giao diện với nút **"Chọn file .plist và .png"**.
- Nhấn nút này để:
  - Chọn file `.plist`: File định nghĩa tọa độ các sprite.
  - Chọn file `.png`: Sprite sheet chứa tất cả các sprite.
- Sau khi chọn, danh sách các sprite sẽ hiển thị trong giao diện.

### 3. Sử dụng các tính năng

Công cụ cung cấp 3 tính năng chính, chọn từ menu dropdown **"Chọn tính năng"**:

#### **Lựa chọn 1: Cắt tất cả sprite**

- Chọn tính năng này và nhấn **"Thực hiện"**.
- Công cụ sẽ cắt tất cả các sprite từ sprite sheet và lưu vào thư mục `extracted_sprites` (nằm cùng thư mục với file `.png`).
- Một thông báo sẽ hiển thị khi hoàn tất, kèm đường dẫn đến thư mục chứa sprite.

#### **Lựa chọn 2: Cắt sprite theo danh sách lựa chọn**

- Chọn các sprite từ danh sách (giữ `Ctrl` để chọn nhiều sprite).
- Chọn tính năng này và nhấn **"Thực hiện"**.
- Công cụ sẽ cắt các sprite đã chọn và lưu vào thư mục `extracted_sprites`.
- Một thông báo sẽ hiển thị khi hoàn tất.

#### **Lựa chọn 3: Xem trước tọa độ 1 sprite**

- Chọn **một sprite** từ danh sách.
- Chọn tính năng này và nhấn **"Thực hiện"**.
- Hai cửa sổ sẽ mở:
  - **Cửa sổ xem trước**: Hiển thị sprite sheet với khung đỏ xung quanh sprite đã chọn.
  - **Cửa sổ sprite đã cắt**: Hiển thị sprite sau khi cắt (đã xử lý xoay nếu `rotated: true`).
- **Chỉnh sửa tọa độ**:
  - Giao diện hiển thị các trường nhập liệu cho:
    - `frame`: Tọa độ `(x, y)` và kích thước `(width, height)` của sprite trên sprite sheet.
    - `sourceColorRect`: Tọa độ và kích thước của vùng màu nguồn.
    - `sourceSize`: Kích thước gốc của sprite.
  - Nhập các giá trị mới vào các trường này.
  - Nhấn **"Cập nhật khung"** để xem trước khung mới trên sprite sheet và sprite đã cắt.
  - Nhấn **"Cập nhật .plist"** để lưu các thay đổi vào file `.plist`.
- **Zoom và cuộn**:
  - Dùng bánh xe chuột để zoom in/out sprite sheet.
  - Dùng thanh cuộn (dọc và ngang) để di chuyển nếu sprite sheet lớn hơn cửa sổ.

### 4. Kiểm tra kết quả

- Các sprite đã cắt được lưu trong thư mục `extracted_sprites`.
- File `.plist` sẽ được cập nhật với các giá trị mới sau khi bạn nhấn "Cập nhật .plist".

## Lưu ý quan trọng

- **Định dạng file** `.plist`:
  - File `.plist` phải có định dạng chuẩn với các trường như `frame`, `rotated`, `sourceColorRect`, `sourceSize`.
  - Ví dụ:

    ```xml
    <key>varietystore_1005.png</key>
    <dict>
        <key>frame</key>
        <string>{{162,71},{150,82}}</string>
        <key>rotated</key>
        <true/>
        <key>sourceColorRect</key>
        <string>{{0,0},{596,16}}</string>
        <key>sourceSize</key>
        <string>{596,16}</string>
    </dict>
    ```
- **Kích thước sprite sheet**:
  - Nếu sprite sheet quá lớn, hãy dùng thanh cuộn hoặc zoom để xem toàn bộ hình ảnh.
- **Giá trị nhập liệu**:
  - Tất cả các giá trị (`x`, `y`, `width`, `height`, v.v.) phải là số nguyên. Nếu nhập số không hợp lệ, công cụ sẽ hiển thị thông báo lỗi.
- **Sao lưu file**:
  - Trước khi chỉnh sửa file `.plist`, hãy sao lưu để tránh mất dữ liệu trong trường hợp có lỗi.

## Hỗ trợ và góp ý

Nếu bạn gặp vấn đề hoặc cần cải tiến thêm, hãy liên hệ hoặc tạo issue trên repository của dự án.

Chúc bạn sử dụng công cụ hiệu quả!


