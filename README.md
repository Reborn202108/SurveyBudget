# 隐私政策站点（静态页）

用于托管「工程勘察设计预算软件」的隐私政策网页，作为 Microsoft Store 提交流程中填写的隐私政策链接。

目标仓库：`Reborn202108/SurveyBudget`（公开、默认分支 `main`）。

**当前状态：站点文件与正文占位均已填实，待推送并启用 Pages。** 已填值：联系邮箱 `jeachow@foxmail.com`、生效日期 `2026-11-19`、公开地址 `https://reborn202108.github.io/SurveyBudget/privacy.html`。所有站内链接均为相对路径，换仓库或改目录结构时无需改页面代码。

## 目录结构

```
/
├─ index.html          站点首页：中英双语简介 + 两个入口
├─ privacy.html        隐私政策（简体中文）
├─ privacy.en.html     隐私政策（English）
├─ assets/
│  └─ style.css        全站唯一样式表（含响应式与打印规则）
├─ .nojekyll           跳过 GitHub Pages 的 Jekyll 构建（纯静态文件，避免多余处理）
└─ README.md           本文件
```

三个页面互链关系：

```
index.html ──> privacy.html ──> privacy.en.html
    ^              |                  |
    └──────────────┴──────────────────┘
```

## 样式规范

- 单一样式表 `assets/style.css`，页面内不写内联样式，不引入任何外部字体、图标库、CDN 或统计脚本。
- 无 JavaScript；页面在禁用脚本的环境下功能完整。
- 主题变量集中在 `:root`：主色 `--brand: #1d4f86`，正文 `--ink: #16202c`，底色 `--bg: #f6f8fb`，内容最大宽度 `--maxw: 860px`。
- 字体使用系统栈（Segoe UI / 微软雅黑 / 苹方 / 思源黑体），不下载字体文件。
- 断点：`max-width: 640px` 进入移动端布局（顶栏换行、首页卡片改单列、表格横向滚动）。
- 表格统一包在 `.table-wrap` 中，窄屏横向滚动，避免撑破页面。
- 打印：`@media print` 隐藏顶栏与页脚，去底色与阴影，表格边框改为细实线并禁止跨页断行，外部链接在纸面后附完整 URL。
- 占位符统一用 `<mark>` 标注（浅黄底 + 虚线下划线），发布前搜索 `<mark>` 即可定位。

## 页面约定

- 正文内容与 `msix/store/privacy-policy.md`、`privacy-policy.html`、`privacy-policy.en.html` 同源，本仓库只做排版与导航，不改写实质内容。
- 所有站内链接使用相对路径（`index.html`、`privacy.html`、`privacy.en.html`、`assets/style.css`），不写死 `github.io` 域名或仓库名。
- 外部链接（Microsoft 隐私声明、WebView2 文档）使用绝对 URL，并带 `rel="noopener"`。
- 中文页 `<html lang="zh-CN">`，英文页 `<html lang="en">`，两页互相声明 `hreflang`。

## 发布步骤（本轮不执行）

前置条件（依据 GitHub 官方文档）：

- GitHub Pages 在 **GitHub Free 下只对公开仓库开放**；私有仓库需要 GitHub Pro / Team / Enterprise。目标仓库为公开仓库，满足这一条。
- 修改发布源需要仓库的 **admin 或 maintainer** 权限。
- 项目站点的地址形如 `https://<username>.github.io/<repository>`；`github.io` 域名默认以 HTTPS 提供。
- 目标仓库 `Reborn202108/SurveyBudget` 的预期站点地址：`https://reborn202108.github.io/SurveyBudget/`（主机名不区分大小写，实际以 Pages 设置页显示为准）。

操作路径：

1. 把本目录内容放到仓库默认分支 `main` 的根目录，提交并推送。
2. 仓库 **Settings → Pages → Build and deployment → Source: Deploy from a branch**，分支选 `main`，目录选 `/ (root)`，保存。
   也可用 API 启用：`POST /repos/Reborn202108/SurveyBudget/pages`，请求体 `{"source":{"branch":"main","path":"/"}}`，需要带 `pages:write` 权限的令牌。
3. 不需要 GitHub Actions，也不需要特定分支命名；分支发布方式即官方推荐的无构建场景方案。
4. 首次发布可能需要等待一段时间（官方说明最长为 10 分钟），之后在 Pages 设置页确认站点地址，并在可用时启用 **Enforce HTTPS**。
5. 站点地址已按上述形态回填 §2 / E2；若 Pages 设置页显示的地址与此不同，需改回填值后重新推送。

## 已填写字段（精确到小节）

中文版 `privacy.html`：

| 位置 | 字段 | 已填值 |
|---|---|---|
| 页头 `.meta` | 生效日期 | `2026-11-19` |
| §2 运营者与联系方式 | 联系邮箱 | `jeachow@foxmail.com` |
| §2 运营者与联系方式 | 本政策公开地址 | `https://reborn202108.github.io/SurveyBudget/privacy.html` |
| §11 政策信息 | 联系邮箱 / 公开地址 / 生效日期 | 同上三项 |

