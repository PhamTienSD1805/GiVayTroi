# Simple Website with GitHub Actions CI/CD

Một dự án website đơn giản với quy trình CI/CD tự động hoàn chỉnh sử dụng GitHub Actions.

## 📋 Mục lục
- [Tính năng](#tính-năng)
- [Cấu trúc thư mục](#cấu-trúc-thư-mục)
- [Cài đặt](#cài-đặt)
- [GitHub Actions Workflows](#github-actions-workflows)
- [Cấu hình Secrets](#cấu-hình-secrets)
- [Deploy lên GitHub Pages](#deploy-lên-github-pages)

## ✨ Tính năng

### Website
- ✅ Responsive design
- ✅ Modern UI với animations
- ✅ Navigation mượt mà
- ✅ Contact form
- ✅ Multiple sections

### CI/CD Pipeline
- 🔨 **Build**: Tự động build với npm và .NET
- 🧪 **Test**: Chạy tests với npm, pytest, và junit
- 🚀 **Deploy**: Tự động deploy lên GitHub Pages
- 🔒 **Security**: Quét mã với CodeQL
- 📢 **Notify**: Thông báo qua Discord và Slack

## 📁 Cấu trúc thư mục

```
project/
├── .github/
│   └── workflows/
│       ├── build.yml        # Build automation
│       ├── test.yml         # Testing automation
│       ├── deploy.yml       # Deployment to GitHub Pages
│       ├── security.yml     # Security scanning
│       └── notify.yml       # Notifications
├── index.html               # Website homepage
├── style.css               # Styling
├── README.md               # This file
├── package.json            # (Optional) NPM configuration
└── .gitignore             # Git ignore file
```

## 🚀 Cài đặt

### 1. Clone hoặc tạo repository mới

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### 2. Thêm các file vào project

Tạo các file sau trong project:
- `index.html` (từ artifact đầu tiên)
- `style.css` (từ artifact thứ hai)
- Tạo thư mục `.github/workflows/` và thêm 5 workflow files

### 3. (Optional) Cài đặt Node.js nếu muốn sử dụng npm

Tạo file `package.json`:

```json
{
  "name": "simple-website",
  "version": "1.0.0",
  "description": "Simple website with CI/CD",
  "scripts": {
    "test": "echo \"No tests specified\" && exit 0",
    "build": "echo \"No build process needed for static site\""
  },
  "keywords": ["website", "ci-cd", "github-actions"],
  "author": "Your Name",
  "license": "MIT"
}
```

### 4. Tạo file .gitignore

```
node_modules/
dist/
build/
.env
*.log
.DS_Store
bin/
obj/
```

## ⚙️ GitHub Actions Workflows

### 1. Build Workflow (`build.yml`)
- **Trigger**: Push hoặc PR vào `main` hoặc `develop`
- **Chức năng**: 
  - Build với npm (nếu có package.json)
  - Build với .NET (nếu có .csproj hoặc .sln)
  - Upload artifacts

### 2. Test Workflow (`test.yml`)
- **Trigger**: Push hoặc PR vào `main` hoặc `develop`
- **Chức năng**:
  - NPM tests
  - PyTest tests
  - JUnit tests (.NET)
  - Tạo test summary

### 3. Deploy Workflow (`deploy.yml`)
- **Trigger**: Push vào `main` hoặc manual
- **Chức năng**:
  - Build project
  - Deploy lên GitHub Pages
  - Tạo deployment summary

### 4. Security Workflow (`security.yml`)
- **Trigger**: Push, PR, hoặc schedule (weekly)
- **Chức năng**:
  - CodeQL analysis (JavaScript, C#, Python)
  - Dependency review
  - NPM security audit
  - .NET security scan

### 5. Notify Workflow (`notify.yml`)
- **Trigger**: Khi workflows khác hoàn thành
- **Chức năng**:
  - Gửi thông báo Discord
  - Gửi thông báo Slack
  - Gửi email khi có lỗi

## 🔐 Cấu hình Secrets

Để sử dụng notifications, bạn cần thêm secrets trong GitHub:

### Vào Settings → Secrets and variables → Actions → New repository secret

1. **DISCORD_WEBHOOK** (Optional)
   - Tạo webhook trong Discord server
   - Server Settings → Integrations → Webhooks → New Webhook
   - Copy Webhook URL

2. **SLACK_WEBHOOK** (Optional)
   - Tạo Slack App tại api.slack.com
   - Enable Incoming Webhooks
   - Copy Webhook URL

3. **EMAIL_USERNAME** (Optional)
   - Gmail address của bạn

4. **EMAIL_PASSWORD** (Optional)
   - Gmail App Password (không phải password thông thường)
   - Tạo tại: myaccount.google.com/apppasswords

5. **EMAIL_TO** (Optional)
   - Email nhận thông báo

## 🌐 Deploy lên GitHub Pages

### Bước 1: Enable GitHub Pages

1. Vào repository → **Settings**
2. Chọn **Pages** từ sidebar
3. Tại **Source**, chọn **GitHub Actions**

### Bước 2: Push code lên GitHub

```bash
git add .
git commit -m "Initial commit with CI/CD"
git push origin main
```

### Bước 3: Xem deployment

- Workflows sẽ tự động chạy
- Vào tab **Actions** để theo dõi
- Sau khi deploy thành công, website sẽ có tại:
  ```
  https://your-username.github.io/your-repo/
  ```

## 📊 Monitoring Workflows

### Xem workflow status:
1. Vào tab **Actions** trong repository
2. Click vào workflow để xem chi tiết
3. Xem logs của từng job

### Status badges:
Thêm vào README để hiển thị status:

```markdown
![Build](https://github.com/your-username/your-repo/workflows/Build/badge.svg)
![Test](https://github.com/your-username/your-repo/workflows/Test/badge.svg)
![Deploy](https://github.com/your-username/your-repo/workflows/Deploy%20to%20GitHub%20Pages/badge.svg)
![Security](https://github.com/your-username/your-repo/workflows/Security%20Scan/badge.svg)
```

## 🛠️ Technologies Used

### Frontend
- HTML5
- CSS3 (với animations)
- JavaScript (Vanilla)

### CI/CD
- GitHub Actions
- Node.js (optional)
- .NET SDK (optional)
- Python (optional)

### Security
- CodeQL
- npm audit
- Dependency review

## 📝 Customization

### Thêm npm build process:

```json
{
  "scripts": {
    "build": "your-build-command",
    "test": "your-test-command"
  }
}
```

### Thêm .NET project:

Workflows tự động nhận diện .csproj hoặc .sln files và chạy:
- `dotnet restore`
- `dotnet build`
- `dotnet test`

### Modify workflows:

Edit các file trong `.github/workflows/` để customize triggers, jobs, hoặc steps.

## 🤝 Contributing

1. Fork repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📄 License

MIT License - Bạn có thể sử dụng tự do cho dự án cá nhân hoặc thương mại.

## 🆘 Troubleshooting

### Workflow không chạy?
- Check Settings → Actions → General → Workflow permissions
- Đảm bảo "Allow all actions" được enable

### Deploy lên GitHub Pages thất bại?
- Check Settings → Pages → Source = "GitHub Actions"
- Verify permissions trong deploy.yml

### Notifications không hoạt động?
- Check secrets đã được thêm đúng chưa
- Workflows sẽ skip notification nếu không có secrets (không bị lỗi)

## 📞 Support

Nếu có vấn đề, hãy:
1. Check workflow logs trong tab Actions
2. Review error messages
3. Create issue trong repository

---

**Made with ❤️ using GitHub Actions**