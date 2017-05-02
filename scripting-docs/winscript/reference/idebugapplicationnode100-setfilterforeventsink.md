---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
设置在特定的 [IDebugApplicationNodeEvents 接口](../../winscript/reference/idebugapplicationnodeevents-interface.md) 实现的筛选器。  它允许脚本调试器筛选编译器生成的子应用程序节点，以使PDM将不再发送事件，当这些已创建或已移除时。  默认情况下，将发送所有节点。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md) 由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### 参数  
 `dwCookie`  
 筛选器的cookie。  
  
 `filter`  
 筛选器。  
  
## 请参阅  
 [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md)