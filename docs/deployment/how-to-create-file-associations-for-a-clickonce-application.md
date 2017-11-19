---
title: "如何： 创建 ClickOnce 应用程序的文件关联 |Microsoft 文档"
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
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 491de73e97bf44ea54d5ccdfb604924ff26c9530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>如何：为 ClickOnce 应用程序创建文件关联
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序可以与一个或多个文件扩展名关联，以便应用程序将自动启动，当用户打开这些类型的文件。 添加到的文件名称扩展支持[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序非常简单。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>若要创建 ClickOnce 应用程序的文件关联  
  
1.  创建[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序通常情况下，或使用现有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
2.  使用文本或 XML 编辑器，如记事本中打开应用程序清单。  
  
3.  查找 `assembly` 元素。 有关详细信息，请参阅 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
4.  作为的子级`assembly`元素中，添加`fileAssociation`元素。 `fileAssociation`元素具有四个属性：  
  
    -   `extension`： 你想要将与应用程序相关联文件扩展名。  
  
    -   `description`： 为的文件类型，将出现在 Windows shell 中的说明。  
  
    -   `progid`： 唯一标识要将其标记在注册表中的文件类型一个字符串。  
  
    -   `defaultIcon`： 要用于此文件类型一个图标。 图标必须添加为应用程序清单中的文件资源。 有关详细信息，请参阅 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
     有关的示例`file`和`fileAssociation`元素，请参阅[ \<fileAssociation > 元素](../deployment/fileassociation-element-clickonce-application.md)。  
  
5.  如果你想要将多个文件类型与应用程序相关联，将添加其他`fileAssociation`元素。 请注意，`progid`属性应为每个不同。  
  
6.  完成应用程序清单后，重新对清单进行签名。 你可以从命令行执行此使用 Mage.exe。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     有关详细信息，请参阅[Mage.exe （清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>另请参阅  
 [\<fileAssociation > 元素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)