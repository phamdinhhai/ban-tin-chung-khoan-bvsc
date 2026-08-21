# Morning Brief Studio

Công cụ thiết kế và xuất ảnh bản tin chứng khoán buổi sáng, chạy hoàn toàn trên trình duyệt.

## Sử dụng

1. Mở `app.html` hoặc URL Vercel.
2. Chỉnh trực tiếp chữ trên dashboard; bôi đen để đổi đậm, màu hoặc cỡ chữ.
3. Dùng panel phải để chỉnh vị trí, kích thước và thuộc tính phần tử.
4. Hoàn thành checklist **Kiểm tra trước khi gửi**.
5. Nhấn **Xuất PNG** để tạo ảnh 3200 × 1800 px từ canvas 1600 × 900.

## Lưu và khôi phục

- **Lưu bản sửa**: lưu project vào `localStorage` của trình duyệt hiện tại.
- **Lưu JSON**: tải file project để sao lưu hoặc chuyển máy.
- **Xuất HTML đã chỉnh**: tạo một bản HTML độc lập có nhúng project.
- Dữ liệu local có thể mất nếu xóa dữ liệu trình duyệt. Nên tải JSON định kỳ.

## Chạy local

Có thể mở trực tiếp `app.html`. Để mô phỏng môi trường web:

```powershell
npx -y serve .
```

## Triển khai Vercel

- Import thư mục này vào Vercel và chọn **Other** / không dùng framework.
- Không cần build command.
- `vercel.json` chuyển URL gốc `/` tới `app.html`.

## Quyền riêng tư và giới hạn

- Ứng dụng không có backend và không tự gửi nội dung bản tin lên máy chủ.
- Font/ảnh upload được nhúng vào project và có thể làm file JSON/HTML lớn.
- `html2canvas` hiện tải từ jsDelivr; trình duyệt cần truy cập CDN khi mở app lần đầu.
- Nội dung và chiến lược trong dashboard chỉ mang tính tham khảo; người dùng chịu trách nhiệm kiểm tra số liệu, nguồn và tính phù hợp trước khi gửi khách hàng.
