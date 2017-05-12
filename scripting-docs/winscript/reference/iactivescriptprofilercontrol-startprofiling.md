---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
分析在脚本引擎的开头。  脚本引擎通过调用创建探查器对象的实例。[CoCreateInstance](http://msdn.microsoft.com/zh-cn/7295a55b-12c7-4ed0-a7a4-9ecee16afdec)。  
  
## 语法  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### 参数  
 `clsidProfilerObject`  
 \[in\]类中标识符\(CLSID要创建的\)探查器对象。  
  
 `dwEventMask`  
 \[in\]一个指定事件类型的4字节的位掩码。  位在 [PROFILER\_EVENT\_MASK 枚举](../../winscript/reference/profiler-event-mask-enumeration.md)定义。  
  
 `dwContext`  
 \[in\]一个传递给探查器对象的4字节的值。  
  
## 返回值  
 返回HRESULT。  可能值如下：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|分析已启用。|  
  
## 请参阅  
 [IActiveScriptProfilerControl 接口](../../winscript/reference/iactivescriptprofilercontrol-interface.md)