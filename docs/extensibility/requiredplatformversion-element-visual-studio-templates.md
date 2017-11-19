---
title: "RequiredPlatformVersion 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f7eb4ada8378ff9009987f56341a65670a3c412
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 元素（Visual Studio 模板）
指定项目模板正常工作所需的操作系统的最低版本。 此元素用于为创建的项目模板[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用。  
  
 `RequiredPlatformVersion`值直接与操作系统的版本进行比较。 如果`RequiredPlatformVersion`高于操作系统版本中未显示的模板**新项目**对话框。 若要为指定模板[!INCLUDE[win8](../debugger/includes/win8_md.md)]或更高版本，请设置`RequiredPlatformVersion`到 6.2.0。 若要为指定模板[!INCLUDE[win81](../debugger/includes/win81_md.md)]或更高版本，请设置 RequiredPlatformVersion 为 6.3.0。  
  
 指定的模板`RequiredPlatformVersion`= 8 是以前的客户与兼容[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]模板。  
  
 VSTemplate  
TemplateData  
.....TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>语法  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 无。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|指定项目模板面向的平台。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
## <a name="remarks"></a>备注  
 此文本指定模板所需的最低操作系统版本。  
  
## <a name="example"></a>示例  
 此示例指定项目模板面向 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更高版本。  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另请参阅  
 [TargetPlatformName 元素 （Visual Studio 模板）](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)