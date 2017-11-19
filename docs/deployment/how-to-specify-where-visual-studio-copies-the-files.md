---
title: "如何： 指定 Visual Studio 将文件复制到其中的内容 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e1bfe41d34c1c507818f7bb255425d31dc2f343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>如何：指定 Visual Studio 复制文件的位置
使用 ClickOnce 发布应用程序时，“`Publish Location`”属性指定放置应用程序文件和清单的位置。 这可以是文件路径或 FTP 服务器的路径。  
  
 你可以指定`Publish Location`属性**发布**页**项目设计器**，或通过使用发布向导。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
> [!NOTE]
>  当使用 ClickOnce 安装多个版本的应用程序时，安装会将应用程序的早期版本移动到位于你指定的发布位置的名为“Archive”的文件夹中。 按照这种方式对早期版本进行存档，可以使安装目录与早期版本所在的文件夹分开。  
  
### <a name="to-specify-a-publishing-location"></a>指定发布位置  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在**发布位置**字段中，通过使用以下格式之一输入发布位置：  
  
    -   若要发布到文件共享或磁盘路径，请输入路径使用 UNC 路径 (\\\Server\ApplicationName) 或文件路径 (C:\Deploy\ApplicationName)。  
  
    -   若要发布到 FTP 服务器，请使用格式 ftp://ftp.microsoft.com/ApplicationName 输入路径。  
  
     请注意，必须存在于文本**发布位置**框中才能浏览 (**...**) 按钮正常工作。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)