---
title: "调试 Office 项目 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 110d6231da40ab59c3979b97441b3ac0ad458b3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-office-projects"></a>调试 Office 项目
  可使用与用于其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目相同的 Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工具来调试 Office 项目。 调试 Office 项目时也可使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试器的功能（如插入断点和查看 **“局部变量”** 窗口中的变量）。 有关 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 调试工具的详细信息，请参阅 [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)。  
  
> [!TIP]  
>  若要简化调试，需在创建和调试应用程序前先关闭所有打开的 Office 应用程序实例。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
## <a name="starting-and-stopping-the-debugger"></a>启动和停止调试器  
 可像开始调试其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目一样开始调试 Office 项目；例如，可以按 F5 键。 当开始调试 VSTO 外接程序项目时，将启动目标 Office 应用程序的新进程并加载 VSTO 外接程序。  
  
 当开始调试文档级项目时，文档或工作簿将在新的 Word 或 Excel 进程中打开。  
  
 当停止调试器时，调试器会突然终止应用程序进程或分离（如果将调试器设置为分离）。 在已终止的 Office 应用程序进程中打开的所有其他文档也将关闭而不发出警告，并且任何未保存的更改都将丢失。 这可能包括调试器运行时打开的所有文档或工作簿。  
  
 通常情况下，最好在停止调试器前从进程中分离，这样可以正常方式退出 Office 应用程序。 如果停止调试器后仍想使用打开的文档或工作表，还可先从进程中分离。  
  
 如果在调试 Word 的文档级自定义项时，反复停止调试器并引起 Word 突然关闭可能会导致损坏 Normal 模板。 如果发生这种情况，可以删除已损坏的 Normal 模板，该模板将在下次打开 Word 时自动重新创建。 但是，不会重新创建任何存储在 Normal 模板中的宏。  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>使用 Office 2013 或 Office 2016 调试 Office 2013 VSTO 外接程序  
 如果你在使用 Visual Studio 2015，并且必须安装 Office 并行这两个版本，Visual Studio 将启动 Office 2016。 如果你正在使用 Visual Studio 2013，Visual Studio 将启动 Office 2013。  
  
 如果想要使用不同的 Office 版本（2013 或 2016）调试 VSTO 外接程序，打开 **“项目设计器”**，然后在 **“调试”** 选项卡上选择 **“启动外部程序”** 选项按钮。 然后，浏览到相应的 Office 应用程序可执行文件的位置。  
  
## <a name="f10-and-f11-behavior"></a>F10 和 F11 行为  
 当开始调试 Office 项目时，F10 和 F11 的行为与开始调试其他 Visual Basic 或 C# 的项目时的行为不同。 在 Visual Basic 或 C# 项目中，调试器将在主函数中停止；在 Office 项目中，Visual Studio 无法控制 Office 应用程序的主函数。 但在调试期间，F10 和 F11 确实具有 Visual Basic 和 C# 项目中的相同函数。  
  
## <a name="displaying-exceptions"></a>显示异常  
 由于托管代码与非托管代码进行交互的方式，Visual Studio 不会显示 Microsoft Office 应用程序引发的错误。 例如，如果通过使用 Visual Studio 中的 Office 开发工具创建的 VSTO 外接程序引发了异常，Microsoft Office 应用程序将继续运行而不显示错误。 若要查看这些错误，将调试器设置为发生公共语言运行时异常时中断。 有关详细信息，请参阅[管理调试器的异常](/visualstudio/debugger/managing-exceptions-with-the-debugger)。  
  
 如果将调试器设置为发生公共语言运行时异常时中断，则所有异常都将中断调试器，包括已处理的异常和一些源自运行时本身的最有可能的异常，而这些可能与项目无关。 未找出的有关 msosec 的错误将显示在每个项目中，但可以放心地忽略。 这些 msosec 异常不会影响解决方案。  
  
 还可在方法周围使用 **Try...Catch** 语句来捕获异常。  
  
 默认情况下，Visual Studio 也不会显示 Office 项目的实时调试错误；但可以启用此功能，这样可看到所引发的错误。 有关详细信息，请参阅[实时调试 Visual Studio 中](/visualstudio/debugger/just-in-time-debugging-in-visual-studio)。  
  
## <a name="command-line-arguments"></a>命令行参数  
 如果将 **“调试”** 属性页上的 **“启动操作”** 设置为 **“启动项目”**，则即使已将命令行参数指定为启动选项，Visual Studio 也不会在调试项目时使用命令行参数。 如果想要在开始调试时使用命令行参数，则除了选择 **“启动项目”** 外，还必须选择 **“启动操作”**。  
  
