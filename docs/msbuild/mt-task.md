---
title: "MT 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT 任务"
  - "MT 任务 (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# MT 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包装 Microsoft 清单工具 mt.exe。  有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上的“Mt.exe”。  
  
## 参数  
 下表描述了 **MT** 任务的参数。  大多数的任务参数和少数几个参数集对应于命令行选项。  
  
> [!NOTE]
>  mt.exe 文档中使用连字符 \(**\-**\) 作为前缀，用于命令行选项，但本主题使用斜杠 \(**\/**\)。  任一前缀均可接受。  
  
|Parameter|说明|  
|---------------|--------|  
|**AdditionalManifestFiles**|可选 **String\[\]** 参数。<br /><br /> 指定一个或多个清单文件的名称。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/manifest** 选项。|  
|**AdditionalOptions**|可选 **String** 参数。<br /><br /> 命令行选项的列表。  例如，"*\/option1 \/option2 \/option\#*"。  将此参数用于指定不用任何其他 **MT** 任务参数表示的命令行选项。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上的“Mt.exe”。|  
|**AssemblyIdentity**|可选 **String** 参数。<br /><br /> 指定清单的 **assemblyIdentity** 元素的特性值。  指定一个逗号分隔的列表，其中第一个组件是 `name` 特性的值，后跟以下格式的一个或多个名称\/值对：*\<特性名\>\=\<特性值\>*。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/identity** 选项。|  
|**ComponentFileName**|可选 **String** 参数。<br /><br /> 指定要从 .rgs 或 .tlb 文件生成的动态链接库的名称。  如果指定 **RegistrarScriptFile** 或 **TypeLibraryFile** MT 任务参数，则此参数是必需的。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/dll** 选项。|  
|**DependencyInformationFile**|可选 **String** 参数。<br /><br /> 指定 Visual Studio 用于跟踪清单工具的生成依赖项信息的依赖项信息文件。|  
|**EmbedManifest**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则在程序集中嵌入清单文件。  如果为 `false`，则会创建为独立的清单文件。|  
|**EnableDPIAwareness**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则添加到将应用程序标记为 DPI 的清单信息。  编写 DPI 可识别的应用程序，可使用户界面通过各种高 DPI 显示设置显得美观一致。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?linkid=737) 网站上的“High DPI”（高 DPI）。|  
|**GenerateCatalogFiles**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则生成编录定义 \(.cdf\) 文件。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/makecdfs** 选项。|  
|**GenerateCategoryTags**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则导致生成类型标记。  如果此参数为 `true`，必须还指定 **ManifestFromManagedAssembly MT** 任务参数。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/category** 选项。|  
|**InputResourceManifests**|可选 **String** 参数。<br /><br /> 从具有指定标识符的 RT\_MANIFEST 类型的资源输入清单。  指定一种具有以下格式的资源：*\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*，其中可选 `resource_id` 参数是一个非负值 16 位数字。<br /><br /> 如果没有指定 `resource_id`，则会使用 CREATEPROCESS\_MANIFEST\_RESOURCE 默认值 \(1\)。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/inputresource** 选项。|  
|**ManifestFromManagedAssembly**|可选 **String** 参数。<br /><br /> 从指定的托管程序集生成清单。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/managedassemblyname** 选项。|  
|**ManifestToIgnore**|可选 **String** 参数。<br /><br /> （未使用。）|  
|**OutputManifestFile**|可选 **String** 参数。<br /><br /> 指定输出清单的名称。  如果省略了此参数，并且只有一个清单正在受操作，则会就地修改该清单。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/out** 选项。|  
|**OutputResourceManifests**|可选 **String** 参数。<br /><br /> 输出具有指定标识符的 RT\_MANIFEST 类型的资源清单。  资源的格式如下：*\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*，其中可选 `resource_id` 参数是一个非负值 16 位数字。<br /><br /> 如果没有指定 `resource_id`，则会使用 CREATEPROCESS\_MANIFEST\_RESOURCE 默认值 \(1\)。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/outputresource** 选项。|  
|**RegistrarScriptFile**|可选 **String** 参数。<br /><br /> 指定要用于免注册 COM 清单支持的注册器脚本 \(.rgs\) 文件。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/rgs** 选项。|  
|**ReplacementsFile**|可选 **String** 参数。<br /><br /> 指定注册器脚本 \(.rgs\) 文件中包含可替换字符串的值的文件。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/replacements** 选项。|  
|**ResourceOutputFileName**|可选 **String** 参数。<br /><br /> 指定用于将清单嵌入到项目输出的输出资源文件。|  
|**Sources**|可选 `ITaskItem[]` 参数。<br /><br /> 指定由空格分隔的清单源文件列表。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/manifest** 选项。|  
|**SuppressDependencyElement**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则生成无依赖项元素清单。  如果此参数为 `true`，还指定 **ManifestFromManagedAssembly MT** 任务参数。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/nodependency** 选项。|  
|**SuppressStartupBanner**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，将在任务开始时防止显示版权和版本编号消息。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/nologo** 选项。|  
|**TrackerLogDirectory**|可选 `String` 参数。<br /><br /> 指定此任务的跟踪日志的中间存储目录。|  
|**TypeLibraryFile**|可选 **String** 参数。<br /><br /> 指定类型库 \(.tlb\) 文件的名称。  如果指定此参数，还要指定 **ComponentFileName MT** 任务参数。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/tlb** 选项。|  
|**UpdateFileHashes**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，将在 **UpdateFileHashesSearchPath MT** 任务参数指定的路径计算文件的哈希值，然后使用计算的值更新清单 **file** 元素的 **hash** 特性的值。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/hashupdate** 选项。  另请参见本表中的 **UpdateFileHashesSearchPath** 参数。|  
|**UpdateFileHashesSearchPath**|可选 `String` 参数。<br /><br /> 指定更新文件哈希时要使用的搜索路径。  将此参数与 **UpdateFileHashes MT** 任务参数一起使用。<br /><br /> 有关更多信息，请参见本表格中的 **UpdateFileHashes** 参数。|  
|**VerboseOutput**|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则显示详细调试信息。<br /><br /> 有关更多信息，请参见 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 网站上“Mt.exe”中的 **\/verbose** 选项。|  
  
## 备注  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)