# 目录

**快速入门**

- [Snapdragon Spaces 概述](./Docs/setup/QuickStartGuide.md)

- **硬件设置**
  
    - [联想 ThinkReality A3 开发套件](./Docs/setup/ThinkRealityA3Setup.md)

- **运行应用程序**
 
    - [在 A3 眼镜运行应用程序](./Docs/setup/LaunchingSpacesAppsA3.md)

**架构**

- [OpenXR](./Docs/architecture/OpenXRForSpaces.md)

- [自定义启动器](./Docs/architecture/CustomLauncher.md)

**功能概述**

- [通用功能](./Docs/features/GeneralFeatures.md)
  
    - [位置跟踪](./Docs/features/GeneralFeatures.md#位置跟踪A)

    - [本地空间锚点](./Docs/features/GeneralFeatures.md#本地空间锚点)

    - [命中测试](./Docs/features/GeneralFeatures.md#命中测试)

    - [相机帧获取](./Docs/features/GeneralFeatures.md#相机帧获取)

- [交互](./Docs/features/Interaction.md)

    - [注视控制器](./Docs/features/Interaction.md#注视控制器)
  
    - [伴侣控制器](./Docs/features/Interaction.md#伴侣控制器)

    - [XR 控制器](./Docs/features/Interaction.md#xr-控制器)

    - [手部跟踪](./Docs/features/Interaction.md#手部跟踪)

- [环境理解](./Docs//features/EnvironmentalFeatures.md)

    - [平面检测](./Docs/features/EnvironmentalFeatures.md#平面检测)
  
    - [图像跟踪](./Docs/features/EnvironmentalFeatures.md#图像跟踪)
  
    - [空间网格划分](./Docs/features/EnvironmentalFeatures.md#空间网格划分)

**设计与用户体验**

- **手部跟踪**
  
    - [最佳实践](./Docs/designux/BestPractices.md)

    - [交互手势](./Docs/designux/InteractionGestures.md)

- [自定义控制器项目](./Docs/designux/CustomControllerProject.md)

- [测试目标图像](./Docs/designux/ImageTargetsToTry.md)

**Unity**

- [Unity 设置指南](./Docs/Unity/SetupGuideUnity.md)

- [场景设置](./Docs/Unity/SceneSetup.md)

- [交互](./Docs/Unity/Interaction.md)

- **交互包指南**

    - [MRTK3 的 Unity 设置指南](./Docs/Unity/MRTK3SampleWinOnly.md)

    - **QCHT 指南**

        - [手部跟踪概述](./Docs/Unity/QCHTGuide/HandTrackingOverview.md)

        - **通用**

            - [导入附加软件包](./Docs/Unity/QCHTGuide/ImportAdditionalPackages.md)
            - [基本场景设置](./Docs/Unity/QCHTGuide/BasicSceneSetup.md)
            - [XR 手部追踪管理器 API](./Docs/Unity/QCHTGuide/HandTrackingAPI.md)
            - [手部 Avatar](./Docs/Unity/QCHTGuide/HandAvatar.md)
            - [手部控制器](./Docs/Unity/QCHTGuide/XRHandController.md)
            - [XR 交互工具包](./Docs/Unity/QCHTGuide/XRInteractionToolkit.md)
  
        - **交互方式**
  
            - [远端交互](./Docs/Unity/QCHTGuide/DistalInteraction.md)
            - [近端交互](./Docs/Unity/QCHTGuide/ProximalInteraction.md)
  
        - **交互功能**

            - [控制框](./Docs/Unity/QCHTGuide/DistalGizmo.md)
            - [虚拟力反馈 (VFF)](./Docs/Unity/QCHTGuide/ProximalVFF.md)
            - [捕捉](./Docs/Unity/QCHTGuide/ProximalSnapping.md)
  
    - [XR Interaction Toolkit Sample](./Docs/Unity/XRITSample.md)

- **示例**

    - [手部跟踪示例](./Docs/Unity/sample/HandTrackingSample.md)

    - [锚点示例](./Docs/Unity/sample/AnchorSample.md)

    - [命中测试示例](./Docs/Unity/sample/HitTestingSample.md)

    - [图像跟踪示例](./Docs/Unity/sample/ImageTrackingSample.md)

    - [平面检测示例](./Docs/Unity/sample/PlaneDetectionSample.md)

    - [相机帧获取示例（实验性）](./Docs/Unity/sample/CameraFrameAccessSample.md)

    - [空间网格示例（实验性）](./Docs/Unity/sample/SpatialMeshingSample.md)

- [Unity 的已知问题](./Docs/Unity/KnownIssues.md)

**虚幻引擎**

- [虚幻引擎设置指南](./Docs/unreal/SetupGuideUE.md)

- [场景设置](./Docs/unreal/SceneSetup.md)

- [交互](./Docs/unreal/Interaction.md)

- [交互示例](./Docs/unreal/InteractionSample.md)

- **示例**

    - [锚点示例](./Docs/unreal/samples/AnchorSample.md)

    - [手部跟踪示例](./Docs/unreal/samples/HandTrackingSample.md)

    - [命中测试示例](./Docs/unreal/samples/HitTestingSample.md)

    - [图像跟踪示例](./Docs/unreal/samples/ImageTrackingSample.md)

    - [平面检测示例](./Docs/unreal/samples/PlaneDetectionSample.md)

    - [相机帧获取示例（实验性）](./Docs/unreal/samples/CameraFrameAccessSample.md)

    - [空间网格示例（实验性）](./Docs/unreal/samples/SpatialMeshingSample.md)

- [虚幻引擎的已知问题](./Docs/unreal/KnownIssues.md)

**[已知问题](./Docs/KnownIssues.md)**

**关于**

- [变更日志](./Docs/about/CHANGELOG.md)

- [第三方许可条款](./Docs/about/ThirdPartyLicenses.md)

- [故障排除](./Docs/about/Troubleshooting.md)

**延伸阅读**

- **Unity**

    - [AR Foundation 文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.2/manual/index.html)

    - [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/index.html)

    - [Unity XR 插件](https://docs.unity3d.com/Manual/com.unity.xr.openxr.html)
  
- **虚幻引擎**

    - [XR 开发](https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/XRDevelopment/)
  
    - [OpenXR 文档](https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/XRDevelopment/OpenXR/)