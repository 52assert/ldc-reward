# Linux.do LDC 打赏助手

一个为 Linux.do 社区帖子添加 LDC 打赏按钮的油猴脚本。

本仓库是 `ldc-reward` 的 fork 维护版，由 dream 维护。原脚本作者为 [@tbphp](https://linux.do/u/tbphp)，本版本基于原脚本修改，许可证保持 MIT。

## 安装

[点击安装 Greasy Fork 版本](https://greasyfork.org/en/scripts/579871-linuxdo-%E6%89%93%E8%B5%8F%E5%8A%A9%E6%89%8B)

也可以手动安装：

1. 安装 Tampermonkey / Violentmonkey 等用户脚本管理器。
2. 打开 [`ldc-reward.user.js`](./ldc-reward.user.js)。
3. 复制脚本内容，新建用户脚本并粘贴保存。
4. 打开 `https://linux.do/` 的帖子页面使用。

## 功能

- 在 Linux.do 帖子楼层操作区添加“打赏”按钮。
- 支持快捷金额和自定义金额。
- 使用 Linux.do Credit 商户后台的 `Client ID` / `Client Secret` 发起打赏。
- 适配新版接口 `https://credit.linux.do/lpay/distribute`。
- 修复严格 CSP 下内联事件处理器被拦截的问题。
- 降低动态页面刷新时重复扫描带来的卡顿风险。

## 使用方法

1. 前往 Linux.do Credit 商户后台创建应用，获取 `Client ID` 和 `Client Secret`。可参考 [官方文档](https://credit.linux.do/docs/how-to-use)。
2. 安装并启用本脚本。
3. 刷新 Linux.do 帖子页面。
4. 首次使用时按提示填入 `Client ID` 和 `Client Secret`。
5. 配置完成后，每个可打赏楼层的操作区会出现“打赏”按钮。

## 安全说明

- `Client ID` / `Client Secret` 通过用户脚本管理器的本地存储保存。
- 脚本不会保存 Cookie。
- 脚本只会向 `credit.linux.do` 发起打赏请求。
- 请不要把自己的 `Client Secret`、`Authorization` 或 Cookie 提交到仓库、Issues 或评论区。

## 变更说明

相对原脚本，本版本主要修改：

- 接口从旧路径改为 `https://credit.linux.do/lpay/distribute`。
- 移除 `onfocus`、`onblur`、`onmouseover`、`onmouseout` 等内联事件，避免触发 Linux.do 的严格 CSP。
- 配置只保留 `Client ID` 和 `Client Secret`，脚本自动生成 `Authorization: Basic ...`。
- 请求头尽量贴近 Credit 站点页面请求环境。
- 403 或解析失败时输出更详细的控制台日志，方便排查。
- 对用户昵称、头像链接等展示内容做基础转义和校验。

## 致谢

感谢原作者 [@tbphp](https://linux.do/u/tbphp) 编写并开源 LINUXDO 打赏助手。本仓库在原脚本基础上做兼容性修复和维护。

## 友情链接

- [LINUX DO - 新的理想型社区](https://linux.do/)

## License

MIT
