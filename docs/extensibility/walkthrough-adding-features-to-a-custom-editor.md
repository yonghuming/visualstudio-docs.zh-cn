---
title: "演练： 将功能添加到自定义编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df3621d87ae80c0eee105183edbc97a4e7ade62f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>演练： 将功能添加到自定义编辑器
创建自定义编辑器后，你可以向其添加更多的功能。  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>若要创建 VSPackage 的编辑器  
  
1.  通过使用 Visual Studio 包项目模板创建自定义编辑器。  
  
     有关详细信息，请参阅[演练： 创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
2.  决定您编辑器来支持单一视图或多个视图。  
  
     支持的编辑器**新窗口**命令时，或具有窗体视图和代码视图，需要单独的文档数据对象和文档视图对象。 在编辑器中，支持单个视图，文档数据对象和文档视图对象可以实现对同一个对象。  
  
     多个视图的示例，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
3.  编辑器工厂实现通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口。  
  
     有关详细信息，请参阅[编辑器工厂](../extensibility/editor-factories.md)。  
  
4.  决定要使用就地激活编辑器还是简化嵌入来管理文档视图对象窗口。  
  
     简化的嵌入编辑器窗口承载标准文档视图中，而非就地激活编辑器窗口托管 ActiveX 控件或其他活动作为其文档视图对象。 有关详细信息，请参阅[简化嵌入](../extensibility/simplified-embedding.md)和[就地激活](../extensibility/in-place-activation.md)。  
  
5.  实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口以处理命令。  
  
6.  通过执行以下提供文档持久性和响应的外部文件更改：  
  
    1.  若要保存该文件，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>编辑器的文档数据对象上。  
  
    2.  若要对外部文件更改做出响应，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>编辑器的文档数据对象上。  
  
        > [!NOTE]
        >  调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>用于获取指向`IVsFileChangeEx`。  
  
7.  与源代码管理的文档编辑事件协调。 具体方法为：  
  
    1.  获取指向的`IVsQueryEditQuerySave2`通过调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>。  
  
    2.  第一个编辑事件发生时，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>方法。  
  
         这将提示用户签出该文件，如果未签出。请务必"未签出文件"条件，以避免遭受错误处理  
  
    3.  同样，在保存文件之前, 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>方法。  
  
         此方法会提示用户以保存该文件，如果尚未保存的或自上次保存以来已更改。  
  
8.  启用**属性**窗口以显示属性编辑器中选定的文本。 具体方法为：  
  
    1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>每个时间文本所选内容更改，传递的实现中<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
    2.  调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服务，以获取指向的指针<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
9. 启用用户拖放项之间编辑器和**工具箱**，或两个外部编辑器 （例如 Microsoft Word) 之间与**工具箱**。 具体方法为：  
  
    1.  实现`IDropTarget`在你的编辑器来提醒 IDE 你的编辑器是放置目标上。  
  
    2.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>视图使你的编辑器可以启用和禁用中的项上的接口**工具箱**。  
  
    3.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>并调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>服务，以获取指向的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>接口。  
  
         这使你的 VSPackage，若要添加新项目添加到**工具箱**。  
  
10. 确定编辑器是否需要任何其他可选功能。  
  
    -   如果您希望您编辑器来支持查找和替换的命令，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>。  
  
    -   如果你想要使用你的编辑器中的文档大纲工具窗口，实现`IVsDocOutlineProvider`。  
  
    -   如果你想要在你的编辑器中使用状态栏，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>并调用`QueryService`为<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>用于获取指向`IVsStatusBar`。  
  
         例如，编辑器可以显示行 / 列信息、 选择模式 （流式传输 / 框中），并插入模式 （插入 / 重叠）。  
  
    -   如果您希望支持你编辑器`Undo`命令时，建议的方法是使用 OLE 撤消管理器模型。 作为替代方法，你可以编辑器句柄`Undo`直接命令。  
  
11. 创建注册表信息，包括有关 VSPackage、 菜单、 编辑器和其他功能的 Guid。  
  
     下面是代码的可使在.rgs 文件脚本来演示如何正确注册编辑器中的泛型示例。  
  
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
  
     这使您可以提供 F1 帮助和动态帮助窗口支持适用于你的编辑器中的项。 有关这方面的详细信息，请参阅[如何： 提供上下文为编辑器](../extensibility/how-to-provide-context-for-editors.md)。  
  
13. 通过实现公开自动化对象模型从你的编辑器`IDispatch`接口。  
  
     有关详细信息，请参阅[导致自动化模型](../extensibility/internals/contributing-to-the-automation-model.md)。  
  
## <a name="robust-programming"></a>可靠编程  
  
-   当 IDE 调用创建编辑器实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 如果编辑器支持多个视图，`CreateEditorInstance`创建文档数据和文档视图对象。 如果文档数据对象已打开，非 null`punkDocDataExisting`值传递到`IVsEditorFactory::CreateEditorInstance`。 编辑器工厂实现必须确定是否兼容的查询在其上的相应接口访问现有的文档数据对象。 有关详细信息，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
-   如果你使用简化的嵌入方法，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>接口。  
  
-   如果你决定使用就地激活，实现以下接口：  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent`接口用于避免 OLE 2 菜单合并。  
  
     你`IOleCommandTarget`实现处理命令，如**剪切**，**复制**，和**粘贴**。 在实现时`IOleCommandTarget`，确定你的编辑器是否需要其自己的.vsct 文件以定义其自己的命令菜单结构，或者如果它可以实现所定义的标准命令[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 通常情况下，编辑器使用和扩展 IDE 的菜单，定义其自己的工具栏。 但是，它通常是必要的编辑器来定义其自己特定的命令，除了使用 IDE 的标准命令集。 若要执行此操作，你的编辑器必须声明其使用，然后在.vsct 文件中定义任何新的命令、 上下文菜单、 顶级菜单和工具栏的标准命令。 如果您创建就地激活编辑器，然后实现<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>和为而不是使用 OLE 2 菜单合并的.vsct 文件中的编辑器中定义的菜单和工具栏。  
  
-   若要防止出现拥挤的 UI 中的菜单命令，你应使用的现有命令在 IDE 中之前在发明新的命令。 共享的命令 SharedCmdDef.vsct 和 ShellCmdDef.vsct 中定义。 这些文件安装的 VisualStudioIntegration\Common\Inc 子目录中的默认情况下你[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]安装。  
  
-   `ISelectionContainer`可以表示单个和多个选择。 每个选定的对象作为实现`IDispatch`对象。  
  
-   IDE 实现`IOleUndoManager`作为服务从可访问<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>或对象可通过实例化<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>。 编辑器实现`IOleUndoUnit`每个接口`Undo`操作。  
  
-   有两个位置的自定义编辑器可以公开自动化对象：  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>另请参阅  
 [导致自动化模型](../extensibility/internals/contributing-to-the-automation-model.md)   
 [如何： 为编辑器提供的上下文](../extensibility/how-to-provide-context-for-editors.md)