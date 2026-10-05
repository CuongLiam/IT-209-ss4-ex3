# Báo cáo Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub

## 1. Khởi tạo khóa SSH
Lệnh tạo cặp khóa SSH (chuẩn Ed25519) dùng để xác thực:
```bash
ssh-keygen -t ed25519 -C "duyho@example.com"
```
Quá trình này sinh ra 2 tệp: khóa riêng tư (`id_ed25519`) để giữ bảo mật ở local và khóa công khai (`id_ed25519.pub`) để đưa lên GitHub.

*Lưu ý: Không bao giờ chia sẻ file khóa private (`id_ed25519`).*

## 2. Liên kết với Remote Repository trên GitHub
Sau khi tạo một repository trống trên GitHub, tôi đã cấu hình liên kết an toàn giữa repository cục bộ và máy chủ bằng giao thức SSH:

```bash
git remote add origin git@github.com:duyho/rikkei-bt3.git
```

Kiểm tra lại cấu hình URL:
```bash
git remote -v
# Output mong đợi:
# origin  git@github.com:duyho/rikkei-bt3.git (fetch)
# origin  git@github.com:duyho/rikkei-bt3.git (push)
```

## 3. Cấu hình và Kiểm tra kết nối SSH
Khóa công khai (Public Key) sau đó được copy và dán vào phần **Settings > SSH and GPG keys** trên tài khoản GitHub.

Để kiểm tra xem xác thực đã thành công chưa:
```bash
ssh -T git@github.com
# Output mong đợi: Hi user! You've successfully authenticated...
```

## 4. Đẩy (push) mã nguồn lên GitHub
Cuối cùng, đẩy mã nguồn của nhánh main từ local lên repository trên GitHub:
```bash
git push -u origin main
```

**URL Kho lưu trữ GitHub (SSH):** `git@github.com:duyho/rikkei-bt3.git`
