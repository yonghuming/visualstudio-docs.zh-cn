---
title: "如何： 面向 Office 多语言用户界面 |Microsoft 文档"
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
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ee88cbcde2a25a13b4c4432afe5a5b1397ab727
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>如何：面向 Office 多语言用户界面
  多语言用户界面 (MUI) 是使最终用户能够更改用户界面 (UI) 的语言的 Microsoft Office 功能。 例如，最终用户使用英语 UI 可以为西班牙语更改 UI 的语言。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果你的应用程序将由使用 Office 的多个语言人员，你可以添加代码以自动更改 UI 字符串以匹配 Office 所使用的用户的计算机上 （如果该用户已安装了正确的资源） 的语言的语言。  
  
### <a name="to-check-the-current-office-ui-setting"></a>若要检查的当前 Office 用户界面设置  
  
1.  使用<xref:System.Threading.Thread.CurrentUICulture%2A>当前线程的属性。 将 UI 字符串以匹配正在使用的当前用户的计算机上运行的 Office 版本的语言的语言设置。  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>另请参阅  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office 解决方案中的晚期绑定](../vsto/late-binding-in-office-solutions.md)  
  
  