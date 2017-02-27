---
title: "源代码管理插件 API 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件函数"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 源代码管理插件 API 功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

源控制插件 API 提供了以下函数，必须由源代码管理插件根据此 API 实现。 每个函数和语义的签名与位标志，此参考中详细介绍了其他参数。  
  
## 初始化和日常工作，  
  
|函数|描述|  
|--------|--------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|关闭项目。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示用户提供对于给定的命令的高级选项。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|返回版本的源代码管理插件。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化源代码管理插件。 被调用一次为每个插件实例。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|打开一个项目。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|泛型函数，用于设置各种选项。 每个选项开头 `SCC_OPT_xxx` 并具有其自己定义的值集。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|调用一次当需要被拔掉了源代码管理插件。|  
  
## 核心源代码管理功能  
  
|函数|描述|  
|--------|--------|  
|[SccAdd](../extensibility/sccadd-function.md)|添加到源代码管理系统的完全限定的路径名通过指定的文件数组。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|允许用户浏览源代码管理系统中已存在的文件，然后将这些文件属于当前项目。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|检查数组中的文件。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|签出的文件数组。|  
|[SccDiff](../extensibility/sccdiff-function.md)|显示指定完全限定的路径名和源代码管理下的版本的本地用户的文件之间的差异。|  
|[SccGet](../extensibility/sccget-function.md)|检索一组文件的只读副本。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|检查调用方具有要求有关的文件的状态 \(通过 `SccQueryInfo`\)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|将导致源代码管理插件来提示用户提供有意义的插件的项目路径。|  
|[SccHistory](../extensibility/scchistory-function.md)|显示完全限定的本地文件名称的数组的历史的记录。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|检查以了解其当前状态的文件的列表。 此外，使用 `pfnPopulate` 函数，当文件不匹配的条件时通知调用方 `nCommand`。|  
|[SccProperties](../extensibility/sccproperties-function.md)|显示文件的完全限定的属性。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|检查以了解其当前状态的完全限定文件的列表。|  
|[SccRemove](../extensibility/sccremove-function.md)|从源代码管理系统中删除完全限定的文件的数组。|  
|[SccRename](../extensibility/sccrename-function.md)|重命名为新名称的源控制系统中的给定的文件。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|访问源控制系统功能的完整范围。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|撤消签出的文件数组。|  
  
## 支持其他功能 \(1.2 版的源控制插件 API\) 的函数  
 此组的函数定义的源控制插件 API 1.2 版中包含的其他功能。 它们提供给更高级的源代码管理功能和功能的访问权限。  
  
|函数|说明|  
|--------|--------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|启动批处理操作。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|创建具有给定名称的现有父项目下的子项目。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|显示由完全限定的路径名称和源代码管理数据库位置指定的本地用户的目录之间的差异。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|检查以了解其当前状态的完全限定目录的列表。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|结束批处理操作。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|返回父路径给定的项目 \(项目必须存在\)。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|检查是否允许多次签出文件。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|检查是否该插件将创建 MSSCCPRJ。源代码管理文件。|  
  
## 支持高级的功能 \(版本 1.3 的源控制插件 API\) 的函数  
 此组的函数定义的源控制插件 API 1.3 版中包含的其他功能。 它们提供给更高级的源代码管理功能和功能的访问权限。  
  
|函数|说明|  
|--------|--------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|向当前项目，从源代码管理中添加的文件的列表。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|从没有用户界面的源代码管理检索文件的列表。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|检索在源代码管理中不同于本地文件的文件的列表。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|检索指定源代码管理插件所支持的扩展的功能的标志。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|检索用户特定的选项。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|检查目录和一个项目或项目受源代码管理中的文件的列表。 找到每个目录和文件名称传递给回调函数。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|检查所做的文件列表的名称更改。 每个文件的名称传递给回调函数，将其更改状态。|  
  
## 要求  
 标头: scc.h  
  
 \(环境 SDK 中提供常见默认中包括文件夹中， *\[驱动器\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc; 在 VSIP 文件夹中，MSSCCI 示例中，还提供 *\[驱动器\]*\\Program Files\\VSIP 8.0\\MSSCCI\)。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [创建了源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)