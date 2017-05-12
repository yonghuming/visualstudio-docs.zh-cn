---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName 方法"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
按删除成员。  
  
## 语法  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### 参数  
 `bstrName`  
 成员的名称将被删除。  
  
 `grfdex`  
 确定成员名称是否区分大小写。  该位置可以是下列值之一：  
  
|值|含义|  
|-------|--------|  
|fdexNameCaseSensitive|请求名称查找完成以区分大小写的方法。  可以通过不支持区分大小写的查找的对象忽略。|  
|fdexNameCaseInsensitive|请求名称查找完成以不区分大小写的方法。  可以通过不支持不区分大小写的查找的对象忽略。|  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成员存在，但不能删除。|  
  
## 备注  
 如果成员删除，DISPID需要保持有效。`GetNextDispID`。  
  
 如果具有给定名称的成员被删除，并且具有相同名称的成员后重新创建，DISPID应相同。  \(仅通过大小写不同的成员是否为“同样”是对象相关。\)  
  
## 示例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)