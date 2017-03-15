---
title: "命令代码枚举器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令代码枚举器"
  - "源代码管理插件，命令代码枚举"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 命令代码枚举器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此枚举器使用的选项中 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和 [SccPopulateList](../extensibility/sccpopulatelist-function.md)以指示为其指定的选项的命令。  
  
## 语法  
  
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
  
## 成员  
 SCC\_COMMAND\_GET  
 对应于 [SccGet](../extensibility/sccget-function.md)。  
  
 SCC\_COMMAND\_CHECKOUT  
 对应于 [SccCheckout](../extensibility/scccheckout-function.md)。  
  
 SCC\_COMMAND\_CHECKIN  
 对应于 [SccCheckin](../extensibility/scccheckin-function.md)。  
  
 SCC\_COMMAND\_UNCHECKOUT  
 对应于 [SccUncheckout](../extensibility/sccuncheckout-function.md)。  
  
 SCC\_COMMAND\_ADD  
 对应于 [SccAdd](../extensibility/sccadd-function.md)。  
  
 SCC\_COMMAND\_REMOVE  
 对应于 [SccRemove](../extensibility/sccremove-function.md)。  
  
 SCC\_COMMAND\_DIFF  
 对应于 [SccDiff](../extensibility/sccdiff-function.md)。  
  
 SCC\_COMMAND\_HISTORY  
 对应于 [SccHistory](../extensibility/scchistory-function.md)。  
  
 SCC\_COMMAND\_RENAME  
 对应于 [SccRename](../extensibility/sccrename-function.md)。  
  
 SCC\_COMMAND\_PROPERTIES  
 对应于 [SccProperties](../extensibility/sccproperties-function.md)。  
  
 SCC\_COMMAND\_OPTIONS  
 对应于 [SccSetOption](../extensibility/sccsetoption-function.md)。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)