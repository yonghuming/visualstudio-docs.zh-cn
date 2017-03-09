---
title: "IDiaSymbol::get_frontEndMinor | Microsoft Docs"
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
  - "IDiaSymbol::get_frontEndMinor 方法"
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索前端次要版本号。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回 front.end 次要版本号。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  返回值为 `S_FALSE` 意味着该属性不是可用于符号。  
  
## <a name="remarks"></a>备注  
 编译器通常由两个主要元素组成︰ 前端 （解析程序），前者用于处理为中间形式分析的源代码，并将中间格式转换为程序集的后端 （代码生成器）。 不常见的前端来安装不同版本比后端。  
  
 前端或后端版本编号由三个部分组成︰ \< 主要>。 \< 次要>。 \< 生成>, ，其中 \< 主要> 是主版本号、 \< 次要> 是次版本号和 \< 生成> 为内部版本号。 例如，13.10.3077。  
  
## <a name="requirements"></a>要求  
  
|要求|描述|  
|-----------------|-----------------|  
|标头：|dia2.h|  
|版本:|DIA SDK 7.0 版|  
  
## <a name="see-also"></a>另请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)