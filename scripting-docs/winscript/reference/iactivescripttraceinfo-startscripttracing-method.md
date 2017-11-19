---
title: "Iactivescripttraceinfo:: Startscripttracing 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing 方法
启动脚本跟踪。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>参数  
 `pSiteTraceInfo`  
 指向主机的 IActiveScriptSiteTraceInfo 的指针。  
  
 `guidContextId`  
 上下文的 GUID。  
  
## <a name="return-value"></a>返回值  
 此方法可能的返回值如下所示：  
  
1.  则为 S_OK： 成功。  
  
2.  E_POINTER:`pSiteTraceInfo`是 NULL 指针。  
  
3.  E_NOTIMPL： 未实现。