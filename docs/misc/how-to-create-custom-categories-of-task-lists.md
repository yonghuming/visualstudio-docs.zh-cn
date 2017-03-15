---
title: "如何：创建任务列表的自定义类别 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "任务列表, 自定义类别"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 如何：创建任务列表的自定义类别
任务自定义类提供对任务如何的控件。 **任务列表** 窗口中显示。  
  
 实现任务自定义类别下列原因的:  
  
-   要控件类在类别列表中显示 \(排序\) 的位置。  
  
-   您需要排序到类别，而没有其他任务按它们之间的任务的若干个子类别。  
  
-   要创建仅任务显示的自定义视图。  
  
    > [!NOTE]
    >  可获得的效果与自定义类别，而不会实际实现自定义的类别。  例如，您可以通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>显示类别的位图或子类别。  任务提供程序列表每个任务然后提供的索引到列表中。  
  
 使用下面的过程中，创建自定义类别在 **任务列表**，注册它。 **任务列表** 。  
  
### 注册自定义任务列表类别  
  
-   调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> 到的自定义类别任务列表中注册。  
  
     每个自定义类必须具有自己的 GUID，在 `guidCat` 参数指定。  在 `dwSortOrder` 参数，请提供您希望此类别排序的位置 \(在列表按类别排序时\)。  则此方法返回实际排序自定义类别的位置在大型列表类别。  
  
     排序内置任务类别的命令，在 <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY> 枚举中定义，下表。  
  
    |类别|值|说明|  
    |--------|-------|--------|  
    |CAT\_ALL|1|不是物理类别。  用于允许任务列表视图显示所有任务。 **任务列表**。|  
    |CAT\_BUILDCOMPILE|10|生成错误、警告和能部署错误。|  
    |CAT\_COMMENTS|20|特殊注释生成的任务，如 “TODO，”取消 “，”或 “表示丐”。|  
    |CAT\_CODESENSE|30|为您生成的错误键入源代码。|  
    |CAT\_SHORTCUTS|40|代码的快捷方式。|  
    |CAT\_USER|50|用户输入的任务。|  
    |CAT\_MISC|60|Vspackage 可能希望添加到 **任务列表**的其他任务。|  
    |CAT\_HTML|70|与网页开发的任务。|  
  
     例如，包括在 CAT\_CODESENSE 和 CAT\_SHORTCUTS 之间的类别，可以通过按值 31 排序顺序的。  但是，在中，因为值为 31 可能由另一个自定义任务类提供程序已使用， **任务列表** 为下一个空槽为您分配任务类别。  此值传回您 `pCat` 参数的。  
  
### 取消注册自定义任务列表类别  
  
-   调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A> 取消注册自定义类别。  
  
## 请参阅  
 [创建自定义任务列表视图](/visual-cpp/misc/creating-custom-task-list-views)