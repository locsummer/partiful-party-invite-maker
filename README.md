# Partiful Party Invite & Poster Maker (Native iOS & Native Android)

Dự án phát triển ứng dụng di động Native riêng biệt cho cả hai nền tảng iOS (Swift + SwiftUI) và Android (Kotlin + Jetpack Compose) theo phong cách thiết kế hiện đại của Partiful.

---

## 1. Tổng quan Kiến trúc

```
partiful-party-invite-maker/
├── ios/                 # Source code Native iOS (Swift, SwiftUI, MVVM, PhotosUI, EventKit, PDFKit)
├── android/             # Source code Native Android (Kotlin, Jetpack Compose, MVVM, Photo Picker, Calendar)
└── README.md
```

## 2. Ba Nhóm Chức Năng Cốt Lõi Đã Hoàn Thành

### Module 1: Thiết kế thiệp / Poster tiệc
- **11 Danh mục mẫu thiệp phong phú:** Sinh nhật (Birthday), Tiệc cưới (Wedding), Tốt nghiệp (Graduation), Halloween, Giáng sinh (Christmas), Năm mới (New Year), Âm nhạc (Music), Ngoài trời (Outdoor), Họp mặt bạn bè (Friends), Khai trương (Grand Opening), Tiệc riêng tư (Private Party).
- **Chỉnh sửa hình ảnh:** Chọn ảnh từ thư viện (PhotosUI / Photo Picker), thay đổi kích thước, phóng to, thu nhỏ, xoay, di chuyển, bộ lọc màu (Neon, Vintage, B&W, Normal), điều chỉnh độ sáng, độ tương phản, độ bão hòa, blur, vignette.
- **Chỉnh sửa văn bản (Typography):** Thêm nhiều layer text, chỉnh sửa nội dung, mẫu câu có sẵn ("YOU ARE INVITED", "HAPPY BIRTHDAY", "LET'S PARTY", "SAVE THE DATE"...), đổi font, cỡ chữ, bảng màu neon, căn chỉnh lề (trái, giữa, phải), in đậm/nghiêng, khoảng cách chữ (tracking), bóng chữ.
- **Sticker & Hiệu ứng:** Thư viện sticker đa dạng (Bánh kem, bóng bay, ly rượu, pháo hoa, nốt nhạc, ngôi sao, trái tim, mũ tốt nghiệp...), điều chỉnh kích thước, xoay, hiệu ứng phát sáng neon (glow effect).
- **Công cụ Editor đa lớp:** Hệ thống Layer z-index, Undo / Redo theo mẫu Memento (lưu tới 30 trạng thái), nhân bản layer, đưa lên trước/xuống sau, khóa layer, tự động lưu bản nháp và khôi phục khi mở lại app.

### Module 2: Xuất và Chia sẻ thiệp
- **Xuất ảnh:** Hỗ trợ PNG (lossless không nén) và JPG (với thanh trượt chất lượng nén 60-100%). Cho phép chọn độ phân giải 1x (Chuẩn 1080p), 2x (HD 4K sắc nét), 3x (Chất lượng in ấn 300 DPI). Giữ đúng bố cục, không mất font, không lệch vị trí text, không mất sticker, ẩn hoàn toàn các thanh công cụ editor khi render.
- **Xuất PDF:** Xuất thiệp thành file PDF vector chuẩn in ấn (300 DPI), giữ nguyên tỷ lệ khung hình.
- **Chia sẻ thủ công:** Mở bảng chia sẻ Native của hệ điều hành (UIActivityViewController trên iOS, Sharesheet Intent trên Android) để gửi trực tiếp qua Zalo, Messenger, SMS, Email...

### Module 3: Lưu sự kiện vào lịch cá nhân
- **Thông tin sự kiện:** Tên sự kiện, địa điểm, mô tả, ngày giờ bắt đầu, ngày giờ kết thúc, ghi chú thêm.
- **iOS:** Tích hợp `EventKit` (`EKEventStore`), lưu vào Apple Calendar và tạo lời nhắc trong Apple Reminders.
- **Android:** Tích hợp `CalendarContract.Events` qua Intent an toàn hoặc Calendar Provider, hỗ trợ thông báo nhắc nhở trước giờ tiệc.
- **Xử lý quyền hệ điều hành:** Kiểm tra quyền, thông báo rõ ràng khi bị từ chối, chuyển hướng màn hình xác nhận trực quan.

## 3. Bản đồ 18 Màn hình hoàn chỉnh
1. Splash Screen
2. Onboarding Screen (3 slides)
3. Home Screen
4. Thư viện mẫu thiệp (Templates Library)
5. Chi tiết mẫu thiệp (Template Detail)
6. Photo Picker (Chọn ảnh)
7. Trình chỉnh sửa thiệp (Card Editor Workspace)
8. Công cụ chỉnh sửa văn bản (Text Editor Bottom Sheet)
9. Thư viện sticker (Sticker Picker Bottom Sheet)
10. Bộ lọc và hiệu ứng (Filter Adjustment Sheet)
11. Màn hình xem trước thiệp sạch (Preview Screen)
12. Màn hình xuất ảnh PNG/JPG (Export Options)
13. Màn hình xuất PDF (PDF Export)
14. Màn hình chia sẻ (Native Sharesheet)
15. Màn hình nhập thông tin sự kiện (Event Details Form)
16. Màn hình xác nhận thêm lịch (Calendar Confirmation)
17. Màn hình quản lý bản thiết kế đã lưu (Saved Projects / Drafts)
18. Settings (Cài đặt)
