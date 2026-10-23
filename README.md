# NgheNhac (bản web) — nghe nhạc trên iPhone bằng Safari

Web app cài được ra màn hình chính iPhone giống app thật. Không cần máy Mac, không cần Xcode, không phải cài lại mỗi 7 ngày.

## App có gì

| Tab | Dùng để |
|---|---|
| **Khám phá** | Nghe nhạc miễn phí, hợp pháp từ Jamendo: thịnh hành, tìm kiếm, thể loại (có mục *Việt Nam*) |
| **Thư viện** | Thêm file MP3/M4A từ iPhone; tạo danh sách phát (vd “Nhạc Việt chill”), *Bài hát đã thích*, trộn bài |
| **Spotify** | Dán link playlist/album/nghệ sĩ Spotify (vd các playlist nhạc Việt) để xem và nghe ngay trong app |
| **Cài đặt** | Nhập Jamendo Client ID, xem dung lượng đã dùng |

Thêm nữa: **phát nền khi khoá màn hình**, điều khiển ở màn hình khoá / Control Center / tai nghe, màn hình “Đang phát” có tua bài, lặp lại, trộn bài, danh sách chờ, phát tiếp theo. Ảnh bìa và tên bài tự đọc từ file MP3.

## Về nhạc Việt “giống Spotify”

Spotify, Zing MP3, NhacCuaTui… **không cho phép** app khác phát trực tiếp kho nhạc của họ (nhạc có bản quyền). Vì vậy NgheNhac dùng 2 cách hợp lệ:

1. **Tab Spotify** – nhúng trình phát chính thức của Spotify. Hiện đầy đủ danh sách bài như trên Spotify.
   - Nếu đã đăng nhập Spotify trong Safari: nghe được trọn bài (tài khoản Premium nghe ổn định nhất); chưa đăng nhập thì chỉ nghe thử 30 giây.
   - Trình phát nhúng **không nghe nền** được khi khoá màn hình — lúc đó bấm biểu tượng ↗ để mở trong app Spotify.
   - Lấy link: trong app Spotify mở playlist → **⋯** → **Chia sẻ** → **Sao chép liên kết** → dán vào tab Spotify.
2. **Thư viện (nhạc trên máy)** – thêm các file nhạc Việt bạn có (nhạc đã mua, file trong iCloud Drive/Tệp). Phần này **nghe nền, nghe offline** và có đủ tính năng danh sách phát như Spotify.

## Bước 1 — Lấy Jamendo Client ID (miễn phí, 2 phút)

1. Vào https://devportal.jamendo.com → **Sign up** và đăng nhập.
2. Chọn **My Applications** → **Create a new app**. Tên tuỳ ý (vd `NgheNhac`), website có thể điền địa chỉ trang của bạn ở bước 2.
3. Sao chép **Client ID**. (Tab Spotify và Thư viện vẫn dùng được khi chưa có ID.)

## Bước 2 — Đưa app lên mạng (miễn phí)

App phải nằm trên một địa chỉ **https** thì iPhone mới cài và phát nền được. Chọn 1 trong 2 cách:

### Cách A: Netlify Drop (dễ nhất, kéo-thả)
1. Giải nén `NgheNhacWeb.zip` trên máy tính → được thư mục `NgheNhacWeb`.
2. Vào https://app.netlify.com/drop, **đăng ký tài khoản miễn phí** (nếu không có tài khoản, trang sẽ bị xoá sau 1 giờ).
3. Kéo **cả thư mục** `NgheNhacWeb` thả vào trang. Chờ vài giây → Netlify cho bạn một link dạng `https://ten-ngau-nhien.netlify.app`.
4. (Tuỳ chọn) *Site configuration → Change site name* để đổi thành `https://nghenhac-cua-ban.netlify.app`.

### Cách B: GitHub Pages
1. Tạo repository mới trên https://github.com (vd `nghenhac`), chọn **Public**.
2. **Add file → Upload files** → kéo toàn bộ nội dung trong thư mục `NgheNhacWeb` (gồm `index.html`, `sw.js`, `manifest.webmanifest`, thư mục `icons`) → **Commit**.
3. **Settings → Pages** → *Source*: **Deploy from a branch**, branch `main`, thư mục `/ (root)` → **Save**.
4. Sau ~1 phút, app ở `https://<tên-github>.github.io/nghenhac/`.

> Cập nhật app sau này: tải lại file mới lên chỗ cũ (Netlify: *Deploys* → kéo thả thư mục mới).

## Bước 3 — Cài lên iPhone

1. Mở link của bạn bằng **Safari** (không dùng Chrome/Zalo/Facebook).
2. Bấm nút **Chia sẻ** (ô vuông có mũi tên lên) → **Thêm vào MH chính** → **Thêm**.
3. Mở **NgheNhac** từ biểu tượng mới trên màn hình chính.
4. Tab **Cài đặt** → dán Jamendo Client ID → **Lưu và kiểm tra**.
5. Tab **Thư viện** → **Thêm nhạc từ iPhone** để chọn file nhạc Việt của bạn.

> Nên luôn mở app từ màn hình chính: iOS giữ nhạc trên máy lâu dài cho web app đã cài, còn khi mở trong tab Safari thường, dữ liệu có thể bị iOS xoá nếu lâu không dùng.

## Lưu ý & mẹo

- **Phát nền:** nhạc từ Jamendo và nhạc trên máy tiếp tục phát khi khoá màn hình hoặc chuyển app. Trường hợp hiếm iOS dừng nhạc khi tự chuyển bài lúc màn hình đang khoá — bấm Phát ở màn hình khoá là tiếp tục.
- **Dung lượng:** mỗi bài MP3 ~3–10 MB. iPhone cho web app dùng khá nhiều dung lượng (thường vài GB); xem trong tab Cài đặt.
- **Xoá dữ liệu Safari** (Cài đặt → Safari → Xoá lịch sử và dữ liệu) sẽ xoá cả nhạc đã thêm; giữ file gốc trong ứng dụng Tệp.
- Jamendo miễn phí cho **mục đích cá nhân, phi thương mại**.

## Cấu trúc thư mục

```
NgheNhacWeb/
├── index.html            – toàn bộ giao diện và logic
├── manifest.webmanifest  – thông tin để cài như app
├── sw.js                 – cho app mở được khi mất mạng
└── icons/                – biểu tượng app
```
