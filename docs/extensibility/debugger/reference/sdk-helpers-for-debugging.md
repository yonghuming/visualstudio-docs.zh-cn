---
title: "SDK 帮助器调试 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9c5d24c8a3a2bb81c87b2cc405a6885b8f23374
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sdk-helpers-for-debugging"></a>SDK 适用于调试的帮助程序
这些函数和声明是有关在 c + + 中实现的调试引擎，表达式计算器和符号提供程序的全局帮助器函数。  
  
> [!NOTE]
>  此时没有托管的版本的这些函数和声明。  
  
## <a name="overview"></a>概述  
 为了使用由 Visual Studio 的调试引擎，表达式计算器和符号提供程序，必须先注册它们。 这可通过设置注册表子项和注册表项，也称为"设置度量值。" 以下全局函数旨在简化了将更新这些度量值的过程。 若要了解这些函数由更新每个注册表子项的布局的注册表位置位置上，请参阅部分。  
  
## <a name="general-metric-functions"></a>常规度量值函数  
 这些是使用的调试引擎的常规函数。 专用于表达式计算器的函数和后面详细说明符号提供程序。  
  
### <a name="getmetric-method"></a>GetMetric 方法  
 从注册表检索度量值。  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|参数|描述|  
|---------------|-----------------|  
|pszMachine|[in]将写入其注册可能是远程计算机的名称 (`NULL`意味着本地计算机)。|  
|pszType|[in]度量值的类型之一。|  
|guidSection|[in]特定引擎、 计算器，异常等的 GUID。这将指定的特定元素的度量值类型下的子部分。|  
|pszMetric|[in]要从中获取度量值。 这对应于特定的值名称。|  
|pdwValue|[in]从度量值的值存储位置。 提供了多种形式的 GetMetric 可以返回一个 dword 值，（如此示例所示）、 BSTR、 GUID 或 Guid 数组。|  
|pszAltRoot|[in]若要使用备用注册表根目录。 设置为`NULL`若要使用默认值。|  
  
### <a name="setmetric-method"></a>SetMetric 方法  
 在注册表中设置指定的度量值。  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|参数|描述|  
|---------------|-----------------|  
|pszType|[in]度量值的类型之一。|  
|guidSection|[in]特定引擎、 计算器，异常等的 GUID。这将指定的特定元素的度量值类型下的子部分。|  
|pszMetric|[in]要从中获取度量值。 这对应于特定的值名称。|  
|dwValue|[in]在度量值的值存储位置。 提供了多种形式的 SetMetric 可以存储 （在本示例中） 的 dword 值、 BSTR、 GUID 或 Guid 数组。|  
|fUserSpecific|[in]如果指标是特定于用户的并且应将写入而不是本地计算机 hive 的用户的配置单元，则为 TRUE。|  
|pszAltRoot|[in]若要使用备用注册表根目录。 设置为`NULL`若要使用默认值。|  
  
### <a name="removemetric-method"></a>RemoveMetric 方法  
 从注册表中删除指定的指标。  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|参数|描述|  
|---------------|-----------------|  
|pszType|[in]度量值的类型之一。|  
|guidSection|[in]特定引擎、 计算器，异常等的 GUID。这将指定的特定元素的度量值类型下的子部分。|  
|pszMetric|[in]要删除度量值。 这对应于特定的值名称。|  
|pszAltRoot|[in]若要使用备用注册表根目录。 设置为`NULL`若要使用默认值。|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections 方法  
 枚举注册表中的各个度量值部分。  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|参数|描述|  
|---------------|-----------------|  
|pszMachine|[in]将写入其注册可能是远程计算机的名称 (`NULL`意味着本地计算机)。|  
|pszType|[in]度量值的类型之一。|  
|rgguidSections|[在中，out]Guid 填充的预分配的数组。|  
|pdwSize|[in]可以存储在的 Guid 的最大数`rgguidSections`数组。|  
|pszAltRoot|[in]若要使用备用注册表根目录。 设置为`NULL`若要使用默认值。|  
  
## <a name="expression-evaluator-functions"></a>表达式计算器函数  
  
|函数|描述|  
|--------------|-----------------|  
|GetEEMetric|从注册表检索度量值。|  
|SetEEMetric|在注册表中设置指定的度量值。|  
|RemoveEEMetric|从注册表中删除指定的指标。|  
|GetEEMetricFile|从指定的度量值获取的文件名称并加载它，以字符串形式返回该文件的内容。|  
  
## <a name="exception-functions"></a>异常函数  
  
|函数|描述|  
|--------------|-----------------|  
|GetExceptionMetric|从注册表检索度量值。|  
|SetExceptionMetric|在注册表中设置指定的度量值。|  
|RemoveExceptionMetric|从注册表中删除指定的指标。|  
|RemoveAllExceptionMetrics|从注册表中删除所有异常度量值。|  
  
