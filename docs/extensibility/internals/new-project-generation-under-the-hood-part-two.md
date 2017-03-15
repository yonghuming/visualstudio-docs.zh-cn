---
title: "生成新的项目︰ 实质上，第二部分 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>生成新的项目︰ 实质上，第二部分
在[生成新的项目︰ 高级选项、 第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我们已了解如何**新项目**对话框框中填充。 让我们假定你已选择**Visual C# Windows 应用程序**、 已填写**名称**和**位置**文本框中，并单击确定。  
  
## <a name="generating-the-solution-files"></a>生成解决方案文件  
 选择应用程序模板将定向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]来解压缩和打开相应的.vstemplate 文件中，并启动一个模板来解释此文件中的 XML 命令。 这些命令创建新的或现有解决方案中的项目和项目项。  
  
 该模板解包源文件，保存.vstemplate 文件的同一个.zip 文件夹从调用项模板。 该模板将这些文件复制到新项目中，相应地进行自定义它们。 项目和项模板的概述，请参阅[NIB: Visual Studio 模板](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)。  
  
### <a name="template-parameter-replacement"></a>模板参数替换  
 当模板复制到新项目项模板时，它用字符串以自定义文件中替换任何模板参数。 一个模板参数是一个特殊的标记，是前面和后面加一个美元符号，例如、 $date$。  
  
 让我们看一个典型的项目项模板。 提取并检查 Program.cs Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 文件夹中。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 如果创建一个新的 Windows 应用程序项目，名为 Simple 时，该模板将替换`$safeprojectname$`参数与项目的名称。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 有关模板参数的完整列表，请参阅[模板参数](../../ide/template-parameters.md)。  
  
## <a name="a-look-inside-a-vstemplate-file"></a>深入介绍。VSTemplate 文件  
 基本的.vstemplate 文件具有此格式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 我们把目光\<TemplateData&1;> 中[生成新的项目︰ 高级选项、 第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 本部分中的标记用于控制的外观**新项目**对话框。  
  
 中的标记\<TemplateContent&1;> 部分生成新项目和项目项的控件。 下面是\<TemplateContent 1> files\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 文件夹中的 cswindowsapplication.vstemplate 文件中的部分。  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<项目&1;> 标记控制项目的生成和\<ProjectItem&1;> 标记控制项目项的生成。 如果参数 ReplaceParameters 为 true，该模板将自定义的项目文件或项目中的所有模板参数。 在这种情况下，所有项目项是自都定义，但 Settings.settings 除外。  
  
 TargetFileName 参数指定的名称和所生成的项目文件或项目的相对路径。 这允许您创建您的项目的文件夹结构。 如果未指定此参数，项目项将具有与项目项模板同名。  
  
 生成 Windows 应用程序文件夹结构如下所示︰  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 第一个且唯一\<项目&1;> 模板读取的标记︰  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 这会指示要通过复制和自定义模板项 windowsapplication.csproj 创建 Simple.csproj 项目文件的新项目模板。  
  
### <a name="designers-and-references"></a>设计器和引用  
 在解决方案资源管理器中，您可以看到属性文件夹存在并且包含预期的文件。 但是，怎么办项目引用和设计器文件依赖项，如到 Resources.resx，Resources.Designer.cs 和属于 Form1.cs form1.designer.cs 呢？  这些设置在 Simple.csproj 文件生成之后会。  
  
 下面是\<ItemGroup&1;> 从 Simple.csproj 创建项目引用︰  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 您可以看到，这些是在解决方案资源管理器中显示的六个项目引用。 下面是从另一个节\<ItemGroup&1;>。 为清楚起见，多行代码已被删除。 本部分使 Settings.Designer.cs 依赖 Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>另请参阅  
 [生成新的项目︰ 实质上，第&1; 部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild1.md)
