---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`NameProfile` 函数会将字符串分配给指定的进程或线程。  
  
 NameProfile API 仅用于检测分析。  NameProfile API 不用于取样分析。  
  
## 语法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### 参数  
 `pszName`  
  
 分析元素的名称。  名称无效（导致 NameProfileA 返回 NAME\_ERROR\_INVALID\_NAME）的原因：  
  
-   传入 NameProfileA 的指针是一个 NULL 值  
  
-   pszName 的字符串数据以数字开头  
  
-   pszName 的字符串数据包含空格  
  
-   pszName 的字符串数据包含以下任意字符: ,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 指示性能数据集合可应用到的分析级别。  下面的 **PROFILE\_CONTROL\_LEVEL** 值可用于指示性能数据集合可应用到的三个级别之一：  
  
|Enumerator|说明|  
|----------------|--------|  
|PROFILE\_GLOBALLEVEL|全局级别设置影响分析运行中的所有进程和线程。|  
|PROFILE\_PROCESSLEVEL|进程级别设置影响指定进程包含的所有线程。|  
|PROFILE\_THREADLEVEL|线程分析级别设置影响指定的线程。|  
  
 `dwId`  
  
 分析级别标识符。  使用系统生成的进程或线程标识符。  
  
## 属性值\/返回值  
 该函数使用 **PROFILE\_COMMAND\_STATUS** 枚举指示成功或失败。  返回值可以是下列值之一：  
  
|Enumerator|说明|  
|----------------|--------|  
|NAME\_ERROR\_ID\_NOEXIST|指定的分析元素不存在。|  
|NAME\_ERROR\_INVALID\_NAME|名称无效。|  
|NAME\_ERROR\_LEVEL\_NOEXIST|指定的分析级别不存在。|  
|NAME\_ERROR\_NO\_SUPPORT|不支持指定的操作。|  
|NAME\_ERROR\_OUTOFMEMORY|内存不可用于记录事件。|  
|NAME\_ERROR\_REDEFINITION|已经为分析元素分配了名称。  此函数中的名称被忽略。|  
|NAME\_ERROR\_TEXTTRUNCATED|包括 null 字符在内的名称文本超过 32 个字符，所以被截断。|  
|NAME\_OK|名称已成功注册。|  
  
## 备注  
 只能为每个进程或线程分配一个名称。  命名分析元素后，会忽略对该元素的 NameProfile 的后续调用。  
  
 如果为不同线程或进程指定了相同名称，则报告中将包含来自该级别中所有具有该名称的元素的数据。  
  
 如果指定当前进程或线程以外的进程或线程，则必须确保在命名之前该进程或线程已初始化并已开始运行。  否则，NameProfile 方法会失败。  
  
> [!IMPORTANT]
>  CreateProcess\(\) 和 CreateThread\(\) API 函数可在初始化其创建的线程或进程之前返回。  
  
## .NET Framework 等效项  
 Microsoft.VisualStudio.Profiler.dll  
  
## 函数信息  
  
|||  
|-|-|  
|**Header**|包含 VSPerf.h|  
|**库**|使用 VSPerf.lib|  
|**Unicode**|作为 `NameProfileW` \(Unicode\) 和 `NameProfileA` \(ANSI\) 实现。|  
  
## 示例  
 下面的代码演示 NameProfile 函数调用。  该示例使用 Win32 字符串宏和 ANSI 编译器设置，确定代码是否调用启用了 ANSI 的函数。  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 请参阅  
 [Visual Studio 探查器 API 参考（本机）](../profiling/visual-studio-profiler-api-reference-native.md)