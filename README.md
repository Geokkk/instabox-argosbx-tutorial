# 在 InstaBox 上部署 ArgoSBX 固定隧道节点 · 小白教程

一份基于真实部署复盘的图文教程：在免费的 InstaBox 沙箱机上，用 Cloudflare Argo 固定隧道 + ArgoSBX 脚本（VMess-WS）搭一个自有域名直达的节点，含全程避坑细节与故障排查表。

📖 **在线阅读**：启用 GitHub Pages 后，本页即为教程正文（`index.html`）。

## 教程涵盖

- 为什么 InstaBox 上直连协议（Reality / Hysteria2 / TUIC）全灭、只有隧道能活
- Cloudflare 固定隧道的创建与 token 的安全传递（不经过任何聊天窗口）
- ArgoSBX 安装的关键变量与三大实测坑：
  - `argo` 变量必须填协议名（如 `argo=vmpt`），不是填 `y`
  - 改变量重跑安装无效，必须用脚本自带的 `rep` 重置
  - 480 分钟上限的冷却报错不是失败
- Public Hostname 的五字段确切填法
- 验证标准：根路径 404 是好消息、WS 握手 101 才算贯通
- 日常维护、故障排查表与账号风险提示

## 环境与版本

- InstaBox 免费机器（4 核 / 8G，Debian 13）
- ArgoSBX V26.7.16（2026 年 10 月实测）
- 教程中的域名均为示例（example.com），请替换为你自己的

## 致谢

- ArgoSBX 脚本：[yonggekkk/argosbx](https://github.com/yonggekkk/argosbx)
- 平台：[InstaBox](https://instabox.sh)
