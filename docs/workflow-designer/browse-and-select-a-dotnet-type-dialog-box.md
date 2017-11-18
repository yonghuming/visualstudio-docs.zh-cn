---
title: "浏览并选择.NET 类型对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: "13"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac184805803e92758e1de93400c957d00e8ebda6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>“浏览并选择 .NET 类型”对话框
在**属性**窗口、 对话框框中或如变量设计器中，当你选择的设计器**浏览类型...**从数据类型的列表，**浏览并选择.NET 类型**对话框中 （在"类型浏览器"以缩写形式称为）。 在此对话框中，可以从程序集和项目的树视图中选择类型。  
  
 在很多用户方案中都使用此对话框，这些方案包括：  
  
-   设置变量或参数的类型时。  
  
-   为一般活动选择类型时。  
  
-   在 <xref:System.Activities.Statements.TryCatch> 活动上添加一个 catch 时。  
  
> [!NOTE]
>  类型浏览器可以显示 Visual Basic 交错数组类型，但不显示多维数组类型。 请参阅[交错数组](http://go.microsoft.com/fwlink/?LinkId=195226)和[多维数组](http://go.microsoft.com/fwlink/?LinkId=195227)有关详细信息。  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>从类型浏览器中选择值或引用类型  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>从类型浏览器中选择值或引用类型  
  
1.  在**类型名称**框中，输入你想要使用的类型的名称。  
  
2.  执行下列操作之一：  
  
    -   当你想要使用的类型名称出现在树中，在后**类型名称**框中，双击该类型以将其选中。  
  
    -   键入足够多的字符中**类型名称**中，用于唯一标识你想要使用，然后按 enter 以选择的类型的类型  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>从类型浏览器中选择一个泛型类型  
  
1.  在**类型名称**框中，键入你想要使用的类型的名称。  
  
2.  当你想要使用的类型名称出现在树中，在后**类型名称**框中，单击以选中它以便出现下拉框的类型。  
  
     选择你想要用于关闭下拉框中中的泛型，然后单击类型**确定**。  
  
## <a name="types-displayed-in-the-type-browser"></a>类型浏览器中显示的类型  
 类型浏览器中显示的类型可能因启动类型浏览器的方式而有所不同。 如果从工作流项目中的启动类型浏览器**vs2010**、 默认情况下的所有引用的程序集中类型和显示引用的项目。 如果从外部启动类型浏览器**vs2010**项目系统 （如重新承载的工作流应用程序或在独立的工作流文件），则默认情况下显示中的所有 AppDomain 中加载的程序集的类型.  
  
 可以按活动设计器开发人员筛选类型浏览器中的类型。 对于任何给定的活动，您可能只看到一个类型子集。 例如，在 <xref:System.Activities.Statements.TryCatch> 活动中，只有从 <xref:System.Exception> 派生的类型显示在类型浏览器中。  
  
## <a name="filtering-search-results-in-the-type-browser"></a>在类型浏览器中筛选搜索结果  
 中的类型列表**类型名称**框获取更短，因为你键入更多字符可找到匹配项。 只有其完全限定名以您键入的字符串开头的类型或者其简短名称以您键入的字符串开头的类型会显示在筛选出的列表中。  
  
 例如:   
  
1.  键入**操作**匹配<xref:System.OperationCanceledException>但不是<xref:System.InvalidOperationException>。 若要匹配 <xref:System.InvalidOperationException>，请开始键入 System.I 或 Invalid。  
  
2.  键入**泛型**匹配<xref:System.GenericUriParser>不中的类型，但<xref:System.Collections.Generic>命名空间。 若要在 <xref:System.Collections.Generic> 命名空间中搜索类型，请键入该命名空间的完全限定名称。  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>使用类型浏览器对话框选择服务协定  
 选择服务协定类型时，类型浏览器只显示具有 <xref:System.ServiceModel.ServiceContractAttribute> 特性的类型。  
  
## <a name="see-also"></a>另请参阅  
 [使用活动设计器](../workflow-designer/using-the-activity-designers.md)