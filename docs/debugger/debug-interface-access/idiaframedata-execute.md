---
title: "Idiaframedata:: Execute |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b284e466ce751e86f488203b4b22c0c18c6573
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
执行堆栈展开，并返回的结果中的堆栈审核帧接口。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>参数  
 `frame`  
 [in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)保留帧寄存器状态的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示可能的此方法的返回值。  
  
|值|描述|  
|-----------|-----------------|  
|E_DIA_INPROLOG|无法执行在序言代码的堆栈帧。|  
|E_DIA_SYNTAX|分析框架程序中遇到错误。|  
|E_DIA_FRAME_ACCESS|无法访问寄存器或内存。|  
|E_DIA_VALUE|计算的值 （例如，被零除） 中的错误。|  
  
## <a name="remarks"></a>备注  
 若要展开堆栈在调试期间调用此方法。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)对象由客户端应用程序接收到寄存器的更新，以便使用的方法实现`execute`方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)