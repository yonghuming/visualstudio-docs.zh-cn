---
title: "PowerPoint 解决方案"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office 解决方案 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "模板 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "解决方案 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "项目 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "PowerPoint [Visual Studio 中的 Office 开发]"
  - "Office 项目 [Visual Studio 中的 Office 开发]，PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# PowerPoint 解决方案
  Visual Studio 提供可用于创建 Microsoft Office PowerPoint 的 VSTO 外接程序的项目模板。 可使用 VSTO 外接程序自动化 PowerPoint、扩展 PowerPoint 功能或自定义 PowerPoint 用户界面 \(UI\)。  
  
 有关 VSTO 外接程序的详细信息，请参阅 [VSTO 外接程序编程入门](../vsto/getting-started-programming-vsto-add-ins.md)和 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)。 如果你不熟悉如何使用 Microsoft Office 编程，请参阅 [入门（Visual Studio 中的 Office 开发）](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 有关相关的视频演示，请参阅[如何：为 Microsoft PowerPoint 创建外接程序？](http://go.microsoft.com/fwlink/?LinkId=132767)。  
  
## 使用 PowerPoint 对象模型自动化 PowerPoint  
 PowerPoint 对象模型公开了许多你能用于自动化 PowerPoint 的模型。 这些类型使你能够编写代码来完成常规任务：  
  
-   以编程方式创建演示文稿并设置其格式。  
  
-   从演示文稿添加或删除幻灯片。  
  
-   添加或更改幻灯片上的形状。  
  
 若要从 VSTO 外接程序访问 PowerPoint 对象模型，请使用项目中 `ThisAddIn` 类的 `Application` 字段。`Application` 字段返回 <xref:Microsoft.Office.Interop.PowerPoint.Application> 对象，该对象表示 PowerPoint 的当前实例。 有关更多信息，请参见[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  
  
 调入 PowerPoint 对象模型时，将使用 PowerPoint 的主互操作程序集中提供的类型。 该主互操作程序集充当 VSTO 外接程序中的托管代码与 PowerPoint 中的 COM 对象模型之间的桥梁。 PowerPoint 主互操作程序集中的所有类型都在 <xref:Microsoft.Office.Interop.PowerPoint> 命名空间中定义。 有关主互操作程序集的详细信息，请参阅 [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 和 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)。  
  
##  <a name="WordOMDocumentation"></a> 使用 PowerPoint 对象模型文档  
 有关 PowerPoint 对象模型的完整信息，可以参考 PowerPoint 主互操作程序集 \(PIA\) 引用和 VBA 对象模型引用。  
  
### 主互操作程序集引用  
 PowerPoint PIA 参考文档描述了 PowerPoint 的主互操作程序集中的类型。 本文档可从以下位置获取：[PowerPoint 2010 主互操作程序集引用](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
 有关 PowerPoint PIA 设计的详细信息（例如 PIA 中类和接口之间的差别以及 PIA 中事件的实现方式），请参阅 [Office 主互操作程序集中的类和接口的概述](http://go.microsoft.com/fwlink/?LinkId=199885)。  
  
### VBA 对象模型引用  
 VBA 对象模型引用在 PowerPoint 对象模型被公开到 Visual Basic for Applications \(VBA\) 代码时记录该对象模型。 有关详细信息，请参阅 [PowerPoint 2010 对象模型引用](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 VBA 对象模型引用中的所有对象和成员都对应于 PowerPoint 主互操作程序集 \(PIA\) 中的类型和成员。 例如，VBA 对象模型引用中的 Presentation 对象都对应于 PowerPoint PIA 中的 <xref:Microsoft.Office.Interop.PowerPoint.Presentation> 类型。 虽然 VBA 对象模型引用提供大多数属性、方法和事件的代码示例，但如果你想要在使用 Visual Studio 创建的 PowerPoint VSTO 外接程序项目中使用它们，则必须将本引用中的 VBA 代码转换成 Visual Basic 或 Visual C\#。  
  
## 自定义 PowerPoint 的用户界面  
 你可以通过以下方式修改 PowerPoint 的 UI。  
  
|任务|更多相关信息|  
|--------|------------|  
|创建自定义任务窗格。|[自定义任务窗格](../vsto/custom-task-panes.md)|  
|向功能区添加自定义选项卡。|[功能区概述](../vsto/ribbon-overview.md)|  
|向功能区上的内置选项卡添加自定义组。|[如何：自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 有关自定义 PowerPoint 和其他 Microsoft Office 应用程序的 UI 的详细信息，请参阅 [Office UI 自定义](../vsto/office-ui-customization.md)。  
  
## 请参阅  
 [演练：创建你的第一个 PowerPoint VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [VSTO 外接程序编程入门](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [Office 开发中的 PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  