## <a name="symbol-provider-functions"></a>符号提供程序函数  
  
|函数|描述|  
|--------------|-----------------|  
|GetSPMetric|从注册表检索度量值。|  
|SetSPMetric|在注册表中设置指定的度量值。|  
|RemoveSPMetric|从注册表中删除指定的指标。|  
  
## <a name="enumeration-functions"></a>枚举函数  
  
|函数|描述|  
|--------------|-----------------|  
|EnumMetricSections|枚举指定的度量值类型的所有度量值。|  
|EnumDebugEngine|枚举已注册的调试引擎。|  
|EnumEEs|枚举已注册的表达式计算器。|  
|EnumExceptionMetrics|枚举所有异常度量值。|  
  
## <a name="metric-definitions"></a>度量定义  
 这些定义可用于预定义的度量值名称。 名称对应于各种注册表项值名称和所有定义为宽字符字符串： 例如， `extern LPCWSTR metrictypeEngine`。  
  
|预定义的度量值类型|描述： 为基的键...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|所有调试引擎度量值。|  
|metrictypePortSupplier|所有端口供应商度量值。|  
|metrictypeException|所有异常度量值。|  
|metricttypeEEExtension|所有表达式计算器扩展。|  
  
|调试引擎属性|描述|  
|-----------------------------|-----------------|  
|metricAddressBP|设置为非零值，指示地址断点的支持。|  
|metricAlwaysLoadLocal|设置非零值才能始终加载本地的调试引擎。|  
|metricLoadInDebuggeeSession|未使用|  
|metricLoadedByDebuggee|设置为非零值，指示使用也可通过被调试的程序，将始终加载的调试引擎。|  
|metricAttach|设置为非零值，指示为附加到的现有程序的支持。|  
|metricCallStackBP|设置为非零值，指示调用堆栈断点的支持。|  
|metricConditionalBP|设置为非零值，指示的设置的条件断点的支持。|  
|metricDataBP|设置为非零值，指示数据中的更改上的断点的设置的支持。|  
|metricDisassembly|设置为非零值，以指示生产的反汇编列表的支持。|  
|metricDumpWriting|设置为非零值，指示转储编写 （转储的内存写入输出设备） 的支持。|  
|metricENC|设置为非零值，以指示支持编辑并继续。 **注意：**自定义调试引擎决不能设置此或应始终将它设置为 0。|  
|metricExceptions|设置为非零值，指示的异常的支持。|  
|metricFunctionBP|设置为非零值，指示命名断点 （中断调用函数名时的断点） 的支持。|  
|metricHitCountBP|设置为非零值，指示的设置的"命中点"断点 （仅在达到一定次数后触发的断点） 的支持。|  
|metricJITDebug|设置为非零值，以指示在实时调试 （当正在运行的进程中发生异常时，将启动调试器） 的支持。|  
|metricMemory|未使用|  
|metricPortSupplier|此设置为端口提供程序的 CLSID 如果实现了一个。|  
|metricRegisters|未使用|  
|metricSetNextStatement|设置为非零值，指示用于设置下一个语句 （这样可以跳过执行的中间语句） 的支持。|  
|metricSuspendThread|设置为非零值，指示挂起线程执行的支持。|  
|metricWarnIfNoSymbols|设置为非零值，指示用户应收到通知，是否没有符号。|  
|metricProgramProvider|将其设置为程序提供程序的 CLSID。|  
|metricAlwaysLoadProgramProviderLocal|将此设置为非零值，表明程序提供程序应始终将加载本地。|  
|metricEngineCanWatchProcess|将其设置为非零值，指示的调试引擎将监视的进程事件而不是程序提供程序。|  
|metricRemoteDebugging|将其设置为非零值，指示用于远程调试的支持。|  
|metricEncUseNativeBuilder|此设置为非零值以指示编辑并继续管理器应使用的调试引擎 encbuild.dll 生成适用于编辑并继续。 **注意：**自定义调试引擎决不能设置此或应始终将它设置为 0。|  
|metricLoadUnderWOW64|将此设置为非零值，指示应在 WOW 下调试对象进程中加载的调试引擎，就时调试 64 位进程;否则，将在 Visual Studio 进程 （这在 WOW64 下运行） 中加载的调试引擎。|  
|metricLoadProgramProviderUnderWOW64|将此设置为非零值，指示该程序提供程序时，应在调试对象进程中加载调试在 WOW; 下的 64 位进程否则，它将在 Visual Studio 进程中加载。|  
|metricStopOnExceptionCrossingManagedBoundary|将其设置为非零值，指示该过程应停止跨托管/非托管代码边界引发的未经处理的异常。|  
|metricAutoSelectPriority|这的优先级设置为针对自动选择的调试引擎 （更高版本值等于更高的优先级）。|  
|metricAutoSelectIncompatibleList|其中包含在自动选择中指定的调试引擎的 Guid，若要忽略的项的注册表项。 这些项是一个数字 （0、 1、 2，依此类推） 使用表示为字符串的 GUID。|  
|metricIncompatibleList|包含与此调试引擎不兼容的调试引擎为指定 Guid 的条目的注册表项。|  
|metricDisableJITOptimization|将其设置为非零值，指示应在调试期间禁用 （对于托管代码） 中实时优化。|  
  
