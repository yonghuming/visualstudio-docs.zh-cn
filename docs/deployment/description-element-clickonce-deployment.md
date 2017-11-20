---
title: "&lt;说明&gt;元素 （ClickOnce 部署） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 41fd9fcee2d0ae954f5ec234bf23cbefd5ccd6da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;说明&gt;元素 （ClickOnce 部署）
标识应用程序信息用于创建 shell 表示和**添加或删除程序**控制面板中的项。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `description` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v1` 命名空间中。 它不包含任何子元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`publisher`|必需。 标识用于在 Windows 中的图标位置的公司名称**启动**菜单和**添加或删除程序**控制面板，为安装配置部署时中的项。|  
|`product`|必需。 标识完整的产品名称。 用作在 Windows 中安装的图标的标题**启动**菜单。|  
|`suiteName`|可选。 标识的子文件夹中`publisher`Windows 中的文件夹**启动**菜单。|  
|`supportUrl`|可选。 指定所示的支持 URL**添加或删除程序**控制面板中的项。 此 URL 的快捷方式也创建应用程序中的支持 Windows**启动**菜单、 何时进行安装的部署配置。|  
  
## <a name="remarks"></a>备注  
 Description 元素中所有的部署配置需要。  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`description`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单。 此代码示例摘自更大的示例为提供[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)