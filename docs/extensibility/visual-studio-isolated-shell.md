---
redirect_url: shell/visual-studio-isolated-shell
title: "Visual Studio 独立 Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc6254be575593056c386360aa0d7c0a83833d75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 独立 Shell
Visual Studio 独立 shell，可创建独立的应用程序可以运行的并行与其他版本的 Visual Studio。 它是主要用于承载专用的工具，可以使用 Visual Studio 服务，但还具有自定义的外观和品牌。 Visual Studio 功能和菜单命令组可以轻松地打开和关闭。 应用程序标题、 应用程序图标和初始屏幕是完全可自定义。 有关可自定义功能的列表，请参阅[自定义独立 Shell](../extensibility/customizing-the-isolated-shell.md)。  
  
 若要使用的独立的 shell 项目，必须安装 Visual Studio SDK。 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 若要创建独立的 shell 应用程序，请从 Visual Studio Shell 隔离的项目开始。 此项目包含你开发和测试独立的 shell 应用程序所需的所有内容。 当你准备好编写部署你的应用程序安装程序，你必须获取从独立的 shell 可再发行组件包[Microsoft Visual Studio Shell （独立） 可再发行组件包](http://go.microsoft.com/fwlink/?LinkId=616022)。  
  
> [!NOTE]
>  你可以访问独立的 shell 可再发行组件包之前，你将需要填写简要客户调查。  填写调查之后, 你将定向到 Visual Studio 连接页，带有可再发行组件包下载链接。  你可以在后续访问的 Visual Studio 连接站点上找到的下载链接**程序 &#124;VISUAL STUDIO 2015 集成和独立 SHELL**选项卡。  
  
> [!NOTE]
>  有关如何部署独立的 shell 基于应用程序的详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="working-with-the-isolated-shell"></a>使用独立 shell  
 Visual Studio 独立 shell 应用程序具有完全访问权限 Visual Studio 服务，并支持特殊的自定义项和品牌。 有多种方法可以自定义独立的 shell 应用程序：  
  
-   Vspackage 和 Managed Extensibility Framework (MEF) 组件部分可用于扩展的独立的 shell 应用程序，就像你将在任何其他 Visual Studio 扩展中使用它们。 有关详细信息，请参阅[扩展独立 Shell](../extensibility/extending-the-isolated-shell.md)。  
  
-   若要使 Visual Studio 功能和菜单命令组可用或不可用，请更新应用程序的用户界面 (UI) 项目中的.vsct 文件。  
  
-   若要删除**选项**页或从应用程序，其他 Visual Studio shell 组件更新.pkgundef 文件的应用程序。  
  
-   若要修改外观的其他方面或外壳程序的行为，请更新应用程序的.pkgdef 文件。  
  
-   当启动应用程序时，还可以指定外壳程序的某些方面。 若要执行此操作，更新 appenvstub.dll 开始入口点调用中的参数。  
  
 有关你可以自定义的不同元素的详细信息，请参阅[的独立 Shell 元素](../extensibility/elements-of-the-isolated-shell.md)。  
  
## <a name="standard-features-of-the-isolated-shell"></a>标准功能的独立 Shell  
 以下功能是标准到 Visual Studio 的所有版本。  
  
|功能类别|功能|  
|----------------------|-------------|  
|IDE 功能|导入/导出设置<br /><br /> 工具箱控件安装程序<br /><br /> 任务列表和错误列表<br /><br /> 输出窗口<br /><br /> 起始页<br /><br /> 属性窗口<br /><br /> 工具箱<br /><br /> “解决方案资源管理器”<br /><br /> “书签”窗口<br /><br /> 类视图<br /><br /> 对象浏览器<br /><br /> “命令”窗口<br /><br /> 文档大纲<br /><br /> 资源视图<br /><br /> 外部工具<br /><br /> Windows Communication Foundation (WCF) 添加服务引用<br /><br /> 语言集成查询 (LINQ) 支持|  
|编辑器/设计器|代码浏览工具 （统一的查找、 源定义，继承）<br /><br /> IntelliSense<br /><br /> 智能标记<br /><br /> 代码片段管理器<br /><br /> 代码段<br /><br /> 重构<br /><br /> 整齐排列<br /><br /> IntelliSense 筛选<br /><br /> “代码定义”窗口<br /><br /> 应用程序设计器<br /><br /> Windows 窗体设计器<br /><br /> Windows Presentation Foundation (WPF) 设计器|  
|调试|C# 表达式计算器<br /><br /> 本地调试<br /><br /> 托管调试<br /><br /> 编辑并继续<br /><br /> 跨线程调试<br /><br /> 可视化效果<br /><br /> 数据提示<br /><br /> 本机调试<br /><br /> 脚本调试<br /><br /> 互操作调试<br /><br /> 实时 (JIT) 调试<br /><br /> 多进程调试<br /><br /> XSLT 调试<br /><br /> 附加到本地进程<br /><br /> 跟踪点<br /><br /> 断点约束|  
|数据|服务器资源管理器 （简体-仅限数据）<br /><br /> 将数据绑定到本地数据 (。MDF 或。MDB)<br /><br /> 数据绑定到对象<br /><br /> 数据绑定到 Web 服务<br /><br /> 完整的数据控件集<br /><br /> XML 编辑器<br /><br /> 将数据绑定到本地数据库服务器<br /><br /> “数据源”窗口|  
|Web|HTML 编辑器<br /><br /> Web 浏览器<br /><br /> Web 窗体设计器<br /><br /> 网站项目<br /><br /> Web 应用程序项目|  
|扩展性|使用 Vspackage 和 MEF 组件|  
  
## <a name="see-also"></a>另请参阅  
 [Shell（独立或集成）](../extensibility/shell-isolated-or-integrated.md)