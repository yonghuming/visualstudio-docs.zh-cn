---
title: "使用 TextTransform 实用工具生成文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
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
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>使用 TextTransform 实用工具生成文件
TextTransform.exe 是一个命令行工具，可用于转换文本模板。 当您调用 TextTransform.exe 时，您作为参数指定的文本模板文件的名称。 TextTransform.exe 调用文本转换引擎，并处理文本模板。 从脚本通常称为 TextTransform.exe。 但是，它不通常必需的因为您可以在 Visual Studio 中或在生成过程中执行文本转换。  
  
> [!NOTE]
>  如果您想要将文本转换作为生成过程的一部分，请考虑使用 MSBuild 文本转换任务。 有关详细信息，请参阅[生成过程中的代码生成](../modeling/code-generation-in-a-build-process.md)。 中的计算机上[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安装后，您也可以编写一个应用程序或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以转换文本模板的扩展。 有关详细信息，请参阅[通过使用自定义宿主处理文本模板](../modeling/processing-text-templates-by-using-a-custom-host.md)。  
  
 TextTransform.exe 位于以下目录中︰  
  
 **\Program Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>语法  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>参数  
  
|**参数**|**描述**|  
|------------------|---------------------|  
|`templateName`|标识你想要转换的模板文件的名称。|  
  
|**选项**|**描述**|  
|----------------|---------------------|  
|**-out** \<文件名&1;>|转换的输出写入到该文件。|  
|**-r** \<程序集&1;>|用于编译和运行文本模板使用程序集。|  
|**-u** \<命名空间&1;>|用于编译模板命名空间。|  
|**我** \<includedirectory&1;>|包含指定的文本模板中包含的文本模板的目录。|  
|**-P** \<referencepath&1;>|要搜索的文本模板中指定的程序集或使用目录**-r**选项。<br /><br /> 例如，要包括为 Visual Studio API 使用的程序集，请使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName&1;> ！\<类名&1;> ！\<程序集名称 | 基本代码&1;>|名称、 完整类型名和可以用于处理文本模板中的自定义指令的指令处理器的程序集。|  
|**-a** [processorName] ！ [directiveName] ！\<parameterName&1;> ！\<parameterValue&1;>|指定参数值为指令处理器。 如果您指定仅参数名称和值，该参数将可供所有指令处理器。 如果指定的指令处理器，参数是只适用于指定的处理器。 如果指定指令的名称，仅当正在处理指定的指令参数才可用。<br /><br /> 若要访问指令处理器或文本模板中的参数值，请使用<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>。</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> 在文本模板中，包括`hostspecific`的 template 指令中，并在调用消息`this.Host`。 例如：<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`。<br /><br /> 始终键入 ！ 将标记，即使省略了可选的处理器和指令的名称。 例如: <br /><br /> `-a !!param!value`|  
|**-h**|提供帮助。|  
  
## <a name="related-topics"></a>相关主题  
  
|任务|主题|  
|----------|-----------|  
|在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案中生成文件。|[使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|编写指令处理器转换自己的数据源。|[自定义 T4 文本转换](../modeling/customizing-t4-text-transformation.md)|  
|编写文本模板化宿主，您可以调用自己的应用程序从文本模板。|[使用自定义宿主处理文本模板](../modeling/processing-text-templates-by-using-a-custom-host.md)|
