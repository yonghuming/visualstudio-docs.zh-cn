---
title: "ProjectType 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 19
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
ms.openlocfilehash: d23be61b83cd3c62b6ab33a271968f500ad8ff81
ms.lasthandoff: 02/22/2017

---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 元素（Visual Studio 模板）
将项目模板分类以使其显示在指定组下**新项目**或**添加新项**对话框。  
  
> [!WARNING]
>  启动 Visual Studio 2012 中的 c + + 支持项目模板。 不支持 Visual Studio 2010 和早期版本中的 c + +。  
  
 \<VSTemplate&1;>  
 \<TemplateData&1;>  
 \<ProjectType&1;>  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|将此模板分类并定义此模板在 **“新建项目”** 或 **“添加新项”** 对话框中的显示方式。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 此值指定的项目模板的类型将创建，并且必须包含下列值之一︰  
  
-   `CSharp`︰ 指定此模板创建[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]项目或项。  
  
-   `VisualBasic`︰ 指定此模板创建[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]项目或项。  
  
-   `Web`︰ 指定此模板创建 Web 项目或项。 如果`ProjectType`元素包含此值，在定义的项目或项的语言[ProjectSubType 元素 （Visual Studio 模板）](../extensibility/projectsubtype-element-visual-studio-templates.md)。  
  
## <a name="remarks"></a>备注  
 `ProjectType` 是 `TemplateData` 的必需子元素。  
  
 值`ProjectType`元素指定该模板中的位置**新项目**或**添加新项**对话框。 例如，具有的模板`ProjectType`值`CSharp`下显示**Visual C#**中的节点**新项目**对话框。  
  
 可以通过使用指定模板子类型[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)元素。  
  
## <a name="example"></a>示例  
 下面的示例演示一个用于项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]应用程序。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType 元素 （Visual Studio 模板）](../extensibility/projectsubtype-element-visual-studio-templates.md)
