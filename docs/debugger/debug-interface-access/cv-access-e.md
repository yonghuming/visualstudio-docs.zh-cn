---
title: "CV_access_e | Microsoft Docs"
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
  - "CV_access_e 枚举"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定范围可见性 \(访问级别\) 成员函数和变量。  
  
## 语法  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elements  
 CV\_private  
 成员有权访问私有。  
  
 CV\_protected  
 保护成员访问。  
  
 CV\_public  
 成员具有公共访问权限。  
  
## 备注  
 `friend` 访问说明符此处不包括，因为可以访问类的私有的和受保护的元素的非成员函数通常使用它。  使用 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) 方法来查找具有 `SymTagFriend` 访问的符号。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)