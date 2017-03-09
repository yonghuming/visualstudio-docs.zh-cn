---
title: WaitStart | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 5
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4b06fbd524d38e339a8196842200ec3743ee31f4
ms.lasthandoff: 02/22/2017

---
# <a name="waitstart"></a>WaitStart
仅当探查器已初始化，或已超过指定秒数时，WaitStart 选项才使 VSPerfCmd.exe Start 子命令返回。 默认情况下，Start 命令将立即返回。 如果 Start 子命令在未初始化探查器的情况下就返回，则将返回一个错误。 如果未指定秒数，Start 命令将无限期等待。  
  
 WaitStart 选项在批处理文件中十分有用，可确保探查器已经过初始化。  
  
## <a name="syntax"></a>语法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>参数  
 `Seconds`  
 从 Start 子命令返回前要等待的秒数。  
  
## <a name="required-options"></a>必需选项  
 WaitStart 选项仅可与 Start 子命令一起使用。  
  
 **Output:** `filename`  
 指定输出文件名。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 在此批处理示例中，Start 命令将等待 5 秒，探查器才会初始化。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```
