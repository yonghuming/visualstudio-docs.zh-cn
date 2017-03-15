---
title: "“XAML 设计器”->“选项”| Microsoft Docs"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: 1
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
translationtype: Human Translation
ms.sourcegitcommit: 7c944afe8c89b8a5e30bf1e5937e848e078954ac
ms.openlocfilehash: f4a4832e5659a46b236cdcf9ff2eecdc3cabf57d

---
# <a name="options-xaml-designer"></a>“XAML 设计器”->“选项”
使用“XAML 设计器”属性页可指定如何在 XAML 文档中设置元素和特性的格式。 若要打开“选项”对话框，请选择“工具”菜单，然后选择“选项”。 若要访问“XAML 设计器”属性页，请选择“XAML 设计器”节点。 打开文档时将应用 XAML 设计器的相关设置。 因此，如果对设置进行更改，则需关闭并重新打开 Visual Studio，才能看到更改。

> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  

## <a name="enable-xaml-designer"></a>启用 XAML 设计器
选择此设置后，将启用 XAML 设计器。 XAML 设计器提供一个可视的工作区域，供你编辑 XAML 文档。 Visual Studio 中的某些功能（例如，用于资源和数据绑定的 IntelliSense）需要启用 XAML 设计器。

下列设置仅在启用 XAML 设计器后可用。 如果更改此选项，则需重新启动 Visual Studio，设置才会生效。

## <a name="default-document-view"></a>默认文档视图
使用此设置来控制是否在加载 XAML 文档时显示设计视图。

|||  
|-|-|  
|**源视图**|指定是否仅在 XAML 视图中显示 XAML 源。 加载大型文档时，此设置非常有用。|  
|**设计视图**|指定是否在 XAML 视图中仅显示可视 XAML 设计器。|  
|**拆分视图**|指定可视 XAML 设计器和 XAML 源是否紧邻出现在 XAML 视图中（基于“拆分方向”设置的位置）。|  

## <a name="split-orientation"></a>拆分方向
使用此设置来控制当编辑 XAML 文档时，XAML 设计器何时以及如何显示。 以下设置仅在“默认文档视图”设置为“拆分视图”时可用。

|||  
|-|-|  
|**垂直**|XAML 源显示在 XAML 视图的左侧，XAML 设计器显示在右侧。|  
|**水平**|XAML 设计器显示在 XAML 视图顶部，XAML 源显示在底部。|  
|**默认**|XAML 文档使用为文档的项目所面向的平台推荐的拆分方向。 对于大多数平台，此值等于“水平”。|  

## <a name="zoom-by-using"></a>缩放方式
使用此设置来确定编辑 XAML 文档时缩放的工作方式。

|||  
|-|-|  
|**鼠标滚轮**|通过滚动鼠标滚轮在 XAML 设计器中进行缩放。|  
|**Ctrl + 鼠标滚轮**|按住 Ctrl 键的同时滚动鼠标滚轮，以在 XAML 设计器中进行缩放。|  
|**Alt + 鼠标滚轮**|按住 Alt 键的同时滚动鼠标滚轮，以在 XAML 设计器中进行缩放。|  

以下设置确定编辑 XAML 文档时设计器的行为。

|||  
|-|-|  
|**创建时自动命名交互元素**|指定在向设计器添加新的交互元素时是否为该元素提供一个默认名称。|  
|**创建元素时自动插入布局属性**|指定在向设计器添加新元素时是否为该元素提供布局属性。|  
|**使用基于象限的布局**|指定当前所选控件是否与最近的父容器边缘对齐。 如果清除此复选框，在移动或创建操作期间将不会更改控件对齐方式。|  
|**自动填充工具箱项**|指定当前解决方案中的用户控件和自定义控件是否自动显示在工具箱中。|  

## <a name="settings-blend-only"></a>设置（仅限 Blend）
使用以下选项来确定使用 Blend 编辑 XAML 文件时的设置。

|||  
|-|-|  
|**缩放方式**|滚动鼠标滚轮或者在按住 Ctrl 或 Alt 键的同时滚动鼠标滚轮，以在 XAML 设计器中进行缩放。|  
|**类型单位**|指定设计器上的度量值是基于点还是基于像素。 由于通用 Windows 应用不支持点，因此如果选择“点”，单位会自动转换为像素。|  

## <a name="artboard-blend-only"></a>美工板（仅限 Blend）
使用以下设置来确定在 Blend 中编辑 XAML 文件时 XAML 设计器的行为。

### <a name="snapping"></a>正在对齐

|||  
|-|-|  
|**显示对齐网格**|选中此选项后，设计器中会显示网格线，以帮助用户对齐控件。 选中“网格线对齐”选项后，添加到设计器的控件会与这些网格线对齐。|  
|**网格线对齐**|添加控件或在设计器中来回移动控件时，它们会与网格线对齐。|  
|**网格线间距**|指定网格线之间的间距是以像素还是以点为单位（由“类型单位”设置确定）。|  
|**对齐线对齐**|指定控件是否与对齐线对齐。|  
|**默认边距**|启用“对齐线对齐”后，指定控件与对齐线之间的间距是以像素还是以点为单位（由“类型单位”设置确定）。|  
|**默认填充**|启用“对齐线对齐”后，指定控件和对齐线之间的额外间距是以像素还是以点为单位（由“类型单位”设置确定）。|  

### <a name="animation"></a>动画
使用此设置来确定在 Blend 中启用依赖（非加速）动画时是否显示警告。

### <a name="effects"></a>效果
使用以下设置来确定在 XAML 设计器中使用 Blend 编辑 XAML 文件时是否呈现效果。

|||  
|-|-|  
|**呈现效果**|指定在 XAML 设计器中使用 Blend 编辑 XAML 文件时是否呈现效果。|  
|**缩放阈值**|指定当选中“呈现效果”复选框时所呈现效果的缩放百分比。 如果缩放值超过此设置，则 XAML 设计器不再呈现效果。|  

## <a name="see-also"></a>另请参阅  
 [WPF 中的 XAML](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [如何：更改 XAML 视图设置](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [XAML 和代码演练](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)



<!--HONumber=Feb17_HO4-->


