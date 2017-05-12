---
title: "IDispatchEx::GetMemberName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberName 方法"
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberName
检索成员的名称。  
  
## 语法  
  
```  
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### 参数  
 `id`  
 标识成员。  使用 `GetDispID` 或 `GetNextDispID` 获取调度标识符。  
  
 `pbstrName`  
 接收该成员的名称 `BSTR` 的地址。  调用应用程序传递给释放此值来。  
  
## 返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|该名称不知道。|  
  
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
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)