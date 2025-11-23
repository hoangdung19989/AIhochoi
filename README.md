# OnLuyen AI Tutor - Hướng dẫn Cài đặt & Triển khai

Chào mừng bạn đến với OnLuyen AI Tutor! Dự án này đã được cấu trúc lại để sử dụng **Vite**, một công cụ xây dựng hiện đại, giúp tối ưu hóa hiệu năng và bảo mật.

Dưới đây là hướng dẫn đầy đủ để bạn có thể chạy dự án trên máy tính cá nhân (local) và triển khai lên nền tảng **Vercel** một cách chuyên nghiệp.

---

## 1. Yêu cầu hệ thống

- **Node.js**: Phiên bản 18.x trở lên.
- **npm** (hoặc yarn, pnpm): Trình quản lý gói của Node.js.
- **Tài khoản GitHub**: Để lưu trữ mã nguồn và kết nối với Vercel.
- **Tài khoản Vercel**: Để triển khai ứng dụng.

---

## 2. Lấy API Key

Để ứng dụng có thể hoạt động, bạn cần có một **Google AI (Gemini) API Key**.

1.  Truy cập [Google AI Studio](https://aistudio.google.com/app/apikey).
2.  Đăng nhập bằng tài khoản Google của bạn.
3.  Nhấp vào **"Create API key"** để tạo một key mới.
4.  Sao chép và lưu lại key này một cách an toàn. Chúng ta sẽ sử dụng nó ở các bước tiếp theo.

---

## 3. Chạy dự án trên máy tính (Local Development)

### Bước 1: Tải mã nguồn về

Mở Terminal (hoặc Command Prompt, Git Bash) và clone kho mã nguồn của bạn từ GitHub:

```bash
git clone <URL_KHO_LUU_TRU_CUA_BAN>
cd <TEN_THU_MUC_DU_AN>
```

### Bước 2: Cài đặt các thư viện cần thiết

Chạy lệnh sau để cài đặt tất cả các thư viện đã được định nghĩa trong `package.json`:

```bash
npm install
```

### Bước 3: Tạo file Biến môi trường

Đây là bước để cung cấp API Key cho dự án khi chạy ở local.

1.  Trong thư mục gốc của dự án, tạo một file mới và đặt tên là `.env`.
2.  Mở file `.env` và thêm vào nội dung sau, thay `YOUR_API_KEY_HERE` bằng API Key bạn đã lấy ở trên:

    ```
    VITE_API_KEY=YOUR_API_KEY_HERE
    ```

    **QUAN TRỌNG:** Tên biến phải bắt đầu bằng `VITE_`. Đây là quy tắc của Vite để biến môi trường có thể được truy cập từ mã nguồn phía client.

### Bước 4: Khởi động server phát triển

Chạy lệnh sau:

```bash
npm run dev
```

Terminal sẽ hiển thị một địa chỉ URL, thường là `http://localhost:5173`. Mở trình duyệt và truy cập địa chỉ này để xem ứng dụng của bạn đang chạy.

---

## 4. Hướng dẫn triển khai lên Vercel (Production)

Vercel là nền tảng được khuyên dùng vì nó tích hợp hoàn hảo với các dự án frontend hiện đại, cung cấp quy trình triển khai tự động và bảo mật biến môi trường.

### Bước 1: Đẩy mã nguồn lên GitHub

Hãy chắc chắn rằng tất cả các file mới (`package.json`, `vite.config.ts`, etc.) đã được commit và đẩy lên kho lưu trữ GitHub của bạn.

### Bước 2: Kết nối Vercel với GitHub

1.  Truy cập [vercel.com](https://vercel.com) và đăng nhập bằng tài khoản GitHub của bạn.
2.  Trên trang Dashboard, nhấp vào **"Add New..." -> "Project"**.

### Bước 3: Import dự án

Vercel sẽ hiển thị danh sách các kho lưu trữ GitHub của bạn. Tìm và nhấp vào nút **"Import"** bên cạnh dự án của bạn.

### Bước 4: Cấu hình dự án trên Vercel

1.  **Framework Preset:** Vercel sẽ tự động nhận diện đây là một dự án **Vite** và chọn sẵn các cài đặt tối ưu. Bạn không cần thay đổi gì.
    *   **Build Command** sẽ là `npm run build`.
    *   **Output Directory** sẽ là `dist`.

2.  **Environment Variables (Biến môi trường) - QUAN TRỌNG NHẤT:**
    *   Mở rộng phần "Environment Variables".
    *   Thêm một biến mới với thông tin sau:
        *   **NAME:** `VITE_API_KEY` (Phải giống hệt tên biến trong file `.env`)
        *   **VALUE:** Dán API Key Gemini của bạn vào đây.
    *   Nhấp vào nút **"Add"**.

### Bước 5: Triển khai

Nhấp vào nút **"Deploy"**. Vercel sẽ tự động cài đặt các thư viện, chạy lệnh `npm run build`, và triển khai các file tĩnh từ thư mục `dist` lên mạng toàn cầu của họ.

Quá trình này chỉ mất khoảng 1-2 phút. Sau khi hoàn tất, bạn sẽ nhận được một URL công khai để truy cập trang web của mình.

**Chúc mừng! Ứng dụng của bạn đã được triển khai thành công, an toàn và chuyên nghiệp!**
