---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`StartProfile` 函数将指定分析级别的计数器设置为 1（开启）。  
  
## 语法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### 参数  
 `Level`  
  
 指示性能数据集合可应用到的分析级别。  下面的 **PROFILE\_CONTROL\_LEVEL** 枚举数可用于指示性能数据集合可应用到的三个级别之一：  
  
|Enumerator|说明|  
|----------------|--------|  
|PROFILE\_GLOBALLEVEL|全局级别设置影响分析运行中的所有进程和线程。|  
|PROFILE\_PROCESSLEVEL|进程级别设置影响指定进程包含的所有线程。|  
|PROFILE\_THREADLEVEL|线程分析级别设置影响指定的线程。|  
  
 `dwId`  
  
 系统生成的进程或线程标识符。  
  
## 属性值\/返回值  
 该函数使用 **PROFILE\_COMMAND\_STATUS** 枚举指示成功或失败。  返回值可以是下列值之一：  
  
|Enumerator|说明|  
|----------------|--------|  
|PROFILE\_ERROR\_ID\_NOEXIST|分析元素 ID 不存在。|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|指定的分析级别不存在。|  
|PROFILE\_ERROR\_MODE\_NEVER|调用该函数时，分析模式设置为 NEVER。|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|分析函数调用、分析级别或者调用和级别的组合尚未实现。|  
|PROFILE\_OK|调用成功。|  
  
## 备注  
 StartProfile 和 StopProfile 控制分析级别的开始\/停止状态。  开始\/停止的默认值为 1。  可在注册表中更改的初始值。  每次调用 StartProfile 会将开始\/停止设置为 1；每次调用 StopProfile 会将其设置为 0。  
  
 当开始\/停止大于 0 时，该级别的开始\/停止状态为 ON。  当它小于或等于 0 时，开始\/停止状态为 OFF。  
  
 当开始\/停止状态和挂起\/继续状态都为 ON 时，该级别的分析状态为 ON。  对于要分析的线程，该线程的全局状态、进程状态和线程级别状态必须为 ON。  
  
## .NET Framework 等效项  
 Microsoft.VisualStudio.Profiler.dll  
  
## 函数信息  
 头：在 VSPerf.h 中声明  
  
 导入库：VSPerf.lib  
  
## 示例  
 下面的示例演示 StartProfile 函数调用。  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 请参阅  
 [Visual Studio 探查器 API 参考（本机）](../profiling/visual-studio-profiler-api-reference-native.md)