# 交互

## 注视控制器

注视控制器（Gaze Controller）扩展用户的目光方向，作为一种触发输入的简单方式

## 伴侣控制器

伴侣控制器（Companion Controller，又名主控制器）是一种软件控制器，它使用智能手机作为 3DoF 控制器进行输入。控制器通过屏幕输入来分配执行行为。但其中的重定位按钮并不向引擎端发送信号，只是传递给应用重置控制器位姿的信号。

## XR 控制器

Snapdragon Spaces 插件包含一组通用 XR 控制器（XR Controllers），用于可视化连接的VR头戴设备。用户可通过管理引擎端的组件来进行 XR 控制器与设备指针之间可视化的选择

Unity 中这一切换是通过 [控制器管理组件](./../Unity/SceneSetup.md) 来进行的，在虚幻引擎中是通过 [激光控制器蓝图](./../unreal/SceneSetup.md) 来进行的。

Unity 中，控制器通过混合形状来为每个按钮状态提供精确的 [视觉反馈](./../Unity/SceneSetup.md)。Unity 也支持 [触觉反馈](./../Unity/SceneSetup.md)。

## 手部跟踪

手部跟踪通过直接触摸或抓取 UI 元素（带或不带虚拟力反馈）以及管理用于与远距离 UI 交互的射线指针或响应特定手势命令，提供了更自然的前向输入选项。目前不支持自定义定义手势。

有关手部跟踪的更多详细信息，包括支持的手势和最佳实践，请参阅 [手部跟踪设计与用户体验](./../designux/BestPractices.md)。

请参考以下示例文档，学习如何集成手部跟踪：

- [扩展 Unity 手部跟踪示例](./../Unity/QCHTGuide/ExtendedHandTrackingSample.md)
- [基础 Unity 手部跟踪示例](./../Unity/sample/HandTrackingSample.md)
- [基础虚幻引擎手部跟踪示例](./../unreal/samples/HandTrackingSample.md)
