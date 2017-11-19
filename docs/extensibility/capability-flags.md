---
title: "功能标志 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5104bff319f4a6517ddccde1da1407156797928e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="capability-flags"></a>功能标志
SCC_CAP_*xxx*标志是用于指示了源代码管理插件的功能的位标志。 SCC_EXCAP_*xxx*标志是指示扩展的功能，并解析为整数值的增量标志。  
  
|功能代码|值|描述|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|支持[SccRemove](../extensibility/sccremove-function.md)和命令。|  
|`SCC_CAP_RENAME`|0x00000002L|支持[SccRename](../extensibility/sccrename-function.md)和命令。|  
|`SCC_CAP_DIFF`|0x00000004L|支持[SccDiff](../extensibility/sccdiff-function.md)和命令。|  
|`SCC_CAP_HISTORY`|0x00000008L|支持[SccHistory](../extensibility/scchistory-function.md)和命令。|  
|`SCC_CAP_PROPERTIES`|0x00000010L|支持[SccProperties](../extensibility/sccproperties-function.md)和命令。|  
|`SCC_CAP_RUNSCC`|0x00000020L|支持[SccRunScc](../extensibility/sccrunscc-function.md)和命令。|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|支持[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)和命令。|  
|`SCC_CAP_QUERYINFO`|0x00000080L|支持[SccQueryInfo](../extensibility/sccqueryinfo-function.md)和命令。|  
|`SCC_CAP_GETEVENTS`|0x00000100L|支持[SccGetEvents](../extensibility/sccgetevents-function.md)和命令。|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|支持[SccGetProjPath](../extensibility/sccgetprojpath-function.md)和命令。|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|支持[SccAddFromScc](../extensibility/sccaddfromscc-function.md)和命令。|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|支持在签出上的注释。|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|支持在签入注释。|  
|`SCC_CAP_COMMENTADD`|0x00002000L|支持在添加注释。|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|支持上删除注释。|  
|`SCC_CAP_TEXTOUT`|0x00008000L|将文本写入提供 IDE 输出函数。|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|将文件而无需增量存储的支持。|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|支持多个文件历史记录。|  
|`SCC_CAP_IGNORECASE`|0x00800000L|支持不区分大小写的文件比较。|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|支持文件时忽略空格的比较。|  
|`SCC_CAP_POPULATELIST`|0x02000000L|支持查找额外文件。|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|对支持注释创建项目。|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|如果在控件下，支持所有状态中的差异。|  
|`SCC_CAP_GET_NOUI`|0x20000000L|插件不支持用户界面为 Get，但仍可能调用 IDE [SccGet](../extensibility/sccget-function.md)。|  
|`SCC_CAP_REENTRANT`|0x40000000L|插件是可重入和线程安全。 在 1.0 版中，假定没有插件为可重入和线程安全。 如果插件的 1.1 设置此位，是否允许该主机在并行中打开多个项目。|  
  
## <a name="capability-bits-added-in-version-12"></a>在版本 1.2 中添加的功能 Bits  
  
|功能代码|值|描述|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|支持[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)。|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|支持[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。|  
|`SCC_CAP_BATCH`|0x00040000L|支持[SccBeginBatch](../extensibility/sccbeginbatch-function.md)和[SccEndBatch](../extensibility/sccendbatch-function.md)。|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|支持[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|支持[SccDirDiff](../extensibility/sccdirdiff-function.md)。|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|在文件上支持多个签出和[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)。|  
|`SCC_CAP_SCCFILE`|0x80000000L|支持 MSSCCPRJ。SCC 文件 （受用户/管理员或替代） 和[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)。|  
  
## <a name="capability-bits-added-in-version-13"></a>版本 1.3 中添加的功能 Bits  
 这些标志传递到一次一个地[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)函数来确定是否支持此功能。  
  
|扩展的功能代码|值|描述|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|支持`SCC_CHECKOUT_LOCALVER`签出的选项。|  
|`SCC_EXCAP_BACKGROUND_GET`|2|支持[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)。|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|支持[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)。|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|支持查找额外的目录。|  
|`SCC_EXCAP_QUERYCHANGES`|5|枚举文件更改的支持。|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|支持[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)。|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|支持[SccGetUserOption](../extensibility/sccgetuseroption-function.md)。|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|在多个线程上调用 SccQueryInfo 的支持。|  
|`SCC_EXCAP_REMOVE_DIR`|9|支持 SccRemoveDir 函数。|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|可以删除签出文件。|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|可以重命名签出文件。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)