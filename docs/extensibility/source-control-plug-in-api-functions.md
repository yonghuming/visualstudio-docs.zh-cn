---
title: "源控件插件 API 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1085312849ce33518654e044a795d6aa4b735e07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-api-functions"></a>源控件插件 API 函数
源控件插件 API 提供以下函数，必须由源代码管理插件根据此 API 实现。 每个函数语义的签名关联的位标志和其他参数将本引用中的详细信息中所述。  
  
## <a name="initialization-and-housekeeping-functions"></a>初始化和管理函数  
  
|函数|描述|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|关闭项目。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示用户提供对于给定的命令的高级选项。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|返回的版本的源代码管理插件。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化源代码管理插件。 它为每个插件实例一次调用。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|打开一个项目。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|泛型函数，用于设置各种选项。 每个选项开头`SCC_OPT_xxx`并具有其自己定义的一组值。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|调用一次时需要是拔出源代码管理插件。|  
  
## <a name="core-source-control-functions"></a>核心源控件函数  
  
|函数|描述|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|将添加到源代码管理系统的完全限定的路径名称由指定的文件的数组。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|允许用户浏览源代码管理系统中已有的文件，然后将这些文件属于当前项目。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|检查数组中的文件。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|签出文件的数组。|  
|[SccDiff](../extensibility/sccdiff-function.md)|显示指定完全限定的路径名称和在源代码管理下的版本的本地用户的文件之间的差异。|  
|[SccGet](../extensibility/sccget-function.md)|检索一组文件的只读副本。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|检查调用方具有要求有关的文件的状态 (通过`SccQueryInfo`)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|将导致源代码管理插件以提示用户输入的插件有意义的项目路径。|  
|[SccHistory](../extensibility/scchistory-function.md)|显示的完全限定的本地文件的名称数组的历史记录。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|检查以了解其当前状态的文件的列表。 此外，使用`pfnPopulate`函数以在文件不匹配的条件时通知调用方`nCommand`。|  
|[SccProperties](../extensibility/sccproperties-function.md)|显示文件的完全限定的属性。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|检查以了解其当前状态的完全限定文件的列表。|  
|[SccRemove](../extensibility/sccremove-function.md)|从源代码管理系统中移除完全限定文件的数组。|  
|[SccRename](../extensibility/sccrename-function.md)|重命名为新名称的源控制系统中的给定的文件。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|访问的完整范围的源控制系统的功能。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|撤消签出文件的数组。|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>支持其他功能 （1.2 版的源控制插件 API） 的函数  
 此组的函数定义包含源控件插件 API 版本 1.2 中的其他功能。 它们提供对更高级的源控制特性和功能的访问。  
  
|函数|描述|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|启动批处理操作。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|创建具有给定名称的现有父项目下的子项目。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|显示由完全限定的路径名称和源代码管理数据库位置指定的本地用户的目录之间的差异。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|检查以了解其当前状态的完全限定目录的列表。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|结束批处理操作。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|返回父路径的给定的项目 （项目必须存在）。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|检查是否允许文件上的多重签出。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|检查是否该插件将创建 MSSCCPRJ。SCC 文件。|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>支持高级的功能 （版本 1.3 的源控制插件 API） 的函数  
 此组的函数定义包含在源控件插件 API 版本 1.3 中的其他功能。 它们提供对更高级的源控制特性和功能的访问。  
  
|函数|描述|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|向当前项目，从源代码管理中添加的文件的列表。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|从没有用户界面的源控件中检索的文件的列表。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|检索在源代码管理中不同的本地文件的文件的列表。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|检索指定源代码管理插件支持扩展的功能的标志。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|检索用户特定的选项。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|检查中一个项目或项目受源代码管理目录和文件的列表。 找到每个目录和文件名称传递给回调函数。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|检查对文件的列表所做的名称更改。 每个文件名传递给带其更改状态的回调函数。|  
  
## <a name="requirements"></a>要求  
 标头： scc.h  
  
 (环境 SDK 中提供常见默认情况下中包括文件夹， *[驱动器]*\Program Files\VSIP 8.0\EnvSDK\common\inc; 在 MSSCCI 示例中，具有的 VSIP 文件夹中还提供*[驱动器]*\ProgramFiles\VSIP 8.0\MSSCCI)。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [创建源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)