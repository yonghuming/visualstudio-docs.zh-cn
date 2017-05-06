---
title: "验证和调试 SharePoint 代码"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "单元测试 [Visual Studio 中的 SharePoint 开发]"
  - "IntelliTrace [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发，IntelliTrace"
  - "Visual Studio 中的 SharePoint 开发，单元测试"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 验证和调试 SharePoint 代码
  通过使用 IntelliTrace 和单元测试，您可以更轻松地调试 SharePoint 解决方案，并确保解决方案中的每个方法都正常运行。  通过按照适用于其他类型的项目的过程进行操作，可以在 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] Service Pack 1 \(SP1\) 中将这些功能用于 SharePoint 项目。  
  
## IntelliTrace  
 通过使用 IntelliTrace，您不仅能确定SharePoint解决方案的当前状态，还能确定过去发生的事件以及这些事件发生的上下文。  您可在SharePoint 解决方案中来回切换记录的感兴趣的事件的不同时间点，并可查看变量在每个时间点的状态和值。  通过使用此动态导航，您可以快捷方便地调试 SharePoint 解决方案，而不必设置很多断点。  您还可将调试会话保存到 IntelliTrace 记录 \(.iTrace 文件\)，之后在 Visual Studio 旗舰版打开它，并且执行崩溃后调试。  .iTrace 文件包括有关特定 SharePoint 错误发生位置的详细信息，因此，您可以更轻松地确定导致错误的原因。  在 .iTrace 文件中的信息是 SharePoint 中的统一的记录系统 \(ULS\) 创建的完全错误日志的子集。  此信息包括只特定于SharePoint的事件，例如当用户配置文件打开或关闭时，SharePoint项目的属性加载，读取或更改时。  您可以配置事件的IntelliTrace记录。  有关更多信息，请参见[使用保存的 IntelliTrace 数据](../debugger/using-saved-intellitrace-data.md)和[配置 IntelliTrace 以收集调试信息](http://msdn.microsoft.com/zh-cn/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
 当 SharePoint 发生错误时，错误对话框显示该特定错误的“依赖项 ID”标识符。  您还可以获取从在 .iTrace 文件中列出的活动的相关 ID。  若要显示所有发生在一个给定的相关ID的事件的列表，您可以在**Analysis**中的IntelliTrace摘要页的部分输入ID。  该部分，可以选择是否显示结果或事件的名称及其调用的信息，如函数名的事件的名称，退出，访问点，参数，和返回值。  
  
 你可以通过选择**F5**得到的IntelliTrace Visual Studio中的事件。  要获得特定于SharePoint的事件，但是，你必须通过使用Microsoft监控代理收集的SharePoint解决方案的IntelliTrace数据。  此工具收集 IntelliTrace 数据和创建部署在 Visual Studio 之外的应用程序的 .iTrace 文件。  有关更多信息，请参见[IntelliTrace 功能](../debugger/intellitrace-features.md)和[使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
## 单元测试  
 可通过执行单元测试（其中，将在测试方法中写入和运行测试代码）更轻松地找出代码中的错误。  这些方法包含空变量和一个 Assert 语句，该语句可用来基于 SharePoint 对象模型验证项目的逻辑和功能。  有关详细信息，请参阅[单元测试代码](../test/unit-test-your-code.md)。  
  
### 对 Microsoft Fakes 框架的支持  
 SharePoint 项目支持基于Microsoft伪造品，是隔离 framework 可以创建基于委托存根测试和填充在应用程序的基于 .NET Framework。  
  使用伪造品结构，您可以创建，维护，插入在单元测试中的伪的实现测试。  这些存根和填充隔离单元测试中从该环境测试。  您可以创建存根，以测试使用接口或非密封选件类具有可重写的方法中的代码。  您可以创建填充硬编码重定向，调用密封类的静态或不可重写的方法来替代上述实现。  您还可以使用具有存根类型和填充类型的委托，动态自定义各个存根成员行为。  有关详细信息，请参阅[用 Microsoft Fakes 隔离测试代码](../test/isolating-code-under-test-with-microsoft-fakes.md)。  
  
## 相关主题  
  
|标题|描述|  
|--------|--------|  
|[使用 IntelliTrace](../debugger/intellitrace.md)|通过使用 IntelliTrace，介绍如何更轻松地调试 Visual Studio 解决方案。|  
|[演练：使用 IntelliTrace 调试 SharePoint 应用程序](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|演示如何使用 IntelliTrace 找出 SharePoint 项目中的编码错误。|  
|[单元测试代码](../test/unit-test-your-code.md)|描述如何使用单元测试来查找您代码中的逻辑错误。|  
  
## 请参阅  
 [提高代码质量](../test/improve-code-quality.md)  
  
  