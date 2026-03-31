![kun-galgame-nuxt4](https://kungal.com/kungalgame.webp)

### **[English](/README.md)** | **[日本語](/docs/readme/jp.md)** | **[简体中文](/docs/readme/chs.md)** | **[繁體中文](/docs/readme/cht.md)**

**联系我们：[Telegram](https://t.me/kungalgame) | [Discord](https://discord.com/invite/5F4FS2cXhX)**

图片来源为游戏 [方舟指令](https://apps.qoo-app.com/en/app/9593) 中的角色鲲（KUN）

> **AI辅助开发说明：** 本项目自 **5.1.0** 版本起使用包含但不限于 Claude Code 等 LLM 辅助工具进行 Vibe Coding。**5.0.70** 及之前版本的所有代码均完全由手工编写。最后一个完全手写的代码库版本见：[v5.0.70 (commit b4ad59e)](https://github.com/KUN1007/kun-galgame-nuxt4/tree/b4ad59eb77d3eaf36d082aa528651039816e1dfa)

# 鲲 Galgame 论坛

## 项目简介

鲲 Galgame 是一个 Galgame 集体，它由无数热爱 Galgame 游戏体裁的人们组成。它目前有以下几个子网站：

- [鲲 Galgame 论坛](https://kungal.com) (本项目)
- [鲲 Galgame 表情包](https://sticker.kungal.com) (一个专注于收集制作 Galgame 表情包的网站)
- [鲲 Galgame 开发文档](https://soft.moe/kun-visualnovel-docs/kun-forum.html) (本论坛是完全开源的，开发文档将会全部公开在这里)
- [鲲 Galgame 导航页面](https://nav.kungal.org/) （完全开源的导航站！ 可以前往鲲 Galgame 所有子网站！）
- [鲲 Galgame 补丁站](https://www.moyu.moe) (目前全球最先进的视觉小说补丁资源网站！永久免费！)
- [鲲 Galgame 论坛下线页面](https://down.kungal.com/) （碰到不得不下线的时候，我们会将论坛强制重定向到此页面）

更多信息请直接访问网站的关于我们页面

https://www.kungal.com/kungalgame

## 特性

- **Galgame 数据库** — 社区驱动的 Galgame 目录，集成 VNDB，支持多语言元数据 (EN / JA / ZH-CN / ZH-TW)、评分、标签、引擎信息和开发者资料
- **资源分享** — 上传和分享游戏补丁、汉化、语音包和其他资源，具备提供者追踪及平台和语言筛选功能
- **讨论论坛** — 功能齐全的话题系统，支持富文本 Markdown 编辑 (Milkdown + CodeMirror)、回复、子评论、投票、点赞和收藏
- **协作编辑** — 采用 Git 风格的 PR (Pull Request) 工作流进行 Galgame 信息编辑，包含编辑历史记录及贡献者致谢
- **实时消息** — 基于 Socket.IO 的聊天系统，支持私信和聊天室
- **萌萌点系统** — 通过贡献（发帖、分享资源、编辑 Galgame 信息）获得的社区声望点数功能
- **多媒体内容编辑** — 支持 KaTeX 数学公式、代码高亮和拖拽上传图片的 Milkdown Markdown 编辑器
- **深色 / 浅色主题** — 系统自带的色彩模式切换，支持自定义页面透明度、字体和背景图片
- **SEO 优化** — 服务端渲染，结构化数据 (Schema.org)、站点地图生成和 Galgame 及话题的 RSS 订阅

## 技术栈

| 层 | 技术 |
|-------|-----------|
| 框架 | [Nuxt 4](https://nuxt.com/) (Vue 3 组合式 API + Nitro 服务器) |
| 样式 | [Tailwind CSS 4](https://tailwindcss.com/) |
| 状态管理 | [Pinia](https://pinia.vuejs.org/) (带持久化) |
| 数据库 | PostgreSQL + [Prisma 7](https://www.prisma.io/) ORM |
| 缓存 | Redis |
| 身份验证 | JWT (双 token — access + refresh) |
| 实时通讯 | [Socket.IO](https://socket.io/) |
| 文件存储 | 兼容 S3 的对象存储服务 (图片与资源) |
| 数据验证 | [Zod](https://zod.dev/) |
| 文本编辑器 | [Milkdown](https://milkdown.dev/) + [CodeMirror](https://codemirror.net/) |
| 部署管理 | PM2 |
| 流量分析 | [Umami](https://umami.is/) |

## 项目结构

```text
├── app/                 # 前端目录 (页面、组件、组合式函数、状态、校验)
├── server/              # 后端目录 (API 路由、插件、WebSocket、定时任务)
├── shared/              # 共享代码 (TypeScript 类型、工具函数)
├── prisma/schema/       # 数据库模型设计 (模块化 .prisma 文件)
├── lib/                 # 核心库 (S3 客户端、图标配置等)
├── scripts/             # 构建与数据库迁移脚本
├── public/              # 静态资源存放点
└── docs/                # 开发文档
```

## 快速开始

```bash
# 安装依赖
pnpm install

# 复制并配置环境变量
cp .env.example .env

# 生成 Prisma 客户端
pnpm prisma:generate

# 推送 schema 到数据库
pnpm prisma:push

# 启动开发服务器 (http://127.0.0.1:1007)
pnpm dev
```

## 脚本命令

| 命令 | 描述 |
|---------|-------------|
| `pnpm dev` | 启动开发服务器 |
| `pnpm build` | 构建生产环境版本 |
| `pnpm lint` | 运行 ESLint 代码检查 |
| `pnpm format` | 运行 Prettier 格式化代码 |
| `pnpm typecheck` | 执行 TypeScript 类型检查 |
| `pnpm prisma:generate` | 生成 Prisma Client 代码 |
| `pnpm prisma:push` | 将 schema 更改应用到数据库结构 |
| `pnpm prisma:studio` | 开启 Prisma Studio GUI 查看数据库 |
| `pnpm start` / `pnpm stop` | 使用 PM2 启动 / 停止生产环境 |

## 加入 / 联系我们

- [Telegram 群组](https://t.me/kungalgame)
- [Twitter / X](https://twitter.com/kungalgame)
- [GitHub 仓库](https://github.com/KUN1007/kun-galgame-nuxt4)
- [Discord 群组](https://discord.com/invite/5F4FS2cXhX)
- [YouTube 频道](https://youtube.com/@kungalgame)
- [Bilibili](https://space.bilibili.com/1748455574)

## License

本项目遵循 `AGPL-3.0` 开源协议
