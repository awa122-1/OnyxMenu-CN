<div align="center">

# NocturneMenu 简体 / 繁體 汉化

**NocturneMenu（原名 OnyxMenu）v1.3.0 中文语言包**

非官方汉化补丁 · 基于上游开源代码制作

[**原模组**](https://github.com/Veltrix-s/OnyxMenu) · [**原模组官网**](https://onyxmenu.kawas-set.workers.dev/) · [**原模组 Discord**](https://discord.gg/cP4MrVUfM7)

![License](https://img.shields.io/badge/license-GPL--3.0-blue)
![Version](https://img.shields.io/badge/upstream-v1.3.0-informational)
![Platform](https://img.shields.io/badge/platform-Windows-lightgrey)

</div>

---

## 目录

- [这是什么](#这是什么)
- [下载哪个版本](#下载哪个版本)
- [汉化了哪些内容](#汉化了哪些内容)
- [安装教程](#安装教程)
- [中文显示成方块怎么办](#中文显示成方块怎么办)
- [已知取舍](#已知取舍)
- [卸载 / 还原](#卸载--还原)
- [自己构建](#自己构建)
- [更新日志](#更新日志)
- [鸣谢](#鸣谢)
- [免责声明](#免责声明)
- [开源协议](#开源协议)
- [相关文档](#相关文档)

---

## 这是什么

这是 [NocturneMenu](https://github.com/Veltrix-s/OnyxMenu) v1.3.0 的**非官方简体 / 繁体中文汉化补丁**。

NocturneMenu 是《Among Us》的一个客户端模组菜单（BepInEx 6 + .NET 6，IL2CPP），
原版只带英文和俄文两种界面语言。本项目把这两套文案全部改写为中文。

汉化方式：**只替换 DLL 内部字符串表（#US 堆）里的文本，不改动任何一行 IL 逻辑代码**。
因此功能、行为、性能与原版完全一致，出现 bug 时也基本可以判定与原版相同。

> ⚠️ **上传前请把本文件里的 `[你的网名]` 替换成你真实的网名**（共 2 处，另一处在 NOTICE.md）
>
> 汉化作者：**[你的网名]**
> 汉化版本：v1.3.0
> 上游版本：[Veltrix-s/OnyxMenu](https://github.com/Veltrix-s/OnyxMenu) v1.3.0

---

## 下载哪个版本

到 [Releases](../../releases) 页面下载，或在 `dist/` 目录里取用。

| 文件 | 界面语言 | 说明 |
|---|---|---|
| `NocturneMenu_v1.3.0_CN-TW.dll` | 简 / 繁 可切换 | **推荐**。语言开关变身为简繁切换 |
| `NocturneMenu_v1.3.0_CN.dll` | 全简体 | 两个语言槽都是简体中文 |
| `NocturneMenu_v1.3.0_TW.dll` | 全繁體 | 两个语言槽都是繁體中文 |
| `NocturneCnFont.dll` | — | 可选中文字体补丁，中文显示成方块时才需要 |

**三个 DLL 只能装一个**，同时放进 `plugins` 会造成重复加载报错。

### 简繁双版怎么切换

装 `_CN-TW.dll` 之后，进菜单 → 实用 / Interface → `Language`：

| Language 选项 | 实际显示 |
|---|---|
| `English` | 简体中文（默认） |
| `Русский` | 繁體中文 |

繁体的用字采用台湾正体（`設置`、`開啟`、`滾輪`、`船員鑽管`），
但**保留游戏内原有术语**，没有套用「網路 / 記憶體」那类台湾词汇替换，
避免和游戏本体与社区通用叫法对不上。

---

## 汉化了哪些内容

原版用 `NocturneText.T(俄文, 英文)` 这个双语函数写死了全部界面文案，
本项目把两个参数分别换成简体与繁体，共处理 **3358 条字符串**：

| 类别 | 数量 | 举例 |
|---|---|---|
| 菜单标签 / 按钮 | 1447 组文本对 | `Kill` → `击杀`、`Vent kick` → `管道踢` |
| 设置项名称 | 484 项 | `Ant walk` → `蚂蚁走`、`Teleport on RMB` → `右键传送` |
| 设置项说明（悬停提示） | 484 条 | 每个开关背后的长段解释文字 |
| 左侧导航页签 | 9 项 | `Home` → `首页`、`Guard` → `守护` |
| 弹出提示 / Toast | 300+ 条 | `Done.` → `完成。`、`Meeting called.` → `已召开会议。` |
| 聊天命令帮助 | 十余条 | `/help`、`/w`、`/color` 的用法说明 |
| 设置分节名 | 21 项 | `Visual` → `视觉`、`Cheats` → `作弊` |

覆盖范围包括：大厅与房主工具、玩家操作、ESP 与视觉、聊天系统、对局回放、
音乐播放器、作弊功能、防护与伪造、外观与主题等全部设置页面。

### 没有被翻译的部分

以下几类字符串**故意保留英文**，因为它们是程序内部的身份标识，
翻译后会直接导致功能失效：

| 字符串 | 用途 |
|---|---|
| `Ban` `Null` `Warn` `normal` | 下拉选项的取值，会和存档里的值做字符串比对 |
| `results` | 解析 JSON（如 Windows 媒体查询结果）用的属性名 |
| `ChocooMenu` | 识别其他模组用户的比对标识 |
| `Игрок` `Реклама` `Advertisement` | 识别游戏原生内容的比对标识 |

所以设置里的个别下拉框选项仍是英文，这是有意为之，不是漏翻。

---

## 安装教程

### 前置条件

1. **《Among Us》Steam 正版**（或同版本客户端）
2. **BepInEx 6**（IL2CPP 版）已正确安装
3. 已安装原版 **NocturneMenu v1.3.0**

> 如果你还没装过原版模组，请先按[原项目文档](https://github.com/Veltrix-s/OnyxMenu)把
> BepInEx 和 NocturneMenu 装好，确认按 `Insert` 能呼出英文菜单，再来装汉化。

### 安装步骤

1. 打开游戏目录下的插件文件夹：

   ```
   <游戏目录>\BepInEx\plugins\
   ```

2. **备份**原版文件，把 `NocturneMenu_v1.3.0.dll` 改名为：

   ```
   NocturneMenu_v1.3.0.dll.bak
   ```

3. 把本项目的汉化 DLL 复制进去（**三选一**）：

   ```
   BepInEx\plugins\NocturneMenu_v1.3.0_CN-TW.dll
   ```

4. 启动游戏，进入主菜单，按 **`Insert`** 呼出菜单。

5. 若中文显示为方块，再把 `NocturneCnFont.dll` 也放进 `plugins`，重启游戏。

### 安装检查清单

- [ ] `plugins` 目录里**只有一个** NocturneMenu 的 DLL
- [ ] 备份文件 `.bak` 不会被 BepInEx 加载（改后缀即可）
- [ ] `BepInEx\LogOutput.log` 里没有红色报错
- [ ] 按 `Insert` 能弹出菜单

---

## 中文显示成方块怎么办

菜单使用 Unity IMGUI 即时绘制文字，默认字体不含汉字，可能出现 `□□□`。

**解决办法**：把 `dist/NocturneCnFont.dll` 放进 `BepInEx\plugins\`，重启游戏。

它会从系统里按顺序查找可用字体渲染中文：

```
Microsoft YaHei UI → Microsoft YaHei → DengXian → SimHei → SimSun
→ Noto Sans CJK SC → Source Han Sans SC → PingFang SC → WenQuanYi Micro Hei
```

这个补丁只接管 GUI 字体，不影响其他任何功能；若不想要，直接删掉即可。

---

## 已知取舍

诚实说明几个无法两全的地方：

1. **部分设置分节的强调色会回落为默认浅灰**
   原版用 `switch(分节名)` 给每个设置分节分配主题色，编译器把它优化成了
   「按字符串长度 + 首字母」的分派表。分节名翻成中文后长度改变，
   这些分节会落到 default 分支。**只影响配色，不影响任何功能与开关。**

2. **设置项说明只有一份**
   悬停提示文字在原版里不是双语的，只有一条英文。本项目将其译成简体，
   切到繁体时这部分仍显示简体。

3. **3 条文案无法分槽**
   `God Mode`、`Quick Chat`、`—` 在原版里两个语言槽共用同一个字面量，
   DLL 内部只有一份存储，因此只能固定为一种语言（本项目固定简体）。

4. **不支持动态本地化切换**
   切换语言后部分缓存文本可能需要重开菜单或重启游戏才会刷新，
   这是原版机制，非汉化引入。

---

## 卸载 / 还原

1. 删除 `BepInEx\plugins\` 里的汉化 DLL
2. 把 `NocturneMenu_v1.3.0.dll.bak` 改回 `NocturneMenu_v1.3.0.dll`
3. （若装过）删除 `NocturneCnFont.dll`
4. 重启游戏

配置文件 `BepInEx\config\` 里的设置不受影响，会原样保留。

---

## 自己构建

本项目遵循 GPL-3.0，完整提供可复现的构建材料。你不需要自己翻译，
只要有一份官方 DLL 就能生成汉化文件。

### 需要

- Python 3.8+（无第三方依赖）
- 官方 `NocturneMenu_v1.3.0.dll`

### 步骤

```bash
# 1. 从上游 Releases 下载官方 DLL
#    https://github.com/Veltrix-s/OnyxMenu/releases

# 2. 生成汉化版（自动定位 #US 堆偏移）
python3 tools/patch_strings.py NocturneMenu_v1.3.0.dll output.dll \
        tools/translations/zh_CN_zh_TW_dual.json

# 3. 也可显式指定堆偏移（v1.3.0 的值）
python3 tools/patch_strings.py NocturneMenu_v1.3.0.dll output.dll \
        tools/translations/zh_CN.json --heap-offset 0xEA0F8 --heap-size 0x33AAC
```

### 原理简述

.NET 元数据的 `#US`（User String）堆按「压缩长度前缀 + UTF-16 + 1 字节标志」
存放字符串，`ldstr` 指令的操作数就是该堆内的字节偏移。

因此只要**把译文写进原记录占用的空间、剩余字节补 0**
（元数据读取器遇到长度为 0 的记录会直接跳过），
所有后续记录的偏移都保持不变，**完全不需要修改任何 IL 指令**。

这也是本项目能做到「只改文字、不动逻辑」的原因。

### 想改译文

直接编辑 `tools/translations/*.json` 即可，格式是 `{"原文": "译文"}`。
注意译文长度不能超过原文长度（受堆空间限制），脚本会自动跳过超长项。

---

## 更新日志

### v1.3.0-cn.3（当前）

- 补全左侧导航页签汉化（`首页 / 实用 / 大厅 / 视觉 / 玩家 / 作弊 / 守护 / 伪造 / 房主`）
- 修复：早期版本误翻了参与运行时比对的常量（`Player` / `Lobby` / `Host` 等），
  会导致菜单无法呼出。现已全部还原为原文。
- 新增纯繁體版本
- 开源：附完整构建脚本与翻译表

### v1.3.0-cn.2

- 新增繁体中文（双语言槽：English=简体，Русский=繁體）

### v1.3.0-cn.1

- 首次发布，完成 3300+ 条文案简体化

---

## 鸣谢

- **[Veltrix-s](https://github.com/Veltrix-s)** — NocturneMenu 原作者，本项目的一切基础
- **BepInEx / HarmonyX 团队** — 模组加载与运行时补丁框架
- **OpenCC** — 简繁转换用字表

---

## 免责声明

> **⚠️ 请在使用前完整阅读以下内容**

1. **仅供学习与技术交流**
   本项目为个人学习 .NET 元数据结构、字符串堆格式与软件本地化技术的产物，
   仅供学习、研究与技术交流使用。

2. **关于商业用途的请求**
   作者**恳请**使用者不要将本项目（含翻译文本、构建脚本、编译产物）
   用于售卖、付费下载、捆绑销售、会员专享等经济获利行为。

   > ⚠️ **重要说明**：以上仅为作者的个人意愿表达，
   > **不构成对 GPL-3.0 的附加限制**，也不改变 GPL-3.0 赋予你的任何权利。
   > 依据 GPL-3.0 第 7 条，本作品不得附带协议之外的额外限制。

3. **非官方作品**
   本项目与 **Innersloth**（《Among Us》开发商）、**Veltrix-s**（NocturneMenu 作者）
   均无任何隶属、合作或授权关系。所有商标、游戏素材与原始代码归各自权利人所有。

4. **使用风险自负**
   使用第三方模组可能违反游戏的服务条款，存在账号被处罚、封禁的风险。
   《Among Us》官方服务器可能检测或拒绝模组客户端。
   **请仅在私人大厅、与朋友同乐或单人测试环境使用，勿在公开对局中影响他人游戏体验。**
   因使用本项目产生的一切后果（含账号封禁、数据丢失、设备损坏）由使用者自行承担，
   汉化作者不承担任何责任。

5. **无担保**
   本项目按「现状」提供，不附带任何明示或暗示的担保，包括但不限于
   适销性、特定用途适用性与非侵权担保。

6. **版权归属**
   NocturneMenu 的著作权归 Veltrix-s 所有，依 GPL-3.0 授权。
   本汉化仅是对其字符串资源的本地化修改，不主张对原作品的任何权利。
   如权利人认为本项目不妥，请联系删除，本项目将立即配合下架。

---

## 开源协议

本项目是 [NocturneMenu](https://github.com/Veltrix-s/OnyxMenu) 的衍生作品，
依上游授权，整体以 **[GNU General Public License v3.0](LICENSE)** 发布。

这意味着你可以自由地使用、修改、再分发本项目，但必须：

- 保留原始版权声明与许可声明（见 [LICENSE](LICENSE) 与 [NOTICE.md](NOTICE.md)）
- 同样以 GPL-3.0 发布你的修改版本
- **公开你修改后的完整源代码**（本项目的对应源码即 `tools/` 下的构建脚本与翻译表）
- 说明你做了哪些修改、修改日期
- 不得附加 GPL-3.0 之外的额外限制

详细条款见 [LICENSE](LICENSE)。

---

## 相关文档

| 文档 | 内容 |
|---|---|
| [docs/upload-guide.md](docs/upload-guide.md) | **手机上如何把本仓库上传到 GitHub**（网页版 / Termux 全流程） |
| [docs/license-guide.md](docs/license-guide.md) | **上传模组汉化前必须搞清楚的协议问题**（GPL-3.0 义务清单） |
| [NOTICE.md](NOTICE.md) | 来源声明与逐项修改说明（GPL-3.0 §5 要求） |
| [tools/patch_strings.py](tools/patch_strings.py) | 构建脚本（复现汉化文件用） |

---

<div align="center">

**如果这个汉化对你有帮助，给个 ⭐ Star 吧**

[⬆ 回到顶部](#nocturnemenu-简体--繁體-汉化)

</div>
