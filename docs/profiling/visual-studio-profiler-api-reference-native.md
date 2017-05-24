---
title: "Visual Studio 探查器 API 参考（本机）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: 142df9fbf327ee8ebc39c3558ef1632a1bd23ae7
ms.contentlocale: zh-cn
ms.lasthandoff: 05/03/2017

---
# <a name="visual-studio-profiler-api-reference-native"></a>Visual Studio 探查器 API 参考（本机）
Visual Studio 探查器 API 允许你以编程方式控制收集的数据量，并在分析期间插入时间戳和分析标记。 若要使用本机 API，请包含 VSPerf.h 头文件，并在项目中添加 VSPerf.lib。  
  
> [!NOTE]
>  默认情况下，VSPerf.h 和 VSPerf.lib 位于“PerfSDK”文件夹中。 例如，\<drive>:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK 目录。  
  
## <a name="in-this-section"></a>本节内容  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>另请参阅  
 [分析工具 API](../profiling/profiling-tools-apis.md)   
 [演练：使用探查器 API](../profiling/walkthrough-using-profiler-apis.md)

