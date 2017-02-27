---
title: "IDiaStackWalkHelper | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2 接口"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

遍历堆栈使用程序的 Facilitates 调试数据库 \(.pdb\) 文件。  
  
## 语法  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## 方法按 VTable 顺序  
 下表显示 `IDiaStackWalkHelper`方法:  
  
|方法|说明|  
|--------|--------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|检索注册的值。|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|设置寄存器值。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|读取数据时阻止可执行图像的内存中。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|搜索指定的堆栈帧最新的函数的返回地址。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|搜索指定的堆栈帧返回地址的某些构造指定的堆栈地址。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|检索包含指定的虚拟地址的堆栈帧。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|检索包含指定的虚拟地址的符号。 **Note:**  符号必须具有该类型 `SymTagFunctionType` \(从 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 枚举的值\)。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|返回 PDATA 数据块与该指定的虚拟地址。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|检索启动的虚拟地址可执行命名虚拟地址是位于可执行的内存空间。|  
  
## 备注  
 此接口由 DIA 代码调用以获取有关可执行文件的信息构造列表堆栈帧在程序执行期间。  
  
## 调用方的说明  
 客户端应用程序实现此接口支持遍历堆栈在程序执行期间。  此接口的实例传递给 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) 或 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 方法。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)