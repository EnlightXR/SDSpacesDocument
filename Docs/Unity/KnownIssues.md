# Unity 的已知问题

目前已知有几个问题可能会影响开发工作流程。这些是已知的问题，将在未来的 Unity 软件包或 `Snapdragon Spaces Services` 运行时版本中解决。

如果本章节未包含您的问题，请查阅全部 SDK [已知问题](./../KnownIssues.md)。

# Gradle 构建问题

在某些情况下，添加自定义控制器存档可能会导致 Gradle 缓存错误。此时，删除在 `Temp > gradleOut` 下的项目文件夹中生成的临时 Gradle 项目文件夹可能会解决该问题。

# 手部跟踪问题

## 通用

- 头部运动可能会引起手部运动。

## 用户体验的局限性

- 释放物体只能使用 [开手手势](./../designux/InteractionGestures.md#开手) 来执行。
- 在某些情况下，手之间的 [遮挡](./../designux/BestPractices.md#遮挡) 可能会导致左右手的反转。
- 如果显示手部 avatar，手指尖可能会出现一些抖动。通常不建议在 AR 内中显示手部 avatar。
