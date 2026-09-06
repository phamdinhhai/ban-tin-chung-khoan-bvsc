# BVSC Report Studio

Studio thiết kế báo cáo chứng khoán chạy hoàn toàn trên trình duyệt, gồm hai mẫu:

- **Bản tin sáng**: tổng quan thị trường, tin tức, nội dung và chiến lược trong ngày.
- **Báo cáo chiến lược**: biến động chỉ số, biểu đồ, chiến lược tuần và tin tức nổi bật.

## Sử dụng

1. Mở `app.html` hoặc URL Vercel.
2. Chọn **Bản tin sáng** hoặc **Báo cáo chiến lược**.
3. Click phần tử để chọn; double-click text để sửa trực tiếp.
4. Kéo phần tử hoặc các cạnh/góc để thay đổi vị trí và kích thước.
5. Dùng panel phải để chỉnh nội dung, hình thức và geometry chính xác.
6. Nhấn **Xuất PNG** khi hoàn tất.

## Báo cáo chiến lược

- **Bảng biến động**: nhập mỗi dòng theo định dạng
  `CHỈ SỐ | ĐÓNG CỬA | THAY ĐỔI | % THAY ĐỔI`.
- Giá trị có dấu `+` tự hiển thị xanh; dấu `-` tự hiển thị đỏ.
- Template có ba khung ảnh: một biểu đồ VNINDEX và hai biểu đồ khối ngoại.
- Double-click khung ảnh hoặc chọn **Thay ảnh** trong Thuộc tính để tải ảnh.
- **Xóa ảnh trong khung** đưa slot về trạng thái chờ upload.
- Khoảng ngày tự tạo theo tuần làm việc thứ Hai–thứ Sáu và vẫn sửa được như text.

## Lưu và khôi phục

- `Ctrl+S` / `Cmd+S` hoặc **Lưu bản sửa** lưu vào trình duyệt.
- Hai template có vùng lưu riêng, không ghi đè lẫn nhau.
- **Lưu JSON** tải project để sao lưu hoặc chuyển máy.
- **Xuất HTML đã chỉnh** tạo file độc lập có thể mở, sửa và xuất lại nhiều vòng.
- Màn hình chọn mẫu hiển thị khi template đã có bản lưu trên trình duyệt.

## Kích thước xuất

- Bản tin sáng: canvas `1600 × 1000px`, PNG `3200 × 2000px`.
- Báo cáo chiến lược: canvas `1600 × 900px`, PNG `3200 × 1800px`.

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
- Font/ảnh upload được nhúng vào project nên file JSON/HTML có thể lớn.
- `html2canvas` tải từ jsDelivr; cần truy cập CDN khi mở ứng dụng lần đầu.
- Nội dung và chiến lược chỉ mang tính tham khảo; người dùng chịu trách nhiệm kiểm tra số liệu và nguồn trước khi gửi khách hàng.
