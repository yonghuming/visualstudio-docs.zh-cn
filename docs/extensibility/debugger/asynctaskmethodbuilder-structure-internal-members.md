---
title: "AsyncTaskMethodBuilder 结构的内部成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0ada26c32124bf2666e1556663ad7043e0d0ffe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 结构的内部成员
本主题介绍的内部成员<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>类。 有关此类的常规信息，请参阅<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>参考主题。  
  
 **命名空间：** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **程序集：** mscorlib （mscorlib.dll) 中  
  
 由于无法访问这些内部成员在.NET Framework 中，以下语法提供共同点中间语言 (CIL)。  
  
## <a name="syntax"></a>语法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>内部成员  
  
|名称|描述|  
|----------|-----------------|  
|[ObjectIdForDebugger 属性](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|获取可用于唯一标识调试器到此生成器的对象。|  
|[m_builder 字段](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|表示此非泛型实例将委托的泛型生成器对象。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [.NET Framework 的并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)