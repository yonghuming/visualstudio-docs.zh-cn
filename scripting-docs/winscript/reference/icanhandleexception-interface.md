---
title: "ICanHandleException 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ICanHandleException interface
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfd9fe2c766d3c390382ccfbcf2a8fd2319e48f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexception-interface"></a>ICanHandleException 接口
允许调用方的脚本引擎的调用方，来指定哪些异常句柄。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`ICanHandleException`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|确定脚本引擎的调用方可以处理指定的异常。|