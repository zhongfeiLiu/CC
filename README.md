# CC

Codex 多账号管理 + Claude Desktop 会话同步，一个 macOS 应用，常驻菜单栏。

*Manage several Codex accounts and keep Claude Desktop's local sessions in sync across your Claude accounts, in one macOS menu bar app.*

## 下载与安装

1. 到 [Releases](https://github.com/zhongfeiLiu/CC/releases/latest) 下载最新的 `CC_<版本>_universal.dmg`（Apple 芯片和 Intel Mac 通用）。
2. 打开 DMG，把 **CC** 拖进“应用程序”文件夹，然后从“应用程序”里打开。

安装包用 Developer ID 签名，并经过 Apple 公证，打开时不会被系统拦下。

## 功能

- **Codex**
  - 管理并切换多个 Codex 账号，查看各账号额度。
  - 本地 API：在本机提供兼容接口，供其他工具使用。
  - 唤醒任务、应用多开（多个 Codex 实例）、会话管理。
- **Claude 会话同步**
  - 让 Claude Desktop 的各个账号看到同一份本地 Code 会话。
  - 切换、添加账号，设置别名，让某个账号暂不参与轮换。
  - 查看用量（5 小时 / 每周），快照与恢复，对话记录保留设置。
  - 后台同步：登录时自动启动，不显示窗口。
- **模型供应商**
  - 只填 API Key 即可接入 OpenRouter 和 DeepSeek，其他供应商可手动添加。
  - 在 Codex 中使用，也可以一键让 Claude Code 改用它（可随时还原）。

## 注意

- **不要让其他程序与 CC 同时管理同一批 Codex 账号**：OpenAI 的 refresh token 只能用一次，一边刷新后，另一边保存的那份就失效了。
- **已经在用 CC Same？** CC 的会话同步引擎来自 [CC Same](https://github.com/songkeys/cc-same)，两者可以并存：
  - 在 CC 里点“接管”之前，CC 与 CC Same 共用它的数据，后台同步仍由 CC Same 负责。
  - 点“接管”后，CC 关闭 CC Same 的后台同步，把数据（含保存的登录）复制到自己的文件夹，CC Same 的原数据不动。
  - 之后如果又用 CC Same 同步或切换账号，CC 会暂停，直到再点一次“接管”。

## 数据位置

| 内容 | 位置 |
|---|---|
| Codex 账号、实例、设置 | `~/.cc-app` |
| Claude 会话同步 | `~/Library/Application Support/com.zhongfeiliu.cc/claude-sync` |
| 同步日志 | `~/Library/Logs/CC/` |

## 致谢

CC 基于以下开源项目，感谢作者们的贡献：

- [Cockpit Tools](https://github.com/jlcodes99/cockpit-tools)（jlcodes）：CC 的 Codex 功能基于它开发。
- [CC Same](https://github.com/songkeys/cc-same)（Songkeys）：CC 的 Claude 会话同步引擎来自它。
- [CLIProxyAPI](https://github.com/router-for-me/CLIProxyAPI)（Luis Pater / Router-For.ME）：本地 API 代理。

## 许可

CC 采用 [CC BY-NC-SA 4.0](LICENSE)（署名-非商业性使用-相同方式共享）：可以免费使用、分享和修改，但不得用于商业用途，分享改编版本时须注明出处并沿用同一许可。所用开源项目及其许可全文见 [NOTICE](NOTICE)。
