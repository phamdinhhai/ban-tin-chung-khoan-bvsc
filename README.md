# BVSC Report Studio

Studio thiết kế báo cáo chứng khoán chạy hoàn toàn trên trình duyệt, gồm hai mẫu chính:

- **Bản tin sáng**: tổng quan thị trường, tin tức, nội dung và chiến lược trong ngày (`1600 × 1000px`).
- **Báo cáo chiến lược**: biến động chỉ số, biểu đồ, chiến lược tuần và tin tức nổi bật (`1600 × 900px`).

## Điểm nổi bật & Cơ chế thao tác

### 1. Giao diện Studio & Điều hướng nhanh
- **Studio Topbar**: chuyển đổi tức thì giữa **Bản tin sáng** và **Chiến lược tuần**, theo dõi trạng thái tự động lưu thời gian thực (`Đã lưu · hh:mm`), Undo/Redo, bật/tắt **Snap** (bắt dính thông minh), bật/tắt **Lưới (Grid)**, chọn độ phân giải xuất PNG (`1×`, `2×`, `3×`) và bảng phím tắt (`?`).
- **Sidebar theo Tab khoa học**:
  - Tab **+ Thêm & Bố cục**: thêm nhanh Text, Card, Ảnh, Widget chỉ số, Bảng biến động, Nhãn tiêu đề (Pill), Đường kẻ, 16 Icon SVG tài chính, Emoji; chọn **Chủ đề màu (Theme Presets)** (BVSC Navy Gold, Ocean Blue, Emerald Finance, Slate Minimal) và kích thước trang nhanh.
  - Tab **Lớp & Kiểm tra**: tìm kiếm/lọc Layer theo tên, Ẩn/Hiện (`👁`), Khóa/Mở (`🔒`), double-click tên Layer để đổi tên, cùng checklist kiểm duyệt chất lượng trước khi gửi.
- **Floating Zoom HUD**: thu/phóng nhanh ở góc dưới phải, bấm vào `%` để về `100%`, bấm **Vừa màn hình** để tự căn khít vùng làm việc, giữ `Ctrl + Con lăn chuột` để zoom hoặc giữ `Space + Kéo chuột` để trượt (pan) vùng nhìn.

### 2. Chỉnh sửa trực tiếp & Căn chỉnh thông minh
- **Smart Snap Guides**: tự động bắt dính và hiển thị đường gióng khi di chuyển phần tử trùng mép hoặc tâm với Canvas và các phần tử khác (giữ `Alt` khi kéo để tạm tắt bắt dính).
- **Quét chọn nhiều mục (Marquee Selection)**: kéo chuột trên vùng nền trống hoặc giữ `Shift + Click` để chọn nhiều phần tử; hỗ trợ `Ctrl+A` (chọn tất cả), `Ctrl+C` / `Ctrl+V` (sao chép & dán phần tử).
- **Căn chỉnh & Phân bổ (Align & Distribute)**: căn lề trái/giữa/phải/trên/giữa dọc/dưới theo Canvas hoặc theo nhóm đang chọn; chia đều khoảng cách ngang/dọc khi chọn từ 3 phần tử trở lên.
- **Rich-text nâng cao**: double-click vào văn bản và bôi đen cụm từ để mở thanh định dạng nổi (Đậm `B`, Nghiêng `I`, Gạch chân `U`, Đổi màu chữ, Highlight nền vàng, Tăng/Giảm cỡ chữ từng cụm).
- **Sửa trực tiếp trên Widget chỉ số & Bảng biến động**:
  - Double-click trực tiếp vào bất kỳ con số, tiêu đề hoặc dòng thống kê nào trong **Widget chỉ số** (`marketWidget`) và **Bảng biến động** (`indexTable`) ngay trên Canvas để sửa nhanh.
  - Hỗ trợ nút **+ Thêm dòng** / **− Xóa dòng cuối** cho Bảng biến động trong bảng thuộc tính.

### 3. Quy trình Hình ảnh & Biểu đồ
- **Dán thẳng từ Clipboard (`Ctrl+V`)**: chụp màn hình biểu đồ (TradingView, FiinTrade, Vietstock...) và nhấn `Ctrl+V` để dán thẳng vào khung ảnh đang chọn hoặc tạo ảnh mới trên trang.
- **Kéo-thả file ảnh (Drag & Drop)**: kéo file ảnh từ máy tính thả trực tiếp vào khung biểu đồ bất kỳ trên Canvas (hoặc thả file `.json` để mở project).
- **Biến đổi & Cắt ảnh (Crop)**:
  - Kéo góc để phóng/thu đúng tỷ lệ; giữ `Shift` khi kéo góc hoặc tắt **Khóa tỷ lệ** để kéo dãn tự do.
  - Kéo nút vàng để xoay (giữ `Shift` để bắt góc mỗi `15°`).
  - Chọn ảnh rồi bấm **Cắt ảnh**, double-click ảnh có nội dung, hoặc chuột phải chọn **Crop hình** (hỗ trợ tỷ lệ Tự do, 1:1, 4:3, 16:9, 9:16 và thanh trượt zoom).

## Tối ưu hiệu năng
- `html2canvas` tải không chặn luồng (`defer` + lazy-load fallback khi xuất).
- **DOM Selection & Inspector Patching**: chọn phần tử, di chuyển và đổi thuộc tính cập nhật trực tiếp lên node DOM mục tiêu thay vì dựng lại toàn bộ cây DOM.
- **Asset Vault Deduplication**: tách riêng dữ liệu ảnh Base64 và font nhúng khỏi chuỗi JSON của từng bước Undo/Redo, giúp thao tác hoàn tác/làm lại tức thì và tiết kiệm bộ nhớ.
- **IndexedDB Singleton**: tái sử dụng kết nối IndexedDB xuyên suốt phiên làm việc.

## Lưu và khôi phục
- `Ctrl+S` / `Cmd+S` hoặc nút **💾 Lưu** lưu toàn bộ text, ảnh, font và bố cục vào IndexedDB của trình duyệt.
- Hai template có vùng lưu độc lập; hỗ trợ **Lưu file JSON**, **Mở file JSON** và **Xuất HTML** độc lập.

## Chạy local

Có thể mở trực tiếp `app.html`. Để mô phỏng môi trường web:

```powershell
npx -y serve .
```

## Triển khai Vercel

- Import repository vào Vercel và chọn **Other** / không dùng framework.
- Không cần build command.
- `vercel.json` chuyển URL gốc `/` tới `app.html`.
