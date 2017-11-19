---
title: "UnInit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
完成图形日志文件，将其关闭，并且在应用主动记录图形信息时释放已使用的资源。  
  
## <a name="syntax"></a>语法  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>备注  
 在销毁 `UnInit` 类的实例后自动调用 `VsgDbg`。 如果 `VsgDbg` 实例未主动记录图形信息，则此操作不起作用。  
  
 在对 `UnInit` 类的实例调用 `VsgDbg` 之后，可通过调用 `Init` 创建新的图形日志文件，并通过调用 `UnInit` 完成此日志文件。 您可以重复此操作所需次数以使用相同的 `VsgDbg` 实例来创建多个独立的图形日志文件。  
  
## <a name="see-also"></a>另请参阅  
 [Init](init.md)