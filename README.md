# PminMod / WebForFun

Một dự án **web tĩnh giải trí** được xây dựng theo phong cách gaming neon tối màu, tập trung vào việc trưng bày nội dung mod, video, ảnh và các trang phụ mở rộng như dịch vụ cày thuê, gallery ảnh và kho skin.

## Giới thiệu

Đây là một website cá nhân theo hướng **nhẹ, dễ chỉnh sửa, dễ deploy**, phù hợp để chạy trên **GitHub Pages** hoặc các nền tảng host static khác mà không cần VPS riêng.

Mục tiêu của dự án là tạo ra một trang web:
- Có giao diện nổi bật, đậm chất game
- Dễ thêm nội dung mới chỉ bằng cách sửa file JSON
- Tách riêng từng khu nội dung để quản lý đơn giản
- Có thể mở rộng thêm các page phụ mà không cần backend phức tạp

## Điểm nổi bật

- Giao diện nền tối, hiệu ứng glow hồng tím, phù hợp phong cách gaming
- Trang chủ hiển thị danh sách nội dung theo danh mục
- Dữ liệu bài viết/mod đọc từ `data.json`
- Điều hướng phụ đọc từ `config.json`
- Hỗ trợ popup giới thiệu / banner / TikTok Shop từ file cấu hình
- Có trang chi tiết tải nội dung riêng (`download.html`)
- Có trang phụ như:
  - `gi/caythue.html`: dịch vụ cày thuê Genshin Impact
  - `ai/gallery.html`: gallery ảnh
  - `lq/skin-gallery.html`: kho ảnh nền / skin Liên Quân
- Dễ tuỳ biến giao diện bằng CSS riêng cho từng khu

## Cấu trúc thư mục

```text
WebForFun-main/
├─ index.html
├─ download.html
├─ config.json
├─ data.json
├─ cmt.json
│
├─ style/
│  ├─ download.css
│  └─ page-template.css
│
├─ gi/
│  ├─ caythue.html
│  └─ style/
│     ├─ caythue.css
│     ├─ diff5.png
│     └─ page-template.css
│
├─ ai/
│  ├─ gallery.html
│  ├─ images.json
│  ├─ src/
│  └─ style/
│     └─ src-gallery.css
│
└─ lq/
   ├─ skin-gallery.html
   ├─ skin-detail.html
   ├─ skins.json
   └─ style/
      ├─ skin-gallery.css
      └─ skin-detail.css
```

## Cách hoạt động

### 1. Trang chủ
`index.html` là trung tâm của toàn bộ website. Trang này sẽ:
- đọc dữ liệu từ `data.json`
- chia nội dung theo danh mục như `mod-lẻ`, `mod-pack`, `mod-reup`
- render card nội dung để người dùng xem trước
- dẫn sang trang chi tiết hoặc trang tải

### 2. Cấu hình mở rộng
`config.json` dùng để cấu hình các phần như:
- danh mục hiển thị
- liên kết phụ bên sidebar/menu
- popup quảng bá hoặc banner giới thiệu

Nhờ đó, bạn có thể thay đổi nhiều phần của web mà không cần sửa sâu vào mã HTML.

### 3. Trang chi tiết / tải nội dung
`download.html` dùng để hiển thị thông tin chi tiết hơn cho từng mục nội dung, ví dụ:
- tên bài
- video preview
- link tải file
- khu bình luận giả lập từ `cmt.json`

### 4. Các page phụ
Ngoài phần mod chính, project còn có những page riêng để mở rộng thương hiệu cá nhân và nội dung:
- trang cày thuê
- gallery ảnh
- gallery skin / ảnh nền game

## Tuỳ chỉnh nội dung

### Sửa danh sách mod / bài đăng
Chỉnh trong file `data.json` theo mẫu:

```json
{
  "key": "mod-001",
  "category": "mod-lẻ",
  "tiêu đề": "Tên nội dung",
  "link video youtube": "https://...",
  "link tải file": "https://...",
  "thumbnail": "https://..."
}
```

### Sửa menu / link phụ / popup
Chỉnh trong `config.json`.

Ví dụ bạn có thể sửa:
- nhãn menu phụ
- đường dẫn sang trang riêng
- ảnh banner popup
- link TikTok Shop / link quảng bá

### Sửa comment hiển thị
Chỉnh trong `cmt.json` để thay đổi dữ liệu bình luận hiển thị ở trang tải.

## Công nghệ sử dụng

- **HTML5**
- **CSS3**
- **JavaScript thuần**
- **JSON** để quản lý dữ liệu
- Có thể deploy bằng **GitHub Pages**

Dự án không phụ thuộc framework nặng, nên rất phù hợp với kiểu web cá nhân nhỏ gọn, dễ sửa trực tiếp bằng VS Code.

## Cách chạy local

Bạn có thể mở nhanh bằng một local server đơn giản.

### Dùng Python

```bash
python -m http.server 8000
```

Sau đó mở trình duyệt tại:

```text
http://localhost:8000
```

> Nên dùng local server thay vì mở file HTML trực tiếp để tránh lỗi đường dẫn hoặc lỗi khi fetch JSON.

## Deploy lên GitHub Pages

1. Đẩy toàn bộ project lên GitHub Repository
2. Vào **Settings > Pages**
3. Chọn branch chứa source chính, thường là `main`
4. Chọn thư mục root
5. Lưu lại và chờ GitHub Pages build

Sau khi deploy xong, website sẽ chạy hoàn toàn dưới dạng static.

## Định hướng mở rộng

Một số hướng nâng cấp tiếp theo cho project:
- thêm nút chia sẻ / QR code cho từng trang
- thêm chế độ lọc, tìm kiếm nhanh
- thêm lazy load cho ảnh/video
- thêm dark/light mode hoặc theme switch
- cải thiện giao diện mobile
- tách dữ liệu theo từng chuyên mục riêng để dễ quản lý hơn
- bổ sung SEO meta cơ bản cho từng page

## Phù hợp với ai?

Dự án này phù hợp cho:
- web giới thiệu mod/game cá nhân
- landing page nội dung giải trí
- trang tổng hợp video, ảnh, tài nguyên tải về
- web showcase nhỏ gọn không cần backend

## Ghi chú

Đây là project thiên về **trình bày nội dung và trải nghiệm giao diện**, nên ưu tiên:
- dễ sửa
- dễ thêm nội dung
- dễ triển khai
- dễ mở rộng theo nhu cầu cá nhân

Nếu bạn muốn tiếp tục phát triển lâu dài, có thể bổ sung backend sau, nhưng với bản hiện tại thì static site đã đủ để vận hành ổn định cho nhu cầu cơ bản.

---

**PminMod / WebForFun**

Một góc web giải trí mang phong cách cá nhân: gọn, đẹp, dễ chỉnh và đậm chất game.
