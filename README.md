# Brclio

Your personal publishing system, powered by Skills.

初衷：AI时代，啥都可以做成 Skills，那么个人网站也应该如此！做出一个 Skills，让大家安装后，就可以使用 Skills 帮忙初始化、配置环境、写文章、甚至部署！

## Cloudflare 部署

网站通过 Cloudflare Pages 连接 GitHub 仓库自动构建，部署配置如下：

| 配置项 | 值 |
| --- | --- |
| Pages 项目 | `brclio-github-io` |
| GitHub 仓库 | `Brclio/Brclio.github.io` |
| 生产分支 | `main` |
| 根目录 | 仓库根目录 |
| 构建命令 | `pnpm run build` |
| 构建输出目录 | `dist` |
| 环境变量 | `NODE_VERSION=22.16.0`、`PNPM_VERSION=8.15.9` |
| 自定义域名 | `brclio.com` |

Git 集成和自定义域名配置完成后，每次推送到 `main` 都会触发自动构建；构建成功后，Cloudflare Pages 自动发布新版本。

日常更新先在本地检查构建，再提交并推送代码：

```sh
pnpm install --frozen-lockfile
pnpm run build
git add .
git diff --cached
git commit -m "更新网站内容"
git push origin main
```

推送后可在 Cloudflare Pages 项目 `brclio-github-io` 的 Deployments 页面查看构建日志和发布结果。
