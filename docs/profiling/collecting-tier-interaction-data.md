---
title: "通过使用 Visual Studio IDE 收集层交互数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "分析工具, ADO.NET 分析"
  - "层交互分析方法"
  - "分析工具, 层交互方法"
  - "ADO.NET 性能分析"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 通过使用 Visual Studio IDE 收集层交互数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

层交互分析提供通过 ADO.NET 服务与数据库通信的多层应用程序中函数的执行时间的其他信息。  收集的数据仅用于同步函数调用。  
  
 **Visual Studio 版本**  
  
 使用 Visual Studio 旗舰版、Visual Studio 高级专业版、Visual Studio 专业版，互可收集分析数据的层交。  但是，层交互分析数据仅能在VS旗舰版和VS高级专业版中查看。  
  
 **Windows 8 和 Windows Server 2012**  
  
 若要在Windows 8 桌面应用程序 和 Windows Server 2012 应用程序收集层有关的交互数据，必须使用检测方法。  不能为 Windows 应用商店应用收集层交互数据。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  您可以在其它支持的 Windows 版本中对所有的分析方法包含层交互数据。  
  
 **性能向导**  
  
 由于在性能向导中的 bug，您必须从性能资源管理器添加层交互数据收集选项到分析运行。  还必须为性能资源管理器目标节点添加项目，可执行文件或网站。  
  
### 通过使用性能会话属性页将层交互数据添加到分析运行中  
  
1.  在 性能资源管理器 中，请从上下文菜单中选择“属性” 。  
  
2.  选中“启用层交互分析”页，然后选中“启动交互分析”复选框。  
  
3.  在“性能资源管理器”中，选择“目标”节点，然后选择指定项目可执行或想要分析的网站。  
  
## 请参阅  
 [“层交互”视图](../profiling/tier-interactions-view.md)