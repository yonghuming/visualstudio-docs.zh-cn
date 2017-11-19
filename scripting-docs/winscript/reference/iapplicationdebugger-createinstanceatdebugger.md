---
title: "IApplicationDebugger::CreateInstanceAtDebugger |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
允许调试器进程中的对象的创建，由代码，它是扩展进程到调试器。  
  
> [!IMPORTANT]
>  不应实现此方法，因为它允许不受信任的代码在受信任的调试器线程中创建任意对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `rclsid`  
 [in]类标识符 (CLSID) 的要创建的对象。  
  
 `pUnkOuter`  
 [in]如果`NULL`，并未作为聚合的一部分创建的对象。 否则为`pUnkOuter`是指向聚合对象的指针`IUnknown`接口 (控制`IUnknown`)。  
  
 `dwClsContext`  
 [in]运行可执行代码的上下文。 值，将从枚举`CLSCTX`。  
  
 `riid`  
 [in]使用与对象进行通信的接口标识符。  
  
 `ppvObject`  
 [out]接收请求中的接口指针的指针变量的地址`riid`。 在成功返回时，*`ppvObject`包含请求的接口指针。 在失败\*`ppvObject`包含`NULL`。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法委托给`CoCreateInstance`。  
  
 当前未实现方法。  
  
## <a name="see-also"></a>另请参阅  
 [IApplicationDebugger 接口](../../winscript/reference/iapplicationdebugger-interface.md)