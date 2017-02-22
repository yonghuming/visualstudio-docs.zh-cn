---
title: "在 XAML 设计器中将对象组织到布局容器中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 在 XAML 设计器中将对象组织到布局容器中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

想象你希望对象出现在页面上的哪个位置；诸如图像、按钮和视频等对象。  也许你希望它们出现在行和列中、在单个行中（垂直或水平）或在固定位置中。  
  
 你已经有机会考虑页面如何显示之后，请选择布局面板。  所有页面都从一个布局面板开始，因为你需要某个容器来向其中添加对象。  默认情况下，它是 **Grid**，但是可以进行更改。  
  
 布局面板可帮助你在页面上排列对象，但是它们的作用不仅于此。  它们可以帮助你针对不同屏幕大小和分辨率进行设计。  当用户运行你的应用时，布局面板中的所有对象都会调整大小以匹配用户设备的屏幕空间。  当然，如果你不希望布局这样做，则可以为布局的一部分或整个布局重写该行为。  可以使用高度和宽度属性对此进行控制。  
  
 此页面介绍布局面板和控件，然后引导你观看帮助你开始使用它们的简短视频。  
  
> [!NOTE]
>  某些视频可能指 Blend 或 Expression Blend，与 Visual Studio 和 Blend for Visual Studio 使用的 XAML 设计器相同。  
  
## 布局面板  
 通过选择这些布局面板之一来开始设计你的页面。  页面可以具有多个布局面板。  例如，你可以从 **Grid** 布局面板开始，然后将一个 **StackPanel** 添加到 **Grid** 中的某个区域，以便你可以在该元素中垂直排列控件。  
  
 以下布局面板是最常用的，不过还有一些其他布局面板。  你可以在 **Assets** 面板中找到所有这些内容。  
  
-   [网格](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> 网格  
 在行和列中排列对象。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用网格](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 将对象排列到相等或统一的网格区域中。  此面板非常适用于排列图像的列表。  
  
 （仅适用于 WPF 项目）  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Canvas  
 按任何所需方式排列对象。  当用户运行你的应用时，这些元素将在屏幕上具有固定位置。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 在单个行中水平或垂直排列对象。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 按顺序从左到右排列对象。  当面板最右边的空间不足时，它会将内容*换行*到下一行，并这样从左到右、从上到下进行。  还可以使自动换行面板的方向垂直，以便对象从上到下、从左到右排列。  
  
 （仅适用于 WPF 项目）  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 排列对象，以使它们停留或*停靠*在面板的一个边缘。  
  
 （仅适用于 WPF 项目）  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## 布局控件  
 也可以向布局控件添加对象。  它们的功能不如布局面板那么丰富，不过你可能会发现它们对于某些情况很有帮助。  
  
 以下布局控件是最常用的，不过还有一些其他布局控件。  你可以在 **Assets** 面板中找到所有这些内容。  
  
-   [边框](#Border)  
  
-   [弹出项](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> 边框  
 围绕创建边框、背景或两者。  只能将一个对象添加到 **Border**。  如果要将边框或背景应用于多个对象，请将布局面板添加到 **Border**。  然后，将对象添加到该面板或控件。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用边框](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> 弹出项  
 在窗口中向用户显示信息或选项。  只能将一个对象添加到 **Popup**。  默认情况下，**Popup** 包含一个 **Grid**，但是可以进行更改。  
  
###  <a name="Scroll"></a> ScrollViewer  
 使用户可以向下滚动页面或页面区域。  只能将一个对象添加到 **ScrollViewer**，因此添加布局面板（如 **Grid** 或 **StackPanel**）很有意义。  
  
###  <a name="View"></a> Viewbox  
 采用与缩放控件十分类似的方式扩展对象。  只能将一个对象添加到 **Viewbox**。  如果要将该效果应用于多个对象，请将布局面板添加到 **ViewBox**，然后将控件添加到该布局面板。  
  
 （仅适用于 WPF 项目）  
  
## 请参阅  
 [在 XAML 设计器中使用元素](../designers/working-with-elements-in-xaml-designer.md)   
 [使用 XAML 设计器创建 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)