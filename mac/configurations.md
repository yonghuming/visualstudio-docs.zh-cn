---
title: "了解生成配置"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="understanding-build-configurations"></a>了解生成配置

## <a name="project-build-configurations"></a>项目生成配置 

项目可以有多种配置，生成时在这些配置之间进行切换可以得到不同的输出。 例如，使用调试配置时，输出将包括调试符号，使得调试程序可以从有故障的应用程序的堆栈跟踪中解决函数名称、参数或变量。 但是，使用调试配置会增加文件大小，因此对计划发布的应用程序并不适合。

每个平台都有针对自己生成特定的配置。 Xamarin.Android 开发一直只存在发布或调试配置。 Xamarin.iOS 具有更多配置。 较新版本的 iOS 项目只具有调试或发布配置，但可针对设备或任何安装的模拟器设置这些配置。

## <a name="solution-configurations"></a>解决方案配置

与项目配置类似，解决方案配置用于创建整个项目的自定义配置。 通过使用“生成”>“配置”项下的“配置映射”选项卡，可以为每个解决方案项分配一个目标配置，如下所示：


 ![配置映射选项](media/projects-and-solutions-image3.png)

有关详细信息，请参阅 James Montemagno 的 [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg)（配置管理器）视频。

## <a name="run-configuration"></a>运行配置

在 Xamarin Studio 的早期版本中，可选择选项将项目设置为“启动项目”，即使用全局运行/调试命令时运行或调试项目。 此项目的项目名称在项目填充中用粗体表示。

在 Visual Studio for Mac 中，可设置运行配置而非设置启动项目。 在工具栏的下拉列表中，运行配置显示在生成配置选择器旁，如下所示：

 ![“运行配置”下拉列表](media/projects-and-solutions-image8.png)

运行配置是一组包含名称和多个配置的执行选项，其中名称和这些配置根据不同用途在项目中进行了定义。 运行配置根据项目级进行定义，虽然可添加所需的数量，但将为每个可执行项目自定创建默认值。 某些项目类型自动生成其他运行配置。 例如，watchOS 项目可生成速览和通知配置。 
 
配置可以与其他开发者共享（此时配置存储在 .csproj 文件中），或保留在本地（此时存储在 .user 文件中）。

### <a name="android-run-configurations"></a>Android 运行配置
 
Android 项目的运行配置可以在运行或调试项目时指定活动、服务或启动的广播接收器。 可以传递额外的意向数据并设置意向标记，测试不同启动条件下的组件。

`MainLauncher` 以外的活动需要添加将 `Exported=true` 添加到活动属性，以在物理设备上调试或定义意图筛选器。

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>运行配置中可能包含的数据的示例

以下列表提供可能包含在运行配置中的数据的一些示例：

* 常规 .NET 项目
    * 可选的启动应用
    * 启动参数
    * 工作目录
    * 环境变量
    * Mono 运行时选项（仅在 Mono 上运行时使用）
* Android 项目
    * 入口点（活动、服务、接收器）
    * 意向参数和数据
* iOS 项目
    * 模式（常规、后台获取）
* iOS 扩展项目
    * 启动应用：默认或自定义
* WatchKit 项目
    * 模式（速览、通知）
    * 通知有效负载
