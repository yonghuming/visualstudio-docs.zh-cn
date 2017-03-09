---
title: "以下项目配置已过期：&lt;configuration&gt;。 是否生成这些项目? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 以下项目配置已过期：&lt;configuration&gt;。 是否生成这些项目?
你正在编辑一个 Visual Studio 项目或已在解决方案资源管理器中选择了一个项目，并且已选择“启动”\(F5\) 项目或“启动\(不调试\)”\(CTRL\+F5\)。 一个或多个项目允许调试而不重新生成，即使自上次生成以来项目已经被修改了也是如此。  
  
 集成开发环境 \(IDE\) 正在请求是否重新生成允许调试（而不重新生成）的项目。  
  
### 响应此消息  
  
-   选择消息底部的一个按钮。 选项为：  
  
|术语|定义|  
|--------|--------|  
|**是**|你将重新生成已过期的项目。 这意味着：<br /><br /> -   如果项目尚未生成，则会生成项目。<br />-   如果自上次生成以来项目已经被修改了，则会重新生成项目。<br />-   调试该项目，或启动而不调试该项目。|  
|**No**|你将仅重新生成这些已过期的项目，这些项目必须在调试前重新生成。 这意味着：<br /><br /> -   如果项目允许调试（不重新生成）（例如，Visual C\+\+ MFC 应用程序项目），则不会重新生成项目。<br />-   如果项目必须在调试前重新生成（例如，一个 Visual Basic 项目），则会重新生成项目。<br />-   调试该项目，或启动（不调试）该项目。|  
|**取消**|当前操作已停止。 没有生成、启动或调试任何项目。|  
  
## 请参阅  
 [“配置管理器”对话框](http://msdn.microsoft.com/zh-cn/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [如何：创建解决方案和项目生成配置](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [如何：创建和移除项目依赖项](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-cn/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/zh-cn/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)   
 [了解生成配置](../ide/understanding-build-configurations.md)   
 [NIB：项目作为容器](http://msdn.microsoft.com/zh-cn/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB：项目中的项管理](http://msdn.microsoft.com/zh-cn/762e606b-7f44-4b66-97a1-e30a703654a0)