---
title: "IDiaStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalker 接口"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用在 .pdb 文件，的信息的方法执行堆栈审核。  
  
## 语法  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaStackWalker`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|检索 x86 平台的一个堆栈帧枚举数。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|检索特定平台类型的一个堆栈帧枚举数。|  
  
## 备注  
 此接口用于获取堆栈帧列出一个加载模块的。  每个方法通过提供必要的信息生成堆栈帧列表的 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 对象 \(实现由客户端应用程序\)。  
  
## 调用方的说明  
 此接口通过调用 `CoCreateInstance` 方法获取与类标识符 `CLSID_DiaStackWalker` 和 `IID_IDiaStackWalker`接口 ID。  该示例演示如何获取此接口。  
  
## 示例  
 此示例演示如何获取 `IDiaStackWalker` 接口。  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)