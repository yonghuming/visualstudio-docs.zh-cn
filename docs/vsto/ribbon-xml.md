---
title: "功能区 XML"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.Ribbon.RibbonXMLItem"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "自定义功能区，XML"
  - "自定义功能区，XML"
  - "功能区 [Visual Studio 中的 Office 开发]，XML"
  - "回调方法"
  - "自定义功能区，显示"
  - "自定义功能区，定义行为"
  - "XML [Visual Studio 中的 Office 开发]，功能区"
  - "自定义功能区，定义行为"
  - "功能区 [Visual Studio 中的 Office 开发]，自定义"
  - "自定义功能区，显示"
ms.assetid: a5945667-40e8-4191-9f1e-71c18ec30a2e
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 功能区 XML
  功能区 \(XML\) 项使你能够通过使用 XML 来自定义功能区。 如果想要通过功能区（可视化设计器）项不支持的方式自定义功能区，请使用功能区 \(XML\) 项。 有关每个项的用途的比较，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## 向项目添加功能区 \(XML\) 项  
 在**“添加新项”**对话框中，可将**“功能区 \(XML\)”**项添加到任何 Office 项目。 Visual Studio 自动将以下文件添加到项目：  
  
-   功能区 XML 文件。 此文件定义功能区用户界面 \(UI\)。 使用此文件添加 UI 元素，例如选项卡、组和控件。 有关详细信息，请参阅本主题稍后将介绍的[功能区 XML 文件引用](#RibbonDescriptorFile)。  
  
-   功能区代码文件。 此文件包含*功能区类*。 此类的名称即你在**“添加新项”**对话框中为**“功能区 \(XML\)”**项指定的名称。 Microsoft Office 应用程序使用此类的实例来加载自定义功能区。 有关详细信息，请参阅本主题稍后将介绍的[功能区类引用](#RibbonExtensionClass)。  
  
 默认情况下，这些文件将向功能区中的**“外接程序”**选项卡添加自定义组。  
  
## 在 Microsoft Office 应用程序中显示自定义功能区  
 将**“功能区 \(XML\)”**项添加到项目后，必须将代码添加到**“ThisAddin”**、**“ThisWorkbook”**或**“ThisDocument”**类，这些类替代 CreateRibbonExtensibilityObject 方法并将功能区 XML 类返回到 Office 应用程序。  
  
 下面的代码示例替代 CreateRibbonExtensibilityObject 方法并返回名为 MyRibbon 的功能区 XML 类。  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
## 定义自定义功能区的行为  
 通过创建*回叫方法*可响应用户操作（例如单击功能区上的按钮）。 回叫方法类似于 Windows 窗体控件中的事件，但它们由 UI 元素的 XML 中的特性标识。 可在功能区类中编写方法，并且控件调用名称与特性值相同的方法。 例如，可创建用户单击功能区上的某个按钮时调用的回叫方法。 创建回叫方法需要两个步骤：  
  
-   将特性分配给功能区 XML 文件中的控件，该文件标识代码中的回叫方法。  
  
-   定义功能区类中的回叫方法。  
  
> [!NOTE]  
>  Outlook 还需要一个额外的步骤。 有关详细信息，请参阅[自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
 有关演示如何从功能区实现应用程序自动化的演练，请参阅[演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)。  
  
### 将回叫方法分配给控件  
 若要将回叫方法分配给功能区 XML 文件中的控件，添加指定回叫方法类型和方法名称的特性。 例如，下面的元素定义具有名为 `OnToggleButton1` 的 **onAction** 回叫方法的切换按钮。  
  
```  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 用户执行与特定控件关联的主要任务时调用 **onAction**。 例如，用户单击切换按钮时调用该按钮的 **onAction** 回叫方法。  
  
 在特性中指定的方法可具有任何名称。 但该名称必须与在功能区代码文件中定义的方法的名称相匹配。  
  
 有许多不同类型的回叫方法可分配给功能区控件。 有关每个控件的可用回叫方法的完整列表，请参阅技术文章[为开发人员自定义 Office \(2007\) 功能区用户界面（第 3 部分，共 3 部分）](http://msdn.microsoft.com/zh-cn/a16c7df5-93f3-4920-baa8-7b7290794c15)。  
  
###  <a name="CallBackMethods"></a> 定义回叫方法  
 定义功能区代码文件中功能区类中的回叫方法。 回叫方法具有以下几个要求：  
  
-   它必须声明为公共。  
  
-   其名称必须匹配分配给功能区 XML 文件中控件的回叫方法的名称。  
  
-   其签名必须与可用于关联功能区控件的某类回叫方法匹配。  
  
 有关功能区控件的回叫方法签名的完整列表，请参阅技术文章[为开发人员自定义 Office \(2007\) 功能区用户界面（第 3 部分，共 3 部分）](http://msdn.microsoft.com/zh-cn/a16c7df5-93f3-4920-baa8-7b7290794c15)。 Visual Studio 不对在功能区代码文件中创建的回叫方法提供 IntelliSense 支持。 如果创建的回叫方法与有效签名不匹配，代码虽然能够编译，但当用户单击控件时不会执行任何操作。  
  
 所有回叫方法都有表示调用了方法的控件的 <xref:Microsoft.Office.Core.IRibbonControl> 参数。 可使用此参数重用多个控件的相同回叫方法。 下面的代码示例演示根据用户单击的控件执行不同任务的 **onAction** 回叫方法。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> 功能区 XML 文件引用  
 可通过将元素和特性添加到功能区 XML 文件来定义自定义功能区。 默认情况下，功能区 XML 文件包含以下 XML。  
  
```  
<?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad"> <ribbon> <tabs> <tab idMso="TabAddIns"> <group id="MyGroup" label="My Group"> </group> </tab> </tabs> </ribbon> </customUI>  
```  
  
 下表介绍功能区 XML 文件中的默认元素。  
  
|元素|描述|  
|--------|--------|  
|**customUI**|表示 VSTO 外接程序项目中的自定义功能区。|  
|**ribbon**|表示功能区。|  
|**tabs**|表示一组功能区选项卡。|  
|**tab**|表示单个功能区选项卡。|  
|**group**|表示功能区选项卡上的一组控件。|  
  
 这些元素具有指定自定义功能区外观和行为的特性。 下表介绍功能区 XML 文件中的默认特性。  
  
|特性|父元素|说明|  
|--------|---------|--------|  
|**onLoad**|**customUI**|标识应用程序加载功能区时调用的方法。|  
|**idMso**|**tab**|标识要显示在功能区中的内置选项卡。|  
|**id**|**group**|标识组。|  
|**label**|**group**|指定在组上显示的文本。|  
  
 功能区 XML 文件中的默认元素和特性是可用元素和特性一小部分。 有关可用元素和特性的完整列表，请参阅技术文章[为开发人员自定义 Office \(2007\) 功能区用户界面（第 2 部分，共 3 部分）](http://msdn.microsoft.com/zh-cn/6b904f55-525f-4520-9b81-a017db65657b)。  
  
##  <a name="RibbonExtensionClass"></a> 功能区类引用  
 Visual Studio 在功能区代码文件中生成功能区类。 将功能区上控件的回叫方法添加到此类。 此类实现 <xref:Microsoft.Office.Core.IRibbonExtensibility> 接口。  
  
 下表介绍此类中的默认方法。  
  
|方法|描述|  
|--------|--------|  
|`GetCustomUI`|返回功能区 XML 文件的内容。 Microsoft Office 应用程序调用此方法，以便获得一个定义自定义功能区用户界面的 XML 字符串。 此方法实现 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法。 **Note:**  应只为返回功能区 XML 文件的内容而实现 `GetCustomUI`；它不应用于初始化 VSTO 外接程序。 特别是，不应在 `GetCustomUI` 实现中尝试显示对话框或其他窗口。 否则，自定义功能区可能无法正确工作。 如果必须运行初始化 VSTO 外接程序的代码，请将代码添加到 `ThisAddIn_Startup` 事件处理程序。|  
|`OnLoad`|将 <xref:Microsoft.Office.Core.IRibbonControl> 参数分配给 `ribbon` 字段。 当 Microsoft Office 应用程序加载自定义功能区时，它们将调用此方法。 此字段可用于动态更新自定义功能区。 有关详细信息，请参阅技术文章[为开发人员自定义 Office \(2007\) 功能区用户界面（第 1 部分，共 3 部分）](http://msdn.microsoft.com/zh-cn/a4fd6d18-d4a8-4e64-bd89-f437208573d3)。|  
|`GetResourceText`|由 `GetCustomUI` 方法调用，以获取功能区 XML 文件的内容。|  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)  
  
  