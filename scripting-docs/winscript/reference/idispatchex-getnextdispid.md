---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID 方法"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
枚举对象的成员。  
  
## 语法  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### 参数  
 `grfdex`  
 确定将项目设置为将枚举。  该位置可以是下列值的组合：  
  
|值|含义|  
|-------|--------|  
|fdexEnumDefault|请求对象枚举默认元素。  使用对象枚举任何元素。|  
|fdexEnumAll|请求对象枚举所有元素。  使用对象枚举任何元素。|  
  
 `id`  
 标识名当前成员。  GetNextDispID在这一步骤后检索枚举中的项目。  使用GetDispID或以前调用了GetNextDispID获取此标识符。  使用DISPID\_STARTENUM值获取第一项的第一个标识符。  
  
 `pid`  
 接收下一个项ID在枚举的DISPID变量的地址。  
  
 如果成员。`DeleteMemberByName` 或 `DeleteMemberByDispID`删除，`DISPID` 需要保持有效。`GetNextDispID`。  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|枚举完成。|  
  
## 示例  
  
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
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)