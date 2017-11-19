---
title: "更新用户界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02bf66cba145b1d5fdaea899ca3af4ca2bcefbe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="updating-the-user-interface"></a>更新用户接口
实现命令后，你可以添加代码以与新的命令的状态更新的用户界面。  
  
 在典型的 Win32 应用程序，该命令集可能持续轮询和用户查看它们时，可以调整单个命令的状态。 但是，因为[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]shell 可以承载无限的数量的 Vspackage，广泛轮询可能会降低响应能力，尤其在托管的代码和 COM 之间的互操作程序集之间轮询  
  
### <a name="to-update-the-ui"></a>若要更新 UI  
  
1.  执行以下步骤之一：  
  
    -   调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>接口可以从获取<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服务，，如下所示。  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         如果参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>为非零 (`TRUE`)，则将以同步方式和立即执行更新。 我们建议传递零 (`FALSE`) 为此参数，以帮助保持良好的性能。 如果你想要避免缓存，应用`DontCache`标志当在.vsct 文件中创建命令。 不过，请谨慎使用标志或可能会降低性能。 有关命令标志的详细信息，请参阅[命令标志元素](../extensibility/command-flag-element.md)文档。  
  
    -   在 ActiveX 控件承载在窗口中使用就地激活模型的 Vspackage，它可能更方便地使用<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>中的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>接口和<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>中的方法<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>接口在功能上等效。 同时会导致环境以重新查询的所有命令的状态。 通常情况下，不立即执行更新。 相反，更新推迟到空闲时间。 Shell 缓存命令状态，以帮助保持良好的性能。 如果你想要避免缓存，应用`DontCache`标志当在.vsct 文件中创建命令。 不过，请使用标志慎重因为可能会降低性能。  
  
         请注意，你可以获取<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>接口通过调用`QueryInterface`方法<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>对象或通过获取的接口<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>服务。  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [实现](../extensibility/internals/command-implementation.md)