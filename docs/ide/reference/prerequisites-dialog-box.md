---
title: "“系统必备”对话框 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: "75"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68e326d8045733fc4f491c51405ed51414a92afd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box
此对话框指定安装哪些必备组件、如何安装以及组件包的安装顺序。  
  
 若要访问此对话框，请在“解决方案资源管理器”中选择项目节点，然后在“项目”菜单上单击“属性”。 当 **“项目设计器”** 出现时，单击 **“发布”** 选项卡。在“发布”页上，单击“系统必备”。 对于安装项目，在“项目”菜单上单击“属性”。 “属性页”对话框出现后，单击“系统必备”。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|元素|说明|  
|-------------|-----------------|  
|**创建用于安装系统必备组件的安装程序**|将应用程序的系统必备组件包含到安装程序 (Setup.exe) 中，以便在安装应用程序之前按照依赖顺序安装这些组件。 默认情况下，该选项是选中的。 如果没有选择此选项，则不会创建 Setup.exe。|  
|**选择要安装的系统必备组件**|指定是否安装组件，如 [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]、Crystal Reports 等等。<br /><br /> 例如，通过选中“SQL Server 2005 Express Edition SP2”旁边的复选框，可以指定安装程序验证目标计算机上是否安装有此组件，如果没有则进行安装。<br /><br /> 有关每个系统必备包的详细信息，请参见本主题后面部分的“系统必备信息”表。|  
|**检查 Microsoft 更新以获取更多可再发行组件**|单击此链接可进入[重新分发组件的引导程序包](http://go.microsoft.com/fwlink/?LinkId=208835)网站检查更新。|  
|**从组件供应商的网站下载系统必备组件**|指定从供应商网站上安装系统必备组件。 这是默认选项。|  
|**从与我的应用程序相同的位置下载系统必备组件**|指定从与应用程序相同的位置安装系统必备组件。 这会将所有系统必备包复制到发布位置。 要让此选项正常工作，系统必备包必须位于开发计算机上。|  
|**从下列位置下载系统必备组件**|指定从选定的位置安装系统必备组件。 可使用“浏览”按钮选择位置。|  
  
## <a name="prerequisites-information"></a>系统必备信息  
 出现在“系统必备”对话框中的系统必备组件可能与下面列表中的不同。 第一次打开对话框时将自动设置**“系统必备”对话框**中所列的必备组件包。 如果随后更改项目的目标框架，则必须手动选择必备组件，以便与新目标框架相匹配。  
  
|元素|说明|  
|-------------|-----------------|  
|**.NET Framework 3.5 SP1**|此程序包会安装下列系统必备组件：<br /><br /> - .NET Framework 2.0、3.0 和 3.5 版<br />- 支持 32 位 (x86) 和 64 位 (x64) 操作系统上的所有 .NET Framework 版本。<br />- 与程序包一起安装的每个 .NET Framework 版本的语言包。<br />- .NET Framework 2.0 和 3.0 服务包。<br /><br /> .NET Framework 3.0 随 Windows Vista 一起提供，.NET Framework 3.5 随 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 一起提供。 .NET Framework 3.5 是针对 32 位操作系统进行编译且目标框架设置为“.NET Framework 3.5”的所有 Visual Basic 和 Visual C# 项目的必需组件，也是针对 64 位操作系统编译的 Visual Basic 和 Visual C# 项目的必需组件。 （不支持 IA64。）注意，默认情况下 Visual Basic 和 Visual C# 项目是针对所有 CPU 体系结构编译的。 有关详细信息，请参阅 [Visual Studio 多目标概述](../../ide/visual-studio-multi-targeting-overview.md)、[再发行 .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) 和[部署 64 位应用程序的必备组件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。<br /><br /> 默认情况下，此项处于选定状态。|  
|**.NET Framework 3.5 SP1 Client Profile**|.NET Framework Client Profile 是完整版 .NET Framework 3.5 SP1 的子集，面向客户端应用程序。 它提供 Windows Presentation Foundation (WPF)、Windows 窗体、Windows Communication Foundation (WCF) 和 ClickOnce 功能的简化子集。 这样可以实现 WPF、Windows 窗体、WCF 和面向 .NET Framework Client Profile 的控制台应用程序的快速部署。 有关详细信息，请参阅 [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)。|  
|**Microsoft .NET Framework 4（x86 和 x64）**|此程序包会为 x86 和 x64 平台安装 .NET Framework 4。<br /><br /> 有关详细信息，请参阅 [Visual Studio 多目标概述](../../ide/visual-studio-multi-targeting-overview.md)、[再发行 .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) 和[部署 64 位应用程序的必备组件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。<br /><br /> 默认情况下，此项处于选定状态。|  
|**Microsoft .NET Framework 4 Client Profile（x86 和 x64）**|.NET Framework 4 Client Profile 是完整版 .NET Framework 4 的子集，面向客户端应用程序。 它提供 Windows Presentation Foundation (WPF)、Windows 窗体、Windows Communication Foundation (WCF) 和 ClickOnce 功能的简化子集。 这样可以实现 WPF、Windows 窗体和面向 .NET Framework 4 Client Profile 的控制台应用程序的快速部署。 有关详细信息，请参阅 [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)。|  
|**Microsoft Office 2007 Primary Interop Assemblies**|此程序包会为 2007 Microsoft Office 产品安装主互操作程序集。 主互操作程序集使托管代码可与 Microsoft Office 应用程序的 COM 对象模型进行交互。 有关详细信息，请参阅 [Office Primary Interop Assemblies](/office-dev/office-dev/office-primary-interop-assemblies)。|  
|**Microsoft Visual Basic PowerPacks 版本 10.0**|Power Pack 是外接程序、控件、组件和工具，可帮助你开发 Visual Basic 应用程序。 此版本包含 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件（使用该组件可以打印 Windows 窗体的内容）和 Printer Compatibility Library（使用它可以不经修改地运行 Visual Basic 6.0 Printer 代码）。|  
|**面向 .NET 2.0 的 Microsoft Visual F# 运行时**|此程序包会为 x86 和 x64 操作系统安装 Visual F# 运行库，它们提供对函数编程以及传统的面向对象及命令性（过程）编程的支持。 如果应用程序或其组件在 Visual F# 和 .NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5 中编写，则必须安装此程序包。<br /><br /> 有关详细信息，请参阅 [F# Language Reference](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf)（F# 语言参考）。|  
|**面向 .NET 4.0 的 Microsoft Visual F# 运行时**|此程序包会为 x86 和 x64 操作系统安装 Visual F# 运行库，它们提供对函数编程以及传统的面向对象及命令性（过程）编程的支持。 如果应用程序或其组件在 Visual F# 和 .NET Framework 4 中编写，则必须安装此程序包。<br /><br /> 有关详细信息，请参阅 [F# Language Reference](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf)（F# 语言参考）。|  
|**Microsoft Visual Studio 2010 报表查看器**|此程序包安装报表查看器控件，你可以使用这些控件向 Windows 窗体和 ASP.NET 应用程序中添加复杂数据报表。|  
|**Microsoft Visual Studio 2010 for Office 运行时（x86 和 x64）**|Visual Studio 中的 Office 开发人员工具提供了易于使用的集成工具，用来通过 Microsoft Office 创建自定义的业务解决方案。 你可以创建托管的智能客户端解决方案，这些解决方案使用 Office 应用程序作为用户界面。 使用这些工具，开发人员可以创建易于部署和维护的安全解决方案。<br /><br /> 有关详细信息，请参阅[如何：使用 ClickOnce 发布 Office 解决方案](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)。|  
|**SQL Server 2005 Express Edition SP2 (x86)**|此程序包安装 Microsoft SQL Server 2005 Express Edition SP2，一个基于 [!INCLUDE[sqprsqext](../../ide/reference/includes/sqprsqext_md.md)] 的数据库应用程序。 SQL Server Express 是 Microsoft SQL Server 桌面引擎 (MSDE) 的替代产品。 SQL Server Express 是免费的并且可以再发行（按照协议），它既可以作为客户端数据库，也可以作为基本的服务器数据库。 除了下列不同外，SQL Server Express 在其他方面都与 SQL Server 2005 相同：<br /><br /> - 不支持企业功能。<br />- 仅限一个 CPU。<br />- 缓冲池的内存大小限制为 1 GB。<br />- 数据库最大大小为 4 GB。|  
|**SQL Server 2008 Express**|此软件包将安装 Microsoft SQL Server 2008 Express，这是免费版的 Microsoft SQL Server 2008，是适用于小型网络、服务器或桌面应用程序的理想数据库。 它可免费用于开发和生产。 随应用程序一起分发 SQL Server 2008 Express 需要先进行免费[注册](http://go.microsoft.com/fwlink/?LinkId=130380)。<br /><br /> 引导程序行为如下：<br /><br /> - 如果计算机已有 SQL Server 2008 Express 或更高版本，则计算机保持在 SQL Server 2008 Express 或更高版本。<br />- 如果计算机没有任何版本的 SQL Server 2008 Express 或更高版本，则软件包安装最新版本的 SQL Server 2008 Express SP1。<br /><br /> 若要了解有关 SQL Server 2008 Express 的详细信息，请访问 [http://go.microsoft.com/fwlink/?LinkId=183586](http://go.microsoft.com/fwlink/?LinkId=183586)。|  
|**Visual C++ 2010 运行库 (IA64)**|此程序包将为 Itanium 体系结构安装 Visual C++ 运行库，以便为 Microsoft Windows 操作系统编程提供例程。 这些例程可自动处理许多 C 和 C++ 语言没有提供的常见编程任务。<br /><br /> 有关详细信息，请参阅 [C 运行时库参考](/cpp/c-runtime-library/c-run-time-library-reference)。|  
|**Visual C++ 2010 运行库 (x64)**|此程序包将为 x64 操作系统安装 Visual C++ 运行库，以便为 Microsoft Windows 操作系统编程提供例程。 这些例程可自动处理许多 C 和 C++ 语言没有提供的常见编程任务。<br /><br /> 有关详细信息，请参阅 [C 运行时库参考](/cpp/c-runtime-library/c-run-time-library-reference)。|  
|**Visual C++ 2010 运行库 (x86)**|此程序包将为 x86 操作系统安装 Visual C++ 运行库，以便为 Microsoft Windows 操作系统编程提供例程。 这些例程可自动处理许多 C 和 C++ 语言没有提供的常见编程任务。<br /><br /> 有关详细信息，请参阅 [C 运行时库参考](/cpp/c-runtime-library/c-run-time-library-reference)。|  
|**Windows Installer 3.1**|此程序包安装 Microsoft Windows Installer 可再发行版本 3.1，以便可以安装 Windows Installer 安装项目。 它预安装在 Windows Server 2003 SP1 和更高版本上。<br /><br /> 默认情况下，此项处于选定状态。|  
|**Windows Installer 4.5**|此程序包安装 Microsoft Windows Installer 可再发行版本 4.5，以便可以安装 Windows Installer 安装项目。|  
  
## <a name="see-also"></a>另请参阅  
 [“项目设计器”->“发布”页](../../ide/reference/publish-page-project-designer.md)   
 [应用程序部署必备](../../deployment/application-deployment-prerequisites.md)   
 [再发行 .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [部署 64 位应用程序的必备组件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Visual Studio 多目标概述](../../ide/visual-studio-multi-targeting-overview.md)