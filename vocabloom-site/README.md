# VocaBloom

Web học từ vựng tiếng Anh — React + Vite. Không cần đăng nhập — dữ liệu lưu ngay trên trình duyệt.

## 1. Chạy thử trên máy (local)

Cần cài **Node.js** (bản 18 trở lên) trước: https://nodejs.org

```bash
cd vocabloom-site
npm install
npm run dev
```

Mở trình duyệt vào địa chỉ hiện lên trong terminal (thường là `http://localhost:5173`).

## 2. Đưa lên internet — cách đáng tin cậy nhất: Vercel CLI

Việc kéo-thả file lên GitHub rất dễ bị lỗi (thiếu file, sai cấu trúc thư mục, lỡ tay tải nguyên file .zip lên...). Cách chắc chắn nhất, ít bước nhất, và đúng 100% cấu trúc là deploy thẳng từ máy bạn lên Vercel bằng dòng lệnh — không cần qua GitHub.

Trong terminal, tại đúng thư mục `vocabloom-site` (đã chạy `npm install` ở bước 1):

```bash
npx vercel login
```
→ Làm theo hướng dẫn (nhập email, Vercel gửi link xác nhận, bấm vào link đó).

```bash
npx vercel --prod
```
→ Trả lời các câu hỏi:
- "Set up and deploy?" → gõ `y`
- "Which scope?" → chọn tài khoản của bạn (Enter)
- "Link to existing project?" → gõ `N`
- "What's your project's name?" → Enter để giữ mặc định (`vocabloom-site`)
- "In which directory is your code located?" → Enter để giữ mặc định (`./`)
- Các câu còn lại → cứ Enter để giữ mặc định

Đợi khoảng 30–60 giây, Vercel sẽ in ra một đường link dạng `https://vocabloom-site-xxxx.vercel.app` — đó là website thật của bạn.

**Muốn cập nhật sau này:** mỗi khi sửa code xong, chạy lại đúng lệnh `npx vercel --prod` trong thư mục đó là web tự cập nhật.

### Nếu vẫn muốn dùng GitHub + Vercel (tự động deploy mỗi khi sửa code)
Vào repo GitHub, kiểm tra chắc chắn các file `package.json`, `index.html`, `vite.config.js`, `vercel.json` và thư mục `src/` (chứa `App.jsx`, `main.jsx`) nằm **ngay tại gốc repo** — không bị lồng thêm một cấp thư mục `vocabloom-site/` nào nữa, và không có file `.zip` nào còn sót lại trong repo. Nếu cấu trúc đúng, import vào Vercel như bình thường (Add New → Project → chọn repo → Deploy).

## 3. Lưu ý quan trọng

- **Lưu dữ liệu:** dữ liệu lưu trong `localStorage` của trình duyệt — lưu lại khi refresh, nhưng không đồng bộ giữa các thiết bị, và mất nếu người dùng xoá dữ liệu duyệt web.
- **Phát âm** dùng công nghệ có sẵn của trình duyệt (Web Speech API), không cần backend.
- **Import Excel** chạy hoàn toàn phía trình duyệt, không upload file lên server nào.
- File `vercel.json` đã cấu hình sẵn build command/output directory rõ ràng, tránh việc Vercel đoán sai cấu hình.

## 4. Các tính năng mới (bản cập nhật gần nhất)

- **Xóa từ vựng/idiom/collocation** trực tiếp từ bảng My Vocabulary hoặc từ màn chi tiết.
- **Thêm thủ công** cả 3 loại (Vocabulary / Idiom / Collocation) — không cần Excel.
- **Import bằng Excel cho cả 3 loại** — vào "Import Vocabulary", chọn tab loại tương ứng, tải template riêng ở "Excel Template".
- **Đánh giá Again/Hard/Good/Easy** giờ được lưu lại trên từng từ (không chỉ dùng một lần khi ôn thẻ). Bạn có thể:
  - Tự chọn mức đánh giá trực tiếp trong bảng My Vocabulary (cột Grade) hoặc trong màn chi tiết từ.
  - Lọc theo mức đánh giá này ở My Vocabulary ("All grades") và ở Practice ("Difficulty": Hard/Good/Easy).
  - Ôn tập riêng theo từng mức trong Flashcards ("Marked Hard/Good/Easy" — có sẵn trong danh sách bộ thẻ).
- **Practice — chọn từ tùy ý:** ở mục "What do you want to practice?", chọn "Choose specific words" để tự tick chọn đúng những từ muốn ôn, thay vì để hệ thống chọn ngẫu nhiên.
