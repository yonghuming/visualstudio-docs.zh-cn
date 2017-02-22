---
title: "如何：指定最终用户将从中进行安装的位置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "部署应用程序 [ClickOnce], 指定安装 URL"
  - "“安装 URL”属性"
  - "安装, 指定安装 URL"
  - "URL, 指定安装 URL"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：指定最终用户将从中进行安装的位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，用户下载和安装应用程序的位置不必是最初发布该应用程序的位置。  例如，在某些组织中，开发人员可能将应用程序发布到测试服务器，然后管理员将该应用程序移动到 Web 服务器。  
  
 在这种情况下，可以使用 `Installation URL` 属性指定用户下载该应用程序的 Web 服务器。  只有这样，应用程序清单才会知道到何处查找更新。  
  
 `Installation URL` 属性可在**“项目设计器”**的**“发布”**页中设置。  
  
 **注意** `Installation URL` 属性还可使用**“发布”**向导进行设置。  有关更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
### 指定安装 URL  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  在“安装 URL”字段中，使用完全限定 URL（格式为 http:\/\/www.microsoft.com\/ApplicationName）或 UNC 路径（格式为 \\\\Server\\ApplicationName）输入安装位置。  
  
## 请参阅  
 [如何：指定 Visual Studio 复制文件的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)