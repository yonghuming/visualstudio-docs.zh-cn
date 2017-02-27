---
title: "如何：自动递增 ClickOnce 发布版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 自动递增发布版本"
  - "部署应用程序 [ClickOnce], 自动递增发布版本"
  - "“发布版本”属性, 递增"
  - "发布, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：自动递增 ClickOnce 发布版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，更改 `Publish Version` 属性会使应用程序发布为更新。  默认情况下，每次发布应用程序时，Visual Studio 都会自动递增 `Publish Version` 的 `Revision` 号。  
  
 在**“项目设计器”**的**“发布”**页中可以禁用该行为。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 禁用自动递增发布版本  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  在**“发布版本”**节中，清除**“自动递增每个版本的修订号”**复选框。  
  
## 请参阅  
 [如何：设置 ClickOnce 发布版本](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)