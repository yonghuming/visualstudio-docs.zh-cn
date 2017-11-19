---
title: "IProvideExpressionContexts 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts 接口
使您能够枚举表达式上下文已知的某些组件。 脚本引擎通常实现此接口。  
  
 过程调试管理器使用此接口来查找与给定线程关联的所有全局表达式上下文。  
  
> [!NOTE]
>  此接口是从感兴趣的线程中调用的。 它是取决于实施者，以确定当前线程并返回相应的枚举器。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`IProvideExpressionContexts`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|返回此组件已知的表达式上下文的枚举。|