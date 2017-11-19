---
title: "IDispatchEx::GetNextDispID |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
枚举对象的成员。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>参数  
 `grfdex`  
 确定要枚举的项。 这可以是以下值的组合：  
  
|值|含义|  
|-----------|-------------|  
|fdexEnumDefault|请求对象枚举的默认元素。 对象允许枚举的元素的任何组。|  
|fdexEnumAll|请求对象枚举的所有元素。 对象允许枚举的元素的任何组。|  
  
 `id`  
 标识的当前成员。 GetNextDispID 检索后此枚举中的项。 使用 GetDispID 或 GetNextDispID 的以前调用来获取此标识符。 使用 DISPID_STARTENUM 值获取的第一项的第一个标识符。  
  
 `pid`  
 枚举中接收的下一项的标识符的 DISPID 变量的地址。  
  
 如果成员删除了`DeleteMemberByName`或`DeleteMemberByDispID`、`DISPID`需要保持对有效`GetNextDispID`。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|枚举是完成的。|  
  
## <a name="example"></a>示例  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)