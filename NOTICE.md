# NOTICE — 版权与修改声明

本文件依据 **GNU General Public License v3.0** 第 5 条（§5 Conveying Modified Source Versions）
的要求，说明本衍生作品的来源与修改内容。

---

## 一、上游作品

| 项目 | 内容 |
|---|---|
| 作品名称 | NocturneMenu（原名 OnyxMenu） |
| 原作者 | Veltrix-s |
| 项目主页 | https://github.com/Veltrix-s/OnyxMenu |
| 官网 | https://onyxmenu.kawas-set.workers.dev/ |
| 原作者 Discord | https://discord.gg/cP4MrVUfM7 |
| 本项目基于的版本 | v1.3.0 |
| 上游许可 | GNU General Public License v3.0 |
| 上游版权声明 | Copyright (C) Veltrix-s |

上游 `LICENSE` 文件已原样完整保留于本仓库根目录，未作任何改动。

---

## 二、本衍生作品

| 项目 | 内容 |
|---|---|
| 作品名称 | NocturneMenu 简体 / 繁體 汉化 |
| 汉化作者 | [你的网名] |
| 首次发布日期 | 2026-11-20 |
| 最后修改日期 | 2026-11-22 |
| 本作品许可 | GNU General Public License v3.0（与上游一致） |
| 作品性质 | 非官方本地化补丁，非上游发布物 |

---

## 三、修改内容说明

本衍生作品**未修改上游的任何源代码文件**，也未重新编译任何程序集。
所有改动均通过对上游编译产物（`NocturneMenu_v1.3.0.dll`）的
.NET 元数据 `#US`（User String）堆进行**字符串替换**实现。

具体修改如下：

### 3.1 修改对象

- 文件：`NocturneMenu_v1.3.0.dll`（上游 Release 发布的编译产物）
- 区域：PE 文件偏移 `0xEA0F8` 起、长度 `0x33AAC` 的 `#US` 字符串堆
- 数量：共替换 **3358 条** UTF-16 字符串字面量

### 3.2 未修改的部分

以下内容全部保持上游原样，一个字节都没有改动：

- 全部 IL 指令（`ldstr` 的 token 偏移因此保持有效）
- 全部元数据表（`#~`、`#Strings`、`#Blob`、`#GUID`）
- PE 头部、节表、文件总长度（与原文件逐字节等长）
- 内嵌资源（82 项，含纹理、地图网格 JSON、依赖 DLL）

验证方式：对整个文件做逐字节比对，差异 100% 落在 `#US` 堆区间内。

### 3.3 修改目的

将界面文案从英文 / 俄文更改为简体中文与繁體中文，方便中文玩家使用。
功能、行为、性能与原版完全一致。

### 3.4 翻译数据的对应源码

GPL-3.0 要求提供修改的「对应源码」。本项目的对应源码为：

```
tools/patch_strings.py                     字符串堆补丁工具
tools/translations/zh_CN.json              简体中文翻译表（3358 条）
tools/translations/zh_TW.json              繁體中文翻译表（3358 条）
tools/translations/zh_CN_zh_TW_dual.json   简繁双槽翻译表（3358 条）
```

任何人可以用上述脚本与翻译表，对官方 DLL 执行一遍即可**逐字节复现**
本仓库 `dist/` 下的全部汉化文件。构建方式见 README 的「自己构建」章节。

### 3.5 附加组件

`dist/NocturneCnFont.dll` 为本项目**原创编写**的独立 BepInEx 插件，
不属于上游作品，用于在系统字体中查找中文字体以渲染 GUI 文本。
该组件同样以 GPL-3.0 发布。

---

## 四、商标与第三方权利

- **Among Us** 为 **Innersloth LLC** 的注册商标与著作权作品。
  本项目不含、不分发游戏的任何原始资源文件。
- **BepInEx**、**HarmonyX** 归各自作者所有。
- 本项目与 Innersloth、Veltrix-s 均无隶属、合作或授权关系。

---

## 五、免责

本作品按「现状」提供，不附带任何担保。使用者自行承担全部风险。
详见 README 的「免责声明」章节。

如权利人认为本衍生作品存在不妥，请通过 Issues 联系，将立即配合处理。
