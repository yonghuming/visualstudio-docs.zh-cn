---
title: "如何：启用 ClickOnce 安全设置 | Microsoft Docs"
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
  - "ClickOnce 部署, 安全性设置"
  - "安全性 [Visual Studio], ClickOnce 应用程序"
  - "安全性设置, ClickOnce 部署"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：启用 ClickOnce 安全设置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必须启用 ClickOnce 应用程序的代码访问安全性，才能发布应用程序。  如果使用“发布”向导发布应用程序，则会自动完成该启用操作。  
  
 在某些情况下，启用代码访问安全性可能会影响生成或调试应用程序时的性能；在这种情况下，则可能希望暂时禁用安全设置。  
  
 在**“项目设计器”**的**“安全”**页中可以启用或禁用 ClickOnce 安全设置。  
  
### 启用 ClickOnce 安全设置  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“安全”**选项卡。  
  
3.  选择**“启用 ClickOnce 安全设置”**复选框。  
  
     现在即可在“安全”页中自定义应用程序的安全设置。  
  
    > [!NOTE]
    >  每次通过**“发布”**向导发布应用程序时，都会自动选中此框。  
  
### 禁用 ClickOnce 安全设置  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“安全”**选项卡。  
  
3.  清除**“启用 ClickOnce 安全设置”**复选框。  
  
     应用程序将使用完全信任安全设置运行；**“安全”**页中的所有设置都将被忽略。  
  
    > [!NOTE]
    >  每次通过“发布”向导发布应用程序时，都会选中该复选框；每次发布成功后，都必须再次清除该复选框。  
  
## 请参阅  
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)