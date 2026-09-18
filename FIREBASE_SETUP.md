# V2 Online – bước kết nối Firebase

Website đã được chuẩn bị để chuyển sang đồng bộ nhiều thiết bị. Cần tạo Firebase project một lần.

1. Mở https://console.firebase.google.com/ và tạo project, ví dụ `family-study-dashboard`.
2. Project Overview → Add app → chọn Web (`</>`) → đặt tên `Family Study Dashboard`.
3. Firebase sẽ hiện object `firebaseConfig`. Chỉ gửi object này cho ChatGPT; KHÔNG gửi service-account private key.
4. Build → Authentication → Sign-in method → bật Email/Password.
5. Build → Firestore Database → Create database → chọn Production mode.
6. Firestore → Rules: dùng nội dung file `firestore.rules`.
7. Tạo 3 tài khoản Authentication: bố/mẹ, học sinh lớp 6, học sinh lớp 3.
8. Sau khi có UID của 3 tài khoản, tạo collection `users` với document ID đúng UID:
   - bố/mẹ: `{ "role": "parent" }`
   - lớp 6: `{ "role": "child", "child": "6" }`
   - lớp 3: `{ "role": "child", "child": "3" }`

Sau khi người dùng gửi firebaseConfig và 3 UID (không cần gửi mật khẩu), ChatGPT sẽ hoàn thiện index.html để đăng nhập và đồng bộ realtime.

Lưu ý: Firebase khuyến nghị dùng Authentication + Firestore Security Rules để bảo vệ dữ liệu web. Không dùng rule allow read, write: if true.
