---
title: "Office 文档上的 Windows 窗体控件的限制"
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
  - "ActiveX 控件 [Visual Studio 中的 Office 开发]"
  - "控件 [Visual Studio 中的 Office 开发], Windows 窗体控件"
  - "Office 文档 [Visual Studio 中的 Office 开发, Windows 窗体控件"
  - "工具箱 [Visual Studio 中的 Office 开发], 不受支持的控件"
  - "用户控件 [Visual Studio 中的 Office 开发], 将控件分组"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], 旧式 ActiveX"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], 限制"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], 工具箱"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], 不受支持的属性和方法"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Office 文档上的 Windows 窗体控件的限制
  添加到 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿中的 Windows 窗体控件与添加到 Windows 窗体中的 Windows 窗体控件之间存在一些差异。  例如，将 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件添加到文档中后，<xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>、<xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> 和 <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> 等属性不能按预期的方式工作。  
  
 其中大部分差异是由在文档上承载 Windows 窗体控件的方式引起的。  将某个 Windows 窗体控件添加到文档中后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会嵌入一个 ActiveX 控件，该控件会在文档中承载这个 Windows 窗体控件。  Windows 窗体控件没有直接嵌入到文档中。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Windows 窗体控件的方法与属性的一些限制  
 Windows 窗体控件有很多方法和属性，它们在文档中的工作方式与它们在 Windows 窗体上的工作方式不同，因此，建议不要使用这些控件。  例如，设置 `Dock` 和 `Anchor` 等属性只会影响控件相对于容器 ActiveX 控件的位置，而不会影响控件在文档上的位置。  下面是对于 Word 和 Excel 来说不受支持的 Windows 窗体控件方法和属性的列表：  
  
-   不受支持的 Excel 控件方法和属性：  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   不受支持的 Word 控件方法和属性：  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 在 Word 文档上，您还不能设置与文本对齐的 Windows 窗体控件的 `Left` 或 `Top` 属性。  在下列情况下，将按照与文本对齐的方式添加 Windows 窗体控件：  
  
-   以编程方式将控件添加到 Word 文档中，并使用某个方法指定控件位置的范围。  
  
-   在设计时将 Windows 窗体控件添加到 Word 文档中。  您可以通过在设计器中修改该控件来更改此设置。  
  
## Office 文档上的 Windows 窗体控件的差异  
 通常，Windows 窗体控件在 Office 文档上的行为与它们在 Windows 窗体上的行为相同，但是也存在一些差异。  下表描述了 Office 文档上的 Windows 窗体控件存在的差异。  
  
