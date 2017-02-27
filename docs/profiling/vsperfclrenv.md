---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令行工具, VSPerfCLREnv"
  - "命令行, 工具"
  - "性能工具, VSPerfCLREnv"
  - "分析工具, VSPerfCLREnv"
  - "VSPerfCLREnv 工具"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCLREnv 工具用于设置配置 .NET Framework 应用程序所需的环境变量。  它使用以下语法：  
  
```  
VsPerfCLREnv [/option]  
```  
  
 您选择的选项取决于您使用的分析属于以下三种分析类型的哪一种：取样、检测或全局。  需要单独选项来将层交互数据包含在分析数据中。  下面的表中描述了每个选项的语法。  
  
> [!NOTE]
>  完成分析后，运行带有 **\/off** 或 **\/globaloff** 选项的 **VSPerfCLREnv** 可删除分析所需的环境变量。  有关更多信息，请参见此处显示的“用于删除环境设置的 VSPerfCLREnv 选项”。  
  
 **用于包括层交互数据的 VSPerfCLREnv 选项**  
  
> [!WARNING]
>  可使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], or [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] 收集层交互分析.  然而层交互分析数据只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 和 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中查看。  
  
 层交互分析提供了有关在多层应用程序中进行 ADO.NET 查询的附加信息。  收集的数据仅用于同步函数调用。  可以使用任何分析方法向任何分析运行中添加交互数据。  
  
 **InteractionOn** 和 **GlobalInteractionOn** 选项启用层交互数据的收集。  在设置分析应用程序所需的 VSPerfCLREnv 环境变量后，必须设置交互选项。  
  
 下面的示例在使用采样方法的分析运行中包括层交互数据：  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 下面的示例包括在 Windows 服务的分析运行中的层交互数据：  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **用于进程检测分析的 VSPerfCLREnv 选项**  
  
 下表描述了用于检测分析的 VSPerfCLREnv 选项：  
  
|选项|说明|  
|--------|--------|  
|**TraceOn**|使用检测方法启用分析。  不启用内存分配分析或对象生存期数据收集。|  
|**TraceGC**|使用检测方法启用内存分配分析。  不启用对象生存期数据收集。|  
|**TraceGCLife**|启用通过用检测方法分析内存分配和收集对象生存期数据的功能。|  
  
 **用于进程采样分析的 VSPerfCLREnv 选项**  
  
 下表描述了用于取样分析的 VSPerfCLREnv 选项：  
  
|选项|说明|  
|--------|--------|  
|**SampleOn**|使用采样方法启用分析。  不启用内存分配分析或对象生存期数据收集。|  
|**SampleGC**|使用采样方法启用内存分配分析。  不启用对象生存期数据收集。|  
|**SampleGCLife**|使用采样方法启用内存分配分析。  也启用对象生存期数据收集。|  
|**SampleLineOff**|禁用收集 .NET 行级分析数据。|  
  
 **用于全局分析的 VSPerfCLREnv 选项**  
  
 若要分析由操作系统（而不是用户）启动的托管服务（如 ASP.NET Web 应用程序），请使用 VSPerfCLREnv 选项中的全局分析选项。  下表描述了 VSPerfCLREnv 选项的全局版本。  这些选项用于在注册表中设置相应的环境变量。  
  
|选项|说明|  
|--------|--------|  
|**GlobalTraceOn**|使用检测方法启用全局分析。  不收集内存分配事件或对象生存期数据。|  
|**GlobalTraceGC**|使用检测方法启用全局内存分配分析。  不启用对象生存期数据收集。|  
|**GlobalTraceGCLife**|使用检测方法启用全局内存分配分析。  也启用对象生存期数据收集。|  
|**GlobalSampleOn**|使用采样方法启用全局分析。  不启用内存分配事件或对象生存期数据收集。|  
|**GlobalSampleGC**|使用采样方法启用全局内存分配分析。  不启用对象生存期数据收集。|  
|**GlobalSampleGCLife**|使用采样方法启用全局内存分配分析。  也启用对象生存期数据收集。|  
  
 **用于删除环境设置的 VSPerfCLREnv 选项**  
  
 分析完托管应用程序后，使用以下选项之一可删除 VSPerfCLREnv 添加的环境变量。  下表描述了如何删除标准环境变量和全局环境变量：  
  
|选项|说明|  
|--------|--------|  
|**Off**|删除标准 .NET 分析的环境变量。  当使用非全局 VSPerfClrEnv 选项来设置探查器环境变量时，使用此选项。|  
|**GlobalOff**|删除全局 .NET 分析的环境变量。  当应用程序由操作系统（而不是探查器）启动时，使用此选项。|  
  
## 备注  
 如果应用程序通过使用 IDE 中的性能资源管理器启动，则这些选项对于分析托管应用程序不是必需的。  性能资源管理器用于为您设置所有必需的环境设置。  
  
 如果在分析期间未设置正确的环境，则分析期间会发出警告，并且不会正确解析托管函数名称。  
  
## 请参阅  
 [通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)