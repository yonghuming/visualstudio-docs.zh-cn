---
title: "项目解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 584f98e9fbe6a8883039cad03e6b0782d225b8bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-solutions"></a>项目解决方案
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 提供可用于创建 Microsoft Office Project 的 VSTO 外接程序的项目模板。 VSTO 外接程序可用于自动运行项目、扩展项目功能或自定义项目用户界面 (UI)。  
  
 有关 VSTO 外接程序的详细信息，请参阅 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 和 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。如果你不熟悉如何使用 Microsoft Office 编程，请参阅[入门 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
## <a name="automating-project-by-using-the-project-object-model"></a>使用项目对象模型实现项目自动化  
 项目对象模型公开了许多可用于实现项目自动化的类型。 可使用这些类型编写代码来完成常规任务，例如以编程方式创建和修改项目中的任务。  
  
 若要从 VSTO 外接程序访问项目对象模型，请使用项目中 `Application` 类的 `ThisAddIn` 字段。 `Application`字段会返回一个表示项目的当前实例的 Microsoft.Office.Interop.MsProject.Application 对象。 有关更多信息，请参见 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 调入项目对象模型时，将使用项目的主互操作程序集中提供的类型。 该主互操作程序集将作为 VSTO 外接程序中的托管代码和项目中的 COM 对象模型之间的桥梁。 项目主互操作程序集中的所有类型 Microsoft.Office.Interop.MSProject 命名空间中都定义。 有关主互操作程序集的详细信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="using-the-project-object-model-documentation"></a>使用项目对象模型文档  
 有关项目对象模型的完整信息，可以参考项目 VBA 对象模型引用。 VBA 对象模型引用在项目对象模型被公开到 Visual Basic for Applications (VBA) 代码时记录该对象模型。 有关详细信息，请参阅 [Project 2010 对象模型引用](http://go.microsoft.com/fwlink/?LinkId=199771)。  
  
 VBA 对象模型引用中的所有对象和成员都对应于项目主互操作程序集 (PIA) 中的类型和成员。 例如，VBA 对象模型引用中的日历对象对应于项目 PIA 中的 Microsoft.Office.Interop.MSProject.Calendar 类型。 虽然 VBA 对象模型引用提供大多数属性、方法和事件的代码示例，但如果想要将其用于使用 Visual Studio 创建的 Project VSTO 外接程序项目，则必须将本引用中的 VBA 代码转换成 Visual Basic 或 Visual C#。  
  
> [!NOTE]  
>  此时，没有任何项目主互操作程序集的参考文档。  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>项目主互操作程序集中的基础结构类型  
 编写使用项目 PIA 的代码时，您可能会注意到许多类型在 VBA 参考中都未涉及。 这些附加类型可以帮助将项目的基于 COM 的对象模型中的对象转换为托管代码，而不是在代码中直接使用。  
  
 有关详细信息，请参阅[Office 主互操作程序集中的类和接口概述](http://go.microsoft.com/fwlink/?LinkId=189592)。  
  
## <a name="customizing-the-user-interface-of-project"></a>自定义项目的用户界面  
 可以通过下列方式来自定义项目 UI：  
  
|任务|更多相关信息|  
|----------|--------------------------|  
|向项目的功能区添加自定义选项卡|[功能区概述](../vsto/ribbon-overview.md)|  
  
 有关自定义项目 UI 和其他 Microsoft Office 应用程序的详细信息，请参阅[Office UI 自定义项](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 创建第一个 VSTO 外接程序项目](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自定义项](../vsto/office-ui-customization.md)   
 [Project 2010 和 Project Server 2010 中的 Office 开发](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  