# Website — QR Trust Scanner (GitHub Pages)

Sinh bởi `python3 Scripts/build_publishing.py` từ `Scripts/web_copy.py`. Tĩnh hoàn toàn: không JavaScript, không tài nguyên ngoài, sáng/tối theo hệ thống, responsive.
4 trang × 7 ngôn ngữ = 28 trang: `index`, `support`, `privacy`, `terms` — `en` ở gốc, các ngôn ngữ khác trong `vi/ zh-hans/ pt-br/ es/ id/ ja/`.

URL theo Golden Rule 15: **https://dlhkaizen.github.io/qrtrustscanner/**

## Xem cục bộ

```bash
python3 -m http.server 8717 --bind 127.0.0.1 --directory 13_APPS/017_QRTrustScanner/PUBLISHING/Website
```

(hoặc cấu hình `qrtrustscanner-website` trong `.claude/launch.json`).

## Đưa lên GitHub Pages — Hồ tự làm (Claude không push)

```bash
# 1. Tạo repo công khai tên đúng là  qrtrustscanner  dưới tài khoản dlhkaizen (trên github.com).
# 2. Đẩy nội dung thư mục này lên nhánh main của repo đó:
cd /tmp && rm -rf qrtrustscanner-site && mkdir qrtrustscanner-site && cd qrtrustscanner-site
cp -R /Volumes/DEV/APP_FACTORY_X/13_APPS/017_QRTrustScanner/PUBLISHING/Website/. .
git init -b main && git add -A && git commit -m "QR Trust Scanner website"
git remote add origin git@github.com:dlhkaizen/qrtrustscanner.git
git push -u origin main
# 3. Repo → Settings → Pages → Source: Deploy from a branch → main / (root) → Save.
# 4. Kiểm bốn URL trả 200 (bắt buộc trước khi nộp App Store — Golden Rule 15 §8, DBG-016):
for p in "" support.html privacy.html terms.html; do curl -s -o /dev/null -w "%{http_code} $p\n" https://dlhkaizen.github.io/qrtrustscanner/$p; done
```

`.nojekyll` có sẵn để GitHub Pages phục vụ file nguyên trạng.
