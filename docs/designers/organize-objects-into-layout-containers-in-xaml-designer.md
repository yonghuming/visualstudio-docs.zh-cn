---
title: "在 XAML 设计器中将对象组织到布局容器中 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7974392d54ab30be77df939206927fd020dc620f
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>在 XAML 设计器中将对象组织到布局容器中
想象希望对象出现在页面上的位置；诸如图像、按钮和视频等对象。 也许你希望它们出现在行和列中、在单个行中（垂直或水平）或在固定位置中。  
  
 在考虑好页面的显示情况后，请选择布局面板。 所有页面都从一个布局面板开始，因为你需要某个容器来向其中添加对象。 默认情况下，它是 Grid，但是可以更改。  
  
 布局面板可帮助你在页面上排列对象，但是它们的作用不仅于此。 它们可以帮助你针对不同屏幕大小和分辨率进行设计。 当用户运行你的应用时，布局面板中的所有对象都会调整大小以匹配用户设备的屏幕空间。 当然，如果不希望布局进行此操作，则可为一部分布局或整个布局重写该行为。 可以使用高度和宽度属性对此进行控制。  
  
 此页面介绍布局面板和控件，然后引导你观看帮助你开始使用它们的简短视频。  
  
> [!NOTE]
>  某些视频可能指 Blend 或 Expression Blend，与 Visual Studio 和 Blend for Visual Studio 使用的 XAML 设计器相同。  
  
## <a name="layout-panels"></a>布局面板  
 通过选择这些布局面板之一来开始设计你的页面。 页面可以具有多个布局面板。 例如，可从 Grid 布局面板开始，然后将一个 StackPanel 添加到 Grid 中的某个区域，即可在该元素中垂直排列控件。  
  
 以下布局面板是最常用的，不过还有一些其他布局面板。 在 Assets 面板中可以找到所有这些内容。  
  
-   [网格](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [画布](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> 网格  
 在行和列中排列对象。  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用网格](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 将对象排列到相等或统一的网格区域中。 此面板非常适用于排列图像的列表。  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 （仅适用于 WPF 项目）  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用 UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> 画布  
 按任何所需方式排列对象。 当用户运行你的应用时，这些元素将在屏幕上具有固定位置。  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用画布](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a>StackPanel  
 在单个行中水平或垂直排列对象。  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 按顺序从左到右排列对象。 面板最右边空间不足时，它会将内容换行到下一行，并采用从左到右、从上到下的换行顺序。 还可以使自动换行面板的方向垂直，以便对象从上到下、从左到右排列。  
  
 （仅适用于 WPF 项目）  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 排列对象，使它们停留或停靠在面板的一个边缘。  
  
 （仅适用于 WPF 项目）  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **观看简短视频：** ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>布局控件  
 也可以向布局控件添加对象。 布局控件功能不如布局面板那么丰富，在某些情况中这些控件可能很有用。  
  
 以下布局控件是最常用的，不过还有一些其他布局控件。 在 Assets 面板中可以找到所有这些内容。  
  
-   [边框](#Border)  
  
-   [弹出项](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> 边框  
 围绕创建边框、背景或两者。 只能将一个对象添加到边框。 如果要将边框或背景应用于多个对象，请将布局面板添加到边框。 然后，将对象添加到该面板或控件。  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 观看简短视频： ![配置已安装的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [使用边框](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> 弹出项  
 在窗口中向用户显示信息或选项。 只能将一个对象添加到弹出项。 默认情况下，弹出项包含一个 Grid，但是可以更改。  
  
###  <a name="Scroll"></a> ScrollViewer  
 使用户可以向下滚动页面或页面区域。 只能将一个对象添加到 ScrollViewer，因此添加 Grid 或 StackPanel 等布局面板很有必要。  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
###  <a name="View"></a> Viewbox  
 采用与缩放控件十分类似的方式扩展对象。 只能将一个对象添加到 Viewbox。 如果要将该效果应用于多个对象，请将布局面板添加到 ViewBox，然后将控件添加到该布局面板。  
  
 （仅适用于 WPF 项目）  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>另请参阅  
 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [使用 XAML 设计器创建 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
