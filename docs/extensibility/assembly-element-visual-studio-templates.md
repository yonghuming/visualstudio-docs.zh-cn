---
title: "Assembly 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9032fa397e8fb4cb443d0209853ba4cfe7a5e53f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 元素（Visual Studio 模板）
指定有关程序集，该模板使用将该程序集的引用添加到项目的信息。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<引用 >  
 \<引用 >  
 \<程序集 >  
  
## <a name="syntax"></a>语法  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[引用](../extensibility/reference-element-visual-studio-templates.md)|指定向项目添加项时要添加的程序集引用。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 此文本指定要向项目中添加项模板实例化时的程序集。 必须通过以下方式之一指定此程序集名称：  
  
-   作为完整的程序集名称。 例如：  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   为简单文本引用。 例如:   
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>备注  
 `Assembly` 是 `Reference` 的必需子元素。  
  
 `Reference`，`References,`和`Assembly`仅可以具有的.vstemplate 文件中使用元素`Type`属性的值`Item`。  
  
## <a name="example"></a>示例  
 下面的示例演示`TemplateContent`项模板的元素。 此 XML 添加 System.dll 和 System.Data.dll 程序集的引用。  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)