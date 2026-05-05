# 搜索引擎切换助手 - 自用扩展版

> 本项目源自 [F9y4ng/GreasyFork-Scripts](https://github.com/F9y4ng/GreasyFork-Scripts)，基于其中的 **「优雅的搜索引擎助手」** (`Google & Baidu Switcher.user.js`) 进行个性化定制，适配我自身使用需求。

---

## 相较于原版的主要改动

### 1. 新增搜索引擎支持

| 搜索引擎 | 搜索类型 | 按钮样式 |
|---------|---------|---------|
| 哔哩哔哩 (Bilibili) | 综合搜索 | 统一浅蓝青渐变按钮 |
| 小红书 (Xiaohongshu) | 综合搜索 | 统一浅蓝青渐变按钮 |

新增的两个搜索引擎与原有引擎集成，支持在所有已支持的搜索引擎之间互相跳转。

### 2. 必应页面快捷跳转按钮

在必应 (Bing) 搜索结果页面的搜索框右侧，新增三个快捷跳转按钮：

```
[ Google | bilibili | 小红书 ]
```

点击即可将当前搜索关键词带到对应搜索引擎，无需重新输入。

同时对必应搜索框右侧按钮做了整理：隐藏用不到的语音搜索按钮，并将清除按钮移动到语音按钮位置，避免被快捷跳转按钮遮挡。

## 预览

![Bing 快捷跳转预览](images/Switcher/bing%20preview.png)

![Bilibili 搜索跳转预览](images/Switcher/bilibili%20preview.png)

### 3. 按钮视觉优化

对所有搜索引擎切换按钮和必应快捷跳转按钮进行了统一的视觉升级：

- 浅蓝青渐变背景：`#77A1D3` → `#79CBCA` → `#77A1D3`
- `background-size: 200% auto`
- Hover 状态切换到 `background-position: right center`
- 白色文字、无边框、柔和浅色阴影
- 保留各搜索引擎原有按钮尺寸和布局

### 4. 关闭自动更新

`@updateURL` 设为 `none`，防止被原版覆盖。

---

## 安装使用

1. 安装脚本管理器扩展（推荐 [Tampermonkey](https://www.tampermonkey.net/)）
2. 点击安装脚本：[`Switcher.user.js`](https://github.com/c858a673-53b4-4ff4-a4c6-e754893fb99b)

---

## 致谢

感谢 [F9y4ng](https://github.com/F9y4ng) 开发的原版「优雅的搜索引擎助手」。
