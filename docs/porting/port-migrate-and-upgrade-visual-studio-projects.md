---
title: "移植、迁移和升级 Visual Studio 项目 | Microsoft Docs"
ms.custom: 
ms.date: 2/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: dac3cb1d7767c2ff76ac25f6a486ad30a8d54831
ms.openlocfilehash: 6b61cbc8460266ac305b12bf14f92d7445bfc900
ms.lasthandoff: 03/03/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>移植、迁移和升级 Visual Studio 项目

Visual Studio 的每个版本通常都支持大部分以前的项目、文件和其他资产类型。 你可以一如既往地使用这些类型，如果你不依赖新功能，Visual Studio 可保留与之前版本（如 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012）的向后兼容性。 （若要了解哪些功能特定于哪个版本，请参阅[发行说明](https://www.visualstudio.com/vs/release-notes/)。）

但是，在以后对某些类型的支持会改变。 较新版本的 Visual Studio 可能不再支持某些类型，或者不再要求迁移或更新这些类型，使其不再向后兼容。 本主题提供有关 Visual Studio 2017 中受影响的项目类型的详细信息。 有关 Visual Studio 2017 支持类型的列表，请参阅[平台目标以及兼容性](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs)主题。

> [!Note]
> 打开某些项目类型需要通过 Visual Studio 安装程序添加相应的工作负荷。


## <a name="projects"></a>项目

以下列表描述了 Visual Studio 2017 中对在之前版本中创建的项目的支持。 如果在此处未看到任何项目或文件类型（此处本应出现这些内容），请参阅[本主题的 Visual Studio 2015 版本](https://msdn.microsoft.com/library/hh266747.aspx)并在下面的注释中记录。

| 项目类型 | 支持 |
| --- | --- |
| .NET Core 项目 (.xproj) | 使用 Visual Studio 2015 旧预览工具创建的项目，其中包括 .xproj 项目文件。 使用 Visual Studio 2017 打开 .xproj 文件时，系统将提示将该文件迁移到 .csproj 格式（执行 .xproj 文件的备份）。 VS2015 及早期版本中不支持 .NET Core 项目的这种 .csproj 格式。  Visual Studio 2017 不支持 .xproj 格式，除非迁移到 .csproj 格式。 |
| ASP.NET Web 应用程序和启用了 Application Insights 的 ASP.NET Core Web 应用程序 | 对于每个 Visual Studio 用户，资源信息存储在每个用户实例的注册表中。 当用户未打开项目，但想要搜索 Azure Application Insights 数据时，可以使用此项。 Visual Studio 2015 使用与 Visual Studio 2017 不同的注册表位置，且未发生冲突。<br/><br/>用户创建 ASP.NET Web 应用程序或 ASP.NET Core Web 应用程序后，资源存储在 .suo 文件中。 用户可在 Visual Studio 2015 或 2017 中打开项目，只要 Visual Studio 支持这两个版本中使用的项目和解决方案，资源信息就可用于这两个版本。 用户需要在每个产品上进行一次身份验证。 例如，如果使用 Visual Studio 2015 创建项目，然后在 Visual Studio 2017 中打开，则用户需要在 Visual Studio 2017 上进行身份验证。 |
| C#/Visual Basic Web 窗体或 Windows 窗体 | 可以在 Visual Studio 2017 和 Visual Studio 2015 中打开项目。 |
| 数据库单元测试项目（.csproj、.vbproj）    | 较旧的数据单元测试项目将在 Visual Studio 2017 中加载，但将使用 GAC 版本的依赖关系。 若要升级单元测试项目以使用最新的依赖关系，请在“解决方案资源管理器”中右键单击该项目，然后选择“转换为 SQL Server 单元测试项目...”。 |
| F# | Visual Studio 2017 可以打开 Visual Studio 2013 和 2015 中创建的项目。 但是，若要在这些项目中启用 Visual Studio 2017 功能，请打开项目属性，将目标 fsharp.core 更改为 F# 4.1。 |
| LightSwitch | Visual Studio 2017 中不再支持 LightSwitch。 使用 Visual Studio 2012 及早期版本创建并在 Visual Studio 2013 或 Visual Studio 2015 中打开的项目将进行升级，之后只能在 Visual Studio 2013 或 Visual Studio 2015 中打开。 |
| Microsoft Azure Tools for Visual Studio | 若要打开这些类型的项目，请首先安装 [Azure SDK for .NET](http://azure.microsoft.com/en-us/downloads/)，然后打开该项目。 如有必要，请更新项目。 |
| 模型-视图-控制器框架 (ASP.NET MVC) | 对 MVC 版本和 Visual Studio 的支持：<ul><li>Visual Studio 2010 SP1 支持 MVC 2 和 MVC 3；通过[ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 下载](https://www.microsoft.com/en-us/download/details.aspx?id=30683)添加 MVC 4 支持</li><li>Visual Studio 2012 仅支持 MVC 3 和 MVC 4</li><li>Visual Studio 2013 仅支持 MVC 4 和 MVC 5</li><li>Visual Studio 2017 和 Visual Studio 2015 支持 MVC 4（可打开现有项目但无法创建新项目）和 MVC 5</li></ul><br/><br/>升级 MVC 版本：<ul><li>有关如何从 MVC 2 自动升级到 MCV 3 的信息，请参阅 [ASP.NET MVC 3 应用程序升级程序](http://go.microsoft.com/fwlink/?LinkID=238178)。</li><li>有关如何从 MVC 2 手动升级到 MVC 3 的信息，请参阅 [将 ASP.NET MVC 2 项目升级到 ASP.NET MVC 3 Tools 更新](http://go.microsoft.com/fwlink/?linkid=238178)。</li><li>有关如何从 MVC3 手动升级到 MVC 4 的信息，请参阅 [将 ASP.NET MVC 3 项目升级到 ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes)。 如果你的项目以 .NET Framework 3.5 SP1 为目标，则必须重定目标才能使用 .NET Framework 4。</li><li>有关如何从 MVC 4 手动升级到 MVC 5 的信息，请参阅 [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2)（如何将 ASP.NET MVC 4 和 API.NET 项目升级到 ASP.NET MVC 5 和 Web API 2）</li></ul> |
| 建模 | 如果允许 Visual Studio 自动更新项目，则可以在 Visual Studio 2015、Visual Studio 2013 或 Visual Studio 2012 中打开该项目。<br/><br/>Visual Studio 2015 和 Visual Studio 2017 之间未更改建模项目的格式，并且项目可以在任一版本中打开和修改。 但是，Visual Studio 2017 中的行为具有差异：<ul><li>建模项目现被称为菜单和模板中的“依赖关系验证”项目。</li><li>Visual Studio 2017 中不再支持 UML 关系图。 UML 文件照常在解决方案资源管理器中列出，但将以 XML 文件形式打开。 使用 Visual Studio 2015 查看、创建或编辑 UML 关系图。</li><li>在 Visual Studio 2017 中，生成建模项目时不再验证体系结构依赖关系。 但将在生成每个代码时进行验证。 此更改不会影响建模项目，但它需要对所验证的代码项目进行更改。 Visual Studio 2017 可以自动对代码项目执行必要的更改（[详细信息](http://go.microsoft.com/fwlink/?LinkId=827800)）。</li></ul> |
| Silverlight | Visual Studio 2017 不支持 Silverlight 项目。 若要继续使用 Silverlight 应用程序，请继续使用 Visual Studio 2015。 |
| Visual C++ | 你可以使用 Visual Studio 2017 打开在 Visual Studio 2015 中原样创建的解决方案和项目，但在较旧版本的 Visual Studio 中创建的项目可能需要升级项目或重定向到较新的工具集才能使用 Visual Studio 2017 生成。 有关详细信息，请参阅[如何：将 Visual C++ 项目升级到 Visual Studio 2015](https://msdn.microsoft.com/en-us/library/hh690665.aspx)和 [Visual C++ 移植和升级指南](https://msdn.microsoft.com/en-us/library/dn986839.aspx)。 |
| Visual Studio 扩展性/VSIX | 将更新 MinimumVersion 14.0 或更低版本中的项目以声明 MinimumVersion 15.0，这样可防止在早期版本的 Visual Studio 中打开该项目。 若要允许在早期版本中打开项目，请将 MinimumVersion 设置为 `$(VisualStudioVersion)`。 另请参阅[如何：将扩展性项目迁移到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。 |
| Visual Studio 实验室管理工具版 | 你可以使用 Microsoft 测试管理器或 Visual Studio 2010 SP1 及更高版本打开在以上任一版本中创建的环境。 但对于 Visual Studio 2010 SP1，在可以创建环境之前，Microsoft 测试管理器的版本必须与 Team Foundation Server 的版本匹配。 |
| Visual Studio Tools for Apache Cordova |可以在 Visual Studio 2017 中打开此项目，但此项目不具有向后兼容性。 从 Visual Studio 2015 中打开某个项目时，系统将提示允许修改项目。 这会将项目升级为使用工具集而非 `taco.json` 文件管理 Cordova 库、该库的平台和插件以及该库的节点/npm 依赖关系的版本控制。 有关详细信息，请参阅[迁移指南](http://taco.visualstudio.com/docs/vs-taco-2017-migration/)。 |
| Windows Communication Foundation, Windows Workflow Foundation | 可以在 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 中打开此项目 |
| Windows Presentation Foundation | 可以在 Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中打开此项目。 |
| Windows 应用商店/手机应用 | Visual Studio 2017 不支持 Windows Store 8.1 和 8.0 的项目，也不支持 Windows Phone 8.1 和 8.0 的项目。 若要继续使用这些应用，请继续使用 Visual Studio 2015。 若要继续使用 Windows Phone 7.x 项目，请使用 Visual Studio 2012。 |
