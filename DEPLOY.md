# 油价看板发布说明

当前可直接发布的文件：

- `index.html`
- `latest.json`

## 方案一：最快拿到公网链接

适合今天就发给朋友。

### Cloudflare Pages 直接上传

1. 登录 Cloudflare。
2. 进入 `Workers & Pages`。
3. 选择 `Create application`。
4. 选择 `Pages`。
5. 选择 `Direct Upload` 或 `Drag and drop your files`。
6. 新建一个项目名，例如 `chengdu-oil-dashboard`。
7. 上传当前目录下的：
   - `index.html`
   - `latest.json`
8. 发布后会得到一个 `*.pages.dev` 链接。

说明：

- 这是最快的分享方式。
- 但它是“手动发布”，以后每天更新后需要重新上传。
- Cloudflare 官方文档说明，`Direct Upload` 项目后续不能切换成 `Git integration`，如果以后要自动化，建议新建另一个项目。

## 方案二：适合后续每天自动更新

适合长期使用。

### GitHub + Cloudflare Pages

1. 新建一个 GitHub 仓库。
2. 把当前 `oil_dashboard` 目录内容上传到仓库根目录。
3. 在 Cloudflare Pages 选择 `Import an existing Git repository`。
4. 构建设置：
   - Production branch: `main`
   - Build command: `exit 0`
   - Build output directory: `.`
5. 首次部署完成后会得到一个固定公网链接。

说明：

- 这种方式更适合以后做“每天自动同步到公网”。
- 后续可以把本地 12:00 定时任务再接一个自动 `git push` 流程。

## 当前推荐

如果你现在只是要先发给朋友：

- 先用 `Cloudflare Pages Direct Upload`

如果你确认后续要长期自动更新：

- 直接走 `GitHub + Cloudflare Pages`
