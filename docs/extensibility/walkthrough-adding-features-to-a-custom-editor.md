---
title: "演练 ︰ 将功能添加到自定义编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的添加功能"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# 演练 ︰ 将功能添加到自定义编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建自定义编辑器后，您可以向其添加更多的功能。  
  
### 若要创建 VSPackage 编辑器  
  
1.  通过使用 Visual Studio Package 项目模板创建的自定义编辑器。  
  
     有关详细信息，请参阅[演练: 创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
2.  决定您的编辑器以支持单个视图或多个视图。  
  
     支持的编辑器 **新窗口** 命令时，或具有窗体视图和代码视图，需要单独的文档数据对象和文档视图对象。 在支持单个视图编辑器中，文档的数据对象和文档视图对象可以实现对同一个对象。  
  
     多个视图的示例，请参阅 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
3.  通过实现来实现编辑器工厂 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 接口。  
  
     有关详细信息，请参阅[编辑器工厂](../extensibility/editor-factories.md)。  
  
4.  决定是否希望你使用在就地激活编辑器或简化的嵌入来管理文档视图对象窗口。  
  
     简化的嵌入编辑器窗口承载标准文档视图中，而在就地激活编辑器窗口承载 ActiveX 控件或其他活动对象作为其文档的视图。 有关详细信息，请参阅[简化的嵌入](../extensibility/simplified-embedding.md)和[就地激活](../misc/in-place-activation.md)。  
  
5.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，以处理命令。  
  
6.  通过执行以下操作来提供文档持久性和响应外部文件的更改 ︰  
  
    1.  若要保存该文件，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 编辑器的文档的数据对象。  
  
    2.  若要对外部文件的更改作出响应，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 编辑器的文档的数据对象。  
  
        > [!NOTE]
        >  调用 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> 若要获取的指针 `IVsFileChangeEx`。  
  
7.  协调与源代码管理的文档编辑事件。 具体方法为：  
  
    1.  获取一个指向 `IVsQueryEditQuerySave2` 通过调用 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>。  
  
    2.  第一个编辑事件发生时，调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法。  
  
         这将提示用户签出该文件，如果尚未签出。 请务必处理"文件未签出"条件，以避免遭受错误  
  
    3.  同样，在保存文件之前, 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 方法。  
  
         此方法会提示用户保存文件，如果尚未保存，或者自上次保存以来已更改。  
  
8.  启用 **属性** 窗口以显示在编辑器中的选定文本的属性。 具体方法为：  
  
    1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 每个时间的文本选择发生更改，传递的实现过程中 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
    2.  调用 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 服务，以获取一个指向 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
9. 使用户能够项目编辑器之间拖放和 **工具箱**, ，或两个外部编辑器 （如 Microsoft Word\) 之间和 **工具箱**。 具体方法为：  
  
    1.  实现 `IDropTarget` 上您的编辑器来提醒您的编辑器是一个拖放目标的 IDE。  
  
    2.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 上使您的编辑器可以启用和禁用中的项的视图接口 **工具箱**。  
  
    3.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> 并调用 `QueryService` 上 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 服务，以获取一个指向 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 接口。  
  
         这使你的 VSPackage，若要添加新项目添加到 **工具箱**。  
  
10. 确定编辑器是否需要任何其他可选功能。  
  
    -   如果您希望您的编辑器来支持查找和替换的命令，实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>。  
  
    -   如果您想要使用您的编辑器中的文档大纲工具窗口，实现 `IVsDocOutlineProvider`。  
  
    -   如果您想要在您的编辑器中使用一个状态栏，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 并调用 `QueryService` 为 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 若要获取的指针 `IVsStatusBar`。  
  
         例如，编辑器可以显示行 \/ 列信息、 选择模式 （流式传输 \/ 框中） 和插入模式 （插入 \/ 重叠）。  
  
    -   如果您希望您的编辑器来支持 `Undo` 命令时，建议的方法是使用 OLE 撤消管理器模型。 作为替代方法，您可以有编辑器句柄 `Undo` 直接命令。  
  
11. 创建注册表信息，包括用于 VSPackage、 菜单、 编辑器和其他功能的 Guid。  
  
     以下是代码，您会将其放在.rgs 文件脚本演示如何正确注册一个编辑器中的一般示例。  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. 实现上下文相关帮助支持。  
  
     这使您可以提供 F1 帮助和动态帮助窗口支持您的编辑器中的项。 有关这方面的更多信息，请参见 [如何︰ 为编辑器提供的上下文](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)。  
  
13. 通过实现公开自动化对象模型从您的编辑器 `IDispatch` 接口。  
  
     有关详细信息，请参阅[导致自动化模型](../extensibility/internals/contributing-to-the-automation-model.md)。  
  
## 可靠编程  
  
-   IDE 调用时，会创建编辑器实例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法。 如果该编辑器支持多个视图， `CreateEditorInstance` 创建文档的数据和文档视图对象。 如果文档数据对象已打开的一个非空 `punkDocDataExisting` 值传递给 `IVsEditorFactory::CreateEditorInstance`。 编辑器工厂实现必须确定是否兼容通过查询在其上的适当接口来访问现有的文档数据对象。 有关更多信息，请参见[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
-   如果您使用简化的嵌入方法，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 接口。  
  
-   如果您决定使用就地激活，实现以下接口 ︰  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` 接口用于避免 OLE 2 菜单合并。  
  
     您 `IOleCommandTarget` 实现处理命令，如 **剪切**, ，**副本**, ，和 **粘贴**。 在实现时 `IOleCommandTarget`, ，确定您的编辑器是否需要其自己的.vsct 文件来定义其自己的命令菜单结构，或者如果它可以实现所定义的标准命令 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 通常情况下，编辑器使用和扩展 IDE 的菜单并定义其自己的工具栏。 但是，通常很有必要用于编辑器来定义其自己特定的命令，除了使用 IDE 的标准命令集。 若要执行此操作，您的编辑器必须声明标准命令它使用，然后在.vsct 文件中定义任何新的命令、 上下文菜单、 顶级菜单和工具栏。 如果您创建在就地激活编辑器，然后实现 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> 并为而不是使用 OLE 2 菜单合并的.vsct 文件中的编辑器中定义的菜单和工具栏。  
  
-   若要防止围在 UI 中的菜单命令，您应使用现有的命令在 IDE 中创造了新的命令之前。 共享的命令来定义 SharedCmdDef.vsct 和 ShellCmdDef.vsct 中。 这些文件安装的 VisualStudioIntegration\\Common\\Inc 子目录中的默认情况下您 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 安装。  
  
-   `ISelectionContainer` 可以快速单个和多个选择。 每个选定的对象作为实现 `IDispatch` 对象。  
  
-   IDE 实现 `IOleUndoManager` 作为可从访问服务 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 或作为一个对象，可以通过实例化 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>。 编辑器实现 `IOleUndoUnit` 为每个接口 `Undo` 操作。  
  
-   有两个位置的自定义编辑器可以公开自动化对象 ︰  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## 请参阅  
 [导致自动化模型](../extensibility/internals/contributing-to-the-automation-model.md)   
 [如何︰ 为编辑器提供的上下文](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)