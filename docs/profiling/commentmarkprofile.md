---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`CommentMarkProfile` 函数在 .vsp 文件中插入数值标记和文本字符串。  为了插入标记和注释，对包含 `CommentMarkProfile` 函数的线程进行的分析必须为 ON。  
  
## 语法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### 参数  
 `lMarker`  
  
 要插入的数值标记。  该标记必须大于或等于 0（零）。  
  
 `szComment`  
  
 指向要插入的文本字符串的指针。  该字符串的长度必须小于 256 个字符（包括 NULL 结束符）。  
  
## 属性值\/返回值  
 该函数使用 **PROFILE\_COMMAND\_STATUS** 枚举指示成功或失败。  返回值可以是下列值之一：  
  
|Enumerator|说明|  
|----------------|--------|  
|MARK\_ERROR\_MARKER\_RESERVED|参数小于或等于 0。  会保留这些值。  未记录标记和注释。|  
|MARK\_ERROR\_MODE\_NEVER|调用该函数时，分析模式设置为 NEVER。  未记录标记和注释。|  
|MARK\_ERROR\_MODE\_OFF|调用该函数时，分析模式设置为 OFF。  未记录标记和注释。|  
|MARK\_ERROR\_NO\_SUPPORT|在此上下文中不支持标记。  未记录标记和注释。|  
|MARK\_ERROR\_OUTOFMEMORY|内存不可用于记录事件。  未记录标记和注释。|  
|MARK\_TEXTTOOLONG|字符串长度超过最大 256 个字符的限制。  注释字符串被截断，并记录了标记和注释。|  
|MARK\_OK|返回 MARK\_OK 指示成功。|  
  
## 备注  
 当通过 VSInstr Mark 命令或函数（CommentMarkAtProfile、CommentMarkProfile 或 MarkProfile）插入标记和注释时，包含标记分析函数的线程的分析状态必须为开启。  
  
 分析标记具有全局范围。  例如，插入到一个线程中的分析标记可用于标记 .vsp 文件中任何线程的数据段的开始或结束。  
  
> [!IMPORTANT]
>  CommentMarkProfile 方法只能用于检测。  
  
## .NET Framework 等效项  
 Microsoft.VisualStudio.Profiler.dll  
  
## 函数信息  
  
|||  
|-|-|  
|**Header**|包含 VSPerf.h|  
|**库**|使用 VSPerf.lib|  
|**Unicode**|作为 `CommentMarkProfileW` \(Unicode\) 和 `CommentMarkProfileA` \(ANSI\) 实现。|  
  
## 示例  
 下面的代码演示 CommentMarkProfile 函数调用。  该示例假定使用 Win32 字符串宏和 Unicode 编译器设置来确定代码是否调用了 [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] 函数调用。  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 请参阅  
 [Visual Studio 探查器 API 参考（本机）](../profiling/visual-studio-profiler-api-reference-native.md)