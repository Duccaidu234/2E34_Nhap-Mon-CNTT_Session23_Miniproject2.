# TechNova Onboarding Kit (`[Lop_MonHoc]_MiniProject_TechNova`)

Bộ hồ sơ Onboarding Số chuẩn hóa dành cho nhân viên mới tại Startup công nghệ **TechNova**, hướng dẫn làm chủ không gian làm việc số, phân quyền cộng tác, bảo mật cá nhân và tự gỡ lỗi sự cố kỹ thuật.

---

## 📌 1. Cấu trúc Cây Thư mục Dự án chuẩn `kebab-case`

```text
technova-onboarding-kit/
├── .env                            # Tệp ẩn chứa thông số cấu hình local (đã ẩn qua .gitignore)
├── docs/
│   ├── README.md                   # Hướng dẫn sử dụng chính (Render chuẩn Markdown)
│   └── srs-onboarding-kit.docx     # Tài liệu SRS đặc tả hệ thống (Word Styles & Auto TOC)
├── cloud-workspace/
│   └── phan-quyen-chia-se.md       # Cấu trúc 5 trụ cột & Bảng ma trận phân quyền
├── browser-setup/
│   └── ho-so-trinh-duyet.md        # Cấu hình đa Profile, Bookmark & Extension
├── security/
│   ├── checklist-bao-mat.md        # Quy tắc 5 KHÔNG, Bitwarden Vault & 2FA/TOTP
│   ├── .env.example                # Tệp mẫu cấu hình biến môi trường
│   └── .gitignore                  # Khai báo chặn các tệp nhạy cảm commit lên Git
└── troubleshooting/
    └── mau-bao-cao-loi.md          # Bug Reporting Framework & Search Operators
```

---

## ☁️ 2. Module 1: Không gian Cộng tác Đám mây (`cloud-workspace/`)

### Mô hình Hybrid Workflow
- **Local Storage:** Làm việc trực tiếp tại ổ cứng local (`C:\TechNova\` hoặc `~/TechNova/`) để đảm bảo tốc độ đọc/ghi nhanh, không giật lag khi compile code.
- **Cloud Synchronization:** Cài đặt **Google Drive for Desktop** (chế độ Stream/Mirror) để tự động sao lưu dữ liệu lên Cloud theo thời gian thực và lưu giữ lịch sử phiên bản (Version History).

### Ma trận Phân quyền & Quy tắc Giao tiếp

| Vai trò Người dùng | Quyền Google Drive | Kênh Giao tiếp (Lark/Slack) | Quy tắc Ứng xử |
| :--- | :--- | :--- | :--- |
| **Owner (Nhân viên mới)** | **Editor** (Thư mục cá nhân) | `#onboarding` | Hỏi đáp 1-1 riêng với Mentor |
| **Đồng đội cùng dự án** | **Editor** (Tắt quyền share tiếp) | `#dev-<ten-du-an>` | Thảo luận kỹ thuật, Reply in Thread |
| **Mentor / Người góp ý** | **Commenter** | `#thong-bao` | Nhận xét góp ý, không sửa trực tiếp |
| **Đối tác / Khách ngoài** | **Viewer (Restricted)** | *Không cấp quyền* | Chỉ chỉ định đích danh Email truy cập |

> ⚠️ **BẪY PHÂN QUYỀN:** Tuyệt đối không bao giờ kết hợp *"Anyone with the link"* với quyền **Editor**.

---

## 🌐 3. Module 2: Thiết lập Trình duyệt Đa Profile (`browser-setup/`)

- **Data Isolation:** Tách biệt 2 Profile độc lập (`Personal` và `TechNova_Work`) để cô lập Cookies, History và Session làm việc.
- **Bookmark Manager (3 Nhóm):**
  - 📁 `01_Work_Dev`: GitHub Enterprise, Jira Board, Figma Design, CI/CD Dashboard.
  - 📁 `02_Onboarding_Docs`: SRS Document, Quy định Công ty, Google Drive Workspace.
  - 📁 `03_Tools`: Bitwarden Vault, StackOverflow, ChatGPT/Gemini, JSON Viewer.
- **Extension Security:** Đặt quyền **Site Access** của các Extension không bắt buộc ở chế độ *"On Click"*.
- **DevTools (F12):** Sử dụng Inspect Element để soi CSS Box Model và thực hiện **Hard Reload (Ctrl + Shift + R)** với option *Disable Cache* trước khi báo cáo lỗi giao diện.

---

## 🔒 4. Module 3: An toàn Thông tin Cá nhân (`security/`)

### 3 Lớp Xác thực Danh tính (MFA) & Zero-Knowledge
1. **Something You Know:** Mật khẩu ngẫu nhiên 16–32 ký tự do **Bitwarden** quản lý.
2. **Something You Have:** Thiết bị sinh mã **TOTP 2FA** qua Authenticator App (Không dùng SMS OTP vì rủi ro SIM Swapping). Lưu 10 Backup Codes vào Bitwarden Vault.
3. **Something You Are:** Vân tay / FaceID mở khóa ứng dụng Vault local.

### Bảo vệ Secrets Dự án
- Thông số kết nối API/DB đặt tại tệp `.env`.
- Thêm `.env` vào tệp `.gitignore` trước commit đầu tiên.
- Tạo `.env.example` chứa các giá trị giả định (dummy) cho đồng đội.

---

## 🔍 5. Module 4: Bộ kỹ năng Tự Tra cứu & Gỡ lỗi (`troubleshooting/`)

### Search Operators & AI Prompting
- **Cú pháp Google:** `site:stackoverflow.com "CORS policy" -angular`
- **Prompt AI 3 Thành phần:**
  1. *Ngữ cảnh:* OS, Ngôn ngữ, Framework & Version đang chạy.
  2. *Lỗi nguyên văn:* Copy toàn bộ StackTrace/Log trong cặp ` ``` `.
  3. *Yêu cầu:* Giải thích nguyên nhân bằng tiếng Việt & đưa ra 3 bước khắc phục.

### Bug Reporting Framework (4 Bước)
$$\text{Context} \longrightarrow \text{Expected Result} \longrightarrow \text{Actual Result} \longrightarrow \text{Log / Screenshot}$$

---

## 📋 6. Checklist Onboarding 7 Ngày đầu

- [x] **Ngày 1:** Đăng ký tài khoản Bitwarden, bật 2FA/TOTP cho Email công ty và GitHub.
- [x] **Ngày 2:** Tạo 2 Profile Trình duyệt độc lập (`Personal` & `TechNova_Work`), import bộ Bookmark.
- [x] **Ngày 3:** Cài đặt Google Drive for Desktop, dựng cây thư mục 5 trụ cột chuẩn `kebab-case`.
- [x] **Ngày 4:** Cấu hình Extension bảo mật, giới hạn Site Access về chế độ *On Click*.
- [x] **Ngày 5:** Thấu hiểu văn hóa giao tiếp: Reply in Thread, tag tên đúng người, không *No-Hello*.
- [x] **Ngày 6:** Thành thạo tra cứu lỗi với toán tử Google và soạn Prompt AI 3 thành phần.
- [x] **Ngày 7:** Hoàn thành kiểm tra thử nghiệm Bug Reporting Framework với phòng IT Support.