|表达式计算器属性|描述|  
|-------------------------------------|-----------------|  
|metricEngine|它将保存的支持指定的表达式计算器的调试引擎的数量。|  
|metricPreloadModules|将其设置为非零值，指示模块应预加载，表达式计算器对程序启动时。|  
|metricThisObjectName|此设置为"this"对象名称。|  
  
|表达式计算器扩展属性|描述|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|支持此扩展的 dll 的名称。|  
|metricExtensionRegistersSupported|支持的寄存器的列表。|  
|metricExtensionRegistersEntryPoint|用于访问寄存器的入口点。|  
|metricExtensionTypesSupported|支持的类型的列表。|  
|metricExtensionTypesEntryPoint|访问类型的入口点。|  
  
|端口供应商属性|描述|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|（对话框中的用户可以使用以选择端口并添加要用于调试的端口） 的端口选取器的 CLSID。|  
|metricDisallowUserEnteredPorts|非零，如果用户输入端口无法添加到端口供应商 （实质上是只读的这使得端口选取器对话框中）。|  
|metricPidBase|分配进程 Id 时使用端口提供程序的基的进程 ID。|  
  
|预定义的 SP 存储类型|描述|  
|-------------------------------|-----------------|  
|storetypeFile|符号存储在单独的文件中。|  
|storetypeMetadata|符号的程序集中的元数据作为存储。|  
  
|杂项属性|描述|  
|------------------------------|-----------------|  
|metricShowNonUserCode|将其设置为非零值，显示非代码。|  
|metricJustMyCodeStepping|将其设置为非零值，指示只能在用户代码中，单步执行可能发生的。|  
|metricCLSID|特定度量值类型的对象的 CLSID。|  
|metricName|特定度量值类型的对象的用户友好名称。|  
|metricLanguage|语言名称。|  
  
## <a name="registry-locations"></a>注册表位置  
 度量值从内存读取和写入到注册表中，尤其是在`VisualStudio`子项。  
  
> [!NOTE]
>  大多数情况下，度量值将写入 HKEY_LOCAL_MACHINE 键。 但是，有时 HKEY_CURRENT_USER 将是目标密钥。 Dbgmetric.lib 处理这两个密钥。 当收到某个度量值，它会搜索 HKEY_CURRENT_USER 第一个，然后 HKEY_LOCAL_MACHINE。 它设置时某个度量值，则一个参数指定要使用哪个顶级项。  
  
 *[注册表项]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[版本根]*\  
  
 *[指标根]*\  
  
 *[指标类型]*\  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[注册表项]*|`HKEY_CURRENT_USER` 或 `HKEY_LOCAL_MACHINE`。|  
|*[版本根]*|Visual Studio 的版本 (例如， `7.0`， `7.1`，或`8.0`)。 但是，此根也可以修改使用**/rootsuffix**切换到**devenv.exe**。 VSIP，对于此修饰符通常是**Exp**，因此版本根是，例如，8.0Exp。|  
|*[指标根]*|这可以是`AD7Metrics`或`AD7Metrics(Debug)`，取决于是否使用 dbgmetric.lib 的调试版本。 **注意：**是否使用 dbgmetric.lib 时，此命名约定应遵守如果必须调试和发布之间的差异必须反映在注册表中的版本。|  
|*[指标类型]*|要写入的度量值的类型： `Engine`， `ExpressionEvaluator`， `SymbolProvider`，等等。这些都被定义为如下所示为 dbgmetric.h `metricTypeXXXX`，其中`XXXX`是特定类型名称。|  
|*[指标]*|要为其赋值才能设置该度量值的项的名称。 实际的组织的度量值取决于度量值的类型。|  
|*[度量值]*|分配给该度量值的值。 值应具有 （字符串、 数字，而等） 的类型取决于该度量值。|  
  
> [!NOTE]
>  格式存储所有 Guid `{GUID}`。 例如 `{123D150B-FA18-461C-B218-45B3E4589F9B}`。  
  
