---
title: "如何：为 Web 站点收集性能数据 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6acfbee87e64e71ae85290ba74f1464af7181228
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>如何：为 Web 站点收集性能数据
可以使用“性能向导”  为 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序收集性能数据。 可以分析在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中打开的 Web 应用程序，也可以分析位于本地计算机且未在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] IDE 中打开的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Web 站点。  
  
> [!NOTE]
>  利用“性能向导”  ，你可以将层交互 (TIP) 数据和/或 JScript 性能数据添加到收集的分析数据中。 TIP 选项从服务器端进程收集数据。 JScript 分析从本地或远程网站运行的脚本处收集数据。 大多数情况下，应只选其中一项。  
  
 根据管理员提供的用户访问权限设置，单个用户可能会有（也可能没有）在托管 ASP.NET 进程的计算机上创建探查器会话的安全权限。 下面的示例说明了用户之间可能存在的差异：  
  
-   如果管理员将驱动程序和服务设置为启动，一些用户可能会访问高级分析功能。  
  
-   域用户可能只能访问样本分析。  
  
-   一些用户可能会拒绝其他所有用户访问分析功能。  
  
 有关详细信息，请参阅[分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)和 [VSPerfCmd](../profiling/vsperfcmd.md) 中的管理选项。  
  
### <a name="to-profile-a-web-site-project"></a>若要分析网站项目  
  
1.  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 或 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] 中打开 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 项目。  
  
2.  在“分析”菜单上，选择“性能探查器”，选择“性能资源管理器”，然后选择“启动”。  
  
3.  在向导的第一页上，选择一种分析方法，然后单击“下一步” 。 有关分析方法的详细信息，请参阅[了解性能收集方法](../profiling/understanding-performance-collection-methods.md)。 请注意，并发可视化工具分析方法对 Web 应用程序不可用。  
  
4.  在“要以哪个应用程序为目标进行分析?”  下拉列表中，请确保选择当前项目，然后单击“下一步” 。  
  
5.  在向导的第三页上，可以选择添加层交互分析 (TIP) 数据和/或网页上运行的 JavaScript 中的数据。  
  
    -   若要收集层交互，请选中“启用层交互分析”  复选框。  
  
    -   若要从网页中运行的 JavaScript 中收集数据，请选中“分析 JavaScript”  复选框。  
  
6.  单击 **“下一步”**。  
  
7.  在向导的第四页上，单击“完成” 。  
  
8.  为 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序创建了性能会话，且在浏览器中启动了网站。 练习要分析的功能，然后关闭浏览器。  
  
     探查器生成数据文件，并在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主窗口中显示数据的摘要视图。  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>未在 Visual Studio 中打开项目的情况下分析网站  
  
1.  打开 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 或 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]。  
  
2.  在“分析”菜单上，选择“性能探查器”，选择“性能资源管理器”，然后选择“启动”。  
  
3.  在向导的第一页上，选择一种分析方法，然后单击“下一步” 。 有关详细信息，请参阅[了解性能收集方法](../profiling/understanding-performance-collection-methods.md)。  
  
4.  在向导的第二页上，选择“分析 ASP.NET 或 JavaScript 应用程序选项”  ，然后单击“下一步” 。  
  
5.  在向导第三页的“运行 Web 应用程序的 URL 或路径是什么”  框中，在应用程序主页上输入 URL，然后单击“下一步” 。  
  
    -   对于基于网站的服务器 (IIS)，键入 URL，如 **http://localhost/MySite/default.aspx**。 这将导致对 MySite 应用程序根目录上本地计算机中的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序进行分析，并且在 Internet Explorer 中启动该站点网页 default.aspx，从而启动会话。  
  
    -   对于基于文件的网站，请键入路径，例如文件 ///**c:\WebSites\MySite\default.aspx**。 这将导致对位于 c:\webSites\MySite 上的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序进行分析，并且在 Internet Explorer 中启动 http://localhost:nnnn/MySite/default.aspx 网页，从而启动会话。  
  
    -   对于想要在其收集 JavaScript 数据的外部网站，键入 URL，例如 http://www.contoso.com。  
  
     有关详细信息，请查看 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 目标二进制文件的属性页。  
  
6.  在向导的第三页上，可以选择添加层交互分析 (TIP) 数据和/或网页上运行的 JavaScript 中的数据。  
  
    -   若要收集层交互，请选中“启用层交互分析”  复选框。  
  
    -   若要从网页中运行的 JavaScript 中收集数据，请选中“分析 JavaScript”  复选框。  
  
7.  单击 **“下一步”**。  
  
8.  在向导的第四页上，单击“完成” 。  
  
9. 这样就为 ASP.NET 应用程序创建了性能会话，并在浏览器中启动了网站。 练习要分析的功能，然后关闭浏览器。  
  
     探查器生成数据文件，并在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主窗口中显示数据的摘要视图。  
  
## <a name="see-also"></a>另请参阅  
 [概述](../profiling/overviews-performance-tools.md)   
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [了解检测数据值](../profiling/understanding-instrumentation-data-values.md)   
 [了解采样数据值](../profiling/understanding-sampling-data-values.md)
