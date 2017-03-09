---
title: "设置颜色、渐变和不透明度 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI 元素设计 [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# 设置颜色、渐变和不透明度
所有 Visual Studio 中的用户界面 \(UI\) 元素都在 Windows Presentation Foundation \(WPF\) 中进行创建。 因此，在创建工具窗口或其他 UI 元素时，可以通过对这些元素设置适当的特性来应用颜色、渐变和不透明度。 可以通过使用“属性”窗口将这些设置设定为指定值，或者可以查询集成开发环境 \(IDE\) 了解系统值。 我们建议，当你希望你的扩展类似于其余 IDE 时，请使用系统值。  
  
 为了向后兼容性，仍支持 Windows 窗体 UI 和本机代码 UI。 有关如何在非 WPF 扩展中设置颜色和渐变的信息，请参阅 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 文档。  
  
## 设置颜色、渐变和不透明度  
 你可以设置更改大多数 XAML 元素的外观，通过设置其 `Background`、`Foreground`、`Opacity` 或其他可视特性实现。 这些特性对应于将 <xref:System.Windows.Media.Brush?displayProperty=fullName> 作为值的特性。  
  
#### 若要在工具窗口中设置背景颜色、渐变和不透明度  
  
1.  打开 MyControl.xaml。  
  
2.  在最高级别 <xref:System.Windows.Controls.UserControl> 元素中的“XAML”窗格中，键入 `background=`。  
  
     IntelliSense 将显示背景特性的颜色列表。  
  
     从该列表中选择某一颜色。  
  
3.  在“属性”窗口中，展开“画笔”节点，然后单击“背景”。  
  
     “属性”窗口将显示颜色选取器。 上述颜色选取器是代表画笔的一行图标。  
  
4.  使用滑块来选择一种颜色。  
  
     XAML 将立即更新以显示新背景颜色。  
  
5.  单击“渐变画笔”图标。  
  
     颜色选取器将更改为渐变选取器。  
  
6.  使用滑块来选择一种渐变。  
  
     XAML 将立即更新以显示新背景渐变。  
  
7.  单击“图像画笔”图标。  
  
     渐变选取器将更改为图像选择工具。  
  
8.  选择一个图像并设置其拉伸和平铺参数。  
  
     XAML 将立即更新以显示新背景图像。  
  
9. 单击“空画笔”图标。  
  
     设计器中的背景将返回为中性，并且将 `BackGround` 特性设置为 `"{x:Null}"`。  
  
## 查询系统值  
 你可以使用 <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName> 类属性查询系统值，此类属性是指在 Visual Studio 其他部分中设置的画笔。  
  
#### 若要通过查询系统值来设置颜色、渐变和不透明度  
  
1.  选择 XAML 元素。  
  
2.  在元素定义中，将该元素的其中一个可视特性设置为 `VsBrushes` 类的属性，如以下示例所示。  
  
     [!CODE [TWShortcutMenu#32](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#32)]  
  
     使用 [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) 扩展使值按要求进行更改（例如，当用户更改设置时）。 必须使用 [X:static](../Topic/x:Static%20Markup%20Extension.md) 扩展，因为 `VsBrushes` 类不是默认 WPF 命名空间的一部分。  
  
## 请参阅  
 [扩展工具窗口](../misc/extending-tool-windows.md)