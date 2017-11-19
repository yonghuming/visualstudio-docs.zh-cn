---
title: "IActiveScript::GetScriptThreadState |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
检索脚本线程的当前状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>参数  
 `stidThread`  
 [in]为其状态所需的线程的标识符或以下特殊线程标识符：  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|基线程;也就是说，在其中的脚本引擎的线程已实例化。|  
|SCRIPTTHREADID_CURRENT|当前正在执行的线程。|  
  
 `pstsState`  
 [out]一个变量来接收指示线程的状态的地址。 状态由一个定义的命名常量值[SCRIPTTHREADSTATE 枚举](../../winscript/reference/scriptthreadstate-enumeration.md)枚举。 如果此参数不会确定当前线程，随时可能更改状态。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了无效的指针。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎具有尚未加载或初始化）。|  
  
## <a name="remarks"></a>备注  
 此方法可以从非基本线程调用不会导致为主机对象或设置为非基本标注[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)接口。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)