|功能|差异|  
|--------|--------|  
|控件 Tab 顺序|无法在放置于 Excel 工作表或 Word 文档上的控件之间按 Tab 跳位。|  
|控件分组|在 Office 文档中，无法使用 <xref:System.Windows.Forms.GroupBox> 控件包含其他控件。  如果直接将多个单选按钮添加到文档中，这些单选按钮并不是互相排斥的。  您可以编写代码使单选按钮互相排斥；但是，首选方法是将单选按钮添加到一个用户控件，然后将此用户控件添加到文档。  有关更多信息，请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Word 控件示例或 Excel 控件示例。|  
|控件类型|文档上使用的 Windows 窗体控件包装在 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的一个类中，该类向控件提供特定于 Excel 工作表或 Word 文档的附加功能。  例如，如果 Excel 工作表上有一个 `Button` 控件，请确保在引用或强制转换对象时将该控件的类型指定为 <xref:Microsoft.Office.Tools.Excel.Controls.Button>，而不是 <xref:System.Windows.Forms.Button>。|  
|控件位置和大小|控件的大小和位置由隶属于容器 ActiveX 控件的属性决定。  ActiveX 控件的属性采用的值与 Windows 窗体控件的等效属性所采用的值不同。  设置控件的 `Top`、`Left`、`Height` 或 `Width` 属性时，使用的单位是点而不是像素。|  
|Word 文档上的控件位置|请记住，如果将控件添加到基于流的版面中，文档内容变化时控件会随内容一同流动。  从**“工具箱”**中拖动控件时，不能将控件锚定在某个段落中，这是因为控件是以与文本对齐的方式添加到 Word 文档中的。  如果使用双击控件等其他方法添加控件，控件会根据针对插入图片设置的 Word 选项插入。<br /><br /> 您不能设置与文本对齐的控件的 `Left` 或 `Top` 属性。<br /><br /> 不能将控件放置在页眉、页脚或子文档中。|  
|控件事件|选择控件后，它会按下面的顺序引发事件：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 取消选择控件后，它会按下面的顺序引发事件：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|控件缩放|将文档的缩放设置更改为 100% 之外的任何其他值时，尽管控件显示为与文档一起缩放，但控件会被禁用。  例如，如果在文档的缩放比例为 130% 时单击某个按钮，会显示一条消息，说明该控件在文档设置为 100% 之前将一直被禁用。  将缩放比例更改回 100% 时，控件又将正常工作。|  
|控件的属性值|尽管在 Windows 窗体上控件的属性被设置为整数值，但是在 Word 文档上，控件的属性被设置为 Single。  在 Excel 中，控件的属性值被设置为 Double。  如果工作表上的控件的 `Height` 和 `Width` 属性超出工作表或屏幕的大小，该值会被截断。|  
|调整控件的大小|如果使用八个大小调节控制点之一调整文档上的控件的大小，在重新选定该控件之前，新的控件尺寸不会在**“属性”**窗口中反映出来。|  
|控件行为|拆分工作表窗口时，Excel 工作表中的控件的行为可能会无法预测。  例如，可能只能在其中一个窗口访问工作表上的 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>。|  
|控件命名|不能使用保留字命名控件。  例如，如果向工作表添加一个 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控件并将控件名称更改为**“System”**，生成项目时就会发生错误。|  
|以编程方式添加控件|请勿使用控件的构造函数在运行时向文档中添加控件。  请改用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的帮助器方法。  例如，可以使用 <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> 方法向工作表添加一个按钮。  如果要添加不受这些帮助器方法支持的控件，可以使用 AddControl 方法。  有关更多信息，请参见[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。|  
|复制控件|如果在运行时复制一个 Windows 窗体控件并将该控件粘贴到文档中，则会向文档中粘贴一个空的容器 ActiveX 控件。  Windows 窗体控件不会出现在新位置，并且原控件的后台代码不会复制到容器 ActiveX 控件中。|  
  
## 文档级项目的限制  
 在文档上使用 Windows 窗体控件的一些限制是针对于文档级项目的。  
  
### 在设计时支持的控件  
 在 Visual Studio 设计器中打开 Excel 工作表或 Word 文档时，某些 Windows 窗体控件会从**“工具箱”**中移除。  这是由于技术方面的限制或者 Word 或 Excel 中已提供相应功能引起的。  Excel 和 Word 项目支持当文档具有焦点时在**“工具箱”**中显示的所有 Windows 窗体控件及其他组件，并且您还可以将第三方控件添加到工作表或文档中。  
  
> [!NOTE]  
>  当文档受保护时，所有控件都会从**“工具箱”**中移除。  有关文档保护的信息，请参见[文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)。  
  
> [!NOTE]  
>  第三方控件的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 特性必须设置为 **true** 才能用于 Office 解决方案。  
  
 **“工具箱”**中没有以下控件和组件：  
  
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
  
### 支持旧版 ActiveX 控件  
 如果您创建的文档级 Office 项目所用的现有 Word 文档或 Excel 工作簿包含 ActiveX 控件，则不会丢失 ActiveX 控件的功能；不过，不支持从 Visual Studio 向文档中添加新的 ActiveX 控件。  例如，如果 Word 文档中来自**“控件”**工具箱的某个按钮运行 Visual Basic for Applications \(VBA\) 宏，则在 Office 项目中使用该文档后，这个按钮将继续运行此宏。  但是，建议您移除 ActiveX 控件和 VBA 宏，将其替换为 Windows 窗体控件和托管代码。  
  
## 请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：为 Office 文档添加 Windows 窗体控件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  