---
title: "如何：为 Office 解决方案设置配置信息 | Microsoft Docs"
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
  - "配置文件 [Visual Studio 中的 Office 开发]"
  - "解决方案 [Visual Studio 中的 Office 开发], 配置文件"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 如何：为 Office 解决方案设置配置信息
  可以使用配置文件来配置特定于 Office 解决方案的设置。  您可以指定诸如程序集绑定策略、远程控制对象、调试和跟踪设置之类的设置。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 向您的 Office 项目添加配置文件  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
2.  在**“类别”**窗格中单击**“常规”**。  
  
3.  在**“模板”**窗格中选择**“应用程序配置文件”**。  
  
4.  在**“名称”**框中，键入程序集的名称并加上扩展名 .config。  例如，名为 ExcelWorkbook1.dll 的 Excel 项目程序集的配置文件会被命名为 ExcelWorkbook1.dll.config。  
  
5.  单击**“添加”**。  
  
6.  根据应用程序配置文件架构来创建配置文件。  有关更多信息，请参见[.NET Framework 的配置文件架构](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)。  
  
 对 Office 项目使用配置文件没有特殊的注意事项。  
  
## 请参阅  
 [.NET Framework 的配置文件架构](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  