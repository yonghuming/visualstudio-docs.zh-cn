---
title: "Idiaframedata:: Get_program |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a26982c1827b9d9b4a7ed09e8aa3af61c9141c9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
检索用于计算的寄存器集之前对当前函数的调用的程序字符串。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回程序字符串。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`如果不支持此属性。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 程序字符串为宏的序列，以便建立序言解释。 例如，典型的堆栈帧可能会使用程序字符串`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`。 格式为反向波兰语表示法，其中这些运算符遵循操作数。 `T0`表示在堆栈上的临时变量。 此示例将执行以下步骤：  
  
1.  将寄存器的内容移动`ebp`到`T0`。  
  
2.  添加`4`到中的值`T0`可以生成一个地址、 从该地址获取的值和值存储在寄存器`eip`。  
  
3.  从存储中的地址获取该值`T0`，并将该值存储在寄存器中`ebp`。  
  
4.  添加`8`到中的值`T0`，并将该值存储在寄存器中`esp`。  
  
 请注意，程序字符串是特定于 CPU 设置为表示由当前的堆栈帧的函数的调用约定。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)