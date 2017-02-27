---
title: "如何：创建多文件项模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项模板, 创建多文件项模板"
  - "多文件项模板"
  - "Visual Studio 模板, 创建多文件项模板"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：创建多文件项模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

项模板只能指定一个项，但有时一个项也包含多个文件。  例如， windows 窗体 Visual Basic 项模板需要以下三个文件:  
  
-   一个 .vb 文件，包含该窗体的代码。  
  
-   一个 .designer.vb 文件，包含该窗体的设计器信息。  
  
-   一个 .resx 文件，包含该窗体的嵌入资源。  
  
 多文件项模板需要使用参数来确保在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建项时使用正确的文件扩展名。  如果您使用**“导出模板”**向导创建项模板，则将自动生成这些参数，且无需进一步编辑。  下列步骤说明如何使用参数来确保创建正确的文件扩展名。  
  
### 手动创建多文件项模板  
  
1.  采用与创建单文件项模板相同的方式创建多文件项模板。  有关更多信息，请参见 [如何：创建项模板](../ide/how-to-create-item-templates.md)。  
  
2.  将 `TargetFileName` 特性添加到每个 `ProjectItem` 元素。  将 `TargetFileName` 特性的值设置为 $fileinputname$.*FileExtension*，其中 *FileExtension* 是要在模板中包含的文件的扩展名。  例如：  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     当向项目中添加从此模板派生的项时，将基于用户在**“添加新项”**对话框中键入的名称来指定文件名。  
  
3.  选择要包含在模板中的文件，右击选定内容，单击**“发送到”**，然后单击**“压缩\(zipped\)文件夹”**。  所选的文件被压缩为一个 .zip 文件。  
  
4.  将该 .zip 文件置于用户项模板位置。  默认情况下，该目录为 \\ my documents \\ Visual Studio *版本*\\ templates \\ ItemTemplates \\。  有关更多信息，请参见[如何：查找和组织模板](../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
## 示例  
 下面的示例演示一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows 窗体模板。  基于此模板创建项时，创建的三个文件的名称将与**“添加新项”**对话框中输入的名称匹配。  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建项模板](../ide/how-to-create-item-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [如何：替换模板中的参数](../ide/how-to-substitute-parameters-in-a-template.md)