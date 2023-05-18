# XR 手部跟踪管理器 API

**XR Hand Tracking Manager API**

| 静态方法 | 描述 |
| -- | -- |
| `GameObject DefaultLeftHandPrefab` | 参考资源文件夹中的默认**Left Hand** 预制件，位于 `Packages > Prefabs > Resources > QualcommHandLeft` |
| `GameObject DefaultRightHandPrefab` | 参考资源文件夹中的默认**Right Hand** 预制件，位于 `Packages > Prefabs > Resources > QualcommHandRight` |
| `void InstantiateHandTrackingManager()`| 使用默认手部预制件实例化 **手部跟踪管理器** |
| `XRHandTrackingManager GetOrCreate(GameObject leftHandPrefab, GameObject rightHandPrefab)`| 获取现有的或创建一个 **手部跟踪管理器**，如果它不存在参数中给定的 **手部预制件** |
| `void Destroy(XRHandTrackingManager manager)`| 销毁给定的**Hand Tracking Manager** 实例或尝试找到并销毁它（如果它确实存在） |

| 非静态方法 | 描述 |
| -- | -- |
| `GameObject LeftHandPrefab` |  |
| `GameObject RightHandPrefab` |  |
| `void StartDevices()` | 在输入系统中启用手部跟踪设备 |
| `void StopDevices()` | 在输入系统中禁用手部跟踪设备 |
| `void RefreshLeftHand()` | 如果预制件已更改，则重新生成左侧对象 |
| `void RefreshRightHand()` | 如果预制件已更改，则重新生成右侧对象 |
| `void ToggleLeftHand(bool visible)` | 切换左手可见性 |
| `void ToggleRightHand(bool visible)` | 切换右手可见性 |
| `void SetLeftHandSkin(HandSkin skin)` | 如果手对象可设置皮肤，则设置左手皮肤 |
| `void SetRightHandSkin(HandSkin skin)` | 如果手对象可设置皮肤，则设置右手皮肤 |


