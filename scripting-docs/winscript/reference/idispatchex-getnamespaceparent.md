---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNameSpaceParent 方法"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
检索对象的命名空间父的接口。  
  
## 语法  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### 参数  
 `ppunk`  
 接收命名空间父的接口 `IUnknown` 接口指针的地址。  
  
## 返回值  
 返回 `S_OK`，如果成功或OLE中定义的错误代码否则为。  
  
## 请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)