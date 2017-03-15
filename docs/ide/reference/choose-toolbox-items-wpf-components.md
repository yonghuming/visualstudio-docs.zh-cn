---
title: "选择工具箱项，WPF 组件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8d34a09ec4716a9ab2d5fbaea6c93657961c1c43
ms.lasthandoff: 02/22/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>选择工具箱项，WPF 组件
“选择工具箱项”对话框中的此选项卡显示了在本地计算机上可用的 Windows Presentation Foundation (WPF) 控件列表。 若要显示此列表，请从“工具”菜单中选择“选择工具箱项”，从而显示“选择工具箱项”对话框，然后选择其中的“WPF 组件”选项卡。 若要对所列组件排序，请选择任意列标题。  
  
-   选中组件旁边的复选框后，该组件的图标将显示在“工具箱”中。  
  
    > [!TIP]
    >  若要将 WPF 控件的实例添加到打开进行编辑的项目文档，请将其“工具箱”图标拖动到“设计”视图面。 组件的默认标记和代码将插入到项目中，以便进行修改。 有关详细信息，请参阅[如何：管理“工具箱”窗口](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)和[如何：操作工具箱选项卡](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)。  
  
-   清除组件旁边的复选框后，将从中“工具箱”中删除相应的图标。  
  
    > [!NOTE]
    >  计算机上安装的 .NET Framework 组件仍然可用，无论其图标是否显示在“工具箱”中。  
  
 “WPF 组件”选项卡上的列包含下列信息：  
  
 名称  
 列出计算机注册表中条目的 WPF 控件的名称。  
  
 Namespace  
 显示定义组件结构的 [NIB：.NET Framework 类库](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29)命名空间的层次结构。 对此列排序可列出计算机上安装的每个 .NET Framework 命名空间中的可用组件。  
  
 程序集名称  
 显示包含每个组件的命名空间的 .NET Framework 程序集的名称。 对此列排序可列出计算机上安装的每个 .NET Framework 程序集中包含的命名空间。  
  
 目录  
 显示 .NET Framework 程序集的位置。 所有程序集的默认位置是全局程序集缓存。 有关全局程序集缓存的详细信息，请参阅[使用程序集和全局程序集缓存](http://msdn.microsoft.com/Library/8a18e5c2-d41d-49ef-abcb-7c27e2469433)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **筛选器**  
 基于文本框中提供的字符串筛选 WPF 控件列表。 将显示四列中的所有匹配项。  
  
 **清除**  
 清除筛选字符串。  
  
 **浏览**  
 开启“打开”对话框，这可导航到包含 WPF 控件的程序集。 将其用于加载不在全局程序集缓存中的程序集。  
  
 **语言**  
 显示包含所选 WPF 控件的程序集的本地化语言。  
  
## <a name="limitations"></a>限制  
 将自定义控件或 <xref:System.Windows.Controls.UserControl> 添加到工具箱具有以下限制。  
  
-   仅适用于在当前项目外部定义的自定义控件。  
  
-   如果将解决方案配置从“调试”更改为“发布”，或从“发布”更改为“调试”，则不能正确更新。 这是因为该引用不是项目引用，而是磁盘上的程序集引用。 如果控件属于当前解决方案，从“调试”更改为“发布”时，项目将继续引用该控件的调试版本。  
  
 此外，如果将设计时元数据应用到自定义控件，而且此元数据指定将 <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> 设置为`false`，则该控件不会出现在“工具箱”中。  
  
 可以通过映射控件的命名空间和程序集，直接在 XAML 视图中引用控件。 有关详细信息，请参阅[如何：将命名空间导入 XAML](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c)。  
  
## <a name="see-also"></a>另请参阅  
 [“选择工具箱项”对话框 (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [工具箱](../../ide/reference/toolbox.md)   
 [如何：在 WPF 应用程序中使用第三方 WPF 控件](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF 设计器](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
