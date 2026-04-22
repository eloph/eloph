# 🐧 企鹅小纸条 · Cloudflare 部署指南

## 📋 部署步骤

### 1. 准备工作

1. **注册 Cloudflare 账号**
   - 访问 https://dash.cloudflare.com/sign-up
   - 创建一个免费账号

2. **获取 Cloudflare API 令牌**
   - 登录 Cloudflare 控制台
   - 点击右上角头像 → "My Profile"
   - 选择 "API Tokens" 标签页
   - 点击 "Create Token"
   - 选择 "Edit Cloudflare Workers" 模板
   - 权限设置：
     - Account - Workers KV Storage: Edit
     - Account - Workers Scripts: Edit
     - Account - Pages: Edit
   - 点击 "Continue to summary" → "Create Token"
   - 复制生成的 API 令牌（重要！）

3. **安装 Cloudflare CLI 工具**
   ```bash
   npm install -g wrangler
   ```

### 2. 部署到 Cloudflare Pages

1. **设置环境变量**
   ```bash
   # Linux/Mac
   export CLOUDFLARE_API_TOKEN="你的API令牌"

   # Windows (PowerShell)
   $env:CLOUDFLARE_API_TOKEN="你的API令牌"
   ```

2. **初始化项目**
   ```bash
   # 在项目目录中执行
   wrangler pages project create penguin-notes
   ```

3. **部署网站**
   ```bash
   # 在项目目录中执行
   wrangler pages deploy . --project-name penguin-notes
   ```

4. **查看部署结果**
   - 部署完成后，会显示访问 URL
   - 类似于：`https://penguin-notes.pages.dev`

### 3. 项目配置

#### Cloudflare Pages 配置

- **构建命令**：无需构建命令（纯静态网站）
- **构建输出目录**：`./`（当前目录）
- **环境变量**：无需特殊环境变量

### 4. 自定义域名（可选）

1. **添加自定义域名**
   - 登录 Cloudflare 控制台
   - 选择 "Pages" → 选择你的项目
   - 点击 "Custom domains" → "Add custom domain"
   - 输入你的域名（如 `notes.yourdomain.com`）
   - 按照提示完成 DNS 配置

2. **HTTPS 配置**
   - Cloudflare 会自动为你的域名配置 HTTPS
   - 通常需要 5-10 分钟完成证书签发

### 5. 部署状态检查

- **部署历史**：在 Cloudflare Pages 控制台查看所有部署记录
- **访问日志**：查看网站访问统计和错误日志
- **预览环境**：每次部署都会生成预览 URL

## 🚀 快速部署命令

```bash
# 完整部署流程
npm install -g wrangler
export CLOUDFLARE_API_TOKEN="你的API令牌"
wrangler pages project create penguin-notes
wrangler pages deploy . --project-name penguin-notes
```

## 📁 项目文件结构

```
/
├── index.html          # 主页面
└── CLOUDFLARE_DEPLOYMENT.md  # 部署指南
```

## 🔧 技术说明

- **静态网站**：纯 HTML/CSS/JavaScript，无需后端
- **数据存储**：使用 localStorage 本地存储
- **响应式设计**：支持桌面和移动设备
- **部署平台**：Cloudflare Pages（全球 CDN，免费）

## 📞 故障排除

### 常见问题

1. **API 令牌错误**
   - 确保 API 令牌有正确的权限
   - 检查环境变量是否正确设置

2. **部署失败**
   - 检查项目文件是否完整
   - 确保网络连接正常

3. **网站访问问题**
   - 检查 Cloudflare Pages 控制台的部署状态
   - 清除浏览器缓存后重试

4. **自定义域名配置**
   - 确保 DNS 记录已正确设置
   - 等待 DNS  propagation（通常需要 5-30 分钟）

## 🎉 部署成功

部署完成后，你的企鹅小纸条网站将：
- 全球 CDN 加速，访问速度快
- 自动 HTTPS 加密
- 零服务器维护
- 支持自定义域名
- 完全免费（Cloudflare Pages 免费计划）

开始使用你的企鹅小纸条网站吧！🐧✨