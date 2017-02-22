---
title: "模板参数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项模板, 参数"
  - "项目模板, 参数"
  - "模板参数 [Visual Studio]"
  - "Visual Studio 模板, 参数"
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 模板参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在对模板进行实例化时,您可以通过模板的参数，替换模板的关键部分的值，如类名和命名空间。  当用户在**“新建项目”**或**“添加新项”**对话框中单击**“确定”**时，这些参数将由后台运行的模板向导替换。  
  
## 声明和启用模板参数  
 模板参数以 $*parameter*$ 格式进行声明。  例如：  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### 启用模板中的参数替换  
  
1.  在模板的 .vstemplate 文件中，定位到与要为其启用参数替换的项对应的 `ProjectItem` 元素。  
  
2.  将 `ProjectItem` 元素的 `ReplaceParameters` 特性设置为 `true`。  
  
3.  在项目项的代码文件中，在合适的位置包括参数。  例如，下面的参数指定用于文件中的命名空间的安全项目名称：  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## 保留的模板参数  
 下表列出了可供所有模板使用的保留的模板参数。  
  
> [!NOTE]
>  模板参数区分大小写。  
  
|Parameter|描述|  
|---------------|--------|  
|`clrversion`|公共语言运行时 \(CLR\) 的当前版本。|  
|`GUID [1-10]`|用于替换项目文件中的项目 GUID 的 GUID。  最多可以指定 10 个唯一的 GUID（例如，`guid1)`）。|  
|`itemname`|用户在**添加新项**对话框中提供的名称。|  
|`machinename`|当前的计算机名称（例如，Computer01）。|  
|`projectname`|用户在**新建项目**对话框中提供的名称。|  
|`registeredorganization`|HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\RegisteredOrganization 中的注册表项值。|  
|`rootnamespace`|当前项目的根命名空间。  此参数仅适用于项目模板。|  
|`safeitemname`|用户在**“添加新项”**对话框中提供的名称，名称中移除了所有不安全的字符和空格。|  
|`safeprojectname`|用户在**“新建项目”**对话框中提供的名称，名称中移除了所有不安全的字符和空格。|  
|`time`|以 DD\/MM\/YYYY 00:00:00 格式表示的当前时间。|  
|`SpecificSolutionName`|解决方案的名称。  当“创建解决方案的目录”被选中，`SpecificSolutionName` 具有解决方案的名称。  当“创建解决方案的目录”没有被选中，`SpecificSolutionName`是空。|  
|`userdomain`|当前的用户域。|  
|`username`|当前的用户名。|  
|`webnamespace`|当前网站的名称。  在 Web 窗体模板中使用此参数以确保类名称是唯一的。  如果网站位于 Web 服务器的根目录下，则此模板参数将解析为 Web 服务器的根目录。|  
|`year`|以 YYYY 格式表示的当前年份。|  
  
## 自定义模板参数  
 除了在参数替换过程中自动使用的保留模板参数外，还可以指定您自己的模板参数和值。参见详细信息，请看[CustomParameters 元素（Visual Studio 模板）](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## 示例：替换文件名  
 可以使用具有 `TargetFileName` 特性的参数为项目项指定变量文件名。  例如，可以指定 .exe 文件使用 `$projectname$` 所指定的项目名称作为文件名。  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## 示例：使用项目名称作为命名空间名称  
 若要将项目名称用于 Visual C\# 类文件 Class1.cs 中的命名空间，请使用下面的语法：  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 在项目模板的 .vstemplate 文件中，在引用 Class1.cs 文件时请包括以下 XML：  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## 请参阅  
 [自定义模板](../ide/customizing-project-and-item-templates.md)