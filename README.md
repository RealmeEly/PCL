# Plain Craft Launcher

[![Stars](https://img.shields.io/github/stars/Meloong-Git/PCL?style=flat&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiI+PHBhdGggZD0iTTggLjI1YS43NS43NSAwIDAgMSAuNjczLjQxOGwxLjg4MiAzLjgxNSA0LjIxLjYxMmEuNzUuNzUgMCAwIDEgLjQxNiAxLjI3OWwtMy4wNDYgMi45Ny43MTkgNC4xOTJhLjc1MS43NTEgMCAwIDEtMS4wODguNzkxTDggMTIuMzQ3bC0zLjc2NiAxLjk4YS43NS43NSAwIDAgMS0xLjA4OC0uNzlsLjcyLTQuMTk0TC44MTggNi4zNzRhLjc1Ljc1IDAgMCAxIC40MTYtMS4yOGw0LjIxLS42MTFMNy4zMjcuNjY4QS43NS43NSAwIDAgMSA4IC4yNVoiIGZpbGw9IiNlYWM1NGYiLz48L3N2Zz4=&logoSize=auto&label=Stars&labelColor=444444&color=eac54f)](https://github.com/Meloong-Git/PCL/)
[![Issues](https://img.shields.io/github/issues/Meloong-Git/PCL?style=flat&label=Issues&labelColor=444444&color=1F883D)](https://github.com/Meloong-Git/PCL/issues)
[![哔哩哔哩](https://img.shields.io/badge/动态-BiliBili-00A4DB?style=flat&labelColor=444444&logoSize=auto)](https://space.bilibili.com/11343203/dynamic)
[![爱发电](https://img.shields.io/badge/赞助-爱发电-946ce6?style=flat&labelColor=444444&logoSize=auto)](https://meloong.com/afd/a/LTCat)

包含 PCL 的大部分源代码，包括 UI 库、动画模块、下载模块、Minecraft 启动模块等！<br/>
代码并不是实时更新的，它会在每次 PCL 发布更新时同步一次。<br/>
非常感谢社区的大力支持！

<br/>

### 相关资源
- [PCL 下载](https://meloong.com/pcl)：下载可免费使用的正式版 PCL！
- [PCL 功能投票](https://github.com/Meloong-Git/PCL/discussions/2)：来参加投票吧，开发者会优先处理票数较高的项目！
- [帮助文档库](https://github.com/LTCatt/PCL2Help)：PCL 内置帮助文档的存储库

---

## 非官方改版操作说明（RealmeEly fork）

> **注意：以下内容仅适用于 RealmeEly 的非官方改版，不是 PCL 官方说明。**
> 本改版与 Mojang、Microsoft 及 PCL 上游维护者无关联。

### 首次使用：配置可选的微软 Client ID / CurseForge API Key

本改版不内置以下密钥，相关功能需要手动配置：

| 环境变量 | 用途 |
|---|---|
| `PCL_MS_CLIENT_ID` | 微软正版登录 |
| `PCL_CURSEFORGE_API_KEY` | CurseForge 搜索与下载 |

#### 方式一：Windows 图形界面（推荐，纯鼠标，永久生效）

1. 按 `Win + R`，输入 `sysdm.cpl`，回车。
2. 打开 **“高级”** 选项卡，点击 **“环境变量...”**。
   - Windows 11 也可以：设置 → 系统 → 系统信息 → 高级系统设置 → 环境变量。
3. 在 **“用户变量”** 区域点击 **“新建...”**（不要用“系统变量”）。
4. 添加微软登录 Client ID：
   - 变量名：`PCL_MS_CLIENT_ID`
   - 变量值：你的 Client ID
   - 点击“确定”。
5. 再次点击 **“新建...”**，添加 CurseForge API Key：
   - 变量名：`PCL_CURSEFORGE_API_KEY`
   - 变量值：你的 API Key
   - 点击“确定”。
6. 所有窗口点击“确定”保存。
7. **完全退出 PCL**，再重新打开。

#### 方式二：CMD 的 `setx`（永久生效，不需要 PowerShell）

按 `Win + R`，输入 `cmd`，回车，然后执行：

```cmd
setx PCL_MS_CLIENT_ID "你的 Client ID"
setx PCL_CURSEFORGE_API_KEY "你的 API Key"
```

说明：

- `setx` 会永久写入**当前用户**的环境变量。
- 不会影响已经打开的 CMD 窗口或正在运行的 PCL；请重新打开 PCL。
- 不要加 `/M`（`/M` 是系统变量，需要管理员权限）。
- 值建议用英文双引号包起来。

#### 验证（`echo` 只读取，不会设置）

新开一个 `cmd` 窗口，执行：

```cmd
echo %PCL_MS_CLIENT_ID%
echo %PCL_CURSEFORGE_API_KEY%
```

能输出对应值说明新进程可以读取到环境变量；`echo` 本身不会创建或保存任何设置。

#### PowerShell 方式（可选）

```powershell
[Environment]::SetEnvironmentVariable("PCL_MS_CLIENT_ID", "<你的 Client ID>", "User")
[Environment]::SetEnvironmentVariable("PCL_CURSEFORGE_API_KEY", "<你的 API Key>", "User")
```

#### 注意事项

- 使用 **“用户变量”** 即可，不需要管理员权限。
- 变量名必须完全一致，前后不要有空格。
- 变量值直接粘贴原始 ID/Key，不要加引号或尖括号（在 `setx` 命令中可用双引号包裹）。
- 如果同名变量已存在，选中后点击 **“编辑...”**，不要重复新建。
- 环境变量只在程序启动时读取，设置后必须完全重启 PCL。
- 如果仍不生效，注销 Windows 再登录，或重启资源管理器。
- CurseForge API Key 属于敏感信息，不要截图或发到公开 issue。

