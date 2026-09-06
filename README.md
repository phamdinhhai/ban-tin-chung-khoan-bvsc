# BVSC Report Studio

Studio thiết kế báo cáo chứng khoán chạy hoàn toàn trên trình duyệt, gồm hai mẫu:

- **Bản tin sáng**: tổng quan thị trường, tin tức, nội dung và chiến lược trong ngày.
- **Báo cáo chiến lược**: biến động chỉ số, biểu đồ, chiến lược tuần và tin tức nổi bật.

## Sử dụng

1. Mở `app.html` hoặc URL Vercel.
2. Chọn **Bản tin sáng** hoặc **Báo cáo chiến lược**.
3. Click phần tử để chọn; double-click text, tiêu đề bảng hoặc từng ô bảng để sửa trực tiếp.
4. Trong bảng, nhấn `Enter`/click ra ngoài để lưu ô hoặc `Escape` để hủy.
5. Kéo phần tử hoặc các cạnh/góc để thay đổi vị trí và kích thước.
6. Nhấn **+ Ảnh** để đặt ảnh tự do trực tiếp lên trang; ảnh mới giữ đúng tỷ lệ và không bị crop.
7. Với ảnh tự do: kéo góc để phóng/thu đúng tỷ lệ; giữ `Shift` khi kéo góc hoặc tắt **Khóa tỷ lệ** để kéo dãn.
8. Kéo nút vàng để xoay; dùng panel phải để lật ngang, lật dọc, khôi phục tỷ lệ hoặc kích thước gốc.
9. Dùng panel phải để chỉnh nội dung, hình thức và geometry chính xác.
10. Nhấn **Xuất PNG** khi hoàn tất.

## Báo cáo chiến lược

- **Bảng biến động**: double-click tiêu đề hoặc từng ô để sửa trực tiếp; cũng có thể nhập nhiều dòng trong panel phải theo định dạng
  `CHỈ SỐ | ĐÓNG CỬA | THAY ĐỔI | % THAY ĐỔI`.
- Giá trị có dấu `+` tự hiển thị xanh; dấu `-` tự hiển thị đỏ sau khi hoàn tất sửa ô.
- Template có ba **khung ảnh**: một biểu đồ VNINDEX và hai biểu đồ khối ngoại.
- Double-click khung ảnh hoặc chọn **Thay ảnh** trong Thuộc tính để tải ảnh; frame hỗ trợ Cover, Contain và Fill.
- **Xóa ảnh trong khung** đưa slot về trạng thái chờ upload.
- Ảnh tạo bằng **+ Ảnh** là ảnh tự do, có thể chuyển sang chế độ Trong khung và ngược lại mà không mất dữ liệu ảnh.
- Các trạng thái khóa tỷ lệ, xoay, lật, kích thước và chế độ ảnh được lưu trong IndexedDB, JSON và HTML.
- Khoảng ngày tự tạo theo tuần làm việc thứ Hai–thứ Sáu và vẫn sửa được như text.

## Lưu và khôi phục

- `Ctrl+S` / `Cmd+S` hoặc **Lưu bản sửa** lưu toàn bộ text, ảnh, font và bố cục vào IndexedDB của trình duyệt.
- Hai template có vùng lưu riêng, không ghi đè lẫn nhau; bản lưu cũ trong `localStorage` được tự động chuyển đổi.
- Nút Back của trình duyệt từ editor quay về màn hình chọn mẫu; Forward mở lại template.
- **Lưu JSON** tải project để sao lưu hoặc chuyển máy.
- **Xuất HTML đã chỉnh** tạo file độc lập có payload được escape an toàn và có thể mở, sửa, xuất lại.
- Màn hình chọn mẫu hiển thị khi template đã có bản lưu trên trình duyệt.

## Kích thước xuất

- PNG được render ở độ phân giải 2×, crop theo khung nội dung và luôn có nền đặc, không còn pixel trong suốt bị hiển thị thành đen.
- Với template phủ kín canvas, Bản tin sáng xuất `3200 × 2000px`; Báo cáo chiến lược xuất `3200 × 1800px`.

## Chạy local

Có thể mở trực tiếp `app.html`. Để mô phỏng môi trường web:

```powershell
npx -y serve .
```

## Triển khai Vercel

- Import repository vào Vercel và chọn **Other** / không dùng framework.
- Không cần build command.
- `vercel.json` chuyển URL gốc `/` tới `app.html`.

## Quyền riêng tư và giới hạn

- Ứng dụng không có backend và không tự gửi nội dung lên máy chủ.
- Bản lưu IndexedDB gắn với đúng trình duyệt và domain hiện tại; hãy dùng JSON/HTML để chuyển máy hoặc sao lưu ngoài trình duyệt.
- Font/ảnh upload được nhúng vào project nên bản lưu và file JSON/HTML có thể lớn.
- Nếu trình duyệt chặn IndexedDB hoặc hết dung lượng, ứng dụng sẽ báo lỗi thay vì báo lưu thành công.
- `html2canvas` tải từ jsDelivr; cần truy cập CDN khi mở ứng dụng lần đầu.
- Nội dung và chiến lược chỉ mang tính tham khảo; người dùng chịu trách nhiệm kiểm tra số liệu và nguồn trước khi gửi khách hàng.
