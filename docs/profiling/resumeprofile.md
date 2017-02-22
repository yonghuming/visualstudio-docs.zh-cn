---
title: "ResumeProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ResumeProfile"
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ResumeProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ResumeProfile` 方法递减指定分析级别的挂起\/继续计数器的值。  
  
## 语法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
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
 Suspend\/Resume 计数器的初始值是 0。  每次调用 SuspendProfile 都会将挂起\/继续计数加一；每次调用 ResumeProfile 则会将其减一。  
  
 当挂起\/继续计数大于 0 时，该级别的挂起\/继续状态为 OFF。  当该计数小于或等于 0 时，挂起\/继续状态为 ON。  
  
 当开始\/停止状态和挂起\/继续状态都为 ON 时，该级别的分析状态为 ON。  对于要分析的线程，该线程的全局状态、进程状态和线程级别状态都必须为 ON。  
  
## .NET Framework 等效项  
 Microsoft.VisualStudio.Profiler.dll  
  
## 函数信息  
 头：在 VSPerf.h 中声明  
  
 导入库：VSPerf.lib  
  
## 示例  
 下面的示例演示 ResumeProfile 函数。  该示例假定已对由 [PROFILE\_CURRENTID](../profiling/profile-currentid.md) 标识的同一线程或进程调用了 SuspendProfile 方法。  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 请参阅  
 [Visual Studio 探查器 API 参考（本机）](../profiling/visual-studio-profiler-api-reference-native.md)