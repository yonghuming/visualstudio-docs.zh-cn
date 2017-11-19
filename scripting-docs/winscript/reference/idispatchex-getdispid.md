---
title: "IDispatchEx::GetDispID |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
将单个成员名称映射到其相应的 DISPID，随后可在后续调用`IDispatchEx::InvokeEx`。  
  
## <a name="syntax"></a>语法  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>参数  
 `bstrName`  
 传入要映射的名称。  
  
 `grfdex`  
 确定用于获取的成员标识符的选项。 这可以是以下值的组合：  
  
|值|含义|  
|-----------|-------------|  
|fdexNameCaseSensitive|在区分大小写方式中进行的名称查找的请求。 可能会忽略由不支持区分大小写查找的对象。|  
|fdexNameEnsure|请求如果不存在的情况下创建的成员。 应使用的值创建新成员`VT_EMPTY`。|  
|fdexNameImplicit|指示基对象未显式指定时，调用方，对象搜索特定名称的成员。|  
|fdexNameCaseInsensitive|在不区分大小写方式中进行的名称查找的请求。 可能会忽略由不支持不区分大小写查找的对象。|  
  
 `pid`  
 指向调用方分配的位置来接收 DISPID 结果指针。 如果发生错误，`pid`包含 DISPID_UNKNOWN。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|内存不足。|  
|`DISP_E_UNKNOWNNAME`|名称未知。|  
  
## <a name="remarks"></a>备注  
 `GetDispID`可以使用而不是`GetIDsOfNames`获取给定成员的 DISPID。  
  
 因为`IDispatchEx`允许的添加和删除的成员的 Dispid 集不保持不变的对象生存期。  
  
 未使用`riid`中的参数`IDispatch::GetIDsOfNames`已删除。  
  
## <a name="example"></a>示例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)