## <a name="source-control"></a>源代码管理  
 调试属性不在源控件下的多个用户中共享。 Visual Basic 和 C# 项目的调试属性存储在特定于用户的文件（*ProjectName*.vbproj.user 或 *ProjectName*.csproj.user）中，但此文件不在源控件下。 如果有多个用户正在调试，则每个用户都必须手动输入调试属性。  
  
## <a name="debugging-cached-datasets-in-a-document-level-project"></a>在文档级项目中调试缓存的数据集  
 每次生成项目时，会清空并重新创建数据集。 如果想要调试缓存的数据集，则必须在 Visual Studio 外部打开文档，然后附加调试器。  
  
## <a name="debugging-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>调试基于 Word 97-2003 文档 (*.doc) 格式的 Word 文档项目  
 若要调试基于 Word 97-2003 文档 (*.doc) 格式的 Word 文档项目，必须将项目文件夹添加到受信任的文件夹列表。 有关如何执行该操作的更多信息，请参阅 [Granting Trust to Documents](../vsto/granting-trust-to-documents.md)。  
  
## <a name="debugging-disabled-add-ins"></a>调试禁用的外接程序  
 Microsoft Office 应用程序可禁用行为异常的 VSTO 外接程序。 Microsoft Office 应用程序禁用 VSTO 外接程序以防止每次启动应用程序时加载有问题的代码。 但是，这也容易在典型的调试过程中导致意外行为。 有关如何重新启用 VSTO 外接程序的信息，请参阅[如何： 重新启用 VSTO 外接程序中，已禁用](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)。  
  
 以下是 Microsoft Office 应用程序使用的两种禁用 VSTO 外接程序的类型：硬禁用和软禁用。  
  
### <a name="hard-disabling"></a>硬禁用  
 当 VSTO 外接程序导致应用程序意外关闭时，可能发生硬禁用。 如果 VSTO 外接程序中的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序正在执行时停止了调试器，则硬禁用也可能发生在开发计算机上。 当硬禁用 VSTO 外接程序时，它将显示在应用程序中的 **“禁用项”** 列表中。  
  
 如果 Office 应用程序硬禁用了通过使用 Visual Studio 中的 Office 开发工具创建的 VSTO 外接程序，则应用程序仅禁用导致故障发生的 VSTO 外接程序。 通过使用 Visual Studio 中的 Office 开发工具为该 Office 应用程序创建的其他 VSTO 外接程序将继续进行加载。  
  
### <a name="soft-disabling"></a>软禁用  
 当 VSTO 外接程序产生不会导致应用程序意外关闭的错误时，可能会发生软禁用。 例如，如果 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序正在执行时，某个应用程序引发了未处理异常，则此应用程序可能软禁用 VSTO 外接程序。 当软禁用 VSTO 外接程序时，它将显示在应用程序中的 **“非活动应用程序外接程序”** 列表中，并且应用程序将更改 VSTO 外接程序的 **LoadBehavior** 注册表项值，从而指示已卸载应用程序。 有关详细信息**LoadBehavior**注册表项，请参阅[VSTO 外接程序的注册表项](../vsto/registry-entries-for-vsto-add-ins.md)。  
  
## <a name="troubleshooting-installation-errors-by-using-the-event-viewer"></a>使用事件查看器进行安装错误疑难解答  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 将安装或卸载 Office 解决方案时引发的所有异常消息都写入到了 Windows 中的事件查看器中。 你可使用这些消息来解决安装和部署问题。  
  
## <a name="troubleshooting-startup-errors-by-using-a-log-file-and-error-messages"></a>使用日志文件和错误消息进行启动错误疑难解答  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可将启动过程中发生的所有错误写入日志文件，或在消息框中显示每个错误。 默认情况下，这些选项是关闭的。 可通过创建环境变量来启用这些选项。  
  
 若要在消息框中显示每个错误，可创建一个名为 `VSTO_SUPPRESSDISPLAYALERTS` 的环境变量并将其设置为 0（零）。 可通过删除环境变量或将其设置为 1（一）来取消消息。  
  
 若要将错误写入日志文件，可创建一个名为 `VSTO_LOGALERTS` 的环境变量并将其设置为 1（一）。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可在包含 VSTO 外接程序的部署清单的文件夹中或在包含与自定义项关联的文档或工作簿的文件夹中创建日志文件。 如果失败， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 将在本地的 %TEMP% 文件夹中创建日志文件。 对于应用程序级 VSTO 外接程序，默认名称为 *add-in name*.vsto.log。 对于文档级项目，日志文件的名称为 *document name*.*extension*.log（如 ExcelWorkbook1.xlsx.log）。 若要停止记录错误，可删除环境变量，或将其设置为 0（零）。  
  
## <a name="see-also"></a>另请参阅  
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [如何： 重新启用 VSTO 外接程序，已禁用](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  