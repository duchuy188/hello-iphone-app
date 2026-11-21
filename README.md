# Hello iPhone App (React Native + Expo)

Ứng dụng iPhone đơn giản hiển thị màn hình **Hello iPhone!** được viết bằng React Native (Expo) và tích hợp sẵn **GitHub Actions** để tự động build ra file `.ipa` trên máy ảo macOS của GitHub (không cần máy Mac cá nhân).

## 1. Cấu trúc thư mục

- `App.js`: Code giao diện chính của ứng dụng (`Hello iPhone!` kèm nút bấm đếm số).
- `app.json`: Cấu hình tên app, `bundleIdentifier` (`com.example.helloiphone`).
- `package.json`: Khai báo thư viện React, React Native và Expo.
- `.github/workflows/ios-build.yml`: Cấu hình GitHub Actions tự động tạo project Xcode (`expo prebuild`), cài CocoaPods và build ra file `Hello-iPhone-Unsigned.ipa`.

## 2. Chạy thử ngay trên iPhone thật (qua Expo Go)

Nếu muốn test trực tiếp khi đang code trên Windows:
1. Tải ứng dụng **Expo Go** từ App Store trên iPhone.
2. Mở terminal tại thư mục dự án và chạy:
   ```bash
   npm install
   npx expo start
   ```
3. Dùng Camera của iPhone quét mã QR hiện trên màn hình terminal để mở app.

## 3. Hướng dẫn đẩy lên GitHub để lấy file `.ipa`

1. Khởi tạo Git và đẩy code lên GitHub repository của bạn:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Hello iPhone app"
   git branch -M main
   git remote add origin https://github.com/<USERNAME>/<REPO_NAME>.git
   git push -u origin main
   ```
2. Vào tab **Actions** trên GitHub repository của bạn.
3. Chọn workflow **Build iOS App (Unsigned IPA & Simulator)** (sẽ tự động chạy khi bạn push lên nhánh `main`, hoặc bạn có thể bấm nút **Run workflow**).
4. Khi chạy xong (khoảng 5–8 phút), kéo xuống mục **Artifacts** ở cuối trang kết quả workflow để tải file **`Hello-iPhone-Unsigned-IPA`** (`.ipa`) về máy.

> **Lưu ý khi cài file `.ipa` lên iPhone thật:**
> File `.ipa` xuất ra là bản **Unsigned** (chưa ký chứng chỉ Apple trả phí). Bạn có thể dùng các công cụ miễn phí trên Windows như **Sideloadly** hoặc **AltStore** để ký bằng Apple ID cá nhân và cài trực tiếp vào iPhone.
