---
title: "(源控制 VSPackage) 保存的查询编辑查询 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "QEQS 事件"
  - "查询编辑查询保存事件"
  - "源代码管理包，查询编辑查询保存事件"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# (源控制 VSPackage) 保存的查询编辑查询
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 编辑器中广播查询编辑器查询保存 \(QEQS\)操作。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 源代码管理存根实现 QEQS 服务，因此，它是 QEQS 事件的接收者。  这些事件然后将委托给当前活动的源代码管理 VSPackage。  积极的源代码管理 VSPackage 执行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 及其方法。  `IVsQueryEditQuerySave2` 接口的方法通常，调用之前直接文档第一次编辑，因此，在文档保存之前。  
  
## QueryEditQuerySave 事件  
 源代码管理 VSPackage 通过执行 `IVsQueryEditQuerySave2` 接口和所需的方法必须处理 QEQS 事件。  在 VSPackage 必须在最小两个方法的简要说明。  实际实现必须与源代码管理模型的逻辑匹配。  
  
### QueryEditFiles 方法  
 ，当所有项或编辑若要修改文件时， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 调用。  理想情况下，此方法调用修改，并且该文件的 *以前* ，在保存文件时。  调用时， `IVsQueryEditQuerySave2::QueryEditFiles` 方法检查特定文件在源代码管理下，它们是否需要通过检查，因此，它们是否可以重新加载。  如果情况妨碍文件是可编辑的， `IVsQueryEditQuerySave2::QueryEditFiles` 方法调用调用过程取消编辑。  指定调用模式调用方也是可能的。  在该 “无”模式下，因此，只有当它不会导致对任何 UI 显示，此方法将操作。  如果 UI 是不可避免的，必须返回标志指示该问题。  
  
 方法的行为是一个可处理方式;也就是说，如果编辑在一个文件中移除，编辑器对于所有文件都被取消。  相反，因此，如果编辑器允许，它允许任意文件。  如果此方法允许一次编辑给定的设置文件，它必须始终以允许编辑在为相同的后续调用设置文件。  允许编辑循环继续，直到文件已关闭，保存并重新加载;直到其属性更改;或在源代码管理包已更改。  要考虑的用例执行 `IVsQueryEditQuerySave2::QueryEditFiles` 方法由多个文件，专用文件，来自用户的取消，并且，内存编辑。  
  
### QuerySaveFiles 方法  
 ，当所有项或编辑需要保存一组文件时， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 调用。  调用时， `IVsQueryEditQuerySave2::QuerySaveFiles` 方法检查特定文件是否为只读，并且它们是否位于源代码管理。  如果文件需要进行检查，调用将委托到源代码管理包。  如果条件阻止保存文件， `IVsQueryEditQuerySave2::QuerySaveFiles` 方法必须通知编辑器取消保存。  与 `IVsQueryEditQuerySave2::QueryEditFiles` 方法，指定要调用模式调用方是可能的。  在该 “无”模式下，因此，只有当它不会导致对任何 UI 显示，此方法将操作。  如果 UI 是不可避免的，必须返回标志指示该问题。  
  
 此方法必须行为以可处理方式;也就是说，如果保存在一个文件中移除，保存对所有文件被取消。  相反，因此，如果保存允许，必须使所有文件。  与 `IVsQueryEditQuerySave2::QueryEditFiles` 方法，要考虑的用例执行 `IVsQueryEditQuerySave2::QuerySaveFiles` 方法由多个文件，专用文件，来自用户的取消，并且，内存编辑。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>