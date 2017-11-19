---
title: "如何： 本地化代码 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c283f8e2b73fdb4ba44322ca09f8fb436d729ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-code"></a>如何：本地化代码
  未本地化的代码使用硬编码的字符串值。 若要本地化代码字符串，将它们替换为对调用<xref:System.Web.HttpContext.GetGlobalResourceObject%2A>，这是一引用的本地化的资源的方法。  
  
## <a name="localizing-code"></a>本地化代码  
  
#### <a name="to-localize-code"></a>若要本地化代码  
  
1.  在**解决方案资源管理器**，打开项目项的快捷菜单，然后选择**添加**，**模块**。  
  
     选择**资源文件**模板。  
  
    > [!NOTE]  
    >  请确保将资源文件添加到 SharePoint 项目项，以便部署类型属性均可用。 稍后在此过程需要使用此属性。  
  
2.  为默认语言资源文件提供一个带.resx 扩展名，例如 MyAppResources.resx 追加你选择的名称。  
  
3.  重复步骤 1 和步骤 2，向 SharePoint 项目项添加单独的资源文件：每种本地化语言各对应一个文件。  
  
     使用相同的基名称为每个本地化的资源文件，但添加区域性 id。 例如，名称 MyAppResources.de DE.resx 德语本地化的资源。  
  
4.  打开每个资源文件并添加本地化的字符串。 在每个文件中使用相同的字符串 ID。  
  
5.  更改的值**部署类型**到每个资源文件的属性**AppGlobalResource** ，使每个文件将部署到服务器的 App_GlobalResources 文件夹。  
  
6.  保留的值**生成操作**作为每个文件的属性**嵌入的资源**。  
  
     嵌入的资源将编译到项目的 DLL 中。  
  
7.  生成项目以创建附属 Dll 的资源。  
  
8.  在**包设计器**，选择**高级**选项卡上，然后添加附属程序集。  
  
9. 在**位置**框中，在前面添加到的位置路径，例如 DE-DE 的区域性 ID 文件夹\\*项目项名称*。 resources.dll。  
  
10. 如果你的解决方案不已引用 System.Web 程序集，添加对它的引用并创建你的代码中添加一条指令<xref:System.Web>。  
  
11. 在您的代码中找到用户可见的所有硬编码的字符串，如 UI 文本、错误和消息文本。 使用以下语法将这些字符串替换为对 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法的调用：  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. 选择 F5 生成并运行应用程序。  
  
13. 在 SharePoint 中，更改默认的显示语言。  
  
     应用程序中出现的本地化的字符串。 若要显示本地化的资源，SharePoint 服务器必须具有匹配资源文件的区域性的语言包安装。  
  
## <a name="see-also"></a>另请参阅  
 [本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何： 本地化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何： 本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：添加资源文件](../sharepoint/how-to-add-a-resource-file.md)  
  
  