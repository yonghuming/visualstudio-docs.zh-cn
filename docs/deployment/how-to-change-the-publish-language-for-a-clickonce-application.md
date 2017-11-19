---
title: "如何： 更改 ClickOnce 应用程序发布语言 |Microsoft 文档"
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
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1643a3bec79b6f0e1b89548ab1a62c3dfd6c6e9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>如何：更改 ClickOnce 应用程序的发布语言
发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，在安装到的语言和开发计算机的区域性的默认设置过程中显示的用户界面。 如果发布的本地化的应用程序，你将需要指定语言和区域性的本地化的版本匹配。 这由`Publish language`为你的项目的属性。  
  
 `Publish language`属性可以在中设置**发布选项**对话框中，可从访问**发布**页**项目设计器**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-change-the-publish-language"></a>若要更改发布语言  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**选项**按钮以打开**发布选项**对话框。  
  
4.  单击**说明**。  
  
5.  在**发布选项**对话框框中，选择一种语言和区域性从**发布语言**下拉列表，然后单击**确定**。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)