英文版 `privacy.en.html`：

| 位置 | 字段 | 已填值 |
|---|---|---|
| 页头 `.meta` | Effective date | `2026-11-19` |
| E2 Operator and contact | Contact email | `jeachow@foxmail.com` |
| E2 Operator and contact | Public URL of this policy | `https://reborn202108.github.io/SurveyBudget/privacy.html` |
| E11 Policy information | Contact email / Public URL / Effective date | 同上三项 |

口径与内容处理记录：

- **运营者与境内合规**：名称口径、ICP/PIPL 提示属内部事项，见仓库之外的 `msix\store\policy-checklist.md` 第五节。政策正文不写具体版本号（统一表述为「通过 Microsoft Store 分发的当前版本」），实际版本以商店上架版本为准，避免发版后忘记同步。
- **§11 / E11**：公开页只保留四行信息表（运营者、联系邮箱、公开地址、生效日期），内部说明不随站点发布。
- **§12 / E12**：已删除原「卸载后窗口状态残留」内部修复说明。卸载后不保留业务数据这一承诺原本就写在 §7 / E7 与 §8 / E8，不需要重复补写。
- **变更记录**：Markdown 与 HTML 已逐条对齐，统一为 §12 / E12「变更记录」。原 Markdown §13 / E13 已改为 §12 / E12，原 §12 / E12 内部修复说明在两份文件中同步删除，小节编号保持连续。

## 发布后验证清单

1. **HTTP 状态**：`curl.exe -sS -o NUL -w "%{http_code} %{url_effective}\n" -L <站点URL>`，期望最终返回 `200` 且 `url_effective` 为最终地址。
2. **HTTPS 与证书**：`curl.exe -vI https://<站点域名>/` 查看 TLS 版本（1.2/1.3）与证书 SAN 是否包含该域名；浏览器地址栏无证书告警。
3. **HTTP 跳转**：`curl.exe -I http://<站点域名>/` 期望返回 `301` 并指向 `https://`。
4. **无登录可访问**：使用无痕窗口（未登录 GitHub）打开首页与两个政策页，均直接显示内容，不出现 GitHub 登录页。
5. **中英两版可达**：首页 → 中文 → 打印/返回 → English → 返回首页，所有跳转均 `200`，无 404。
6. **相对链接完整**：点击页内全部导航链接，确认 `assets/style.css` 正常加载（页面不是无样式裸文本）。
7. **无本地路径**：检索页面源码，确认 `href`/`src` 中不存在 `file://`、`C:\`、`D:\`、`localhost` 或本机绝对路径；正文中以文字形式描述 `127.0.0.1` 属内容本身，不是链接。
8. **编码正确**：中文页与英文页均声明 UTF-8，中文不出现乱码；英文页中的中文运营者名称正常显示。
9. **地址可长期引用**：用于 Partner Center 的 URL 不带查询参数、不带临时令牌、不依赖登录态；确认 `https://` 开头且无多余重定向。
10. **Pages 侧状态（需登录）**：`GET /repos/{owner}/{repo}/pages` 返回的 `status` 为 `built`、`https_certificate.state` 为 `approved`，与浏览器实际访问一致。

## 两个软件共用一份站点的建议

结论：**推荐一个仓库、两个子目录（`/kcsj/`、`/geo/`），根目录放一个总入口。** 不建议现在就把两份内容写进去。

理由：

- 一个仓库对应一个 Pages 站点，多份政策用子目录区分最省事，不需要第二套域名、证书与发布配置。
- 相对路径不受影响：从 `/` 进 `/kcsj/` 或 `/geo/` 都能用 `./`、`../` 表达，换仓库名无需改代码。
- 每款软件在 Partner Center 各填各自的 URL（`.../kcsj/privacy.html`、`.../geo/privacy.html`），互不覆盖。
- 公共样式只需维护一份，`assets/style.css` 放在根目录，两个子目录用 `../assets/style.css` 引用。

需要接受的代价：

- 项目站点的 URL 含仓库名，仓库改名后两个软件的链接会一起变，需要同步更新 Partner Center。
- 两套政策同仓同分支，一方改动会触发整站重新发布（静态站影响很小）。

备选方案：

- **两个独立仓库**：两套 URL 完全解耦，但要维护两份样式与发布设置，改版时容易漏改。
- **`<username>.github.io` 用户站点**：URL 固定为根域名，仓库改名不影响链接；代价是该账号只能有一个用户站点，所有静态内容都要放进同一仓库。若未来还有第三个软件或帮助页，这个方案最省心。

迁移方式（现在无需执行）：把当前三个 HTML 与 `assets/` 整体移入 `/kcsj/`，相对链接原样可用；新增 `/geo/` 时复制同一套骨架即可。

## 本轮边界

- 仓库由用户在 GitHub 上自行创建；本轮未创建仓库、未推送、未启用 Pages。
- 未修改任何原始正文文件（`privacy-policy.md` / `.html` / `.en.html`）。
- 未引入 CI、构建脚本或第三方依赖。
