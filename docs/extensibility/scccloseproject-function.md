---
title: "SccCloseProject 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCloseProject
helpviewer_keywords: SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d37dc9bff7652856109fb4ec29c8eaa52f1d2507
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="scccloseproject-function"></a>SccCloseProject 函数
此函数将关闭项目，将标记特定会话的末尾。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 源控件插件上下文结构。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功关闭该项目。|  
|SCC_E_PROJNOTOPEN|不没有当前打开任何项目。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 [SccOpenProject](../extensibility/sccopenproject-function.md)始终将在此函数之前调用。 对此函数的调用后跟调用`SccOpenProject`函数或[SccUninitialize](../extensibility/sccuninitialize-function.md)，以便完全结束到源代码管理系统的连接。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)