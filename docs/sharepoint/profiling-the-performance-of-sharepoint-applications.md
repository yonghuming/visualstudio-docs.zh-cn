---
title: "分析 SharePoint 应用程序的性能 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0effe0190d54d05d706127a8e5fada66af1c7ab6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>分析 SharePoint 应用程序的性能
  如果 SharePoint 应用程序正在执行速度缓慢或效率低下，你可以使用 Visual Studio 中的分析功能来识别有问题的代码和其他元素。 通过使用负载测试功能，可以确定 SharePoint 应用程序在压力，如多个用户同时访问应用程序时的执行方式。 通过运行 web 性能测试，可以测量应用程序在 web 上找到的执行方式。 通过使用编码的 UI 测试，你可以验证整个 SharePoint 应用程序，包括其用户界面，是否工作正常。 当在一起使用这些测试时，它们可以帮助你在部署你的应用程序之前识别性能问题。  
  
## <a name="profiling-tools-overview"></a>分析工具概述  
 分析是指观察并记录你的应用程序的性能行为运行的过程。 通过分析你的应用程序，您可以发现一些问题，例如瓶颈，代码效率低下和导致应用程序运行缓慢或使用过多内存的内存分配问题。 例如，你可以使用分析以确定你的代码，代码段，通常称为会显著降低你的应用程序的总体性能的热点。 确定热点后，你通常可以优化或消除它们。  
  
 可以使用在集成的开发环境 (IDE) 中的多个分析工具确定并找到这些类型的性能问题。 对于其他类型的 Visual Studio 项目一样，这些工具可为 SharePoint 项目相同的方式。 分析工具性能向导将引导您完成创建性能会话，使用你指定的测试。 性能会话是一套用于从应用程序，以及一个或多个分析运行的结果中收集性能信息的配置数据。 性能会话存储在你的项目文件夹，而且你可以查看在**性能资源管理器**。 有关详细信息，请参阅[了解性能收集方法](/visualstudio/profiling/understanding-performance-collection-methods)。  
  
 创建并在你的应用程序上运行的配置文件分析后，报表将提供有关其性能的详细信息。 此报表可以随时间、 分层函数调用堆栈或调用关系树中包括等关系图的 CPU 使用率的项目。 报表的具体内容可以不同，具体取决于测试运行，如采样或检测的类型。 有关详细信息，请参阅[分析工具报告概述](http://go.microsoft.com/fwlink/?LinkId=224689)。  
  
## <a name="performance-session-process"></a>性能会话进程  
 若要分析的应用程序，启动时通过使用分析工具性能向导创建性能会话。 在菜单栏上，选择**分析**，**启动性能向导**。 完成该向导，你输入你的性能会话，例如所需的配置文件方法和要分析的应用程序所需的信息。 有关详细信息，请参阅[How to： 性能向导分析网站或 Web 应用程序使用](http://go.microsoft.com/fwlink/?LinkId=224692)。 作为替代方法，你可以使用命令行选项来设置和运行性能会话。 有关详细信息，请参阅[使用分析工具从命令行](http://go.microsoft.com/fwlink/?LinkId=224703)。 如果你想要手动配置每个方面的性能会话，请参阅[如何： 手动创建性能会话使用分析工具](http://go.microsoft.com/fwlink/?LinkId=224691)。 你还可以创建性能会话从单元测试，通过在**测试结果**窗口中，打开单元测试的快捷菜单，然后选择**创建性能会话**。  
  
 设置性能会话后，保存会话配置、 服务器配置为提供的分析数据，并在应用程序运行。 当你使用应用程序，则性能数据写入日志文件。 性能会话中列出**性能资源管理器**下**目标**文件夹。 性能会话完成后，其报告将显示在**报表**文件夹中的**性能资源管理器**。 若要显示报表，请打开在**性能资源管理器**。 若要查看或配置性能会话的属性，请打开其快捷菜单中的**性能资源管理器**，然后选择**属性**。 有关性能会话的特定属性的详细信息，请参阅[配置分析工具性能会话](http://go.microsoft.com/fwlink/?LinkId=224694)。 有关如何解释性能会话的结果的信息，请参阅[分析分析工具数据](http://go.microsoft.com/fwlink/?LinkId=224704)。  
  
## <a name="stress-testing"></a>压力测试  
 你可以通过在 Visual Studio Ultimate 中创建负载测试和 web 性能测试中分析你的应用程序的压力性能。 当你在 Visual Studio 中创建负载测试时，你指定的因素，调用的情况下，测试针对应用程序的组合。 这些因素包括负载模式、 测试组合模型、 测试组合、 网络组合和 web 浏览器组合。 负载测试方案可以包含单元测试和 web 性能测试。  
  
 图 1： 负载测试结果示例  
  
 ![运行负载测试关系图视图](../sharepoint/media/load-webgraphs.png "运行负载测试关系图视图")  
  
 Web 性能测试模拟最终用户可以在与 SharePoint 应用程序进行交互。 你可以创建 web 性能测试，通过在浏览器会话录制 HTTP 请求或使用**Web 性能测试记录器**。 Web 请求出现在**Web 性能测试编辑器**在浏览器会话完成之后。 然后，你可以调试中的结果**Web 性能测试结果查看器**。 你可以通过使用可以手动构建 web 性能测试**Web 性能测试编辑器**。  
  
## <a name="testing-user-interfaces"></a>测试用户界面  
 编码的 UI 测试自动驱动器通过其用户界面 (UI) 的 SharePoint 应用程序。 这些测试涵盖 UI 控件，如按钮和菜单，以验证它们正常工作。 这种测试是验证或其他逻辑执行在 UI 中，如在网页中的情况特别有用。 编码的 UI 测试还可用于自动化手动测试。 你可以创建编码的 UI 测试 SharePoint 应用程序相同的方式创建其他类型的应用程序的测试。 有关详细信息，请参阅[测试 SharePoint 2010 应用程序使用编码的 UI 测试](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[演练：分析 SharePoint 应用程序](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|演示如何在 SharePoint 应用程序上执行的采样配置文件分析。|  
|[发布前对应用进行性能测试](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|描述如何创建负载测试，帮助你压力测试 SharePoint 应用程序。|  
|[单元测试代码](/visualstudio/test/unit-test-your-code)|描述如何使用单元测试在你的代码中查找逻辑错误。|  
|[使用编码的 UI 测试来测试 SharePoint 2010 应用程序](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|介绍如何测试 SharePoint 应用程序的用户界面。|  
  
## <a name="see-also"></a>另请参阅  
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [测试应用](/devops-test-docs/test/test-apps-early-and-often)   
 [提高代码质量](/visualstudio/test/improve-code-quality)  
  
  