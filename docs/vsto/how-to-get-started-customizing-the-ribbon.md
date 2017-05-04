---
title: "如何：开始自定义功能区 | Microsoft Docs"
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
  - "自定义功能区, 向项目添加功能区"
  - "自定义功能区, 向项目添加功能区"
  - "功能区 [Visual Studio 中的 Office 开发], 添加"
  - "功能区 [Visual Studio 中的 Office 开发], 自定义"
ms.assetid: 9eb6b8b3-1842-4cb3-8229-273ce35c64fb
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：开始自定义功能区
  若要自定义 Microsoft Office 应用程序的功能区，请将一个**“功能区\(可视化设计器\)”**或**“功能区\(XML\)”**项添加到 Office 项目中。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 将功能区添加到项目中  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
2.  在**“添加新项”**对话框中，选择**“功能区\(可视化设计器\)”**或**“功能区\(XML\)”**。  有关这些模板的更多信息，请参见[功能区概述](../vsto/ribbon-overview.md)。  
  
3.  在**“名称”**框中键入功能区项的名称。  
  
     名称不能包含下列字符：  
  
    -   井号 \(\#\)  
  
    -   百分号 \(%\)  
  
    -   “and”符 \(&\)  
  
    -   星号 \(\*\)  
  
    -   竖线 \(|\)  
  
    -   反斜杠 \(\\\)  
  
    -   冒号 \(:\)  
  
    -   双引号 \("\)  
  
    -   小于号 \(\<\)  
  
    -   大于号 \(\>\)  
  
    -   问号 \(?\)  
  
    -   正斜杠 \(\/\)  
  
    -   前导或尾随空格 \(' '\)  
  
    -   为 Windows 或 DOS 保留的名称（如“nul”、“aux”、“con”、“com1”、“lpt1”等）  
  
4.  单击**“确定”**。  
  
 功能区项出现在**“解决方案资源管理器”**中。  有关后续步骤的信息，请参见[功能区概述](../vsto/ribbon-overview.md)。  
  
## 请参阅  
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  