---
title: "&lt;appAddin&gt;元素 （Visual Studio 中的 Office 开发） |Microsoft 文档"
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <appAddin> element
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5637a449ea40f6e4f910e061c7e2e324c91ae70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt;元素 （Visual Studio 中的 Office 开发）
  `appAddin` 命名空间的 `vstov4` 元素存储 VSTO 外接程序特定于自定义项的信息。  
  
## <a name="syntax"></a>语法  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `appAddin` 元素是必需的，它位于 `vstov4` 命名空间中。 在应用程序清单中定义的 `appAddin` 元素只有一个。  
  
 `appAddin` 元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`application`|必需。 标识 Microsoft Office 应用程序。 值可以是以下值之一：Excel、InfoPath、Outlook、PowerPoint、Project、Visio 或 Word。|  
|`loadBehavior`|可选。 默认情况下，通过将此值设置为 启用了 `loadBehavior` 。 为进行调试，可以通过将此值设置为 2 来禁用 VSTO 外接程序。 有关详细信息，请参阅 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)中标题为“LoadBehavior 值”的表。|  
|`keyName`|必需。 此值是该应用程序将用于加载 VSTO 外接程序的注册表项名称。 有关更多信息，请参见 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)。|  
  
 `appAddin` 元素具有以下子元素。  
  
### <a name="friendlyname"></a>FriendlyName  
 可选。 `friendlyName`元素述[&#60; friendlyName &#62;元素 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>说明  
 可选。 `description`元素述[&#60; 说明 &#62;元素 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 仅为包含窗体区域的 Outlook VSTO 外接程序所需。 `formRegions`元素述[&#60; formRegions &#62;元素 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>VSTO 外接程序示例  
  
### <a name="description"></a>说明  
 下面的代码示例说明了使用 `appAddin` 部署的 Outlook 解决方案中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]元素。 此代码示例摘自 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大的示例。  
  
### <a name="code"></a>代码  
  
```  
<vstov4:appAddIn   
  application="Outlook"   
  loadBehavior="3"   
  keyName="ContosoOutlookAddIn">  
  <vstov4:friendlyName>  
    ContosoOutlookAddIn  
  </vstov4:friendlyName>  
  <vstov4:description>  
    ContosoOutlookAddIn - Outlook VSTO Add-in   
    created with Visual Studio Tools for Office  
  </vstov4:description>  
  <vstov4:formRegions>  
    <vstov4:formRegion  
        name="OutlookAddIn1.FormRegion1">  
      <vstov4:messageClass name="IPM.Note" />  
      <vstov4:messageClass name="IPM.Contact" />  
      <vstov4:messageClass name="IPM.Appointment" />  
    </vstov4:formRegion>  
  </vstov4:formRegions>  
</vstov4:appAddIn>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)  
  
  