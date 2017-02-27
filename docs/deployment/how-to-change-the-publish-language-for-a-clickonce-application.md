---
title: "如何：更改 ClickOnce 应用程序的发布语言 | Microsoft Docs"
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
  - "ClickOnce 部署, 更改发布语言"
  - "“发布语言”属性"
  - "发布, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：更改 ClickOnce 应用程序的发布语言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，在安装过程中显示的用户界面默认为开发计算机的语言和区域性。  如果您要发布经过本地化的应用程序，则需要指定语言和区域设置以与本地化版本相匹配。  这由项目的 `Publish language` 属性确定。  
  
 在**“发布选项”**对话框（可从**“项目设计器”**的**“发布”**页访问）中可以设置 `Publish language` 属性。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 更改发布语言  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  单击**“选项”**按钮打开**“发布选项”**对话框。  
  
4.  单击**“说明”**。  
  
5.  在**“发布选项”**对话框中，从**“发布语言”**下拉列表中选择语言和区域性，然后单击**“确定”**。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)