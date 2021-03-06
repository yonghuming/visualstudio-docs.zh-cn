---
title: "命令代码枚举器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8404b06e566f8d2efc40742c00d1a857af68261
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-code-enumerator"></a>命令代码枚举器
此枚举器使用的选项中[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)和[SccPopulateList](../extensibility/sccpopulatelist-function.md)以指示为其指定的选项的命令。  
  
## <a name="syntax"></a>语法  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## <a name="members"></a>成员  
 SCC_COMMAND_GET  
 对应于[SccGet](../extensibility/sccget-function.md)。  
  
 SCC_COMMAND_CHECKOUT  
 对应于[SccCheckout](../extensibility/scccheckout-function.md)。  
  
 SCC_COMMAND_CHECKIN  
 对应于[SccCheckin](../extensibility/scccheckin-function.md)。  
  
 SCC_COMMAND_UNCHECKOUT  
 对应于[SccUncheckout](../extensibility/sccuncheckout-function.md)。  
  
 SCC_COMMAND_ADD  
 对应于[SccAdd](../extensibility/sccadd-function.md)。  
  
 SCC_COMMAND_REMOVE  
 对应于[SccRemove](../extensibility/sccremove-function.md)。  
  
 SCC_COMMAND_DIFF  
 对应于[SccDiff](../extensibility/sccdiff-function.md)。  
  
 SCC_COMMAND_HISTORY  
 对应于[SccHistory](../extensibility/scchistory-function.md)。  
  
 SCC_COMMAND_RENAME  
 对应于[SccRename](../extensibility/sccrename-function.md)。  
  
 SCC_COMMAND_PROPERTIES  
 对应于[SccProperties](../extensibility/sccproperties-function.md)。  
  
 SCC_COMMAND_OPTIONS  
 对应于[SccSetOption](../extensibility/sccsetoption-function.md)。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)