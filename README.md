# YT-DLP Web 下载器

一个基于 yt-dlp 的 Web 应用程序，支持使用自定义 Cookie 下载视频。

## 功能特性

- 🎥 支持YouTuBe
- 🍪 支持自定义 Cookie 文件上传
- 📊 实时下载进度显示
- 🎛️ 可配置的视频质量和格式
- 📱 响应式 Web 界面
- 🔄 多任务并发下载
- 📁 文件管理和下载

## 安装和运行

### 1. 安装依赖

```bash
pip install -r requirements.txt
```

### 2. 运行应用

```bash
python app.py
```

应用将在 `http://localhost:5000` 启动。

## 使用说明

### 1. 上传 Cookie 文件

- 点击或拖拽上传 Cookie 文件（.txt 格式）
- Cookie 文件用于访问需要登录的视频内容

### 2. 下载视频

1. 在输入框中粘贴视频 URL
2. 点击"获取信息"查看视频详情
3. 选择视频质量和格式
4. 点击"开始下载"

### 3. 管理下载任务

- 查看所有下载任务的状态
- 实时监控下载进度
- 下载完成后可直接下载文件

## API 接口

### 获取视频信息
```
POST /api/info
Content-Type: application/json

{
    "url": "视频URL",
    "cookies_file": "cookie文件名（可选）"
}
```

### 开始下载
```
POST /api/download
Content-Type: application/json

{
    "url": "视频URL",
    "options": {
        "format": "best[ext=mp4]"
    },
    "cookies_file": "cookie文件名（可选）"
}
```

### 获取任务状态
```
GET /api/task/{task_id}
```

### 获取所有任务
```
GET /api/tasks
```

### 下载文件
```
GET /api/download/{task_id}
```

### Cookie 管理
```
POST /api/cookies  # 上传 Cookie 文件
GET /api/cookies   # 获取 Cookie 文件列表
```

## 配置选项

### 下载选项

- `format`: 视频格式和质量选择
- `outtmpl`: 输出文件名模板
- `cookiefile`: Cookie 文件路径

### 应用配置

- `DOWNLOAD_DIR`: 下载文件存储目录
- `COOKIES_DIR`: Cookie 文件存储目录
- `MAX_CONCURRENT_DOWNLOADS`: 最大并发下载数

## 安全注意事项

1. Cookie 文件包含敏感信息，请妥善保管
2. 不要在生产环境中暴露应用端口
3. 定期清理下载文件以节省存储空间

## 故障排除

### 常见问题

1. **下载失败**: 检查网络连接和视频 URL 有效性
2. **Cookie 无效**: 确保 Cookie 文件格式正确且未过期
3. **权限错误**: 确保应用有写入下载目录的权限

### 日志查看

应用运行时会在控制台输出详细日志，包括：
- 下载进度
- 错误信息
- 任务状态变化

## 技术栈

- **后端**: Flask + yt-dlp
- **前端**: Bootstrap 5 + 原生 JavaScript
- **文件处理**: 多线程下载队列
- **存储**: 本地文件系统

## 许可证

MIT License

