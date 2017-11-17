---
title: "如何： 指定 ClickOnce 应用程序的开始菜单名称 |Microsoft 文档"
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b27cf6d67cef1098a54277d4857b75d3fba0ff65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>如何：指定 ClickOnce 应用程序的“开始”菜单名称
当[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]用于联机和脱机安装应用程序，条目添加到**启动**菜单和**添加或删除程序**列表。 默认情况下，显示名称是应用程序的程序集的名称相同，但你可以通过设置更改的显示名称**产品名称**中**发布选项**对话框。  
  
 **产品名称**将显示在 publish.htm 页; 上为已安装的脱机应用程序，它将是中的项名称**启动**菜单中，并且也将显示中的名称**添加或删除程序**。  
  
 **发布者名称**将显示上述 publish.htm 页上**产品名称**，对于已安装的脱机应用程序，它也将是包含中的应用程序的图标的文件夹的名称和**启动**菜单。  
  
 你可以设置**产品名称**和**发布者名称**中的属性**发布选项**对话框中，可在上找到**发布**页**项目设计器**。  
  
### <a name="to-specify-a-start-menu-name"></a>若要指定的开始菜单名称  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**选项**按钮以打开**发布选项**对话框。  
  
4.  单击**说明**。  
  
5.  在**发布选项**对话框框中，输入要在中显示的名称**产品名称**。  
  
6.  或者，可以输入发布者名称中的**发布者名称**。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)