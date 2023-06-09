# 虚幻引擎的已知问题

目前已知有几个问题可能会影响开发工作流程。这些是已知的问题，将在未来的虚幻引擎插件或 `Snapdragon Spaces Services` 运行时（runtime）中得到解决。

如果本节未提到您的问题，请检查 SDK 的全部 [已知问题](./../KnownIssues.md)。

## 空间锚点向后兼容性问题

为避免在销毁锚点时发生崩溃，请使用插件版本 0.13.0 或更高版本编译应用程序。请注意，使用插件版本 0.12.1 及更低版本构建的应用程序与 Snapdragon Spaces Services 版本 0.13.0 及更高版本不兼容。

## 重置位置

目前，在地图加载时重置地图位置这一功能，无法按预期运行。

## 虚幻编辑器的启动问题

某些防火墙可能会阻止虚幻编辑器进行正确启动。您或可通过在虚幻编辑器安装路径下的 `引擎/二进制文件/Win64` （`Engine/Binaries/Win64`）中对 **CrashReportClientEditor.exe** 重命名为其他名称，以解决这一问题。

## 渲染问题

### Widget 性能问题

当使用默认的 `Development` 配置部署应用程序时，在查看器（Viewer）上的世界空间（world space）UI widget（时，帧率和性能会大幅降低。不幸的是，此问题的根本原因尚不清楚。Widget 出现问题时，您应选择 `Shipping` 配置。
