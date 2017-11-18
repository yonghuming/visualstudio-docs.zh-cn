---
title: "IActiveScript::Close |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
使脚本引擎放弃任何当前加载的脚本，丢失其状态，并释放任何它具有对其他对象，因此输入已关闭的状态的接口指针。 事件接收器、 立即执行的脚本文本和已正在进行的宏调用完成之前的状态更改 (使用[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)取消正在运行的脚本线程)。 接口释放以防止出现循环引用问题之前，必须创建主机调用此方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|值|含义|  
|-----------|-------------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|不应调用 （例如，脚本引擎本来就处于关闭状态）。|  
|`OLESCRIPT_S_PENDING`|此方法已排队成功，但尚未未更改状态。 当状态更改站点是在回叫[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|方法成功，但该脚本已关闭。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)