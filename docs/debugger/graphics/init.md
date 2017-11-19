---
title: "Init |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f32e2e4c5c57359acdc4348f0a83399096383ff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="init"></a>Init
准备图形诊断的应用内组件来主动捕获图形信息并将其记录到图形日志文件。  
  
## <a name="syntax"></a>语法  
  
```C++  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>参数  
 `vsgLogGetter`  
 一个可调用的实体（如函数、函数指针、lambda 或函数对象），它可将由 `wchar_t` 组成的缓冲区长度和指向该缓冲区的指针用作参数，并返回 `void`。 通过调用此可调用的实体，可确定将用于记录图像信息的文件名，并在返回前将其写入指定的缓冲区中。  
  
## <a name="remarks"></a>备注  
 在通过将其构造函数的 `Init` 参数指定为 `VsgDbg` 来构造 `bDefaultInit` 类的实例时将自动调用 `true` 函数；否则，必须在主动捕获并记录图形信息之前显式调用 `Init`。  
  
 可通过调用 `UnInit` 来完成并关闭活动图形日志文件，然后通过再次调用 `Init` 捕获更多的图形信息并将这些信息记录到新图形日志文件。 您可使用相同的 `VsgDbg` 实例将此操作重复所需次数以创建多个单独的图形日志文件。  
  
## <a name="see-also"></a>另请参阅  
 [UnInit](init.md)