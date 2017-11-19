---
title: "可替换参数 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 80f9770fe0e6a0294ec43e450acc75f55b8ddbe2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="replaceable-parameters"></a>可替换参数
  可替换参数，或*令牌*，可以在项目文件内使用，为其实际值在设计时未知的 SharePoint 解决方案项提供值。 它们在功能上类似于标准 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 模板标记。 有关详细信息，请参阅[模板参数](/visualstudio/ide/template-parameters)。  
  
## <a name="token-format"></a>令牌格式  
 令牌开头并以美元符号 （$） 字符。 使用任何令牌替换为实际值中，在部署时为 SharePoint 解决方案包 (.wsp) 文件打包项目。 例如，令牌**$SharePoint.Package.Name$**可能解析为字符串"测试 SharePoint 包"。  
  
## <a name="token-rules"></a>令牌的规则  
 以下规则适用于令牌：  
  
-   令牌可以在行中的任意位置指定。  
  
-   令牌不能跨越多个行。  
  
-   相同的标记可能多次指定同一行上和同一文件中。  
  
-   可在同一行中指定不同的令牌。  
  
 未提供警告或错误情况下，不符合这些规则的令牌将被忽略。  
  
 清单转换，从而允许编辑的用户可以使用令牌清单模板之后立即执行替换的字符串值的标记。  
  
### <a name="token-name-resolution"></a>标记名称解析  
 在大多数情况下，标记会解析为无论其中包含特定值。 但是，如果该令牌与包或功能，令牌的值取决于包含它。 例如，如果功能是中打包，则令牌`$SharePoint.Package.Name$`解析为"包 A"的值 如果同一功能位于包 B 中，然后`$SharePoint.Package.Name$`解析为"包 b"。  
  
## <a name="tokens-list"></a>标记列表  
 下表列出了可用的标记。  
  
|名称|描述|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|包含项目文件，如"NewProj.csproj"的名称。|  
|$SharePoint.Project.FileNameWithoutExtension$|不带文件扩展名包含项目文件的名称。 例如，"NewProj"。|  
|$SharePoint.Project.AssemblyFullName$|包含项目的显示名称 （强名称） 的输出程序集。|  
|$SharePoint.Project.AssemblyFileName$|包含项目的名称的输出程序集。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|包含项目的名称的输出程序集，不带文件扩展名。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|包含项目的公钥令牌的输出程序集，转换为字符串。 ("x2"中的 16 个字符的十六进制格式。)|  
|$SharePoint.Package.Name$|包含包的名称。|  
|$SharePoint.Package.FileName$|包含包的定义文件的名称。|  
|$SharePoint.Package.FileNameWithoutExtension$|包含包的定义文件的名称 （不含扩展名）。|  
|$SharePoint.Package.Id$|包含包的 SharePoint ID。 如果多个包中使用的功能时，将更改此值。|  
|$SharePoint.Feature.FileName$|包含的功能，例如 Feature1.feature 的定义文件的名称。|  
|$SharePoint.Feature.FileNameWithoutExtension$|功能定义文件中，不带文件扩展名的名称。|  
|$SharePoint.Feature.DeploymentPath$|包含包中的功能的文件夹的名称。 此令牌相当于功能设计器中的"部署路径"属性。 一个示例值是"Project1_Feature1"。|  
|$SharePoint.Feature.Id$|包含功能 SharePoint ID。 此令牌，因为具有所有功能级别令牌，可以用仅由一项功能，通过包中包含文件不直接添加到外部功能的包。|  
|$SharePoint.ProjectItem.Name$|获取从项目项 （不文件名称） 的名称**ISharePointProjectItem.Name**。|  
|$SharePoint.Type。\<GUID >。AssemblyQualifiedName $|与标记的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 匹配的类型的程序集限定名。 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式为小写，并与 Guid.ToString("D") 格式（即 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx）对应。|  
|$SharePoint.Type。\<GUID >。FullName $|在令牌中的 GUID 匹配的类型的全名。 GUID 的格式为小写，并对应于 Guid.ToString("D") 格式 (即，xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>添加扩展标记替换文件扩展名列表中  
 虽然理论上可以由属于 SharePoint 项目项包含在程序包中，默认情况下，任何文件使用令牌[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]搜索仅在包文件、 清单文件和具有以下扩展名的文件中的令牌：  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web 部件  
  
-   DWP  
  
 这些扩展定义的`<TokenReplacementFileExtensions>`Microsoft.VisualStudio.SharePoint.targets 文件中的元素位于...\\< 程序文件\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 文件夹。  
  
 但是，可以将其他文件扩展名添加到列表。 若要执行此操作，将添加`<TokenReplacementFileExtensions>`到 SharePoint 项目文件中的任意 PropertyGroup 之前定义的元素\<导入 > 的在 SharePoint 目标文件。  
  
> [!NOTE]  
>  编译项目后，将发生标记替换，因为你不应添加为编译的文件类型，如.cs、.vb 或.resx 的文件扩展名。 仅在不编译的文件中替换标记。  
  
 例如，若要将文件名称扩展".myextension"和".yourextension"添加到的标记替换文件扩展名的列表中，要到.csproj 文件添加以下：  
  
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
  
 或者，你可以直接向.targets 文件添加扩展。 但是，这样做会更改在本地系统上，而不仅仅是打包的所有 SharePoint 项目扩展列表自己。 在系统上的唯一开发人员或如果您的大多数项目需要的话，这可能很方便。 但是，由于它是特定于系统的此方法不是非常易于移植，并且因此，建议你添加的任何扩展到项目文件相反。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  