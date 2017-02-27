---
title: "更新用户界面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新的用户界面"
  - "更新用户界面的命令"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# 更新用户界面
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

实现命令后，您可以添加代码以使用新命令的状态更新用户界面。  
  
 在典型的 Win32 应用程序，可以连续轮询命令集，可以按用户查看这些调整各个命令的状态。 但是，由于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外壳程序可以承载无限的数量的 Vspackage，广泛轮询可能会降低响应性，尤其在托管的代码和 COM 之间的互操作程序集之间轮询  
  
### 若要更新 UI  
  
1.  执行以下步骤之一：  
  
    -   调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 界面可从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服务，但，如下所示。  
  
        ```c#  
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
  
         如果参数的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 为非零 \(`TRUE`\)，然后以同步方式和立即执行更新。 我们建议您传递零 \(`FALSE`\) 为此参数，以帮助保持良好的性能。 如果你想要避免缓存，应用 `DontCache` 标志时在.vsct 文件中创建的命令。 不过，请谨慎使用此标志或性能可能会降低。 有关命令标志的详细信息，请参阅 [命令标志元素](../extensibility/command-flag-element.md) 文档。  
  
    -   在承载在窗口中使用称为就地激活模型的 ActiveX 控件的 Vspackage，它可能更方便地使用 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 方法。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 接口和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 接口在功能上等效。 同时会导致该环境以重新查询所有命令的状态。 通常情况下，不立即执行更新。 相反，更新推迟到空闲时间。 命令行界面缓存命令状态来帮助保持良好的性能。 如果你想要避免缓存，应用 `DontCache` 标志时在.vsct 文件中创建的命令。 不过，该标志谨慎使用因为性能可能会降低。  
  
         请注意，您可以获得 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 接口通过调用 `QueryInterface` 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 对象，或通过获取从接口 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服务。  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [实现](../extensibility/internals/command-implementation.md)