---
title: "目录状态代码枚举器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 998ce86fdf714c65763748971e89fa45ec289a51
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="directory-status-code-enumerator"></a>目录状态代码枚举器
`SccDirStatus`枚举器包含在源代码管理系统中指定的目录的状态的命名常量值。 此枚举由[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。 这是在源控件插件 API 的 1.2 版中引入的。  
  
## <a name="syntax"></a>语法  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>成员  
 SCC_DIRSTATUS_INVALID  
 无法获取状态;不要依赖于它。  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 目录不是在源代码管理下。  
  
 SCC_DIRSTATUS_CONTROLLED  
 目录是在源代码管理下。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 项目对应于此目录为空。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)