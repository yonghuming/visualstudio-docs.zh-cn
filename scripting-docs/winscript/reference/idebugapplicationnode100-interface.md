---
title: "IDebugApplicationNode100 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 接口"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 接口
`IDebugApplicationNode100` 接口扩展 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)的功能。  通过调用 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)的实现的QI可以获取此接口的实例。  
  
> [!IMPORTANT]
>  此接口由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IDebugApplicationNode100` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|获取文本文档所指定的筛选器隐藏。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|确定指定的文档是否属于某一个此节点的子节点。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|设置在特定的 [IDebugApplicationNodeEvents 接口](../../winscript/reference/idebugapplicationnodeevents-interface.md) 实现的筛选器。  它允许脚本调试器筛选编译器生成的子应用程序节点，以使PDM将不再发送事件，这些节点创建或移除时。  默认情况下，将发送所有节点。|