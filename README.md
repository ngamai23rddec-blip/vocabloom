# VocaBloom

Web học từ vựng tiếng Anh — React + Vite.

## 1. Chạy thử trên máy (local)

Cần cài **Node.js** (bản 18 trở lên) trước: https://nodejs.org

```bash
cd vocabloom-site
npm install
npm run dev
```

Mở trình duyệt vào địa chỉ hiện lên trong terminal (thường là `http://localhost:5173`).

## 2. Đưa lên internet (deploy) — chọn 1 trong các cách sau

### Cách dễ nhất: Vercel (miễn phí)
1. Vào https://vercel.com, đăng nhập bằng GitHub/Google.
2. Đẩy thư mục `vocabloom-site` lên một repo GitHub (hoặc dùng lệnh `vercel` từ Vercel CLI: `npx vercel`).
3. Chọn "Import Project" → chọn repo đó. Vercel tự nhận ra đây là project Vite/React, chỉ cần bấm Deploy.
4. Sau ~1 phút bạn sẽ có link dạng `vocabloom.vercel.app`.

### Cách 2: Netlify (miễn phí, kéo-thả)
1. Chạy `npm run build` để tạo thư mục `dist/`.
2. Vào https://app.netlify.com/drop, kéo thả thư mục `dist` vào đó.
3. Netlify cho ngay một link công khai.

### Cách 3: GitHub Pages
1. `npm run build` để tạo `dist/`.
2. Đẩy nội dung `dist/` lên nhánh `gh-pages` của repo GitHub (có thể dùng gói `gh-pages`: `npm i -D gh-pages`, thêm script `"deploy": "gh-pages -d dist"` vào `package.json`, rồi chạy `npm run deploy`).
3. Bật GitHub Pages trong Settings → Pages, chọn nhánh `gh-pages`.

## 3. Lưu ý quan trọng

- **Dữ liệu người dùng** (từ vựng đã thêm, tiến độ học, thống kê) được lưu trong `localStorage` của trình duyệt. Nghĩa là:
  - Dữ liệu **lưu lại** khi tải lại trang (refresh).
  - Dữ liệu **không đồng bộ** giữa các thiết bị/trình duyệt khác nhau — mỗi trình duyệt có một bản riêng.
  - Nếu người dùng xóa dữ liệu duyệt web (clear browsing data) thì dữ liệu VocaBloom cũng mất.
  - Muốn nhiều người dùng có tài khoản riêng và đồng bộ nhiều thiết bị, cần thêm một backend thật (ví dụ Firebase, Supabase, hoặc server + database riêng) — đây là bước nâng cấp sau này, không có trong bản hiện tại.
- **Phát âm** dùng công nghệ có sẵn của trình duyệt (Web Speech API), không cần backend, nhưng chất lượng giọng đọc phụ thuộc vào trình duyệt/hệ điều hành của người dùng.
- **Import Excel** dùng thư viện SheetJS (`xlsx`), chạy hoàn toàn phía trình duyệt (client-side), không cần upload file lên server nào cả.
