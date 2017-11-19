---
title: "卸载和重新加载注意事项嵌套项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf34a3fe708a6ecab200262224da395b9fa37ecb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸载和重新加载嵌套项目时的注意事项
当实现嵌套的项目类型时，你必须卸载并重新加载项目时执行附加步骤。 若要正确通知解决方案事件侦听器，必须正确提升`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。  
  
 你必须将提升这些事件以这种方式的一个原因是不希望源代码管理 (SCC) 才可从服务器中删除项，然后将其添加回作为什么新的内容，如果没有`Get`从源代码管理操作。 在这种情况下，将超出 SCC 加载的新文件，并且你必须卸载并重新加载的所有文件，它们仍然是不同的情况下。 SCC 调用`ReloadItem`。 该调用的实现是删除项目，然后重新在通过实现再次创建它`IVsFireSolutionEvents`调用`OnBeforeUnloadProject`和`OnAfterLoadProject`。 当你执行此实现时，SCC 将得到通知，到该项目是暂时删除并再次添加。 因此，SCC 不会不运行项目时项目已从服务器中实际删除，然后再次添加。  
  
## <a name="reloading-projects"></a>重新加载项目  
 若要支持的嵌套项目重新加载，则实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 实现中`ReloadItem`，关闭嵌套的项目，然后重新创建它们。  
  
 通常当重新加载项目，则 IDE 将引发<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>和`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`事件。 但是，对于将删除并重新加载嵌套的项目，父项目启动过程，不 IDE。 因为父项目不会引发解决方案事件，IDE 不包含信息有关进程的初始化，不会引发事件。  
  
 若要处理此过程中，父项目调用`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>接口关闭<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>接口。 `IVsFireSolutionEvents`提供一些功能，告知 IDE 引发`OnBeforeUnloadProject`事件来卸载嵌套的项目，然后引发`OnAfterLoadProject`事件重新加载相同的项目。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [嵌套项目](../../extensibility/internals/nesting-projects.md)