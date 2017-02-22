---
title: "如何：指定 ClickOnce 应用程序的发布页 | Microsoft Docs"
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
  - "ClickOnce 部署, 指定发布页"
  - "部署应用程序 [ClickOnce], 指定发布页"
  - "“发布页”属性"
  - "发布, ClickOnce"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：指定 ClickOnce 应用程序的发布页
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，会生成默认网页 \(publish.htm\) 并与应用程序一起发布。  此页包含应用程序的名称、用来安装应用程序和\/或所有系统必备的链接以及到介绍 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的帮助主题的链接。  使用项目的**“发布页”**属性可以指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的网页名称。  
  
 发布页一旦指定，即会在下次发布时复制到发布位置；再次发布时，它也不会被覆盖。  如果希望自定义该页的外观，则完全可以这样做而不必担心丢失所做的更改。  有关更多信息，请参见[如何：自定义 ClickOnce 的默认网页](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。  
  
 **“发布页”**属性可以在**“发布选项”**对话框中设置，该对话框可从**“项目设计器”**的**“发布”**窗格中访问。  
  
### 指定 ClickOnce 应用程序的自定义网页  
  
1.  当**“解决方案资源管理器”**中有项目选中时，在**“项目”**菜单上，单击**“属性”**。  
  
2.  选择**“发布”**窗格。  
  
3.  单击**“选项”**按钮打开**“发布选项”**对话框。  
  
4.  单击**“部署”**。  
  
5.  在**“发布选项”**对话框中，确保选中**“发布后打开部署网页”**复选框（默认应选中）。  
  
6.  在**“部署网页:”**框中输入网页的名称，然后单击**“确定”**。  
  
### 防止每次发布时启动发布页  
  
1.  当**“解决方案资源管理器”**中有项目选中时，在**“项目”**菜单上，单击**“属性”**。  
  
2.  选择**“发布”**窗格。  
  
3.  单击**“选项”**按钮打开**“发布选项”**对话框。  
  
4.  单击**“部署”**。  
  
5.  在**“发布选项”**对话框中清除**“发布后打开部署网页”**复选框。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [如何：自定义 ClickOnce 的默认网页](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)