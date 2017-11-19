---
title: "如何： 实现嵌套的项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26456122d8b2cb0e89cfcda929cf68306959a31e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-nested-projects"></a>如何： 实现嵌套的项目
当你创建嵌套的项目类型，存在几个附加步骤必须实现。 父项目采用上某些相同解决方案具有为其嵌套 （子） 项目的职责。 父项目是类似于解决方案的项目的容器。 具体而言，有几个解决方案和通过要生成嵌套的项目的层次结构的父项目必须引发的事件。 创建嵌套的项目的以下过程介绍了这些事件。  
  
### <a name="to-create-nested-projects"></a>若要创建嵌套的项目  
  
1.  集成的开发环境 (IDE) 通过调用加载父项目的项目文件和启动信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>接口。 创建父项目并将其添加到解决方案。  
  
    > [!NOTE]
    >  此时，它是太早，父项目以创建嵌套的项目，因为必须创建父项目，然后才能创建子项目的过程中。 此序列中，父项目可以将设置应用到子项目，如果需要子项目可以获取从父项目的信息。 此序列是如果它是在客户端需要如源代码管理 (SCC) 和解决方案资源管理器。  
  
     父项目必须等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>之前项目，它可以创建其嵌套的 （子） 由 IDE 调用方法。  
  
2.  IDE 调用`QueryInterface`上的父项目<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>。 如果此调用成功，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>若要打开的所有父对象的嵌套项目的父级的方法。  
  
3.  父项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>将要创建的方法来通知嵌套项目的侦听器。 SCC，例如，正在侦听这些事件以了解是否在顺序中发生的解决方案和项目的创建过程中的步骤。 如果按顺序执行步骤，该解决方案可能被未与源代码管理正确注册。  
  
4.  父项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>及其子项目的每个上的方法。  
  
     你传递<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>到`AddVirtualProject`方法，以指示应将虚拟 （嵌套） 的项目添加到项目窗口中，从生成中, 排除添加到源代码管理，依次类推。 `VSADDVPFLAGS`允许您控制的可见性嵌套的项目和指示哪种功能都与之关联。  
  
     如果你重新加载具有项目存储在父项目的项目文件中，父项目调用的 GUID 的先前存在子项目`AddVirtualProjectEx`。 之间的唯一区别`AddVirtualProject`和`AddVirtualProjectEX`在于`AddVirtualProjectEX`有一个参数，以使该父项目来指定每个实例`guidProjectID`的子项目，以启用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>函数正确。  
  
     如果没有可用的未 GUID，如将其添加到父次解决方案添加新嵌套的项目时，创建一个项目。 它负责的父项目以保留该项目在其项目文件中的 GUID。 如果你删除嵌套的项目，还可以删除该项目的 GUID。  
  
5.  IDE 调用`M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren`的父项目的每个子项目的方法。  
  
     父项目必须实现`IVsParentProject`如果你想要嵌套项目。 但是父项目永远不会调用`QueryInterface`为`IVsParentProject`即使它具有其下的父项目。 解决方案处理调用`IVsParentProject`和实现，如果调用`OpenChildren`创建嵌套的项目。 `AddVirtualProjectEX`始终从调用`OpenChildren`。 它永远不应由父项目以按顺序保留层次结构创建的事件调用。  
  
6.  IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子项目的方法。  
  
7.  父项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>方法来通知侦听器是否已创建父级的子项目。  
  
8.  IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>父项目在打开所有子项目后的方法。  
  
     如果已存在，父项目通过调用创建每个嵌套的项目的 GUID `CoCreateGuid`。  
  
    > [!NOTE]
    >  `CoCreateGuid`是要创建 GUID 时调用的 COM API。 有关详细信息，请参阅`CoCreateGuid`和 MSDN 库中的 Guid。  
  
     父项目存储在其项目文件中要检索下次在 IDE 中打开此 GUID。 请参阅有关的调用与相关的详细信息的步骤 4`AddVirtualProjectEX`检索`guidProjectID`子项目。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>父 ItemID 然后调用方法时，按照约定你委托中嵌套的项目。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>检索嵌套了你想要在父类上调用时，委托中的项目节点的属性。  
  
     由于父和子项目以编程方式进行实例化，你可以在此时设置嵌套的项目的属性。  
  
    > [!NOTE]
    >  不仅执行您收到的上下文信息从嵌套的项目中，但您也可以要求父项目是否为该项的任何上下文通过检查<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。 以这种方式，可以向单个嵌套项目中添加额外的动态帮助特性和特定的菜单选项。  
  
10. 层次结构生成以通过调用在解决方案资源管理器中显示<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>方法。  
  
     将层次结构传递给环境中，通过`GetNestedHierarchy`生成以在解决方案资源管理器中显示层次结构。 在这种方式，解决方案知道项目存在并且可以由生成管理器，用于生成，或者可以允许在项目中将源代码管理下的文件。  
  
11. 创建 Project1 的所有嵌套的项目后，控制权传递回解决方案，并且为 Project2 重复此过程。  
  
     用于创建嵌套的项目这个相同流程进行具有子级的子项目。 在这种情况下，如果 BuildProject1，是 Project1 的子级，具有子项目，则将创建它们之后 BuildProject1 和之前 Project2。 该过程是递归函数，从顶部向下生成层次结构。  
  
     当已关闭嵌套的项目，因为用户关闭解决方案或特定于项目本身，另一种方法上`IVsParentProject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>，调用。 父项目包装调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>方法替换<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>方法来通知解决方案事件侦听器嵌套的项目，正在关闭。  
  
 以下主题处理多个实现嵌套的项目时需要考虑其他概念：  
  
 [卸载和重新加载嵌套项目的注意事项](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [嵌套项目的向导支持](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [实现嵌套项目的命令处理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [筛选嵌套项目的 AddItem 对话框](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>另请参阅  
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)