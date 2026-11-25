# Changelog

Mọi thay đổi đáng kể của skill ghi ở đây. Định dạng theo [Keep a Changelog](https://keepachangelog.com/vi/1.1.0/), phiên bản theo [SemVer](https://semver.org/lang/vi/).

## [Unreleased]

## [1.0.0] - 2026-11-25

### Added

- Tách thành repo độc lập (microservice skill): `skill.json` khai báo hợp đồng giao tiếp và skill phụ thuộc, CI kiểm tính nhất quán, Release tự đóng zip.
- Ẩn danh hoá: bỏ tham chiếu tới dự án áp dụng cụ thể; skill dùng được cho mọi dự án.

### Lịch sử trước khi tách repo

- Cập nhật 20/11/2026 (phương án C): đặc tả bỏ dòng Tác nhân (UC × vai trò ở RTM); §7 bỏ bảng tổng hợp (chép lại «Chờ xác nhận», mức sẵn sàng).
- Cập nhật 20/11/2026: tài liệu TL-03 chỉ giữ định nghĩa — liên kết BR ↔ REQ và độ phủ REQ loại BR thuộc RTM TL-04 (D10_BR, D04_REQ); thêm `shared_rules.req_as_rule`; JSON khác giữ nguyên.
