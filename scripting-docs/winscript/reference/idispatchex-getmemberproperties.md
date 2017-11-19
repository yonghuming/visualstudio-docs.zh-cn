---
title: "IDispatchEx::GetMemberProperties |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
检索成员的属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>参数  
 `id`  
 标识成员。 使用`GetDispID`或`GetNextDispID`若要获取调度标识符。  
  
 `grfdexFetch`  
 确定要检索的属性。 这可以是下列出的值的组合`pgrfdex`和/或以下值的组合：  
  
|值|含义|  
|-----------|-------------|  
|grfdexPropCanAll|将合并 fdexPropCanGet、 fdexPropCanPut、 fdexPropCanPutRef、 fdexPropCanCall、 fdexPropCanConstruct 和 fdexPropCanSourceEvents。|  
|grfdexPropCannotAll|将合并 fdexPropCannotGet、 fdexPropCannotPut、 fdexPropCannotPutRef、 fdexPropCannotCall、 fdexPropCannotConstruct 和 fdexPropCannotSourceEvents。|  
|grfdexPropExtraAll|将 fdexPropNoSideEffects 和 fdexPropDynamicType 合并。|  
|grfdexPropAll|将合并 grfdexPropCanAll、 grfdexPropCannotAll 和 grfdexPropExtraAll。|  
  
 `pgrfdex`  
 地址`DWORD`接收请求的属性。 这可以是以下值的组合：  
  
|值|含义|  
|-----------|-------------|  
|fdexPropCanGet|可以使用 DISPATCH_PROPERTYGET 获取该成员。|  
|fdexPropCannotGet|无法使用 DISPATCH_PROPERTYGET 获得成员。|  
|fdexPropCanPut|可以使用 DISPATCH_PROPERTYPUT 设置成员。|  
|fdexPropCannotPut|成员不能通过 DISPATCH_PROPERTYPUT 设置。|  
|fdexPropCanPutRef|可以使用 DISPATCH_PROPERTYPUTREF 设置成员。|  
|fdexPropCannotPutRef|成员不能通过 DISPATCH_PROPERTYPUTREF 设置。|  
|fdexPropNoSideEffects|成员没有任何副作用。 例如，调试器无法安全地 get/组/调用此成员而无需更改正在调试的脚本的状态。|  
|fdexPropDynamicType|成员是动态的并且可在对象的生命周期中更改。|  
|fdexPropCanCall|可以作为一种方法使用 DISPATCH_METHOD 调用成员。|  
|fdexPropCannotCall|不能作为一种方法使用 DISPATCH_METHOD 调用成员。|  
|fdexPropCanConstruct|可以作为构造函数使用 DISPATCH_CONSTRUCT 调用成员。|  
|fdexPropCannotConstruct|不能作为构造函数使用 DISPATCH_CONSTRUCT 调用成员。|  
|fdexPropCanSourceEvents|成员可以激发事件。|  
|fdexPropCannotSourceEvents|成员不能激发事件。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|名称未知。|  
  
## <a name="example"></a>示例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)