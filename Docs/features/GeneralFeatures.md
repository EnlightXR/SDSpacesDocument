# 通用功能

Snapdragon Spaces 提供提供一系列功能，帮助开发者创造 XR 体验。下方的简要列表概述了 SDK 中包含哪些功能，供您创造 XR 体验时使用。

## 位置跟踪

位置跟踪能够精确映射环境，并能够在 3D 空间内以 6DoF 的方式对位置、方位和方向进行 XR 设备的预估。开发人员能够据此了解和跟踪终端用户相对于世界的位置。XR 内容将根据终端用户的位置、头部方位和方向在场景中进行正确的呈现。

## 本地空间锚点

本地锚点能将 XR 内容置于特定空间位置，这一空间位置是通过位置跟踪生成的地图上给定的位置和方向生成的，在会话期间将保留在本地。

使用本地锚点的相关问题，请参考示例文档：

- [Unity 锚点示例](./../Unity/sample/AnchorSample.md) 
- [虚幻引擎锚点示例](./../unreal/samples/AnchorSample.md)

在运行时保存和加载锚点的相关问题，请参考示例文档的特定章节：

- [Unity Spaces 锚点储存](./../Unity/sample/AnchorSample.md#Spaces%20%E9%94%9A%E7%82%B9%E5%82%A8%E5%AD%98)
- [虚幻引擎加载和锚点保存](./../unreal/samples/AnchorSample.md#%E5%8A%A0%E8%BD%BD%E5%92%8C%E4%BF%9D%E5%AD%98%E9%94%9A%E7%82%B9)

## 命中测试

命中测试可用于通过将射线发送到世界中并检查任何命中结果来检索现实世界中的物理点

如何进行命中测试的相关问题，请参考示例文档：

- [Unity 命中测试示例](./../Unity/sample/HitTestingSample.md)
- [虚幻引擎命中测试示例](./../unreal/samples/HitTestingSample.md)

## 相机帧获取

相机帧获取功能提供了查询 XR 设备 RGB 相机的可能性。检索到的数据可用于多种目的，例如创建远程解决方案或将数据馈入第三方感知库中。

如何捕获相关的问题，请参考示例文档：

- [Unity 相机帧获取示例](./../Unity/sample/CameraFrameAccessSample.md) 
- [虚幻引擎相机帧获取示例](./../unreal/samples/HitTestingSample.md) 
