# 变更日志

这个格式基于 [保留变更日志](https://keepachangelog.com/en/1.0.0/)，并且该项目遵循 [语义化版本](https://semver.org/spec/v2.0.0.html)。

## [0.13.0] - 2023-05-04

### Unity

#### 添加

- 手部跟踪已启用作为示例中的默认输入模式（如果项目中包含 QCHT包）。否则，注视指针是默认输入模式

- 可选图像跟踪模式可以设置，以更好地控制底层图像跟踪算法的计算周期。有关此更改的更多信息，请访问 [图像跟踪](./../Unity/sample/ImageTrackingSample.md) 部分。

- 在 Base Runtime 设置中添加了 **Prevent Sleep Mode** 项目设置，以防止所有设备上的应用程序屏幕超时。

- 添加了新的 `OriginLocationUtility` 类，以帮助获取会话原点，独立于类型（`ARSessionOrigin` 或 `XROrigin`）。

- 启用 Passthrough 透视时，如果会话摄像机的背景设置不正确，则会发出警告。

- Unity 构建版本现在包含在示例的主菜单中的信息面板中。

#### 变更

- 改变了所有示例的外观。

- 将 QCHT 交互包更新到版本 4.0.0-pre.11。

- 在示例中，已将已弃用的 ARPoseDriver 组件替换为TrackedPoseDriver。

- 优化代码以确保与 Unity 2022.1、2022.2 和 2023.1（Beta）的基本兼容性。

- 对包内 SpacesLauncher.aar 和 ServicesHelper.aar 存档进行了代码优化和更新。

- Hit Testing 和 Plane Detection 的生命周期改进和更改：
  - 删除了为 AR 射线设置的内部距离限制。
  - 平面范围的计算已更改，可能会 [破坏向后兼容性](./../KnownIssues.md#破坏向后兼容性)。

- 强制启用不安全代码的验证规则已从插件中删除，并移至 `CameraFrameAccessSampleController.cs`，因为它仅在示例中需要。

- 当禁用场景理解后端时，Plane Detection、Image Tracking 和 Hit Testing子系统将请求运行时相机权限，而不是应用程序相机权限。

#### 修复

- 修复了注视交互器位置计算的问题。

- 修复了禁用“在主机上启动控制器”选项时，windowFocusChanged添加未添加到Unity活动中的问题。

- 在 Base Runtime 功能选项中，导出 Headless 选项在最终清单中正确删除 SpacesLauncher 活动的意图。

- 如果不再需要，底层的 Hit Testing、Plane Detection和Spatial Meshing 提供程序将正确停止。在旧版运行时中，这种行为可能会破坏预期的应用程序功能，因为提供程序无法在 20-40 秒内启动。因此，此修复可能会 [破坏向后兼容性](./../KnownIssues.md#破坏向后兼容性)。

- 优化 Camera Frame Access 生命周期，以防止该功能初始化不正确。

### Unreal Engine

#### 添加

- 在示例中启用了手部跟踪作为默认输入模式。

- 新的手部跟踪组件，用于远端交互。

- 可选图像跟踪模式可以设置，以更好地控制底层图像跟踪算法的计算周期。有关此更改的更多信息，请访问 [图像跟踪](./../unreal/samples/ImageTrackingSample.md) 部分。

- 增加了一个项目设置，以防止应用程序屏幕超时。

- Camera Frame Access 功能异步计算RGB帧以获得更好的性能。

- 添加了自定义节点“Toggle Spaces Feature”，作为“Toggle AR Capture”的替代启动感知功能。

#### 变更

- 改变了所有示例的外观。

- 再次将屏幕方向“横向向左”（Landscape Left）设置为强制设置。

- 将“Point”手势标记为已弃用。
  
- 对包内 SpacesLauncher.aar 和 ServicesHelper.aar 存档进行了代码优化和更新。

- 当使用注视时，在信息面板中箭头滚动方向被反转。

- Hit Testing 和 Plane Detection 的生命周期改进和更改：
  - 删除了为 AR 射线设置的内部距离限制。
  - 平面范围的计算已更改，可能会 [破坏向后兼容性](./../KnownIssues.md#破坏向后兼容性)。

- 当禁用场景理解后端时，Plane Detection、Image Tracking和Hit Testing子系统将请求运行时相机权限，而不是应用程序相机权限。

#### 修复

- 修复了在编辑器中运行手部跟踪时崩溃的问题。

- 修复了在应用程序进程外部（例如，在 Snapdragon Spaces Services 进程或第三方库中）调用 `std::join` 时崩溃的问题。

- 修正了感知功能的加载，使它们仅在需要时加载。

- 如果不再需要，底层的 Hit Testing、Plane Detection 和 Spatial Meshing 提供程序将正确停止。在旧版运行时中，这种行为可能会破坏预期的应用程序功能，因为提供程序无法在20-40秒内启动。因此，此修复可能会破坏向后兼容性。

- 修正了使用 Spatial Meshing 时的内存泄漏。

### Snapdragon Spaces Services

#### 添加

- 添加了 `xrSetImageTargetsTrackingModeQCOM` 和 `xrStopImageTargetTrackingQCOM` 方法支持，以设置图像跟踪模式。

#### 变更

- 图像跟踪、Hit Testing 和 Plane Detection 现在在 Snapdragon Spaces Services 进程上运行，而不是在应用程序进程上运行，这取决于是否内部使用了场景理解后端。
  
- Camera Frame Access 功能的改进。这些更改可能会 [破坏向后兼容性](./../KnownIssues.md#破坏向后兼容性)

#### 修复

- 修复了手部跟踪层中眼镜拔掉/插入问题。

- 修复了在插拔眼镜后启动应用程序时出现黑屏问题。


## [0.12.1] - 2023-04-03

### Unity

#### 添加

- 已将 Oculus Touch 控制器交互配置文件添加到功能验证列表中。应默认启用以确保完全支持示例。

- Spaces Hand 组件已被标记为已弃用。

- 使用 QCHT Interaction 包中的示例替代旧的手部跟踪示例。

#### 变更

- VR 中的 Passthrough现在可以在每个场景中使用 X 和 A 按钮切换开关。

- 改进了 Hit Testing 的可视化效果。

#### 修复

- Spatial Meshing 子系统创建的空间网格现在会自动更新，而不是每帧重新创建。

- 已优化权限检查以防止在 Android 13 上出错。

### Unreal Engine

#### 添加

- 将手部跟踪网格添加为 AR Capture 模式，并弃用了获取手部网格的旧方法。

- 支持 UE5.0。

#### 变更

- 改进了 Hit Testing 的可视化效果。

#### 修复

- 从蓝图中删除了 ARAnchor 和 Raycast 的提及。

- 注视指针始终绘制在 3D 内容之上。
- 
- 当命中距离设置为无穷大时，Hit Testing 不再会出现问题。

- 改进了 Camera Frame Access 以防止在某些条件下崩溃。

### Snapdragon Spaces Services

#### 添加

图像跟踪现在使用 RGB 摄像头而不是左侧跟踪摄像头，从而将目标的识别和跟踪距离增加了许多倍。

#### 变更

- 修复了长时间使用设备后可能出现的黑线伪影问题。

- 不再出现应用平面旋转时的失真伪影。

- 改进了渲染延迟以修复撕裂伪影。

## [0.11.1] - 2023-02-14

### Unity

#### 新增

- **⚠ 实验性的** 空间网格子系统支持和 **[新示例场景](./../Unity/sample/SpatialMeshingSample.md)**。
- **⚠ 实验性的** 相机帧获取支持和 **[新示例场景](./../Unity/sample/CameraFrameAccessSample.md)**。
- **[MR 设备的直通支持](./../Unity/SceneSetup.md#透视仅适用于-mr-设备)**。

#### 变更

- 支持的Unity版本更改为 **2021.3.16f1** ，并升级了特定软件包：
    - Unity OpenXR 插件版本升级到 1.6.0。
    - AR Foundation 版本升级到 4.2.7。
    - XRIT 版本升级到 2.0.6。
- 禁用使用 `在查看器上启动应用程序` 和 `在主机上启动 Spaces 控制器` 构建时，将完整的**UnityCustomLauncher.aar** 从构建中删除。
- 如果感知子系统没有启动或相机权限未启用，示例中的 UI 会显示警告消息。
- 示例中，切换到主机控制器后，主机控制器射线将被重置。
- 更新了 OpenXR 结构体到最新版本。
- 默认的命中测试后端已从运行时更改为 **XR_APILAYER_QTI_scene_understanding**  层。
- 默认平面检测后端已从运行时更改为 **XR_APILAYER_QTI_scene_understanding**  层。
- 删除了一个功能验证规则，该规则防止应用程序在多线程渲染开启时进行构建。
- QCHT 软件包的更新，支持 MRTK 和更小的改进。

#### 修复

- 现在，从应用内部转换后直到下一次更新关节姿势之前，手部关节数组的 **SpacesHand** 组件将进行缓存。
- 修正了 OpenXR 功能中 OpenXR 结构初始化错误的问题。

### 虚幻引擎

#### 新增

- **⚠ 实验性** 空间网格子系统支持和 **[新示例场景](./../unreal/samples/SpatialMeshingSample.md)**。
- **⚠ 实验性** 相机帧访问支持和 **[新示例场景](./../unreal/samples/CameraFrameAccessSample.md)**。
- **[MR 设备的通行支持](./../unreal/SceneSetup.md#透视仅适用于-mr-设备)**。
- 插件设置中的其他选项：
    - **无头导出**: 此选项启用后，将导出没有启动器标记的 apk，且该 apk 在应用程序启动器（App Launcher）中不可见。
    - **替代启动活动**: 此值允许设置其他活动，而不是从 SpacesLauncherActivity 启动的虚幻引擎的默认活动。
    - **跳过权限检查**: 启用此功能将跳过应用程序启动时进行的权限检查。
- 新增 XR 控制器模型，包括 **[按钮和摇杆动画](./../unreal/SceneSetup.md)**。
- 增加了 **[控制器触觉反馈](./../unreal/SceneSetup.md)**。

#### 变更

- 示例中如果感知子系统未启动或相机权限未启用，则会通过 UI 显示警告消息。
- 切换到主机控制器后，示例中的射线将被重置。
- 默认的命中测试后端已从运行时更改为 **XR_APILAYER_QTI_scene_understanding** 层。
- 默认平面检测后端已从运行时更改为 **XR_APILAYER_QTI_scene_understanding** 层。

#### 修复

- 在 OpenXR 功能中修复了错误的 OpenXR 结构初始化。

### Snapdragon Spaces Services

#### 新增

- 新增了**XR_APILAYER_QTI_scene_understanding** OpenXR 层，用于通过 **XR_MSFT_scene_understanding** 和**XR_QCOM_ray_casting** 扩展进行空间网格化和命中测试。
- 新增了 **XR_QCOMX_camera_frame_access** 扩展，用于相机帧访问到 **XR_APILAYER_QCOM_retina_tracking** OpenXR 层。
- 新增了 **XR_APILAYER_QCOM_backwards_compatibility** OpenXR 层，以处理旧应用程序向运行时发送过时结构的情况。
- 将 **XR_UNITY_android_present** 扩展新增到运行时。

## [0.10.0] - 2022-12-15

### Unity

#### 新增

- 新的 XR 控制器模型，包括 [按钮和摇杆动画](./../Unity/Interaction.md#xr-控制器的控制器动画)。
- 增加了 [控制器触觉反馈](./../Unity/Interaction.md#控制器触觉反馈)。

### Snapdragon Spaces Services

#### 修复

- 修复了同时加载或保存两个或更多锚点的问题。
- 修复了同时保存/加载多个锚点时的问题。

## [0.9.0] - 2022-11-24

### Unity

#### 新增

- 支持 Oculus Touch 控制器交互配置文件。
- 输入控制器根据可用的输入配置文件进行更改（[控制器管理器](./../Unity/SceneSetup.md)）。
- 在预制件中新增了一个新的公共字段 `SpacesHandManager`，以符合其他 `TrackableManager` 实现。
- **QCHT 核心软件包增加：**
    - 新增了对 [XR 交互工具箱](./../Unity/QCHTGuide/XRInteractionToolkit.md) 的支持。
- **QCHT 交互软件包增加：**
    - 新增了一个准星激活阈值，与激光激活阈值配合使用，以便在悬停时设置准星显示，而在静止时设置激光显示。新的准星激活阈值的默认值可以与激光激活阈值相同，以保持向后兼容性。
    - 新增了对 [XR 交互工具箱](./../Unity/QCHTGuide/XRInteractionToolkit.md) 的支持。

#### 变更

- 主控制器的重新居中按钮将激光重置为头部朝前的位置，而不是会话原点。
- 在锚点示例中新增了命中测试以进行锚点放置。
- 注视准星位置使用 `XR.eyeTexture` 大小值，而不是屏幕大小值。

#### 修复

- **QCHT 核心包修复：**
    - 改进手部模拟系统。
    - 移除 `QCHTUtils` 中的警告。
    - 修复 `QCHTInstanceColor` 着色器问题。
- **QCHT 交互包修复：**
    - 如果在交互时无法进行手部跟踪，则释放可交互物体。

### 虚幻引擎

#### 新增

- 支持 Oculus Touch 控制器交互配置文件。
- 输入控制器根据可用的输入配置文件（[激光控制器](./../unreal/SceneSetup.md)）进行更改。
- 新增 [手部网格化](./../unreal/samples/HandTrackingSample.md#手部网格查看器) 以可视化手部跟踪。
- 在 API 中新增了 [启动和停止功能](./../unreal/samples/HandTrackingSample.md#手部跟踪管理器)，以管理手部跟踪并防止后台执行。
- 在构建前新增了 [强制性项目设置](./../unreal/SetupGuideUE.md#步骤-4更改项目设置)。
- 新增异步线程用于图像跟踪器的创建。
    - 新增一个 [委托来通知跟踪器何时准备就绪](./../unreal/samples/ImageTrackingSample.md#图像-ar-会话配置)。

#### 变更

- 主控制器的重新居中按钮将激光重置为头部朝前的位置，而不是会话原点。
- 在锚点示例中新增了命中测试以进行锚点放置。
- 将示例渲染模式更改为前向。
- 更改输入命名和 **需要在项目设置中重新设置输入绑定**。

#### 修复

- 修复了实时传送时 pawn 的命中测试偏移。
- 修复了显示重叠问题。

### Snapdragon Spaces Services

#### 新增

- 如果 Snapdragon Spaces Services 输入源可用，XR 控制器将自动新增到 Snapdragon Spaces Services 输入源中。

#### 变更

- 改进了跟踪图像目标偏移。

## [0.8.1] - 2022-10-14

### Snapdragon Spaces Services

#### 修复

- 修复了在没有任何查看器连接时启动应用程序崩溃的问题。

## [0.8.0] - 2022-10-13

### Unity

#### 新增

- 在锚点示例场景中新增新的图例面板，以区分不同 Gizmo 可视化表示的含义。
- 在基础运行时功能（BaseRuntimeFeature）设置中新增其他选项：
  - **无头导出**：此选项启用后，将导出没有启动器标记的 apk，且该 apk 在应用程序启动器（App Launcher）中不可见。
  - **替代启动活动**: 此值允许设置其他活动，而不是从 SpacesLauncherActivity 启动的 Unity的默认活动。
  - **跳过权限检查**: 启用此功能将跳过应用程序启动时进行的权限检查。
- **QCHT 核心软件包新增内容：**
    - 现在可以通过右键单击场景并选择 `QCHT > QCHTManager` 直接创建 `QCHTManager`。
    - MeshLocal 边界框。
- **QCHT 交互软件包新增内容：**
    - 在物理射线检测准星上新增了一个具有 ZTest off 着色器的自定义材质。
    - 与 `QCHTRay` 相关的新增内容：
        - 新增了光线的 `bendUp` 强度。
        - 新增了光线的 `BendRatioActivationThreshold` 值。
    - 与 `ControlBox` 相关的新增内容：
        - 在编辑器中新增了比例偏移属性，以避免对象在盒子内部被裁剪。
        - 在初始盒子尺寸计算中新增了对象旋转，以避免对象不在其轴心上时出现奇怪行为。
        - 在编辑器中新增了移动约束，以锁定用户的水平/垂直移动。

#### 变更

- 应用程序生命周期的改进使得 Spaces 应用程序无需强制停止就可以顺序启动。
- **⚠ 实验性** 的 `Spaces 锚点储存` 现在支持多线程加载和保存调用。加载已保存的锚点不再阻塞主线程。
- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 存档更新了更好的触控板可视化效果。
- **QCHT 核心软件包更改：**
    - 数据填充改进
- **QCHT 交互软件包更改：**
    - 适用于 Unity 2021.3.x 的新抓取点编辑器
    - 改进过的 `HandPoseDriver`。
    - 更新手部 alpha 管理。
    - `QCHTRay` 相关更改：
        - 当手部不移动时，停止计算射线中间点，以提高射线弯曲的稳定性感觉。
        - 射线现在只朝上弯曲。
        - 当手部不移动时，射线弯曲计算稳定性提高。
- `ControlBox` 相关更改：
    - 通用提升

#### 修复

- **QCHT 交互软件包更改：**
    - 为 Unity 2021.3.x 新增了新的抓取点编辑器。
    - 在 Unity 编辑器中保存预制件到不可变文件夹时出现错误。
    - 当使用 `QCHTControlBox` 颜色设置时，修正了应用于准星的错误颜色。
    - `QCHTRay`
        - 修复了 QCHTRay 并避免在错误状态下禁用准星。

### 虚幻引擎

#### 新增

- 在锚定示例场景中新增了新的图例面板，以对不同的 Gizmo 可视化表示意义进行区分。

#### 变更

- 应用程序生命周期的改进使得 Spaces 应用程序无需强制停止就可以顺序启动。
- **⚠ 实验性** 的 `Spaces 锚点储存` 现在支持多线程加载和保存调用。加载已保存的锚点不再阻塞主线程。
- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 存档已更新，触控板可视化效果更好。

#### 修复

- 移除了有关缺少引擎版本的警告
- 在示例项目中移除了未使用的 SteamVR 引用
- 当 Pawn 位置被移动时，命中测试行为正确

### Snapdragon Spaces Services

#### 变更

- 应用程序生命周期的改进使得 Spaces 应用程序无需强制停止就可以顺序启动。
- 改进了视觉性能，实现更流畅的展现（减少撕裂效果）。

#### 修复

- 现在可以正常跟踪两个或更多图像。
- 较大集合的图像目标的目标名称不再损坏。
- 在命中测试开启时停用平面检测，不再会导致应用程序崩溃。
- 来电后手部跟踪会正确地恢复。
- 设备重启后的黑屏问题已解决。

## [0.7.0] - 2022-08-31

### Unity

#### 新增

- **⚠ 实验性** `Spaces 锚点储存`，用于将锚点保存和加载到本地存储，并在 [锚点示例场景](./../Unity/sample/AnchorSample.md#spaces-锚点储存) 中进行更新。
- **QCHT 核心软件包新增内容：**
  - 新增了对自定义着色器的 URP（通用渲染管线）支持
  - 提供工具提示以改善开发者体验
- **QCHT 交互软件包新增内容：**
    - 新增了对自定义着色器的 URP（通用渲染管线）支持
    - 即使手部存在，也可以隐藏手部（Hand Presenter）
    - 允许显示或不显示幽灵手（Hand Presenter）
    - 可以更改射线大小以进行远端交互（图形和物理射线检测器）
    - 提供工具提示以改善开发者体验

#### 变更

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 归档文件更新了明/暗模式设置和触觉反馈切换。
- 射线检测子系统支持连续命中测试，附带 [更新的示例场景](./../Unity/sample/HitTestingSample.md)。
- [更新手部跟踪包](./../Unity/sample/HitTestingSample.md)。
- [组件版本](./Troubleshooting.md#组件版本) 面板现在包括滚动视图，以便将来可以容纳更多组件。
- 开发者软件包中包含更新的 Snapdragon Spaces Services。
- **QCHT核心软件包变更：**
    - 重新组织 UI 组件并重命名变量，以提高理解和开发体验。
- **QCHT交互软件包变更：**
    - 重新组织 UI 组件并重命名变量，以便更易理解和提供更好的开发者体验，适用于以下组件：
        - 手部展示器（Hand Presenter）
        - QCHT 射线
        - QCHT 控制盒
        - 抓取点
        - 近场交互器
    - 将交互类型从 `Simple` 、`VFF` 、`Ghost Only` 重命名为 `Triggering` 、`Colliding` 、`None`。
    - 仅允许使用 4 个手势进行近场交互（捏合、抓取、指向、开手）
    - 默认不从手部 .fbx 导入材质
    - 所有自定义编辑器脚本逻辑移动到相应脚本中
    - 所有纹理资源移动到纹理（texture）文件夹中
    - `QCHTPhysicsRaycaster` 支持事件掩码
    - 创建控制盒设置并新增句柄（handles）显示类型

#### 修复

- `Spaces Hand` 组件中的手部关节姿势已在世界空间中进行修复，而不是只相对于头部姿势。
- 修复了 Unity 2021 增量构建管道的构建问题。
- **QCHT 交互包修复：**
    - 激光位置偏移
    - 改进了捕捉（snapping）功能
    - 在射线检测拖动时新增了 `射线状态（RayState）` 选项
    - 点击 **编辑姿势** 后重新绘制场景视图
    - QCHT 交互控制器不再需要手部展示器
    - 修复了在触发和碰撞手之间切换时出现的问题

### 虚幻引擎

#### 新增

- 手部跟踪支持和 [新的示例场景](./../unreal/sample/HandTrackingSample.md)。
- **⚠ 实验性**支持从本地存储加载和保存锚点，并在 [锚点示例场景](./../unreal/samples/AnchorSample.md#加载和保存锚点#-加载和保存锚点)
  
#### 更改

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 档案已更新，具有浅色/深色模式设置和触觉反馈开关。
- 射线检测子系统支持连续命中测试，并使用 [更新的示例场景](./../unreal/samples/HitTestingSample.md)。
- [组件版本](./Troubleshooting.md#组件版本) 面板现在包括一个滚动视图，以便将来可以新增更多组件。
- 更新了开发者包中的 Snapdragon Spaces Services。

#### 修复

- 修复了增量构建的构建问题。

### Snapdragon Spaces Services

#### 变更

- Snapdragon Spaces Services 设置界面中，移除了选择输入源这一需要。

## [0.6.1] - 2022-07-22

### Unity

#### 新增

- 在应用程序启动时，为 Snapdragon Spaces Services 新增了相机权限检查，并提示在 Snapdragon Spaces Services Android 设置中进行启用（如果之前未授权）。

### 虚幻引擎

#### 新增

- 在应用程序启动时，为 Snapdragon Spaces Services 新增了相机权限检查，并提示在 Snapdragon Spaces Services  Android 设置中进行启用（如果之前未授权）。

### Snapdragon Spaces Services

#### 新增

- 新增了相机权限提示，以防尚未授权。
- 在 UI 中新增了相机权限状态。

#### 修复

- 修复了 Snapdragon Spaces Services 中未授予相机权限时，应用程序无法启动的问题。

## [0.6.0] - 2022-07-21

### Unity

#### 新增

- 支持自定义手部跟踪子系统和 [新示例场景](./../Unity/sample/HandTrackingSample.md)。
- 在开发者包中包含了 [单独的手部跟踪包](./../Unity/QCHTGuide/ImportAdditionalPackages.md)，以扩展手部跟踪功能。
- **⚠ 实验性质** 支持射线投射子系统和 [新示例场景](./../Unity/sample/HitTestingSample.md)。
- 示例增加：
    - 通过主菜单可访问 [组件版本](./Troubleshooting.md#组件版本) 信息。
    - 控制器类型（注视或设备射线）在应用启动和场景切换时被保存。

#### 更改

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 存档已更改为类型为 [微软混合现实运动控制器配置文件](https://registry.khronos.org/OpenXR/specs/1.0/html/xrspec.html#_microsoft_mixed_reality_motion_controller_profile)，相比上一个版本增加了一个触控板。
- 更新了开发包中包含的 Snapdragon Spaces Services。
- 在图像跟踪子系统中新增了检查，以防止设置和使用错误的图像候选项。

#### 修复

- 修复了一个 bug，该 bug 阻止最终构建中包含文件名中包含 **SpacesController** 的自定义控制器。

### 虚幻引擎

#### 新增

- 图像跟踪支持和 [新的示例场景](./../unreal/samples/ImageTrackingSample.md)。
- **⚠ 实验性** 的射线投射支持和 [新的示例场景](./../unreal/samples/HitTestingSample.md)。
- 示例新增:
    - 通过主菜单可访问 [组件版本](./Troubleshooting.md#组件版本) 信息。
    - 控制器类型（注视或设备射线）在应用启动和场景切换时进行保存。

#### 变更

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 存档已更改，现在是类型为 [微软混合现实运动控制器配置文件](https://registry.khronos.org/OpenXR/specs/1.0/html/xrspec.html#_microsoft_mixed_reality_motion_controller_profile)，相比上一个版本增加了一个触控板。
- 更新了开发者包中包含的 Snapdragon Spaces Services。

## [0.5.0] - 2022-06-01

### Unity

#### 新增

- 增加了跟踪图像子系统支持和 [新的示例场景](./../unreal/samples/ImageTrackingSample.md)。
- 在 `BaseRuntimeFeature` 设置中新增了 `Launch Spaces Controller` 和 `Use Custom Controller` 选项。
- 新增 `Custom Controller Package` 文件夹，其中包含一个 Android Studio 项目，用于将自定义 Android 存档构建到开发人员包中。
- 示例新增内容：
    - 按住主机控制器的 `Menu` 按钮将关闭示例。
    - 将示例脚本封装在自己的命名空间中。
    - 在 `GazeInteractor` 组件中新增了垂直偏移量以移动准星。

#### 更改

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 被移出 Snapdragon Spaces Services 并作为 Android 存档文件包含在 Unity 软件包中。
- 更新了开发者软件包中包含的 Snapdragon Spaces Services 版本。
- 将包中的 OpenXR 插件版本依赖（从 1.2.8）更新到 1.4.2。
- 重命名并简化了软件包中 `Editor` 文件夹中包含的编辑器脚本。

#### 修复

- 修复了头部锁定内容的抖动问题。
- 改进了锚点和平面检测子系统的生命周期，在启动和停止子系统时进行优化。
- 修复了示例中的问题：
    - 再次减小了注视射线的大小。
    - 改进了 `GazeInteractor` 计算，使其独立于平台的水平一半得到正确计算。


### 虚幻引擎

#### 新增

- 支持平面检测和 [新的示例场景](./../unreal/samples/PlaneDetectionSample.md)。
- 在插件设置中新增了 `Launch Spaces Controller` 和 `Use Custom Controller` 选项。
- 新增了 `Custom Controller Package` 文件夹，其中包含一个 Android Studio 项目，用于将自定义 Android 归档文件构建到开发人员包中。

#### 更改

- [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 从 Snapdragon Spaces Services 中移出，并作为 Android 归档文件放入虚幻引擎插件中。
- 更新了开发人员包中包含的 Snapdragon Spaces Services。

#### 修复

- 修复了头部锁定内容的抖动问题。
- 示例修复：
    - 浮动 UI 面板在向其移动时正确保持距离。
    - 优化了 `GazeInteractor` 计算，使其独立于平台的水平一半得到正确计算。

## [0.4.1] - 2022-04-28

### Unity

#### 修复

- 更新了开发者软件包中的 Snapdragon Spaces Services，修复了 ThinkReality A3 配置值读取错误的问题。

### 虚幻引擎

#### 修复

- 更新了开发者包中的 Snapdragon Spaces Services，修复了 ThinkReality A3 配置值读取错误的问题。

## [0.4.0] - 2022-04-28

### Unity

#### 新增

- 增加了对 Motorola Edge+ 和 Motorola Edge 30 Pro 的支持。
- 支持平面检测子系统和 [新的示例场景](./../Unity/sample/PlaneDetectionSample.md)。
- 在启动应用程序之前新增了一个对话框，以授予相机权限（用于平面检测和未来的跟踪类型）。
- 在主菜单中新增了一个退出按钮，以退出应用程序。

#### 更改

- 更新了带有新 UI 的 [主机控制器](./../setup/LaunchingSpacesAppsA3.md)。
- 不再支持以前的 SM8450 QRD 设备。
- 使用平面检测跟踪层更新了 OpenXR 运行时。
- `UnityServicesHelper.aar` 被拆分为`UnityServicesHelper.aar` 和 `UnityCustomLauncher.aar`，通过 OpenXR 项目设置中的 `BaseRuntimeFeature` 选项禁用后者。

#### 修复

- 此版本将 OpenXR 姿态数据转换为 Unity 姿态数据，应用正确的坐标系统进行修改。

### 虚幻引擎

#### 新增

- 新增了对 motorola edge+ 和 motorola edge 30 pro 的支持。
- 在主菜单中新增了退出按钮以退出应用程序。
- 应用程序可以在查看器设备上正确启动，无需使用adb启动命令。

#### 更改

- 更新了具有新 UI 的 [主机控制器](./../setup/LaunchingSpacesAppsA3.md)。
- 不再支持旧的 SM8450 QRD 设备。
- 使用平面检测跟踪层更新了 OpenXR 运行时。

#### 修复

- 减小了注视射线的大小。

## [0.3.0] - 2022-03-15

### Unity

#### 新增

- 支持锚点子系统和 [新的示例场景](./../Unity/sample/AnchorSample.md)。
- 支持 [主机控制器](./../setup/LaunchingSpacesAppsA3.md)。
- 提供会话子系统以检索跟踪状态和支持的功能。
- 在示例场景中，通过 `SampleController` 禁用屏幕超时和所有从中派生的控制器。
- AR 会话原点在每个场景更改时进行重置。可以在  `SampleController` 组件中设置一个值来进行控制。

#### 变更

- 更新了带有锚点层的 OpenXR 运行时。
- XR 交互工具包示例场景再次启用。
- 如果 OpenXR 插件和 `BaseRuntimeFeature` 未进行设置，则 `UnityServicesHelper.aar` 会从最终构建中删除。
- `Head Tracking Sample` 被重命名为 `Positional Tracking Sample`。
- 设备和注视点预制件已从 `AR 相机` 中解耦，不再需要将它们作为其子物体。
- 自定义的 `Snapdragon Spaces 控制器配置文件` 被移除，新的默认配置文件是 `Khronos Simple Controller Profile` 。

#### 修复

- `AR Camera` 的编辑器移动（由 `EditorCameraController` 控制）现在在 `AR Session Origin` 下的本地空间中进行。
- `BaseRuntimeFeature` 不再检查运行时并显示对话框，如果启用了该功能但未启用 OpenXR 插件。

### 虚幻引擎

#### 新增

- 增加了 ARPin 支持和 [新的示例地图](./../unreal/samples/AnchorSample.md)。
- 增加了 [主机控制器](./../setup/LaunchingSpacesAppsA3.md) 支持。
- 通过 `ControlScreensaver` 节点禁用了 `BP_Pawn` 中的屏幕超时功能。
- 在每次地图更改时重置跟踪原点。该值可以在 `BP_Pawn` 组件中进行设置。

#### 更改

- 使用锚点层更新了 OpenXR 运行时。
- 再次启用了交互示例地图。
- 将 `Head Tracking Sample` 重命名为 `Positional Tracking Sample`。

#### 修复

- 修复了在 `Positional Tracking Sample` 中使用的播放网格（player mesh）。
- 进行了其他美化方面的改进。

## [0.2.0] - 2022-02-01

### Unity

#### 新增

- 应用程序现在直接在查看器上启动其上下文，不再需要自定义 adb 启动命令。

#### 更改

- 更新了 OpenXR 运行时。
- 主机上不再显示上下文以注册 UI 输入，因此禁用了交互示例。

#### 修复

- 减小浮动 UI 的大小以易于交互。
- 其他美观方面的改进。

### 虚幻引擎

#### 新增

- `Snapdragon Spaces` 插件（需要 OpenXR 插件）。
- 主菜单和示例地图，用于演示 6DoF 头部移动。
- （禁用）示例地图，用于演示与 3D 对象和 2D UI 的交互。

## [0.1.3] - 2021-12-07

### Unity

#### 变更

- 更新 OpenXR 运行时。现在启动和停止问题已经解决。

## [0.1.2] - 2021-12-01

### Unity

#### 新增

- 在归档中新增了 `NOTICE.txt` 文件。
- 在菜单项下的 **窗口 > Snapdragon Spaces > 增加场景到构建设置（Window > Snapdragon Spaces > Add Scenes to Build Settings）** 中新增了一个帮助程序，以自动将示例场景新增到构建设置中。

#### 更改

- 优化和简化了场景和脚本。
- UI 进行了细微的改进。

#### 修复

- **`GyroOverride`** 不再在编辑器中抛出错误。
- 修复了长按操作缺失的错误。

## [0.1.1] - 2021-11-15

### Unity

#### 新增

-  `基础运行时功能` （`BaseRuntimeFeature`）新增了项目验证规则，以避免缺少项目设置。
- OpenXR 运行时已更新。

## [0.1.0] - 2021-11-03

### Unity

#### 新增

- `基础运行时功能` （`BaseRuntimeFeature`） 用于 OpenXR 插件。
- 示例场景，演示 6DoF 头部运动。
- 示例场景，展示如何使用 XR 交互工具包。
