# XSMB Predictor - iOS unsigned IPA

Đây là dự án iOS bọc `4cang.html` bằng WKWebView, không phải trình duyệt Safari shortcut.

## Tạo IPA bằng GitHub Actions (không cần Mac)
1. Tạo repository GitHub riêng (ví dụ `XSMB-iOS`) và upload **toàn bộ nội dung trong thư mục này**, giữ nguyên `.github/workflows/build-ipa.yml`.
2. Vào tab `Actions` > `Build XSMB Unsigned IPA` > `Run workflow` (hoặc chờ job tự chạy sau push vào `main`).
3. Khi build thành công, mở lượt chạy > mục `Artifacts` > `XSMBPredictor-Unsigned-IPA`.
4. Tải ZIP artifact, giải nén lấy `XSMBPredictor-unsigned.ipa`.
5. Dùng công cụ/chứng chỉ phù hợp để **ký lại** rồi cài iPhone. IPA này *không có chữ ký*, không thể cài ngay.

## Lưu ý
- Build dùng GitHub-hosted macOS + XcodeGen, chưa được kiểm chứng chạy thực tế trên iOS 27.
- Workflow cần internet lúc build để tải Tailwind và Chart.js, sau đó nhúng file JS vào IPA. Ứng dụng không cần mạng để tải hai thư viện này sau khi cài.
- Số liệu KQXS trong HTML vốn là mẫu/lịch sử; không có tính năng lấy dữ liệu mới tự động qua API trong bản này. Nhập dữ liệu vào tab Sổ Kết Quả.
- Dữ liệu người dùng lưu bằng localStorage của WKWebView, có thể mất khi xóa/cài lại ứng dụng.
- Nguồn gốc `4cang.html` giữ nguyên thuật toán; đây là bản đóng gói, không khẳng định độ chính xác dự đoán.
- Không thêm WebExtension hoặc quyền đặc biệt; bundle ID: `com.huang9933.xsmbpredictor`.
