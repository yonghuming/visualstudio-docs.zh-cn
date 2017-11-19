---
title: "CustomParameters 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90515cfa8a3aea03336aaee5503cb41df4704953
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters 元素（Visual Studio 模板）
组的自定义参数的向导进行参数替换时要传递给模板向导。  
  
## <a name="syntax"></a>语法  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|可选元素。<br /><br /> 包含自定义参数名称和从模板创建项目或项时要使用的值。 `CustomParameter` 元素中可能有零个或零个以上的 `CustomParameters` 元素。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定模板的内容。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用模板中的多个自定义参数。 当从具有以下自定义参数的所有实例的模板创建项目或项`$color1$`和`$color2$`在模板文件将替换为`Red`和`Blue`分别。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>另请参阅  
 [CustomParameter 元素 （Visual Studio 模板）](../extensibility/customparameter-element-visual-studio-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)