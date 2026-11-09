# 漫匣

一款在 Android 和 Windows 上独立运行的漫画搜索、下载与离线阅读工具。把在线章节和本地漫画整理进同一个书架，下载后无需联网即可阅读。

## 下载

当前正式版：**1.2.3**。本地开发版为 **1.2.4**（新增漫画人、修复 YY 空章节标题），尚未发布；以下链接指向已发布安装包。

| 平台               | 下载直达                                                     | 使用方式                                        |
| ------------------ | ------------------------------------------------------------ | ----------------------------------------------- |
| Android 8.0 及以上 | [下载 APK](https://github.com/QAQ767/manga-pocket-releases/releases/download/v1.2.3/manga-pocket-1.2.3.apk) | 打开安装；已有旧版可直接覆盖，保留书架          |
| Windows x64        | [下载便携版 ZIP](https://github.com/QAQ767/manga-pocket-releases/releases/download/v1.2.3/manga-pocket-1.2.3-windows-x64.zip) | 完整解压后运行 `MangaPocket.exe`，无需另装 Java |

[最新发布页](https://github.com/QAQ767/manga-pocket-releases/releases/latest) · [历史版本与更新说明](https://github.com/QAQ767/manga-pocket-releases/releases) · [SHA-256 校验文件](https://github.com/QAQ767/manga-pocket-releases/releases/download/v1.2.3/SHA256SUMS.txt)

升级前无需卸载；Windows 请先退出程序，再替换程序文件。安装包下载需要能够访问 GitHub。

## 能做什么

- **搜索与下载**：按漫画名称或作者查找作品，选择章节下载，检查已收藏漫画的新章节。
- **离线书架**：分类、隐藏、搜索、重命名，按最近阅读排序并保存阅读进度。
- **连续阅读**：长条滚动、跨章衔接、缩放、夜间调暗和可调速度的自动阅读。
- **本地导入与导出**：导入 PDF、图片 ZIP／CBZ、7z／CB7、RAR／CBR，将漫画合并导出为 PDF。
- **跨设备迁移**：Android 与 Windows 可在同一局域网扫码直传，也可通过文件备份迁移漫画与阅读记录。

## 怎么实现

Android 使用原生 Java 界面，Windows 使用 JavaFX。两端共用漫画源适配、下载任务、书架数据和备份等核心逻辑，各自在本机运行。

不同漫画源由独立适配器读取公开接口或网页，统一转换为作品、章节和图片信息。下载按章节完成并生成本地 PDF，完成一章即可入库阅读，中断后可复用已有缓存。

阅读器按可见区域分块渲染 PDF，Android 使用系统 `PdfRenderer`，Windows 使用 Apache PDFBox；文档和图片缓存设有容量限制，避免把整本漫画一次性渲染成大图。

漫画与阅读记录保存在本机。跨设备直传使用局域网连接，文件备份通过清单和 SHA-256 校验内容；应用更新从 GitHub Releases 获取安装包并校验摘要。

## 漫画来源与致谢

已发布版内置 YY漫画、拷贝漫画、MangaDex、E-Hentai、JM 和离线示例，并支持自定义 JM 兼容接口及通用 JSON 接口。各源的内容、中文章节和更新速度取决于源站；普通网站首页不能直接当作通用漫画接口使用。

漫画及翻译归相应创作者所有。本项目不实现付费解锁、登录限制或验证码绕过。开源组件许可、参考项目和来源致谢见 [NOTICE.txt](NOTICE.txt)。
