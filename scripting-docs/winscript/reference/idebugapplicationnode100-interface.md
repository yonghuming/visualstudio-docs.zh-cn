---
title: "IDebugApplicationNode100 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 接口
`IDebugApplicationNode100`接口扩展的功能[IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)。 此接口的实例可以通过调用的实现 QueryInterface [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)。  
  
> [!IMPORTANT]
>  实现此接口由 PDM 10.0 版和更高。 在 activdbg100.h 中发现。  
  
## <a name="methods"></a>方法  
 `IDebugApplicationNode100` 接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|获取由指定的筛选器隐藏的文本文档。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|确定此节点的子节点之一是否属于指定的文档。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|对特定设置的筛选器[IDebugApplicationNodeEvents 接口](../../winscript/reference/idebugapplicationnodeevents-interface.md)实现。 它允许脚本调试器，若要筛选出编译器生成的子应用程序节点，以便 PDM 将不再发送事件时创建或删除节点。 默认情况下，将发送所有节点。|