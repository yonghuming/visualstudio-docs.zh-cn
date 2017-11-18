---
title: "什么 &#39; s Visual Studio 中设计的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: "32"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: ce1172baf41cf670b253b2420f5538607addfeb7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="what39s-new-for-design-in-visual-studio"></a>什么 &#39; s 用于 Visual Studio 中设计的新功能

## <a name="live-dependency-validation"></a>实时依赖关系验证

删除不需要的依赖关系是管理技术债务的重要组成部分。
依赖项的实时验证现在包含，提供有关问题，精确的信息，并完全获益错误列表和编辑器中的新功能。

![在操作中的实时依赖关系验证](media/dep-validation-whatsnew-01.png)

已更改的创作体验，以使依赖项验证更容易地发现、 更易于访问，更改到"依赖项关系图"从"层关系图"术语。

**体系结构**菜单现在包含直接创建依赖项关系图的命令：

![体系结构菜单上的实时依赖项](media/dep-validation-whatsnew-02.png)

...和中层依赖项关系图中和及其说明的属性名称已更改，以使它们更有意义：

![实时更新的依赖项属性名称](media/dep-validation-whatsnew-03.png)

现在，你看到立即在解决方案中的当前代码分析结果中所做的更改的影响每次保存关系图。 你无需再等待完成"验证依赖关系"命令。

有关更多详细信息，请参阅[这篇博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。 
 
## <a name="uml-designers-have-been-removed"></a>已删除 UML 设计器

已从 Visual Studio Enterprise 的此版本中删除的 UML 设计器。

* UML 关系图现在显示为 XML 文件
* UML 模型资源管理器不再存在
* 建模的项目引用不再用于依赖关系验证
* 不再显示解决方案资源管理器中的"层引用"节点
* 不再使用依赖项 （层） 关系图上的"验证"生成操作-已删除的生成任务 
* 为版本之间的往返维护的项目结构
* 你可以仍打开、 创建、 编辑和保存为 XML 的依赖项 （层） 关系图
* TFS 工作项链接到依赖项 （层） 关系图不是可在设计图面上访问
* 不再支持后从链接到 DSL 或图层 
* 不再支持 UML 建模 SDK 的可扩展性

但是，支持可通过可视化.NET 和 c + + 代码的体系结构为[代码图](map-dependencies-across-your-solutions.md)，和的依赖项验证上面所述的重大改进。

如果你的 UML 设计器的大量用户，你可以继续使用 Visual Studio 2015 或更早版本，而你决定备用工具对于你的 UML 需求。

有关更多详细信息，请参阅[这篇博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>对体系结构和建模工具的版本支持  

Visual Studio 有多个版本。 并非所有版本支持体系结构和建模工具。 下表显示每个工具的可用性。  
  
|**功能**|**Enterprise**|**Professional**|**Community**|**速成版**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**代码图**|是|请参阅注释 (1)|-|-|  
|**依赖项关系图**|是|请参阅注释 (2)|请参阅注释 (2)|-|  
|**定向关系图**（DGML 关系图）|是|是|是|-|  
|**代码克隆**|是|-|-|-|  
  
注释 (1)：仅支持读取代码图、筛选代码图、添加新的泛型节点以及从所选内容创建新的定向关系图。

注释 (2): 仅支持读取依赖项关系图。
