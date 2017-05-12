---
title: "可替换参数"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "可替换参数 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 可替换参数"
  - "Visual Studio 中的 SharePoint 开发, 标记"
  - "标记 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 可替换参数
  可在项目文件内使用可替换参数或标记为 SharePoint 解决方案项提供值，这些解决方案项的实际值在设计时是未知的。  它们类似于标准函数 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 模板标记。  有关详细信息，请参阅[模板参数](../ide/template-parameters.md)。  
  
## 标记格式  
 标记以美元符号 \($\) 字符开始和结束。  若在部署时将项目打包成 SharePoint 解决方案包 \(.wsp\) 文件，则使用的任何标记都将替换为实际值。  例如，标记 **$SharePoint.Package.Name$** 可能会解析为字符串“Test SharePoint Package”。  
  
## 标记规则  
 下列规则适用于标记：  
  
-   可以在行中的任意位置指定标记。  
  
-   标记不能跨多个行。  
  
-   可以在同一行上和同一文件中多次指定同一标记。  
  
-   可以在同一行上指定不同的标记。  
  
 不遵循上述规则的标记将被忽略，而不提供警告或错误。  
  
 在清单转换之后立即用字符串值替换标记，从而允许用户编辑的清单模板使用标记。  
  
### 标记名解析  
 大多数情况下，标记会解析为一个特定的值，无论标记包含在哪个位置中。  但是，如果标记与包或功能相关，则标记的值取决于包含标记的位置。  例如，如果功能位于包 A 中，则标记 `$SharePoint.Package.Name$` 将解析为值“包 A”。如果相同的功能位于包 B 中，则 `$SharePoint.Package.Name$` 将解析为“包 B”。  
  
## 标记列表  
 下表列出了可用的标记。  
  
|名称|说明|  
|--------|--------|  
|$SharePoint.Project.FileName$|包含项目文件的名称，例如“NewProj.csproj”。|  
|$SharePoint.Project.FileNameWithoutExtension$|包含项目文件的名称，不带文件扩展名。  例如“NewProj”。|  
|$SharePoint.Project.AssemblyFullName$|包含项目的输出程序集的显示名称（强名称）。|  
|$SharePoint.Project.AssemblyFileName$|包含项目的输出程序集的名称。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|包含项目的输出程序集的名称，不带文件扩展名。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|包含项目的输出程序集的公钥标记（已转换为字符串）。（格式为“x2”十六进制格式，长度为 16 个字符。）|  
|$SharePoint.Package.Name$|包含程序包的名称。|  
|$SharePoint.Package.FileName$|包含程序包的定义文件的名称。|  
|$SharePoint.Package.FileNameWithoutExtension$|包含程序包的定义文件的名称\(不带扩展名\)。|  
|$SharePoint.Package.Id$|包含程序包的 SharePoint ID。  如果在多个程序包中使用功能，则此值将发生更改。|  
|$SharePoint.Feature.FileName$|包含功能的定义文件的名称，例如 Feature1.feature。|  
|$SharePoint.Feature.FileNameWithoutExtension$|功能定义文件的名称，不带文件扩展名。|  
|$SharePoint.Feature.DeploymentPath$|包含包中的功能的文件夹的名称。  此标记等同于功能设计器中的“部署路径”属性。  示例值为“Project1\_Feature1”。|  
|$SharePoint.Feature.Id$|包含功能的 SharePoint ID。  此标记（与所有功能级别的标记一样）只能通过功能由包含在包中的文件使用，而不直接添加到功能之外的包中。|  
|$SharePoint.ProjectItem.Name$|从 **ISharePointProjectItem.Name** 中获取的项目项的名称（不是其文件名）。|  
|$SharePoint.Type.\<GUID\>.AssemblyQualifiedName$|程序集限定与标记的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 匹配的类型的名称。  [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式为小写，并与 Guid.ToString\("D"\) 格式（即 xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx）对应。|  
|$SharePoint.Type.\<GUID\>.FullName$|与标记中的 GUID 匹配的类型的全名。  GUID 的格式为小写，并与 Guid.ToString\("D"\) 格式（即 xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx）对应。|  
  
## 向标记替换文件扩展名列表中添加扩展名  
 虽然从理论上说，属于包中包含的 SharePoint 项目项的任何文件都可以使用标记，但默认情况下，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只会搜索包文件、清单文件和具有以下扩展名的文件中的标记：  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 目标文件这些扩展名由 Microsoft.VisualStudio.SharePoint.targets 文件中的 `<TokenReplacementFileExtensions>` 元素定义，该文件位于 …\\\<program files\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools 文件夹中。  
  
 不过，您可以向列表中添加其他文件扩展名。  为此，请将 `<TokenReplacementFileExtensions>` 元素添加到在 SharePoint 目标文件的 \<Import\> 之前定义的 SharePoint 项目文件中的任意 PropertyGroup 中。  
  
> [!NOTE]  
>  由于标记替换是在编译项目之后发生的，因此不应为编译的文件类型添加文件扩展名（例如 .cs、.vb 或 .resx）。  仅在未编译的文件中替换标记。  
  
 例如，若要将文件扩展名“.myextension”和“.yourextension”添加到标记替换文件扩展名的列表中，则需要向 .csproj 文件中添加以下内容：  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 或者，您可以将扩展名直接添加到 .targets 文件中。  不过，这样做会更改在本地系统上打包的所有 SharePoint 项目（而不仅仅是您自己的项目）的扩展名列表。  如果您是系统的唯一开发人员，或者您的大多数项目有此需求，则采用此方法可能会比较方便。  但由于此方法是特定于系统的，它具有的可移植性不高，因此建议您改为向项目文件中添加扩展名。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  