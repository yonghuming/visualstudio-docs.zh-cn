---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID 方法"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
映射单个成员名称对其对应的DISPID，在随后可以使用的后续调用 `IDispatchEx::InvokeEx`。  
  
## 语法  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### 参数  
 `bstrName`  
 通过在要映射的名称。  
  
 `grfdex`  
 确定获取成员标识符的选项。  该位置可以是下列值的组合：  
  
|值|含义|  
|-------|--------|  
|fdexNameCaseSensitive|请求名称查找完成以区分大小写的方法。  不支持区分大小写的查找的对象忽略。|  
|fdexNameEnsure|请求成员创建，如果它已不存在。  新成员应当由该值 `VT_EMPTY`创建。|  
|fdexNameImplicit|指示调用方对象搜索特定名称的成员，则基对象未显式指定。|  
|fdexNameCaseInsensitive|请求名称查找完成以不区分大小写的方法。  不支持不区分大小写的查找的对象忽略。|  
  
 `pid`  
 用于接收DISPID结果的调用方分配的位置的指针。  如果发生错误，`pid` 包含DISPID\_UNKNOWN。  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|内存不足。|  
|`DISP_E_UNKNOWNNAME`|该名称不知道。|  
  
## 备注  
 `GetDispID` 可用于而不是 `GetIDsOfNames` 获取对特定成员的DISPID。  
  
 由于 `IDispatchEx` 允许成员的添加和删除，设置Dispid不保持不变为对象的生存期。  
  
 移除了 `IDispatch::GetIDsOfNames` 中未使用的 `riid` 参数。  
  
## 示例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)