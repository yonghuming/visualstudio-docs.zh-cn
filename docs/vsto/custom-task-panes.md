---
title: "自定义任务窗格"
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
  - "外接程序 [Visual Studio 中的 Office 开发], 自定义任务窗格"
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发], 自定义任务窗格"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发], 关于自定义任务窗格"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发], 创建"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发], 多个应用程序窗口"
  - "多个带有自定义任务窗格的应用程序窗口 [Visual Studio 中的 Office 开发]"
  - "Visual Studio 中的 Office 开发, 任务窗格"
  - "任务窗格 [Visual Studio 中的 Office 开发]"
  - "任务窗格 [Visual Studio 中的 Office 开发], 关于自定义任务窗格"
  - "任务窗格 [Visual Studio 中的 Office 开发], 创建"
  - "任务窗格 [Visual Studio 中的 Office 开发]。多个应用程序窗口"
  - "用户界面面板 [Visual Studio 中的 Office 开发]"
  - "用户界面 [Visual Studio 中的 Office 开发], 自定义任务窗格"
ms.assetid: 9a415109-5333-433e-95c6-3d59ce9c4d02
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 自定义任务窗格
  任务窗格是一个用户界面面板，通常停靠在 Microsoft Office 应用程序中某一窗口的一侧。  自定义任务窗格为你提供了一钟方法，使你可以创建自己的任务窗格并为用户提供熟悉的界面来访问你的解决方案的功能。  例如，界面中可以包含运行代码以修改文档或显示来自数据源的数据的控件。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  自定义任务窗格不同于操作窗格。  操作窗格是 Microsoft Office Word 和 Microsoft Office Excel 的文档级自定义项的一部分。  有关详细信息，请参阅[操作窗格概述](../vsto/actions-pane-overview.md)。  
  
## 自定义任务窗格的优点  
 使用自定义任务窗格，可以将各种功能集成到一个熟悉的用户界面中。  可以使用 Visual Studio 工具快速创建自定义任务窗格。  
  
### 熟悉的用户界面  
 Microsoft Office system 中应用程序的用户已经熟悉使用任务窗格，如 Word 中的**“样式和格式”**任务窗格。  自定义任务窗格的行为方式类似于 Microsoft Office system 中的其他任务窗格。  用户可以将自定义任务窗格停靠在应用程序窗口的不同侧，或者可以将自定义任务窗格拖动到窗口中的任何位置。  可以创建一个 VSTO 外接程序，使之同时显示多个自定义任务窗格，而且用户可以分别控制每个任务窗格。  
  
### Windows 窗体支持  
 使用 Visual Studio 中的 Office 开发工具创建的自定义任务窗格的用户界面基于 Windows 窗体控件。  可以使用熟悉的 Windows 窗体设计器来设计自定义任务窗格的用户界面。  还可以使用 Windows 窗体中的数据绑定支持将数据源绑定到任务窗格中的控件。  
  
## 创建自定义任务窗格  
 可以利用下面两个步骤创建基本的自定义任务窗格：  
  
1.  通过将 Windows 窗体控件添加到 <xref:System.Windows.Forms.UserControl> 对象来创建自定义任务窗格的用户界面。  
  
