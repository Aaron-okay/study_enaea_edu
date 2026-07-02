# ENAEA Study Assistant

<div align="center">

# 🚀 ENAEA Study Assistant

**适用于广东省学习公社在线学习平台的 Python 学习辅助工具**

> ⚠️ 当前版本 **不支持倍速学习**，程序将按照平台正常学习节奏发送学习心跳。

<br>

![Python](https://img.shields.io/badge/Python-3.9+-3776AB?logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-广东省学习公社-00A86B)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Version](https://img.shields.io/badge/Version-v1.0.0-blue)
![Status](https://img.shields.io/badge/Status-Maintained-success)

</div>

---

> [!WARNING]
>
> **本项目仅供学习交流与技术研究使用，请勿用于任何商业用途或违反平台相关规定的行为。**

---

# 📚 目录

- [✨ 功能特点](#features)
- [⚙️ 工作原理](#️work)
- [💻 环境要求](#requirements)
- [📦 安装依赖](#installation)
- [🚀 快速开始](#quick-start)
- [⚠️ 注意事项](#️notes)
- [❓ 常见问题（FAQ）](#faq)
- [🛣 开发计划](#roadmap)
- [📄 免责声明](#disclaimer)

---

# ✨ <a id="features">功能特点</a>

✔ 自动登录平台账号

✔ 自动获取未完成培训项目

✔ 自动分析章节学习状态

✔ 自动计算章节剩余学习时长

✔ 使用动态规划算法自动规划课程

✔ 自动选择最优视频学习方案

✔ 自动发送学习心跳

✔ 实时统计学习进度


---

# ⚙️ <a id="work">工作原理</a>

程序整体工作流程如下：

```text
账号登录
    │
    ▼
获取 Cookie
    │
    ▼
获取培训项目（circleId）
    │
    ▼
获取章节列表
    │
    ▼
分析学习进度
    │
    ▼
计算剩余学习时长
    │
    ▼
获取课程列表
    │
    ▼
动态规划课程组合
    │
    ▼
获取视频列表
    │
    ▼
动态规划视频组合
    │
    ▼
模拟学习心跳
    │
    ▼
更新学习进度
```

> [!TIP]
>
> 本程序不会直接修改服务器数据，而是模拟浏览器正常学习过程中产生的网络请求，因此整体流程更加接近真实学习行为。

---

# 💻 <a id="requirements">安装依赖</a>

| 项目 | 要求 |
|------|------|
| 推荐版本 | Python 3.10 / 3.11 |
| 操作系统 | Windows / Linux / macOS |

---

# 📦 # ✨ <a id="installation">安装依赖</a>

推荐使用 **pip** 安装：
```bash
pip install requests beautifulsoup4
```

---

# 🚀 <a id="quick-start">快速开始</a>

## Step 1：获取 Cookie

首先进入学习平台：

> https://www.study.enaea.edu.cn/login.do

登录成功以后，进入任意课程页面。

随后按下：

- <kbd>F12</kbd>
- 或 <kbd>Fn</kbd> + <kbd>F12</kbd>

打开开发者工具。

然后依次点击：

```text
Network（网络）
      ↓
刷新页面（F5）
      ↓
在搜索栏中搜索："sensorsdata2015
      ↓
Headers
      ↓
Request Headers
      ↓
Cookie
```

如下图所示：

<p align="center">
<img width="100%" src="https://github.com/user-attachments/assets/20baa6db-a97b-4111-9c20-11f07ed8723b">
</p>

复制完整 Cookie，例如：

```python
cookie = "sensorsdata2015jssdkcross=......"
```

然后修改程序：

```python
cookie = ""
```

改为：

```python
cookie = "你的Cookie"
```

保存即可。

> [!IMPORTANT]
>
> Cookie 仅首次使用时需要配置。
>
> 如果切换其它账号，则必须重新获取新的 Cookie。

---

## Step 2：配置账号

修改程序中的账号密码：

```python
login_name = "手机号"

password = "登录密码"
```

---

## Step 3：运行程序

执行：

```bash
python enaea_edu-beta.py
```


# ⚠️ <a id="notes">注意事项</a>

## 学习心跳

程序默认每 **60 秒** 发送一次学习心跳：

```python
watch_videos(interval=60)
```

如需修改：

```python
watch_videos(interval=30)
```

> [!WARNING]
>
> 不建议修改为过小的数值。
>
> 平台默认约 **60 秒** 接收一次学习心跳。
>
> 若发送过于频繁，可能出现：
>
> ```text
> request frequently!
> ```
>
> 从而导致学习失败。

---

# ❓ <a id="faq">常见问题</a>

<details>

<summary><strong>❓ VR 类型课程无法学习？</strong></summary>

目前版本暂不支持 **VR（external_link）** 类型课程。

后续版本将逐步支持。

</details>

<details>

<summary><strong>❓ 学习进度没有增加？</strong></summary>

请检查：

- Cookie 是否失效；
- 平台接口是否更新；
- 是否修改了学习间隔；
- 当前课程是否属于 Video 类型；
- 网络是否正常。

建议保持默认 **60 秒** 心跳。

</details>

---

# 🛣 <a id="roadmap">开发计划</a>

- [ ] 支持类型为： external_link（VR）课程
- [ ] 自动更新 Cookie
- [ ] 配置文件支持
- [ ] 多账号支持


---

# 📄 <a id="disclaimer">免责声明</a>

> [!CAUTION]
>
> **本项目仅供学习、技术研究及接口分析交流使用。**

本项目涉及的所有接口、请求流程均来源于浏览器正常访问网页过程中产生的网络请求，仅用于学习以下内容：

- Python 自动化开发
- HTTP/HTTPS 网络请求
- Cookie 管理
- Web 页面解析
- 接口分析与逆向研究

请在使用本项目之前，确保已阅读并理解目标平台的用户协议、服务条款及相关法律法规。

## 严禁用于以下用途

- ❌ 商业用途
- ❌ 营利活动
- ❌ 绕过平台正常学习要求
- ❌ 干扰平台正常运行
- ❌ 违反国家法律法规
- ❌ 违反平台使用协议

> [!IMPORTANT]
>
> 使用本项目所产生的一切后果（包括但不限于账号异常、账号封禁、学习记录异常、法律责任等），均由使用者本人自行承担，与项目作者无关。

若目标平台认为本项目存在侵权或违规行为，请及时联系项目维护者，本项目将第一时间进行处理或删除相关内容。

下载、安装、运行或修改本项目，即视为您已阅读、理解并同意本免责声明的全部内容。
