---
title: "如何：重新启用已禁用的 VSTO 外接程序"
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
  - "VST.Warning.DisabledAddIn"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "禁用的外接程序"
  - "外接程序 [Visual Studio 中的 Office 开发]，禁用"
  - "外接程序 [Visual Studio 中的 Office 开发]，启用"
ms.assetid: 69719a0a-984c-42cd-80a2-1367c866e5df
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：重新启用已禁用的 VSTO 外接程序
  Microsoft Office 应用程序可禁用行为异常的 VSTO 外接程序。 当你尝试对 VSTO 外接程序进行调试时，如果应用程序不加载它，则此应用程序可能已硬禁用或软禁用此 VSTO 外接程序。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## 硬禁用的 VSTO 外接程序  
 当 VSTO 外接程序导致应用程序意外关闭时，可能发生硬禁用。 如果 VSTO 外接程序中的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序正在执行时停止了调试器，则硬禁用也可能发生在开发计算机上。  
  
#### 若要重新启用 VSTO 外接程序  
  
1.  在应用程序中，单击**“文件”**选项卡。  
  
2.  单击 *ApplicationName***“选项”**按钮。  
  
3.  在类别窗格中，单击**“外接程序”**。  
  
4.  在详细信息窗格中，确保 VSTO 外接程序显示在**“禁用的应用程序外接程序”**列表中。  
  
     **“名称”**列指定程序集的名称，**“位置”**列指定应用程序清单的完整路径。  
  
5.  在**“管理”**框中，单击**“禁用项”**，然后单击**“跳转”**。  
  
6.  选择 VSTO 外接程序并单击**“启用”**。  
  
7.  单击**“关闭”**。  
  
## 软禁用的 VSTO 外接程序  
 当 VSTO 外接程序产生不会导致应用程序意外关闭的错误时，可能会发生软禁用。 例如，如果 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序正在执行时，某个应用程序引发了未处理异常，则此应用程序可能软禁用 VSTO 外接程序。  
  
> [!NOTE]  
>  当重新启用软禁用的 VSTO 外接程序时，应用程序将立即尝试加载该 VSTO 外接程序。 如果最初导致应用程序软禁用 VSTO 外接程序的问题未得到解决，则该应用程序将再次软禁用 VSTO 外接程序。  
  
#### 若要重新启用 VSTO 外接程序  
  
1.  在应用程序中，单击**“文件”**选项卡。  
  
2.  单击 *ApplicationName***“选项”**按钮。  
  
3.  在类别窗格中，单击**“外接程序”**。  
  
4.  在详细信息窗格中，确保 VSTO 外接程序显示在**“非活动应用程序外接程序”**列表中。  
  
     **“名称”**列指定程序集的名称，**“位置”**列指定应用程序清单的完整路径。  
  
5.  在**“管理”**框中，单击**“COM 外接程序”**，然后单击**“跳转”**。  
  
6.  在**“COM 外接程序”**对话框中，选中已禁用 VSTO 外接程序旁的复选框。  
  
7.  单击“确定”。  
  
## 请参阅  
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [调试 Office 项目](../vsto/debugging-office-projects.md)   
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)  
  
  