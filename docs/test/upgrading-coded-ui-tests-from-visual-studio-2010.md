---
title: "从 Visual Studio 2010 升级编码的 UI 测试 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 33
ms.author: douge
manager: douge
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
ms.openlocfilehash: e1bc50e4b6458103ee2443828f2a666d5f230d62
ms.lasthandoff: 03/03/2017

---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>从 Visual Studio 2010 升级编码的 UI 测试
在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 中创建的包含编码 UI 测试的测试项目在 Visual Studio 2012 中打开时会自动修复。 如果测试项目已签入源控件中，则会签出项目文件进行此修复。 修复后，这些包含编码 UI 测试的测试项目既可用于 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1，也可用于 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]。  
  
 **要求**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
>  Visual Studio 包括多个测试项目类型。 如果创建新的编码 UI 测试，将在编码 UI 测试项目类型中创建。 有关详细信息，请参阅[从 Visual Studio 的早期版本升级测试](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。  
  
> [!WARNING]
> 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 或与 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 并行安装的 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中打开包含编码 UI 测试的  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 测试项目时，必须重新生成该测试项目。  
  
> [!WARNING]
>  当在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中打开创建于 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 且仅包含单元测试的测试项目时，无法向其添加编码 UI 测试。 同样，也无法向创建于 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的单元测试项目添加编码 UI 测试。  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Visual Studio 2010 和 Visual Studio 2012 之间的兼容性问题  
 下表列出了在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之间迁移编码 UI 测试时应注意的问题。  
  
> [!CAUTION]
>  有一个关于编码 UI 测试项目中的引用在解决方案资源管理器中不显示的已知问题。 有关详细信息，请参阅 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 安装媒体上包含的自述文件。  
  
|编码 UI 功能|问题|解决方案|  
|----------------------------|-----------|--------------|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 不支持 Silverlight UI 测试|**生成将失败**<br /><br /> 如果你有 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 功能包 2，并且为 Silverlight 应用程序创建了编码 UI 测试项目，这些项目将无法在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中打开。|我们建议仅在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 功能包 2 中管理这些项目。|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 不支持 Firefox UI 测试|**生成将成功，但测试运行将失败**<br /><br /> 如果你有 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 功能包 2，并且为 Firefox 中的 Web 应用程序创建了编码 UI 测试项目，这些项目将无法在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中打开。|我们建议仅在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 功能包 2 中管理这些项目。|  
|已在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中添加新的 UI 代码测试 API|**生成将失败**<br /><br /> 如果使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中的新 UI 测试 API 创建编码 UI 测试，这些项目将无法在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中打开。|只能在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中管理使用新 API 的项目。|  
|在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中，已在 csproj 文件的“Choose”语句内添加引用。 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，我们将使用 Feedback targets 文件来包含编码 UI 测试程序集引用。|在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，无法向创建于 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]（或 SP1）且不包含编码 UI 测试的测试项目添加编码 UI 测试。<br /><br /> 修复过程将增加 targets 文件和 Choose 语句。 如果测试项目中没有编码 UI 测试，该项目将被标记为已修复，并且当在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中添加编码 UI 测试时，不会添加相应的引用。|必须使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 在同一解决方案中创建新的测试项目，并在其中添加新的编码 UI 测试。 或者，也可以将编码 UI 测试添加到 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 的测试项目中，并在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中打开该项目。|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a>Visual Studio 2010 SP1 更新  
 可从 [Microsoft 下载中心 ](http://www.microsoft.com/download/details.aspx?id=34677)下载为 Visual Studio 2012 和 Windows 8 提供兼容性支持的[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 更新，该更新也可用作 Visual Studio 更新。  
  
 应用更新以后，以下 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 编码 UI 测试工具功能将针对 Windows 8 有所改进：  
  
-   可以在运行 Windows 8 的计算机上为基于 Microsoft .NET Framework 4.5 的 Windows Presentation Foundation (WPF) 控件运行编码 UI 测试。  
  
-   可以在运行 Windows 8 的计算机上为 64 位 (x64) Internet Explorer 10 运行编码 UI 测试。  
  
 此更新还包含对以下问题的修复：  
  
-   **代码覆盖率：**无法在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 中打开由 Visual Studio 2012 创建的代码覆盖率文件 (.coverage)。  
  
-   **闲置测试项目：** 你的团队有一个分配给 Team Foundation Server (TFS) 2010 中的无效用户的测试项目。 例如，某位用户离开了公司，但仍有一个分配给他的测试用例。 你将 TFS 2010 升级到 TFS 2012。 并使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 连接到升级后的 TFS 服务器。 你无法使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 将测试项目分配给任何 TFS 用户。  
  
-   **负载测试：** 当在运行 Windows 8 的计算机上使用局域网 (LAN) 配置文件以外的网络类型运行负载测试时，网络模拟器驱动程序会导致操作系统崩溃。 有关详细信息，请参见 [知识库文章 2736182](http://support.microsoft.com/kb/2736182)。  
  
## <a name="see-also"></a>另请参阅  
 [移植、迁移和升级 Visual Studio 项目](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [从 Visual Studio 的早期版本升级测试](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [使用 UI 自动化来测试代码](../test/use-ui-automation-to-test-your-code.md)   
 [通过现有操作录制生成编码的 UI 测试](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [支持编码的 UI 测试和操作录制的配置和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

