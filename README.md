# STATVERSE – Hướng dẫn triển khai (bản đầy đủ)

## Các tệp trong dự án
| Tệp | Dùng để làm gì |
|---|---|
| index.html | Toàn bộ website (đưa lên GitHub) |
| netlify.toml | Cấu hình Netlify, link hồ sơ /profile/... và quyền micro, camera (đưa lên GitHub) |
| README.md | Hướng dẫn này (đưa lên GitHub) |
| supabase/schema.sql | Bảng diễn đàn – CHẠY TRONG SUPABASE |
| supabase/schema_friends.sql | Hồ sơ, kết bạn, chat – CHẠY TRONG SUPABASE |
| supabase/schema_update.sql | Cho phép dán ảnh vào bài đăng – CHẠY TRONG SUPABASE |
| supabase/schema_barem.sql | Đề, barem, bài nộp – CHẠY TRONG SUPABASE |

Các tệp .sql KHÔNG chạy trên web. Bạn mở từng tệp, copy toàn bộ nội dung, dán vào Supabase.

## Bước 1 – Supabase (làm 1 lần)
1. Vào https://supabase.com/dashboard, mở project của bạn.
2. Menu trái chọn **SQL Editor → New query**.
3. Lần lượt dán và bấm **Run** theo ĐÚNG thứ tự: schema.sql → schema_friends.sql → schema_update.sql → schema_barem.sql. Mỗi lần dán một tệp.
4. **Authentication → Providers → Email**: tắt "Confirm email" để thử nhanh.
5. Cấp quyền giảng viên: **Authentication → Users**, copy User UID của giảng viên, rồi chạy trong SQL Editor:
   `insert into teachers(user_id) values ('UID-DAN-VAO-DAY');`

## Bước 2 – GitHub
1. https://github.com/new, đặt tên repo (ví dụ statverse), bấm Create.
2. Bấm **uploading an existing file**, kéo vào: `index.html`, `netlify.toml`, `README.md` (3 tệp này nằm ngoài cùng, không để trong thư mục con).
3. Bấm **Commit changes**.

## Bước 3 – Netlify
1. https://app.netlify.com → **Add new site → Import an existing project → GitHub** → chọn repo.
2. Build command: để trống. Publish directory: `.` → **Deploy**.
3. Copy link dạng `https://ten-ban.netlify.app`.
4. Quay lại Supabase: **Authentication → URL Configuration**, dán link vào **Site URL** và **Redirect URLs**, bấm Save.

## Bước 4 – Dùng thử
- Mở link Netlify bằng Chrome hoặc Edge. Dán API key lấy tại https://aistudio.google.com/apikey → Tải danh sách model → Kết nối → Đăng ký.
- Thử từng mục: Giải bài, micro, chụp ảnh đề, Diễn đàn, Bạn bè (cần 2 tài khoản để thử chat), Trò chơi.

## Sửa web về sau
Sửa index.html trên GitHub (Add file → Upload files, ghi đè). Netlify tự cập nhật sau ít phút.

## Lưu ý
- Publishable key của Supabase được phép công khai. KHÔNG dán secret key vào code.
- API key AI Studio của mỗi người chỉ lưu trên trình duyệt của họ.
- Nếu bị giới hạn lượt dùng AI, hãy chọn model khác ở nút ⚙ Model.
