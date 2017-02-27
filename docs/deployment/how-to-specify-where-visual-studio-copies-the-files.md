---
title: "如何：指定 Visual Studio 复制文件的位置 | Microsoft Docs"
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
  - "“发布位置”属性"
  - "发布, 指定位置"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：指定 Visual Studio 复制文件的位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 ClickOnce 发布应用程序时，“`Publish Location`”属性指定放置应用程序文件和清单的位置。  这可以是文件路径或 FTP 服务器的路径。  
  
 可以在`Publish Location`“项目设计器”的**“发布”**页上或使用发布向导指定“**”属性。** 有关详细信息，请参阅[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
> [!NOTE]
>  当使用 ClickOnce 安装多个版本的应用程序时，安装会将应用程序的早期版本移动到位于你指定的发布位置的名为“Archive”的文件夹中。  按照这种方式对早期版本进行存档，可以使安装目录与早期版本所在的文件夹分开。  
  
### 指定发布位置  
  
1.  在**“解决方案资源管理器”**中选择了项目的情况下，在**“项目”**菜单上单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  在**“发布位置”**字段中，使用以下格式之一输入发布位置：  
  
    -   若要发布到文件共享或磁盘路径，请使用 UNC 路径 \(\\\\Server\\ApplicationName\) 或文件路径 \(C:\\Deploy\\ApplicationName\) 输入路径。  
  
    -   若要发布到 FTP 服务器，请使用格式 ftp:\/\/ftp.microsoft.com\/ApplicationName 输入路径。  
  
     请注意，**“发布位置”**框中必须存在文本才能使“浏览”（**“...”**）按钮正常工作。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)