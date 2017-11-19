---
title: "限制的 Windows 窗体 Office 文档上的控件 |Microsoft 文档"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f8842bd80832211f02532ca706416416325663b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitations of Windows Forms Controls on Office Documents
  有一些 Windows 窗体控件添加到 Microsoft Office Word 文档或 Microsoft Office Excel 工作表和添加到 Windows 窗体的 Windows 窗体控件之间的差异。 例如，添加<xref:Microsoft.Office.Tools.Word.Controls.Button>控件到文档中，属性如<xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>， <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>，和<xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A>不会按你所料方式。  
  
 其中许多差异是由引起顺便说一下控件位于该 Windows 窗体上的文档。 Windows 窗体控件添加到文档时[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]嵌入 ActiveX 控件然后承载 Windows 窗体控件在文档中的。 直接在文档中未嵌入 Windows 窗体控件。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows 窗体控件的方法和属性的限制  
 有多种方法和不起作用相同的方式在文档上以及就象在 Windows 窗体上，因此，建议，因此它们无法使用 Windows 窗体控件的属性。 例如，如设置属性`Dock`和`Anchor`仅影响将控件与容器 ActiveX 控件，而不是文档的位置。 下面是不支持的方法和 Word 和 Excel 的 Windows 窗体控件的属性的列表：  
  
-   不支持的方法和 Excel 控件的属性：  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   不支持的方法和 Word 控件的属性：  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 你还不能设置`Left`或`Top`与在 Word 文档上的文本对齐的 Windows 窗体控件的属性。 Windows 窗体控件与在以下情况下的文本对齐添加：  
  
-   可以以编程方式向 Word 文档添加控件，并使用指定位置的范围的方法。  
  
-   在设计时向 Word 文档添加 Windows 窗体控件。 可以通过修改设计器中的控件来更改这种情况。  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office 文档上的 Windows 窗体控件中的差异  
 Windows 窗体控件通常具有相同的行为在 Office 文档上作为它们在 Windows 窗体上执行操作，但也存在一些差异。 下表介绍 Office 文档上的 Windows 窗体控件中存在的差异。  
  
|功能|差异|  
|-------------------|----------------|  
|控件的 tab 键次序|你无法通过放置在 Excel 工作表或 Word 文档上的控件选项卡。|  
|控件分组|不能使用<xref:System.Windows.Forms.GroupBox>控件，以包含 Office 文档上的其他控件。 当您直接向文档添加多个单选按钮时，单选按钮不互相排斥。 你可以编写代码以使单选按钮互斥;但是，首选的方法是向用户控件添加单选按钮，然后将用户控件添加到文档。 有关详细信息，请参阅的 Word 控件示例或 Excel 控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。|  
|控件类型|提供的类中包装 Windows 窗体控件在文档上使用[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，使控件其他功能特定的 Excel 工作表或 Word 文档。 例如，如果你有`Button`控制 Excel 工作表，请务必将类型指定为<xref:Microsoft.Office.Tools.Excel.Controls.Button>而非<xref:System.Windows.Forms.Button>引用或该对象强制转换时。|  
|控件位置和大小|由属于容器 ActiveX 控件的属性确定的大小和位置的控件。 ActiveX 控件属性需要值与 Windows 窗体控件的等效属性不同。 当你将设置`Top`， `Left`， `Height`，或`Width`控件的属性，它用来衡量中点，而不是像素。|  
|在 Word 文档上的控件位置|如果将控件添加到基于流的布局，请记住，控件会一同流动的内容的内容发生更改。 你不能将控件锚定到段落时将其从**工具箱**因为到与文本对齐的 Word 文档添加控件。 如果你使用另一种方法添加控件，如双击该控件，控件将插入根据您已为插入图片设置单词选项。<br /><br /> 无法设置`Left`或`Top`与文本对齐的控件的属性。<br /><br /> 无法将控件放在页眉或页脚，或在子文档。|  
|控件事件|选择控件时，它会引发事件按下列顺序：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 当取消选择控件时，它会引发事件按下列顺序：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|缩放控件|在将文档的缩放设置更改为 100%以外的任何内容，控件将被禁用，虽然它们会对显示缩放的文档。 例如，如果你单击按钮时您的文档位于 130%缩放时，它将显示一条消息控件已被禁用，直到缩放设置为 100%。 将缩放级别更改为 100%时，控件将正常工作。|  
|控件属性值|尽管 Windows 窗体上控件的属性设置为一个整数值，它们将设置为单个 Word 文档上的控件。 在 Excel 中，控件的属性值设置为双精度值。 如果`Height`和`Width`的工作表上的控件的属性超过了工作表或屏幕的大小，则该值被截断。|  
|控件的大小调整|如果你调整文档使用其中一个八个大小调整控点上的控件，新的控件维度不会反映在**属性**窗口，直到重新控件。|  
|控件行为|当拆分工作表窗口时，Excel 工作表上的控件可能会发生不可预测行为。 例如，访问<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>工作表上可能仅能在一个窗口中。|  
|控件命名|不能使用保留的字来命名控件。 例如，如果你添加<xref:Microsoft.Office.Tools.Excel.Controls.Button>到工作表和名称更改为**系统**，生成项目时，会发生错误。|  
|以编程方式添加控件|不使用控件的构造函数以在运行时向文档添加控件。 相反，使用提供的帮助器方法[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，使用<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>方法将一个按钮添加到工作表。 如果你想要添加这些帮助器方法不支持的控件，你可以使用 AddControl 方法。 有关更多信息，请参见 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。|  
|复制控件|如果你复制的 Windows 窗体控件和在运行时将其粘贴到文档，一个空容器 ActiveX 控件将粘贴到文档。 在新位置中，不显示 Windows 窗体控件中，位于该原始控件背后的代码不会复制到容器 ActiveX 控件。|  
  
## <a name="limitations-in-document-level-projects"></a>文档级项目中的限制  
 使用文档上的 Windows 窗体控件的一些限制是唯一的文档级别项目。  
  
### <a name="control-support-at-design-time"></a>在设计时控制支持  
 某些 Windows 窗体控件会从**工具箱**的 Excel 工作表或 Word 文档时在 Visual Studio 设计器中打开。 这是技术方面的限制或因为功能已在 Word 或 Excel 内可用。 Excel 和 Word 项目支持的 Windows 窗体控件和其他组件中显示所有**工具箱**当文档具有焦点，而且还可以向工作表或文档添加第三方控件。  
  
> [!NOTE]  
>  所有控件都会从**工具箱**当受保护文档。 文档保护有关的信息，请参阅[在文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)。  
  
> [!NOTE]  
>  第三方控件必须具有<xref:System.Runtime.InteropServices.ComVisibleAttribute>属性设置为**true**才可以使用 Office 解决方案中。  
  
 下面的控件和组件将不可用在**工具箱**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>对旧 ActiveX 控件的支持  
 如果创建使用现有的 Word 文档或包含 ActiveX 控件的 Excel 工作簿的文档级 Office 项目时，ActiveX 控件的功能不会丢失;但是，没有任何支持将新的 ActiveX 控件添加到你从 Visual Studio 中的文档。 例如，如果您的 Word 文档都有一个按钮从**控件**工具箱中运行的 Visual Basic for Applications (VBA) 宏，它将继续运行宏后已在 Office 项目使用的文档。 但是，建议你删除 ActiveX 控件和 VBA 宏并将其替换为 Windows 窗体控件和托管代码。  
  
## <a name="see-also"></a>另请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Windows 窗体上的控件 Office 文档概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：将 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  