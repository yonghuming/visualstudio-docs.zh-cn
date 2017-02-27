---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program 方法"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索用于计算在调用之前设置的注册到当前函数的程序字符串。  
  
## 语法  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回程序字符串。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果此属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 程序字符串被解释以便建立序言宏的序列。  例如，典型的堆栈帧可能使用程序 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`字符串。  布局是逆波兰表示形式，运算符按照操作数。  `T0` 表示堆栈上的一个临时变量。  此示例执行以下步骤:  
  
1.  移动注册 `ebp` 内容移到 `T0`。  
  
2.  添加 `4` 到 `T0` 的值生成地址，以便从该地址处的值，并将值存储在注册 `eip`。  
  
3.  获取在注册 `ebp`值从在 `T0` 存储的地址处的值和存储。  
  
4.  添加 `8` 到 `T0` 的值并存储该值在注册 `esp`。  
  
 请注意程序字符串是特定于 CPU 和到当前堆栈帧表示的函数的调用约定设置。  
  
## 请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)