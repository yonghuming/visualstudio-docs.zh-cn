---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

返回范围的起始地址的部分部件本地符号是有效的。  
  
## 语法  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### 参数  
 `section`  
 \[out\] 返回起始地址范围的部分部件。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
> [!NOTE]
>  一返回的错误代码表示符号没有活动范围信息。  
  
## 备注  
 部分和扭曲窗体的地址是符号是有效范围的开头。  
  
 获取该地址的偏移量部件，使用 [IDiaSymbol::get\_liveRangeStartAddressOffset](../Topic/IDiaSymbol::get_liveRangeStartAddressOffset.md)。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia100.dll  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)