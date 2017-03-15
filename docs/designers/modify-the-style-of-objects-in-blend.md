---
title: "修改 Blend 中对象的样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 修改 Blend 中对象的样式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

自定义对象的最简单方法是在**属性**窗格中设置属性。  
  
 如果你希望重复使用设置或设置组，请创建可重复使用的资源。  这可以是*样式*、*模板*或如自定义颜色一样简单的对象。  还可以使控件基于其状态以不同方式出现。  例如，按钮在用户单击它时变为绿色。  
  
 **本主题内容**：  
  
-   [画笔：修改对象的外观](#Brushes)  
  
-   [样式和模板：在控件之间创建一致的外观](#Styles)  
  
-   [可视状态：基于其状态更改控件的外观](#Visual)  
  
-   [资源：创建颜色、样式和模板，并在以后重复使用它们](#Resources)  
  
##  <a name="Brushes"></a> 画笔：修改对象的外观  
 如果要更改对象外观，请向它应用画笔。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [画笔编辑器](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor)。  
  
### 在对象上绘制重复图像或图案  
 可使用*平铺画笔*在对象上绘制重复图像或图案。  
  
 若要创建平铺画笔，请首先创建*图像画笔*、*图形画笔*或*视觉画笔*资源。  
  
 使用图像创建图像画笔。  下图显示图像画笔、平铺的图像画笔和翻转的图像画笔。  
  
 使用矢量图形（如路径或形状）创建图形画笔。  下图显示图形画笔、平铺的图形画笔和翻转的图形画笔。  
  
 通过控件（如按钮）创建视觉画笔。  下图显示视觉画笔和平铺的视觉画笔。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [平铺画笔](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes)。  
  
##  <a name="Styles"></a> 样式和模板：在控件之间创建一致的外观  
 可以一次性设计控件的外观和行为，然后将该设计应用于其他控件，以便不必分别进行维护。  
  
 **是否应使用样式？**：如果只是想设置默认属性（如按钮的颜色），请使用*样式*。  即使在应用了样式之后，也可以修改控件。  
  
 **是否应使用模板？**：如果想要更改控件的结构，请使用*模板*。  假设将图形或徽标转换为按钮。  在向其应用模板之后，无法修改控件。  
  
### 创建模板或样式  
 可通过两种方法创建模板。  可以将美工板上的任何对象转换为控件，也可以使模板基于现有控件。  
  
 若要将任何对象转换为控件模板，请选择对象，然后在“工具”菜单上，选择“构成控件”。  
  
 如果想要使模板基于现有控件，请选择美工板上的对象。  然后，在美工板顶部，选择痕迹导航按钮，选择“编辑模板”，然后选择“编辑副本”或“创建空白项”。  
  
 若要创建样式，请选择对象，在“对象”菜单上选择“编辑样式”，然后“编辑副本”或“创建空白项”。  
  
-   选择“编辑副本”可从控件的默认样式或模板开始。  
  
-   选择“创建空白项”可从头开始。  
  
 仅当编辑已创建的样式或模板时，“编辑当前形状”选项才会出现。  对于仍在使用默认系统模板的控件，它不会出现。  
  
 在“创建样式资源”对话框中，可以命名样式或模板以便可以在以后使用它，也可以将样式或模板应用于该类型的所有控件。  
  
> [!NOTE]
>  不能为控件的每种类型都创建样式或模板。  如果控件不支持它们，则痕迹导航按钮不会出现在美工板上方。  
>   
>  若要返回主文档的编辑范围，请单击“返回范围”![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b")。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [创建样式](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95)。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [在 Expression Blend 中创建控件模板](http://msdn.microsoft.com/en-us/expression/cc263912.aspx)。  
  
### 将样式或模板应用于控件  
 在[对象和时间线](http://msdn.microsoft.com/zh-cn/135a5a5e-ec6d-4f38-8827-60e284cd5f57)面板中右键单击某个对象，选择“编辑模板”，然后选择“应用资源”。  
  
### 还原控件的默认样式或模板  
 选择控件，在[属性](http://msdn.microsoft.com/zh-cn/135a5a5e-ec6d-4f38-8827-60e284cd5f57)面板中，找到“样式”或“模板”属性。  然后，单击“高级选项”![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb")，然后在快捷菜单上单击“重置”。  
  
##  <a name="Visual"></a> 可视状态：基于其状态更改控件的外观  
 控件可以基于用户交互而具有不同的视觉外观。  例如，可以在用户单击时使按钮变为绿色，也可以运行动画。  可使用过渡缩短或延长可视状态之间的时间。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [管理你的 WPF 控件的状态](https://www.youtube.com/watch?v=m0PlkF5i6uw)。  
  
##  <a name="Resources"></a> 资源：创建颜色、样式和模板，并在以后重复使用它们  
 可以将项目中的几乎所有对象转换为资源。  资源只是可以在应用程序中的不同位置重复使用的对象。  例如，可以一次性创建一种颜色，使它成为资源，然后在多个对象上使用该颜色。  若要更改所有这些对象的颜色，只需更改该颜色资源。  
  
 **观看简短视频：** ![配置已安装功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [对资源的简要了解](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources)。  
  
## 请参阅  
 [使用 Blend for Visual Studio 创建 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)