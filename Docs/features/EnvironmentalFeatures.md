# 环境理解

Snapdragon Spaces 提供了一系列环境理解功能，以帮助开发人员创建 XR 体验。

请注意，以下功能是为室内体验构建和测试的，需要具有适度光照的理想条件。由于当前硬件设计的性质，不同的环境和光照条件可能提供不同程度的感知质量准确性。因此，在当前硬件上不建议使用或支持使用室外用例，我们同时正在为未来的设计进行改进。

## 平面检测

平面检测能够识别物理环境中水平平面和垂直平面。这一能力能让开发者将 AR 内容锚定到这些表面，包括墙面、地板和桌子等平面上。

如何检测平面，请参考示例文档：

- [Unity 平面检测示例](./../Unity/sample/PlaneDetectionSample.md)
- [虚幻引擎平面检测示例](./../unreal/samples/PlaneDetectionSample.md)

## 图像跟踪

图像跟踪能够识别和跟踪图像目标，以便对这些图像目标进行虚拟增强。

点击 [此处](./../designux/ImageTargetsToTry.md) 查看当前用于图像跟踪的图像目标。

如何识别图像目标，请参考示例文档：

- [Unity 图像跟踪示例](./../Unity/sample/ImageTrackingSample.md)
- [虚幻引擎图像跟踪示例](./../unreal/samples/ImageTrackingSample.md)

## 空间网格划分

空间网格能够创建与物理环境相近的网格。

如何启用空间网格划分，请参考示例文档：

- [Unity 空间网格示例](./../Unity/sample/SpatialMeshingSample.md)
- [虚幻引擎空间网格示例](./../unreal/samples/SpatialMeshingSample.md)