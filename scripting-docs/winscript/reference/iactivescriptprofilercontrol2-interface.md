---
title: "IActiveScriptProfilerControl2 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bc0dfa31b37a6bf99427c8eddfe2bd038da9b9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 接口
提供添加启动或停止分析运行脚本时的功能的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|通知探查器已启动所有适用的脚本引擎上进行分析。 这使您能够获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]开始分析时处于运行状态。|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|通知探查器将停止所有适用的脚本引擎上进行分析。 这使您能够获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]时停止分析运行。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerControl 接口](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Active Script Profiler 接口](../../winscript/reference/active-script-profiler-interfaces.md)