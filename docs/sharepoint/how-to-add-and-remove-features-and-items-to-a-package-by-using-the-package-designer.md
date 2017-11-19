---
title: "如何： 添加和移除功能和包项使用包设计器 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7dfa2c5d-3ac7-4573-abac-12a5e16efd1d
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9da26de3b5a3a71927e7518ff126a7186c01d7e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>如何：使用包设计器在包中添加和移除功能和项
  当创建 SharePoint 解决方案时，Visual Studio 会将默认 SharePoint 功能添加到解决方案中的包。 然后才能最终部署，你可以添加和移除 SharePoint 项目项和修改 SharePoint 包的功能。  
  
 或者，可以使用打包资源管理器添加和删除 SharePoint 项目项。 你还可以查看和更改的层次结构的 SharePoint 项目项和放入包 (.wsp) 的功能。 有关详细信息，请参阅[如何： 添加和使用打包资源管理器中删除功能和包项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
## <a name="adding-features-to-a-sharepoint-package"></a>将功能添加到 SharePoint 包  
 在包设计器可用于将功能添加到 SharePoint 包。  
  
#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>若要添加与包设计器的 SharePoint 功能  
  
1.  打开**包设计器**。  
  
     有关详细信息，请参阅[如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  通过执行一个或多个以下的步骤中添加一个或多个 SharePoint 功能：  
  
    1.  双击中的每个项**解决方案中的项**你想要添加的列表。  
  
    2.  选择你想要添加，，然后选择一项**添加**按钮 (>)。  
  
    3.  选择**全部添加**按钮 (>>) 若要同时添加所有项。  
  
     例如，你可以双击中的项**解决方案中的项**列表以将其添加到**包中的项**列表。  
  
     SharePoint 项目项和功能出现在**包中的项**列表。  
  
## <a name="removing-features-from-a-sharepoint-package"></a>从 SharePoint 包中删除功能  
 在包设计器可用于向 SharePoint 包中删除功能。  
  
#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>若要删除与在包设计器的 SharePoint 功能  
  
1.  在**包中的项**列表中，选择你想要删除，然后选择一项**删除**(<) 按钮，或选择**全部删除**按钮 (<<) 若要删除所有项。  
  
     SharePoint 项出现在**解决方案中的项**列表。  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [如何： 创建包](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
  