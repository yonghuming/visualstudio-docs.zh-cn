---
title: "新的项目生成： 实质上，第二部分 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7dc04752b034f666dfcb1d72b500f2c12f54fba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="new-project-generation-under-the-hood-part-two"></a>新的项目生成： 实质上，第二部分
在[新项目生成： 高级选项、 第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我们已了解如何**新项目**对话框框中填充。 假设你已选择**Visual C# Windows 应用程序**、 已填写**名称**和**位置**文本框中，并单击确定。  
  
## <a name="generating-the-solution-files"></a>生成解决方案文件  
 选择应用程序模板将定向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]来解压缩和打开相应的.vstemplate 文件中，并启动一个模板来解释此文件中的 XML 命令。 这些命令创建新的或现有解决方案中的项目和项目项。  
  
 模板解包源文件，请调用同一保存.vstemplate 文件的.zip 文件夹中的项模板。 该模板将这些文件复制到新项目中，相应地自定义它们。 项目和项模板的概述，请参阅[NIB: Visual Studio 模板](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)。  
  
### <a name="template-parameter-replacement"></a>模板参数替换  
 当模板复制到新项目项模板时，它用字符串以自定义文件中替换任何模板参数。 一个模板参数是一个特殊的令牌，例如跟美元符号，所以前面、 $date$。  
  
 让我们看一下典型的项目项模板。 提取并检查 Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 文件夹中的 Program.cs 中。  
  
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
  
 如果创建名为简单的新 Windows 应用程序项目，将替换模板`$safeprojectname$`项目同名的参数。  
  
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
  
## <a name="a-look-inside-a-vstemplate-file"></a>详细介绍。VSTemplate 文件  
 基本.vstemplate 文件的此格式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 我们讨论过\<TemplateData > 部分中[新项目生成： 高级选项、 第一部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 本部分中的标记用于控制的外观**新项目**对话框。  
  
 中的标记\<TemplateContent > 部分中的新项目和项目项的生成的控件。 下面是\<TemplateContent > 从 files\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 文件夹中的 cswindowsapplication.vstemplate 文件的部分。  
  
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
  
 \<项目 > 标记控制项目的生成和\<ProjectItem > 标记控制项目项的生成。 如果参数 ReplaceParameters 为 true，该模板将自定义项的项目文件中的所有模板参数。 在这种情况下，所有项目项是自都定义，但 Settings.settings 除外。  
  
 TargetFileName 参数指定的名称和所生成的项目文件或项目的相对路径。 这允许您创建你的项目的文件夹结构。 如果未指定此参数，项目项将具有与项目项模板相同的名称。  
  
 生成的 Windows 应用程序文件夹结构如下所示：  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 第一个和唯一\<项目 > 标记中的模板读取：  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 这会指示要通过复制和自定义模板项 windowsapplication.csproj 创建 Simple.csproj 项目文件的新项目模板。  
  
### <a name="designers-and-references"></a>设计器和引用  
 在解决方案资源管理器中，你可以看到属性文件夹存在并且包含预期的文件。 但什么有关项目引用，并且设计器文件依赖项，如到 Resources.resx，Resources.Designer.cs 和属于 Form1.cs Form1.Designer.cs？  这些设置在 Simple.csproj 文件时生成。  
  
 下面是\<o u p > 从 Simple.csproj 创建的项目引用：  
  
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
  
 你可以看到，这些是在解决方案资源管理器中显示的六个项目引用。 下面是从另一个节\<o u p >。 为清楚起见，多行代码已被删除。 本部分使 Settings.Designer.cs 依赖于 Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>另请参阅  
 [生成新项目：揭秘，第 1 部分](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)