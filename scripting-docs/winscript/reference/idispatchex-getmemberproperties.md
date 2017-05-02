---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties 方法"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
检索成员的特性。  
  
## 语法  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### 参数  
 `id`  
 标识成员。  使用 `GetDispID` 或 `GetNextDispID` 获取调度标识符。  
  
 `grfdexFetch`  
 确定检索哪些属性。  这可能是值的组合列表中 `pgrfdex` 下和\/或下列值的组合：  
  
|值|含义|  
|-------|--------|  
|grfdexPropCanAll|合并fdexPropCanGet、fdexPropCanPut、fdexPropCanPutRef、fdexPropCanCall、fdexPropCanConstruct和fdexPropCanSourceEvents。|  
|grfdexPropCannotAll|合并fdexPropCannotGet、fdexPropCannotPut、fdexPropCannotPutRef、fdexPropCannotCall、fdexPropCannotConstruct和fdexPropCannotSourceEvents。|  
|grfdexPropExtraAll|合并fdexPropNoSideEffects和fdexPropDynamicType。|  
|grfdexPropAll|合并grfdexPropCanAll、grfdexPropCannotAll和grfdexPropExtraAll。|  
  
 `pgrfdex`  
 接收请求的属性 `DWORD` 的地址。  该位置可以是下列值的组合：  
  
|值|含义|  
|-------|--------|  
|fdexPropCanGet|使用DISPATCH\_PROPERTYGET，该成员可用。|  
|fdexPropCannotGet|使用DISPATCH\_PROPERTYGET，该成员不能获得。|  
|fdexPropCanPut|使用DISPATCH\_PROPERTYPUT，该成员可以设置。|  
|fdexPropCannotPut|使用DISPATCH\_PROPERTYPUT，该成员不能设置。|  
|fdexPropCanPutRef|使用DISPATCH\_PROPERTYPUTREF，该成员可以设置。|  
|fdexPropCannotPutRef|使用DISPATCH\_PROPERTYPUTREF，该成员不能设置。|  
|fdexPropNoSideEffects|该成员没有任何副作用。  例如，调试器安全性可能get\/set\/调用此成员，而不更改正在调试的脚本的状态。|  
|fdexPropDynamicType|在对象的生存期内，该成员是动态的，它可以更改。|  
|fdexPropCanCall|使用DISPATCH\_METHOD，该成员可以调用作为方法。|  
|fdexPropCannotCall|使用DISPATCH\_METHOD，该成员不能调用作为方法。|  
|fdexPropCanConstruct|使用DISPATCH\_CONSTRUCT，该成员可以调用作为构造函数。|  
|fdexPropCannotConstruct|使用DISPATCH\_CONSTRUCT，该成员不能调用作为构造函数。|  
|fdexPropCanSourceEvents|该成员可激发事件。|  
|fdexPropCannotSourceEvents|该成员不能激发事件。|  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|该名称不知道。|  
  
## 示例  
  
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
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)