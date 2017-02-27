---
title: "如何：自定义 ClickOnce 应用程序的默认网页 | Microsoft Docs"
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
  - "Publish.htm 网页"
  - "ClickOnce 部署默认网页"
  - "部署应用程序 [ClickOnce], 发布"
  - "发布, ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：自定义 ClickOnce 应用程序的默认网页
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将 ClickOnce 应用程序发布到 Web 时，会自动生成一个网页与应用程序一起发布。  默认页包含应用程序的名称，还包含安装应用程序，安装系统必备或访问 MSDN 上的帮助的链接。  
  
> [!NOTE]
>  该页上的实际链接取决于查看该页的计算机以及要包括的系统必备。  
  
 网页的默认名称为 Publish.htm；可以在**“项目设计器”**中更改该名称。  有关更多信息，请参见[如何：指定 ClickOnce 应用程序的发布页](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。  
  
 仅当检测到较新版本时才会发布 Publish.htm 网页。  
  
> [!NOTE]
>  对**“发布”**设置的更改不会影响 Publish.htm 页，只有一种情况例外：如果在最初发布后添加或移除系统必备，系统必备列表将不再准确。  需要编辑系统必备链接的文本才能反映这些更改。  
  
### 自定义发布网页  
  
1.  将 ClickOnce 应用程序发布到 Web 位置。  有关更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
2.  在 Web 服务器上，使用 Visual Web Designer 或其他 HTML 编辑器打开 Publish.htm 文件。  
  
3.  按照需要自定义该页并进行保存。  
  
4.  可选。  若要阻止 Visual Studio 覆盖自定义发布网页，请取消选中“发布选项”对话框中的**“每次发布后都自动生成部署网页”**。  
  
## 请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：与 ClickOnce 应用程序一起安装系统必备组件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [如何：指定 ClickOnce 应用程序的发布页](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)