---
title: "如何： 使用 WPF 树可视化工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e30d1fbd8cd23a514d1036bc43c809626c665d73
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>如何：使用 WPF 树可视化工具
可以使用 WPF 树可视化工具浏览 WPF 对象的可视化树，并查看该树中所含对象的 WPF 依赖项属性。 有关可视化树的详细信息，请参阅[WPF 中的树](/dotnet/framework/wpf/advanced/trees-in-wpf)。 有关依赖项属性的详细信息，请参阅[依赖项属性概述](/dotnet/framework/wpf/advanced/dependency-properties-overview)。  
  
 当你打开 WPF 树可视化工具时，你将看到两个窗格：**可视化树**左侧和**属性***名称***:** *类型*右侧窗格中的。 选择中的任何对象**可视化树**窗格中，与**属性***名称***:***类型*窗格自动更新以显示该对象的属性。  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>打开 WPF 树可视化工具  
  
1.  在数据提示中，**监视**窗口中，**自动**窗口中，或**局部变量**窗口中的，WPF 对象名称旁单击放大镜图标旁边的箭头。  
  
     将会显示可视化工具列表。  
  
2.  单击**WPF 树可视化工具**。  
  
### <a name="to-search-the-visual-tree"></a>搜索可视化树  
  
-   在**可视化树**窗格中，键入你想要在中搜索的字符串**搜索**框。  
  
     WPF 树可视化工具将立即在可视化树中查找与你键入的字符串匹配的第一个对象。 键入更多字符可找到更精确的匹配项。  
  
    -   若要转到可视化树中的下一个匹配项，请单击**下一步**。  
  
    -   若要返回到上一个匹配项的更多信息，请单击**Prev**。  
  
    -   若要清除搜索条件，请单击**清除**。  
  
### <a name="to-search-the-properties-list"></a>搜索属性列表  
  
-   在**属性***名称***:***类型*窗格中，键入你想要在中搜索的字符串**筛选**框。  
  
     WPF 树可视化工具将立即查找与你键入的字符串匹配的属性；现在，列表中仅显示与键入的字符串匹配的那些属性。 键入更多字符可找到更精确的匹配项。  
  
    -   若要清除搜索条件，请单击**清除**。  
  
### <a name="to-close-the-visualizer"></a>关闭可视化工具  
  
-   单击**关闭**对话框中右上角的图标。  
  
## <a name="see-also"></a>另请参阅  
 [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [WPF 中的树](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [依赖项属性概述](/dotnet/framework/wpf/advanced/dependency-properties-overview)