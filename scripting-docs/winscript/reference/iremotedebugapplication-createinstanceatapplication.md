---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
允许对象的创建在中由进程外对应用程序的代码应用程序进程。  
  
## 语法  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### 参数  
 `rclsid`  
 \[in\]类中标识符\(以捕获对象创建。  
  
 `pUnkOuter`  
 \[in\]充当聚合一部分，因此，如果 `NULL`，就不能创建对象。  否则，`pUnkOuter` 是指向复合对象的 `IUnknown` 接口\(控件 `IUnknown`\)。  
  
 `dwClsContext`  
 \[in\]运行的可执行代码上下文。  值从枚举 `CLSCTX`中采用。  
  
 `riid`  
 \[in\]用于的接口标识符与对象进行通信。  
  
 `ppvObject`  
 \[out\] `riid` 指针变量的地址，该变量接收请求的接口指针。  在成功返回，\*`ppvObject` 包含请求的接口指针。  在失败，\*`ppvObject` 包含 `NULL`。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `CoCreateInstance`的此方法委托。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)