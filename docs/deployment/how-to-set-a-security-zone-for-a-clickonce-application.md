---
title: "如何：为 ClickOnce 应用程序设置安全区域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "ClickOnce 部署, 安全性设置"
  - "代码访问安全, ClickOnce 应用程序"
  - "安全区域, ClickOnce 应用程序"
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：为 ClickOnce 应用程序设置安全区域
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

为 ClickOnce 应用程序设置代码访问安全权限时，需要在“项目设计器”的“安全”页上从基本权限集开始。  
  
 在大多数情况下，还可以选择包含受限权限集的“Internet”区域，或选择包含较大权限集的“本地 Intranet”区域。 如果应用程序需要自定义权限，则可以通过选择“自定义”安全区域实现该操作。 有关设置自定义权限的详细信息，请参阅 [如何：设置 ClickOnce 应用程序的自定义权限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)。  
  
### 设置安全区域  
  
1.  在“解决方案资源管理器”中选择一个项目，然后在“项目”菜单上单击“属性”。  
  
2.  单击**“安全”**选项卡。  
  
3.  选中“启用 ClickOnce 安全设置”复选框。  
  
4.  选择“这是部分可信的应用程序”选项按钮。  
  
     “ClickOnce 安全权限”部分中的控件已启用。  
  
5.  在“将要从中安装应用程序的区域”下拉列表中，选择一个安全区域。  
  
## 请参阅  
 [如何：设置 ClickOnce 应用程序的自定义权限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)