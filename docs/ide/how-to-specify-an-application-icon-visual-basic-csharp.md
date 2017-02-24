---
title: "如何：指定应用程序图标（Visual Basic、C#）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 18
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6889879efe06e8b0541aa08017292a92a736ea50

---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>如何：指定应用程序图标（Visual Basic、C#）
项目的 `Icon` 属性指定将针对已编译应用程序在文件资源管理器和 Windows 任务栏中显示的图标文件 (.ico)。  
  
 `Icon` 属性可以在“项目设计器”的“应用程序”窗格中进行访问；它包含作为资源或内容文件添加到项目中的图标列表。  
  
> [!NOTE]
>  在设置应用程序的图标属性后，你可能还要设置应用程序中每个“窗口”或“窗体”的 `Icon` 属性。 有关 Windows Presentation Foundation (WPF) 独立应用程序的窗口图标的信息，请参阅 <xref:System.Windows.Window.Icon%2A> 属性。  
  
### <a name="to-specify-an-application-icon"></a>如要指定应用程序图标  
  
1.  在“解决方案资源管理器”中，选择项目节点（而非“解决方案”节点）。  
  
2.  在菜单栏上，依次选择“项目”、“属性”。  
  
3.  当“项目设计器”出现时，选择“应用程序”选项卡。  
  
4.  **(Visual Basic)** 在“图标”列表中，选择一个图标 (.ico) 文件。  
  
     **C#** 在“图标”列表附近，选择“\<浏览...>”按钮，然后浏览到所需图标文件的位置。  
  
## <a name="see-also"></a>另请参阅  
 [应用程序页、项目设计器 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [应用程序页、项目设计器 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [管理应用程序属性](../ide/application-properties.md)  
 [如何：添加或删除资源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)


<!--HONumber=Feb17_HO4-->


