---
title: "如何： 为 ClickOnce 应用程序自定义默认网页 |Microsoft 文档"
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
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fefafa0f9ea04a62d6ae79bd18834e36a1480f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>如何：自定义 ClickOnce 应用程序的默认网页
在发布 ClickOnce 应用程序到 Web，网页上自动生成并随应用程序一起发布。 默认页包含的应用程序和链接，以安装应用程序、 安装系统必备组件，或访问 MSDN 上的帮助的名称。  
  
> [!NOTE]
>  在页看到的实际链接取决于在其中查看页面的计算机和要包括的先决条件。  
  
 网页上的默认名称是 Publish.htm;你可以更改中的名称**项目设计器**。 有关详细信息，请参阅[如何： 为 ClickOnce 应用程序指定发布页](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。  
  
 仅当检测到较新版本时，才会被发布 Publish.htm 网页。  
  
> [!NOTE]
>  对所做的更改你**发布**设置将不会影响 Publish.htm 页中的，有一个例外： 如果添加或删除最初发布后的系统必备组件，系统必备组件的列表将不再准确。 你将需要编辑的先决条件的链接，以反映所做的更改的文本。  
  
### <a name="to-customize-the-publish-web-page"></a>若要自定义发布网页  
  
1.  发布 ClickOnce 应用程序以便对某一 Web 位置。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
2.  在 Web 服务器上，在可视 Web 设计器或另一个 HTML 编辑器中打开 Publish.htm 文件。  
  
3.  自定义为所需的页面，并将其保存。  
  
4.  可选。 若要阻止 Visual Studio 覆盖你自定义的发布 Web 页，取消选中**自动生成部署网页后每个发布**发布选项对话框中。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何： 与 ClickOnce 应用程序一起安装系统必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [如何：指定 ClickOnce 应用程序的发布页](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)