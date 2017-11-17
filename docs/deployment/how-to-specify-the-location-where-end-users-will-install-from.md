---
title: "如何： 指定最终用户将从安装位置 |Microsoft 文档"
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
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 41a601febff80b002512a3783d8405dc42e5d766
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>如何：指定最终用户将从中进行安装的位置
发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，用户可以下载和安装应用程序的位置不一定是最初在其中发布应用程序的位置。 例如，在某些组织开发人员可能应用程序发布到临时服务器，然后管理员将移动到 Web 服务器应用程序。  
  
 在这种情况下，你可以使用`Installation URL`属性来指定用户将转至以下载应用程序的 Web 服务器。 这是必需的因此，应用程序清单知道在何处查找更新。  
  
 `Installation URL`属性可以设置上**发布**页**项目设计器**。  
  
 **请注意**`Installation URL`还可以使用设置属性**PublishWizard**。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-specify-an-installation-url"></a>若要指定安装 URL  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在安装 URL 字段中，输入使用完全限定的 URL 使用格式 http://www.microsoft.com/ApplicationName 或使用格式的 UNC 路径的安装位置\\\Server\ApplicationName。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 指定 Visual Studio 将文件复制到其中的内容](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)