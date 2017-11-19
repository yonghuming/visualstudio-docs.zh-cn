---
title: "VSIX 包剖析 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519993c8527b0cd64c283416cd60eb48112e6886
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 包的剖析
VSIX 包是包含一个或多个 Visual Studio 扩展，以及元数据，Visual Studio 将使用来进行分类并安装扩展的.vsix 文件。 该元数据包含在 VSIX 清单和 [Content_Types].xml 文件。 VSIX 包还可能包含一个或多个 Extension.vsixlangpack 文件提供本地化的安装文本，并可能包含其他 VSIX 包来安装依赖项。  
  
 VSIX 包格式遵循开放式打包约定 (OPC) 标准。 包中包含二进制文件和支持文件，[Content_Types].xml 文件以及.vsix 清单文件。 一个 VSIX 包可能包含多个项目或甚至多个具有其自己的清单的包的输出。  
  
> [!NOTE]
>  VSIX 包中包含的文件的名称不能包含空格，也不在定义保留在统一资源标识符 (URI)，作为的字符[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)。  
  
## <a name="the-vsix-manifest"></a>VSIX 清单  
 VSIX 清单包含有关要安装扩展和如下所示 VSX 架构信息。 有关详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。 有关示例 VSIX 清单，请参阅[PackageManifest 元素 （根元素，VSX 架构）](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
 必须命名为 VSIX 清单`extension.vsixmanifest`时包含在.vsix 文件。  
  
## <a name="the-content"></a>内容  
 VSIX 包可能包含模板、 工具箱项、 Vspackage 或任何其他类型的 Visual Studio 支持的扩展。  
  
## <a name="language-packs"></a>语言包  
 VSIX 包可能包含一次或更多 Extension.vsixlangpack 文件的安装过程中提供本地化的文本。 有关详细信息，请参阅[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="dependencies-and-references"></a>依赖关系和引用  
 VSIX 包可能包含其他 VSIX 包作为引用。 每个这些其他包必须包含其自身 VSIX 清单。  
  
 如果用户尝试安装具有依赖关系的扩展，安装程序将验证该用户的系统上安装了所需的程序集。 如果未找到所需的程序集，**扩展和更新**显示缺少的程序集的列表。  
  
 如果扩展清单包括一个或多个[引用](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)元素，**扩展和更新**将在系统上，安装的扩展插件对每个引用的清单进行比较，并安装如果尚未安装，请引用扩展。 如果已安装早期版本的引用的扩展，较新版本将替换它。  
  
 如果多项目解决方案中的项目包括到另一个项目的引用同一解决方案中，VSIX 包包括该项目的依赖项。 可以通过单击该引用对于内部的项目，然后在重写此行为**属性**窗口中，设置**输出组包含在 VSIX**属性`BuiltProjectOutputGroup`。  
  
 若要在 VSIX 包中包含从引用的程序集的附属 Dll，将添加`SatelliteDllsProjectOutputGroup`到**输出组包含在 VSIX**属性。  
  
## <a name="installation-location"></a>安装位置  
 在安装期间，**扩展和更新**寻找 %localappdata%\microsoft\visualstudio\14.0\extensions 下的某个文件夹中的 VSIX 包的内容。  
  
 默认情况下，安装仅适用于当前用户，因为 %localappdata%是一个特定于用户的目录。 但是，如果你设置[AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)到清单元素`True`，将在安装该扩展...\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions 和将可供计算机的所有用户。  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 [Content_Types].xml 文件标识扩展的.vsix 文件中的文件类型。 Visual Studio 期间安装此包使用此文件，但不会安装文件本身。 有关此文件的详细信息，请参阅[[Content_types].xml 文件的结构](the-structure-of-the-content-types-dot-xml-file.md)。  
  
 [Content_Types].xml 文件，需要通过开放式打包约定 (OPC) 标准。 有关 OPC 的详细信息，请参阅[OPC: 新标准打包您数据的](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 网站上。