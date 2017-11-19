---
title: "IDispError 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>IDispError 接口
提供详细的上下文错误的信息。  
  
> [!NOTE]
>  未实现此接口。  
  
 除了从继承的方法`IUnknown`、`IDispError`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|检索特定类型的错误信息。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|检索下一步`IDispError`对象。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|检索中的错误代码`IDispError`对象。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|返回的类或引发错误的应用程序依赖于语言的编程标识符。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|返回的帮助文件的路径和解释该错误，如有可能的主题的上下文 ID。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|返回错误的文本说明。|