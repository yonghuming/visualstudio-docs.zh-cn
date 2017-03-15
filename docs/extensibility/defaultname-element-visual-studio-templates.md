---
title: "DefaultName 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d1bed42c1afe574f9d50f8598b038ce6055d8332
ms.lasthandoff: 02/22/2017

---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 元素（Visual Studio 模板）
创建时指定 Visual Studio 项目系统将生成项目或项的名称。  
  
 \<VSTemplate&1;>  
 \<TemplateData&1;>  
 \<DefaultName&1;>  
  
## <a name="syntax"></a>语法  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必需的元素。<br /><br /> 将此模板分类并定义此模板在 **“新建项目”** 或 **“添加新项”** 对话框中的显示方式。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 此文本指定项目或项的默认名称。  
  
## <a name="remarks"></a>备注  
 `DefaultName` 是可选元素。  
  
 对于项目，此元素指定在磁盘存储项目的目录的名称。 对于项目，它指定源代码文件的文件名。  
  
 当您创建的项目时，您可以修改默认名称使用**名称**选项，即从可用**新项目**对话框或**添加新项**对话框。  
  
 如果不希望项目系统以生成项目或项的默认名称，然后设置[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)元素`False`。  
  
## <a name="example"></a>示例  
 下面的示例演示为针对标准项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]类。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)
