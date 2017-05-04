---
title: "如何：通过主互操作程序集面向 Office 应用程序 | Microsoft Docs"
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
  - "应用程序开发 [Visual Studio 中的 Office 开发], 自动化"
  - "程序集 [Visual Studio 中的 Office 开发], PIA 引用"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 自动化"
  - "Visual Studio 中的 Office 主互操作程序集, 添加引用"
  - "主互操作程序集 [Visual Studio 中的 Office 开发], 添加引用"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：通过主互操作程序集面向 Office 应用程序
  在创建新的 Office 项目时，Visual Studio 会自动添加对生成该项目所需的 Microsoft Office 主互操作程序集 \(PIA\) 的引用。  在以下方案中，必须添加对其他 PIA 的引用：  
  
-   想要在项目中使用其他 Microsoft Office 应用程序的功能。  例如，你可能想要在 Microsoft Office Word 的项目中使用 Microsoft Office Excel 中的功能。  
  
-   你想要自动化在 Visual Studio 中没有专用项目的 Microsoft Office 应用程序，如 Microsoft Office Access。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 添加对主互操作程序集的引用  
  
1.  打开 Office 项目，并在**“解决方案资源管理器”**中选择项目名称。  
  
2.  在**“项目”**菜单上，单击**“添加引用”**。  
  
3.  在**“框架”**选项卡上，在**“组件名称”**列表中选择所需 PIA。  有关可用的 Microsoft Office 主互操作程序集的详细信息，请参阅 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)。  
  
     在面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的项目中，程序集引用的**“嵌入互操作类型”**属性默认情况下设置为**“True”**。  通过使用此设置，你的解决方案在最终用户计算上不需要 PIA。  有关详细信息，请参阅[设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)。  
  
    > [!NOTE]  
    >  在 Office 项目中，始终使用**“添加引用”**对话框的**“.NET”**选项卡（而不是**“COM”**选项卡）来添加对 Office PIA 的引用。  有关详细信息，请参阅 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)。  
  
4.  单击“确定”。  
  
     程序集名称将显示在**“解决方案资源管理器”**的**“引用”**文件夹中。  
  
## 请参阅  
 [Office 主互操作程序集](../vsto/office-primary-interop-assemblies.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [如何：安装 Office 主互操作程序集](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  