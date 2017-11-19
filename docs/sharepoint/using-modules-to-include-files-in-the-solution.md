---
title: "使用模块包括解决方案中的文件 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
ms.assetid: 74d1d69f-5cd9-452f-8d35-e1f4d8a084fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 484ae234839876922b6c04767d67ed56f85a108d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-modules-to-include-files-in-the-solution"></a>使用模块包括解决方案中的文件
  可能有些时候你可能想要将文件部署到 SharePoint 服务器而不考虑其文件类型，如新的主页面。 若要执行此操作，可以使用*模块*(无法将其与混淆[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]代码模块)。 模块是 SharePoint 解决方案中的文件的容器。 时部署了解决方案，该模块中的文件会复制到 SharePoint 服务器上的指定文件夹中。  
  
## <a name="module-items-and-elements"></a>模块项和元素  
 若要创建模块，将其添加到项目通过选择在**添加新项**对话框。 然后，修改其 Elements.xml 文件以包含你想要部署，其中它们位于在系统上，且它们应复制 SharePoint 服务器上的文件的名称。  
  
 下面是一个模块 Elements.xml 文件的示例：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 新创建的模块包含以下默认文件：  
  
|文件名|描述|  
|---------------|-----------------|  
|Elements.xml|模块定义文件。|  
|Sample.txt|作为模块中的文件的示例占位符文件。|  
  
 Elements.xml 文件包含下列元素：  
  
|元素名称|描述|  
|------------------|-----------------|  
|元素|包含所有模块中定义的元素。|  
|模块|模块元素具有单个属性，*名称*，采用格式指定该模块的名称`<Module Name="Module1">`。<br /><br /> 请注意，如果你更改模块的名称 (或其*文件夹名称*属性)，你必须手动更新中的模块元素的名称。<br /><br /> 如果在模块元素中，指定该文件的子目录[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) 将自动为其创建匹配的目录结构。|  
|文件|文件元素具有两个参数，*路径*和*Url*。<br /><br /> 路径： 名称和位置的 SharePoint 解决方案中的文件。 格式是， `Path="Module1\Sample.txt"`。<br /><br /> -Url: 在 SharePoint 服务器部署该文件的位置。 格式是， `Url="Module1/Sample.txt"`。<br /><br /> 类型： 一个可选属性，它具有两个设置： *GhostableInLibrary*和*Ghostable*。 格式是， `Type="GhostableInLibrary"`。 指定*GhostableInLibrary*意味着该文件将添加到要添加到库时伴随文件的列表项以及在 SharePoint 文档库。 指定*Ghostable*导致要添加到 SharePoint 文档库之外的文件。|  
  
 你想要部署的每个文件需要一个单独`<File>`Elements.xml 中的元素条目。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 通过使用模块包括文件](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [如何： 设置文件](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  