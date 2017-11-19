---
title: "IDebugApplicationNodeEvents 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents 接口
提供有关的事件接口`IDebugApplicationNode`接口。  
  
 除了从继承的方法`IUnknown`、`IDebugApplicationNodeEvents`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|处理事件的子节点添加到调试应用程序节点对象时。|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|处理事件时从调试应用程序节点对象中删除一个子节点。|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|处理表明调试应用程序节点对象已分离从父节点的事件。|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|处理表明调试应用程序节点对象已附加到父节点的事件。|  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)