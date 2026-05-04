# 搜索引擎切换助手 - 自用扩展版

> 本项目源自 [F9y4ng/GreasyFork-Scripts](https://github.com/F9y4ng/GreasyFork-Scripts)，基于其中的 **「优雅的搜索引擎助手」** (`Google & Baidu Switcher.user.js`) 进行个性化定制，适配我自身使用需求。

---

## 相较于原版的主要改动

### 1. 新增搜索引擎支持

| 搜索引擎 | 搜索类型 | 按钮样式 |
|---------|---------|---------|
| 哔哩哔哩 (Bilibili) | 综合搜索 | 蓝色渐变 (`#00a1d6` → `#00d4ff`) |
| 小红书 (Xiaohongshu) | 综合搜索 | 红色渐变 (`#ff2442` → `#ff6b6b`) |

新增的两个搜索引擎与原有引擎集成，支持在所有已支持的搜索引擎之间互相跳转。

### 2. 必应页面快捷跳转按钮

在必应 (Bing) 搜索结果页面的搜索框右侧，新增三个快捷跳转按钮：

```
[ Google | bilibili | 小红书 ]
```

点击即可将当前搜索关键词带到对应搜索引擎，无需重新输入。

### 3. 按钮视觉优化

对所有新增按钮及 Google 搜索按钮进行了统一的视觉升级：

- 渐变背景色（各引擎品牌色渐变）
- `#f6f7f8` 浅灰描边，与原有按钮形成区分
- 文字阴影增加层次感
- Hover 状态：边框变白 + 阴影加强 + 上浮动效 (`translateY(-1px)`)
- `transition: all 0.3s ease` 平滑过渡

### 4. 关闭自动更新

`@updateURL` 设为 `none`，防止被原版覆盖。

---

## 安装使用

1. 安装脚本管理器扩展（推荐 [Tampermonkey](https://www.tampermonkey.net/)）
2. 点击安装脚本：[`Switcher.user.js`](Switcher.user.js)

---

## 致谢

感谢 [F9y4ng](https://github.com/F9y4ng) 开发的原版「优雅的搜索引擎助手」。