### <a name="debug-engines"></a>调试引擎  
 下面是在注册表中的调试引擎度量值组织。 `Engine`为调试引擎的度量值的类型名称并且对应于*[指标类型]*上面的注册表子树中。  
  
 `Engine`\  
  
 *[引擎 guid]*\  
  
 `CLSID` = *[类 guid]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 `PortSupplier`\  
  
 `0` = *[端口供应商 guid]*  
  
 `1` = *[端口供应商 guid]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[引擎 guid]*|调试引擎的 GUID。|  
|*[类 guid]*|实现此调试引擎的类的 GUID。|  
|*[端口供应商 guid]*|端口供应商，如果任何 GUID。 许多的调试引擎使用默认端口供应商，并因此不指定其自己的供应商。 在此情况下，该子项`PortSupplier`将不存在。|  
  
### <a name="port-suppliers"></a>端口供应商  
 下面是注册表中的端口供应商指标的组织。 `PortSupplier`是的端口供应商提供的度量值的类型名称并且对应于*[指标类型]*。  
  
 `PortSupplier`\  
  
 *[端口供应商 guid]*\  
  
 `CLSID` = *[类 guid]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[端口供应商 guid]*|端口提供程序的 GUID|  
|*[类 guid]*|实现此端口供应商的类的 GUID|  
  
### <a name="symbol-providers"></a>符号提供程序  
 下面是在注册表中的符号供应商度量值组织。 `SymbolProvider`是符号提供程序的度量值的类型名称并且对应于*[指标类型]*。  
  
 `SymbolProvider`\  
  
 *[符号提供程序 guid]*\  
  
 `file`\  
  
 `CLSID` = *[类 guid]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 `metadata`\  
  
 `CLSID` = *[类 guid]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[符号提供程序 guid]*|符号提供程序的 GUID|  
|*[类 guid]*|实现此符号提供程序的类的 GUID|  
  
### <a name="expression-evaluators"></a>表达式计算器  
 下面是在注册表中的表达式计算器度量值组织。 `ExpressionEvaluator`是表达式计算器的度量值的类型名称并且对应于*[指标类型]*。  
  
> [!NOTE]
>  度量值类型`ExpressionEvaluator`未定义中 dbgmetric.h，因为假定所有度量值的更改的表达式计算器将经过适当的表达式计算器指标函数 (的布局`ExpressionEvaluator`子项是某种程度上复杂，因此详细信息隐藏在 dbgmetric.lib）。  
  
 `ExpressionEvaluator`\  
  
 *[语言 guid]*\  
  
 *[供应商 guid]*\  
  
 `CLSID` = *[类 guid]*  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 `Engine`\  
  
 `0` = *[调试引擎 guid]*  
  
 `1` = *[调试引擎 guid]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[语言 guid]*|一种语言的 GUID|  
|*[供应商 guid]*|供应商的 GUID|  
|*[类 guid]*|实现此表达式计算器的类的 GUID|  
|*[调试引擎 guid]*|此表达式计算器适用于调试引擎的 GUID|  
  
### <a name="expression-evaluator-extensions"></a>表达式计算器扩展  
 下面是在注册表中的表达式计算器扩展度量值组织。 `EEExtensions`为计算器扩展的表达式的度量值的类型名称并且对应于*[指标类型]*。  
  
 `EEExtensions`\  
  
 *[扩展 guid]*\  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[扩展 guid]*|表达式计算器扩展的 GUID|  
  
### <a name="exceptions"></a>异常  
 下面是在注册表中的异常度量值组织。 `Exception`是的异常的度量值的类型名称并且对应于*[指标类型]*。  
  
 `Exception`\  
  
 *[调试引擎 guid]*\  
  
 *[异常类型]*\  
  
 *[异常]*\  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
 *[异常]*\  
  
 *[指标] = [度量值]*  
  
 *[指标] = [度量值]*  
  
|占位符|描述|  
|-----------------|-----------------|  
|*[调试引擎 guid]*|支持异常的调试引擎的 GUID。|  
|*[异常类型]*|标识可以处理的异常的类的子项常规标题。 典型的名称是**c + + 异常**， **Win32 异常**，**公共语言运行时异常**，和**本机运行时检查**。 这些名称还用于标识异常向用户的特定类。|  
|*[异常]*|异常的名称： 例如， **_com_error**或**控制中断**。 这些名称还用于标识向用户的特定异常。|  
  
## <a name="requirements"></a>要求  
 这些文件位于[!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)]SDK 安装目录 (默认情况下， *[驱动器]*files\microsoft Visual Studio 2010 SDK\\)。  
  
 标头： includes\dbgmetric.h  
  
 库： libs\ad2de.lib、 libs\dbgmetric.lib  
  
## <a name="see-also"></a>另请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)