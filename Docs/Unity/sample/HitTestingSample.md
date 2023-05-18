# 命中测试示例

本示例对在现实世界中的点和平面进行命中测试进行了演示。关于通过射线检测进行命中测试以及 AR Foundation 的 `AR 射线检测子系统` （`AR Raycast Subsystem` ） 组件的基本信息，请参考 [Unity 文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.2/manual/raycast-manager.html)。使用此功能，必须先打开 `Project Settings > XR Plug-in Management > OpenXR (> Android Tab)`，找到 OpenXR 插件设置并启用该功能。文档中将交替使用 **射线检测（ray casting）** 和 **命中测试（hit testing）** 这两个等价术语。

## 示例的工作原理

将 `AR Raycast Manager` （AR 射线检测管理器）添加到 `AR Session Origin` 游戏对象后，射线检测子系统将被启用。如果没有可用的平面管理器，则 `Hit Testing` 功能将为命中测试创建基础。如果后续生成一个平面管理器，则底层平面检测子系统将针对该管理器进行调整，命中跟踪可能会有所不同（例如，结果将取决于在平面管理器上设置的平面过滤器）。为了获得最佳结果，如果您也使用命中测试，请启用平面管理器上的所有过滤器。如果您不使用单独的平面管理器，则命中测试功能将进行自动处理以获得最佳结果。

`AR Raycast Manager`  组件提供了一个字段，用于定义成功与平面相交时要生成的预制件。对于此示例，预制件留空（left blank），因为这一功能已经在 `Hit Testing Sample Controller` 组件中实现。

射线检测管理器的 `Raycast` 函数将根据射线是否命中平面返回布尔值。命中结果将被添加到 `ARRaycastHit` 列表中，并按距离升序排序（即，最近的排在最前）。

```
    public void Update() {
        CastRay();
        _activeIndicator.transform.position = _desiredPosition;
    }

    private void CastRay() {
        Ray ray = new Ray(_cameraTransform.position, _cameraTransform.forward);

        List<ARRaycastHit> hitResults = new List<ARRaycastHit>();
        if (_raycastManager.Raycast(ray, hitResults)) {
            _desiredPosition = hitResults[0].pose.position;
            ...
        }
        else {
            ...
        }
    }
```

示例场景具有默认的红色 gizmo 指示器，可跟随注视点移动。每帧都会从头部起点创建一条射线，指向注视方向。如果射线碰到平面，则指示器 gizmo 将改变颜色并移动到命中位置。如果没有碰到任何物体，则指示器 gizmo 将保持不变。
