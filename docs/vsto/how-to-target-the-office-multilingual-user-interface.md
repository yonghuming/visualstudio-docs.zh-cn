---
title: "如何：面向 Office 多语言用户界面 | Microsoft Docs"
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
  - "全球化 [Visual Studio 中的 Office 开发], 用户界面目标"
  - "本地化 [Visual Studio 中的 Office 开发], 用户界面目标"
  - "MUI [Visual Studio 中的 Office 开发]"
  - "多语言用户界面 [Visual Studio 中的 Office 开发]"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 全球化"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 本地化"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：面向 Office 多语言用户界面
  多语言用户界面 \(MUI\) 是 Microsoft Office 的一项功能，它使最终用户可以更改用户界面 \(UI\) 的语言。  例如，一位使用英文 UI 的最终用户可以将 UI 的语言更改为西班牙文。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果使用多语言 Office 的用户将使用您的应用程序，您可以添加代码以自动更改 UI 字符串的语言，使之与用户计算机上的 Office 所使用的语言相匹配（如果该用户已安装了正确的资源）。  
  
### 检查当前 Office 用户界面设置  
  
1.  使用当前线程的 <xref:System.Threading.Thread.CurrentUICulture%2A> 属性。  设置 UI 字符串的语言，以与用户计算机上当前所运行 Office 版本使用的语言相匹配。  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## 请参阅  
 [如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)  
  
  