2.  通过将用户控件传递到 VSTO 外接程序中的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> 对象来实例化自定义任务窗格。  此集合返回一个新的 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象，可用于修改任务窗格的外观并响应用户事件。  
  
 有关详细信息，请参阅[如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
### 创建用户界面  
 使用 Visual Studio 中的 Office 开发工具创建的所有自定义任务窗格均包含一个 <xref:System.Windows.Forms.UserControl> 对象。  此用户控件提供自定义任务窗格的用户界面。  可以在设计时或运行时创建用户控件。  如果在设计时创建用户控件，则可使用 Windows 窗体设计器来构造任务窗格的用户界面。  
  
### 实例化自定义任务窗格  
 创建包含自定义任务窗格用户界面的用户控件之后，必须实例化 <xref:Microsoft.Office.Tools.CustomTaskPane>。  若要执行此操作，请通过调用其中一种 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法来传递 VSTO 外接程序中的用户控件 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection>。  此集合公开为 `ThisAddIn` 类的 `CustomTaskPanes` 字段。  下面的代码示例应从 `ThisAddIn` 类中运行。  
  
 [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法返回一个新的 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象。  可使用此对象修改任务窗格的外观并响应用户事件。  
  
### 在多个窗口中控制任务窗格  
 自定义任务窗格与文档框架窗口关联，该窗口向用户呈现文档或项的视图。  仅当关联的窗口可见时，任务窗格才可见。  
  
 若要确定显示自定义任务窗格的窗口，请在创建任务窗格时使用相应的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法重载：  
  
-   若要将任务窗格与活动窗口关联，请使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法。  
  
-   若要将任务窗格与指定窗口托管的文档关联，请使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法。  
  
 在多个窗口处于打开状态的情况下，某些 Office 应用程序需要显式指令来确定何时创建或显示任务窗格。  因此，务必要考虑在代码中的何处实例化自定义任务窗格，以确保任务窗格与应用程序中的相应文档或项一起出现。  有关详细信息，请参阅[在应用程序窗口中管理自定义任务窗格](#Managing)。  
  
## 从任务窗格中访问应用程序  
 如果想要通过用户控件实现应用程序的自动化，则可以通过在代码中使用 `Globals.ThisAddIn.Application` 来直接访问对象模型。  静态 `Globals` 类提供对 `ThisAddIn` 对象的访问权限。  此对象的 `Application` 字段是进入应用程序对象模型的入口点。  
  
 有关 `ThisAddIn` 对象的 `Application` 字段的详细信息，请参阅[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  有关演示如何从自定义任务窗格中实现应用程序自动化的演练，请参阅[演练：从自定义任务窗格自动化应用程序](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)。  有关 `Globals` 类的详细信息，请参阅[对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)。  
  
## 管理任务窗格的用户界面  
 创建任务窗格之后，可以使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象的属性和事件来控制任务窗格的用户界面，并在用户更改任务窗格时进行响应。  
  
### 使自定义任务窗格可见  
 默认情况下，任务窗格不可见。  若要使任务窗格可见，则必须将 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> 属性设置为 **true**。  
  
 用户可以通过单击任务窗格一角的**“关闭”**按钮 \(X\) 随时关闭任务窗格。  但是，没有可供用户再次打开自定义任务窗格的默认方法。  如果用户关闭了自定义任务窗格，那么用户无法再次查看该自定义任务窗格，除非提供一种显示窗格的方法。  
  
 如果在 VSTO 外接程序中创建了自定义任务窗格，则还应创建一个可供用户单击来显示或隐藏该自定义任务窗格的 UI 元素，如按钮。  如果在支持自定义功能区的 Microsoft Office 应用程序中创建了自定义任务窗格，则可以向功能区中添加一个控件组，其中包含用于显示或隐藏自定义任务窗格的按钮。  有关演示如何执行此操作的演练，请参阅[演练：将自定义任务窗格与功能区按钮同步](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)。  
  
 如果在不支持自定义功能区的 Microsoft Office 应用程序中创建了自定义任务窗格，则可以添加一个显示或隐藏自定义任务窗格的 <xref:Microsoft.Office.Core.CommandBarButton>。  
  
### 修改任务窗格的外观  
 可以使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象的属性控制自定义任务窗格的大小和位置。  可以使用自定义任务窗格中包含的 <xref:System.Windows.Forms.UserControl> 对象的属性对自定义任务窗格的外观做出许多其他更改。  例如，可以使用用户控件的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 属性指定自定义任务窗格的背景图像。  
  
 下表列出了使用 <xref:Microsoft.Office.Tools.CustomTaskPane> 属性可以对自定义任务窗格做出的更改。  
  
|任务|属性|  
|--------|--------|  
|更改任务窗格的大小|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|更改任务窗格的位置|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|隐藏任务窗格或使其可见|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|阻止用户更改任务窗格的位置|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### 对自定义任务窗格事件进行编程  
 你可能希望 VSTO 外接程序在用户修改自定义任务窗格时进行响应。  例如，如果用户将窗格方向从垂直更改为水平，你可能希望重新定位控件。  
  
 下表列出可以对其进行处理以响应用户对自定义任务窗格所做更改的事件。  
  
|任务|Event|  
|--------|-----------|  
|当用户更改任务窗格的位置时进行响应。|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|当用户隐藏任务窗格或使其可见时进行响应。|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## 清理任务窗格使用的资源  
 创建自定义任务窗格之后，只要 VSTO 外接程序在运行，<xref:Microsoft.Office.Tools.CustomTaskPane> 对象就会保留在内存中。  即使当用户单击任务窗格一角的**“关闭”**按钮 \(X\) 后，对象仍保留在内存中。  
  
 若要在 VSTO 外接程序仍在运行时清理任务窗格使用的资源，请使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 或 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 方法。  这些方法从 `CustomTaskPanes` 集合中删除指定的 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象，并调用该对象的 <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> 方法。  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 会在卸载 VSTO 外接程序时自动清理自定义任务窗格使用的资源。  请不要在项目的 `ThisAddIn_Shutdown` 事件处理程序中调用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 或 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> 方法。  这些方法将引发 <xref:System.ObjectDisposedException>，因为 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 会在调用 `ThisAddIn_Shutdown` 之前清理 <xref:Microsoft.Office.Tools.CustomTaskPane> 对象使用的资源。  有关 `ThisAddIn_Shutdown` 的详细信息，请参阅 [Office 项目中的事件](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> 在多个应用程序窗口中管理自定义任务窗格  
 在使用多个窗口显示文档和其他项的应用程序中创建自定义任务窗格时，你需要进行额外的步骤来确保在用户希望显示任务窗格时任务窗格是可见的。  
  
 所有应用程序中的自定义任务窗格都与文档框架窗口关联，该窗口向用户呈现文档或项的视图。  仅当关联的窗口可见时，任务窗格才可见。  但是，并非所有应用程序都以相同的方式使用文档框架窗口。  
  
 下列应用程序组具有不同的开发要求：  
  
-   [Outlook](#Outlook)  
  
-   [Word、InfoPath 和 PowerPoint](#WordAndInfoPath)  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 有关相关的视频演示，请参阅[如何实现：在 Word VSTO 外接程序中管理任务窗格？](http://go.microsoft.com/fwlink/?LinkId=136781)。  
  
##  <a name="Outlook"></a> Outlook  
 为 Outlook 创建自定义任务窗格时，自定义任务窗格与特定资源管理器或检查器窗口关联。  资源管理器是用于显示文件夹内容的窗口，检查器是用于显示诸如电子邮件或任务等项的窗口。  
  
 如果希望为多个资源管理器或检查器窗口显示自定义任务窗格，则需要在资源管理器或检查器窗口打开时创建自定义任务窗格的新实例。  为此，请处理在创建资源管理器或检查器窗口时引发的事件，然后在事件处理程序中创建任务窗格。  还可以处理资源管理器和检查器事件以隐藏或显示任务窗格，具体情况视哪个窗口处于可见状态而定。  
  
 若要将任务窗格与特定的资源管理器或检查器关联，请使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法创建任务窗格，并将 <xref:Microsoft.Office.Interop.Outlook.Explorer> 或 <xref:Microsoft.Office.Interop.Outlook.Inspector> 对象传递给 *window* 参数。  有关创建自定义任务窗格的详细信息，请参阅[自定义任务窗格概述](../vsto/custom-task-panes.md)。  
  
 有关演示如何为每个打开的电子邮件消息创建任务窗格的演练，请参阅[演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
### Outlook 事件  
 若要监视资源管理器窗口的状态，你可以处理以下与资源管理器相关的事件：  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 若要监视检查器窗口的状态，你可以处理以下与检查器相关的事件：  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### 禁止在 Outlook 中显示自定义任务窗格的多个实例  
 若要禁止 Outlook 窗口显示自定义任务窗格的多个实例，应在关闭每个窗口时从 `ThisAddIn` 类的 `CustomTaskPanes` 集合中显示删除自定义任务窗格。  调用关闭窗口时引发的事件中的 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> 方法，例如 <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> 或 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>。  
  
 如果不显式删除自定义任务窗格，Outlook 窗口可能会显示该自定义任务窗格的多个实例。  Outlook 有时会回收窗口，并且回收的窗口会保留对曾附加到这些窗口的任何自定义任务窗格的引用。  
  
##  <a name="WordAndInfoPath"></a> Word、InfoPath 和 PowerPoint  
 Word、InfoPath、和 PowerPoint 会在不同的文档框架窗口中显示每个文档。  为这些应用程序创建自定义任务窗格时，自定义任务窗格只与特定文档关联。  如果用户打开其他文档，自定义任务窗格将会隐藏，直到之前的文档再次处于可见状态。  
  
 若要为多个文档显示自定义任务窗格，请在用户创建新文档或打开现有文档时创建该自定义任务窗格的新实例。  为此，请处理在创建或打开文档时引发的事件，然后在事件处理程序中创建任务窗格。  还可以处理文档事件以隐藏或显示任务窗格，具体情况视哪个文档处于可见状态而定。  
  
 若要将任务窗格与特定的文档窗口关联，请使用 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> 方法创建任务窗格，并将 <xref:Microsoft.Office.Interop.Word.Window>（对于 Word）、<xref:Microsoft.Office.Interop.InfoPath.WindowObject>（对于 InfoPath）或 <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow>（对于 PowerPoint）传递给 *window* 参数。  
  
### Word 事件  
 若要监视 Word 中文档窗口的状态，你可以处理以下事件：  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### InfoPath 事件  
 若要监视 InfoPath 中文档窗口的状态，你可以处理以下事件：  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### PowerPoint 事件  
 若要监视 PowerPoint 中文档窗口的状态，你可以处理以下事件：  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## 请参阅  
 [如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [演练：从自定义任务窗格自动化应用程序](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [演练：将自定义任务窗格与功能区按钮同步](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  