---
title: "属性窗口的按钮: | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性窗口中按钮"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 属性窗口的按钮:
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

默认情况下根据开发语言和产品类型，某些按钮。 **属性** 窗口中将显示工具栏。  在所有情况下， **类**、 **按字母顺序排列**、 **属性**和 **属性页** 按钮显示。  在 Visual C\# 和 Visual Basic， **事件** 按钮将显示。  在某些 Visual C\+\+ 项目， **VC\+\+ 消息** 和 **VC 重写** 按钮显示。  其他按钮能用于任何其他项目类型中显示。  有关 **属性** 窗口的按钮的更多信息，请参见 [属性窗口](../../ide/reference/properties-window.md)。  
  
## " 属性 " 窗口按钮的实现  
 当您单击 **类** 按钮时， Visual Studio 会调用在具有焦点排序其属性按类别的对象的 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 接口。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 在提供给 **属性** 窗口的 `IDispatch` 对象实现。  
  
 具有 11 预定义的属性类别，具有负值。  可以定义自定义类别，但是，建议您为其分配正值使用预定义的类别区分它们。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> 方法返回指定的属性的相应属性类别值。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> 方法返回包含类名称的字符串。  ，因为 Visual Studio 知道标准属性类别值时，才需要提供自定义类别值支持。  
  
 当您单击 **按字母顺序排列** 按钮时，属性按字母顺序显示名称。  名称由 `IDispatch` 检索基于一个本地化的排序算法。  
  
 当 **属性** 窗口打开时， **属性** 按钮自动显示选定状态。  在环境的其他部分，同一个按钮显示，因此，您可以单击它显示 **属性** 窗口。  
  
 ，如果 `ISpecifyPropertyPages` 没有为选定的对象，实现 **属性页** 按钮不可用。  属性页显示通常与解决方案和项目的配置相关属性，但是，它们也是与项目项 \(例如，在 Visual C\+\+ 中为\)。  
  
> [!NOTE]
>  使用非托管代码，不能添加工具栏按钮。 **属性** 窗口。  若要添加工具栏按钮，必须创建从 <xref:System.Windows.Forms.Design.PropertyTab>派生的托管对象。  
  
## 请参阅  
 [将属性扩展](../../extensibility/internals/extending-properties.md)