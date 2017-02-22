---
title: "SDK 帮助器调试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "注册表中，调试 SDK"
  - "调试 SDK，注册表位置"
  - "dbgmetric.h"
  - "度量值 [调试 SDK]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# SDK 帮助器调试
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

这些函数和说明是函数为实现调试引擎的全局帮助器，表达式计算器和符号提供程序 C\+\+ 的。  
  
> [!NOTE]
>  如果没有这些函数和说明的托管版本此时。  
  
## 概述  
 为了使调试引擎，表达式计算器，并且， Visual Studio 将使用的符号提供程序，必须访问它们。  这可以通过将注册表子项和项完成，也称为 “设置规格”。以下全局功能旨在简化更新这些指标处理。  有关注册表位置的部分查看这些功能更新每个注册表子项的格式。  
  
## 泛型指标功能  
 这些是使用的泛型函数调试引擎。  表达式计算器和符号提供程序的专用功能发生下面详细说明。  
  
### GetMetric 方法  
 从注册表中检索一个指标。  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|说明|  
|---------------|--------|  
|pszMachine|\[in\] 注册要写入一个可以远程计算机的名称 \(`NULL` 表示本地计算机\)。|  
|pszType|\[in\] 一个度量类型。|  
|guidSection|\[in\] 特定引擎、计算器、异常等的 GUID。  这指定小节在一个度量类型下为特定元素。|  
|pszMetric|\[in\] 将获取的指标。  这对应于特定值名称。|  
|pdwValue|\[in\] 值的存储位置。的指标。  会返回一 GetMetric 的几个类似 \(在此示例中为\)， BSTR、 GUID 或数组 GUID。|  
|pszAltRoot|\[in\] 使用的备用注册表根。  设置为 `NULL` 使用默认值。|  
  
### SetMetric 方法  
 设置在注册表中指定的指标。  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|说明|  
|---------------|--------|  
|pszType|\[in\] 一个度量类型。|  
|guidSection|\[in\] 特定引擎、计算器、异常等的 GUID。  这指定小节在一个度量类型下为特定元素。|  
|pszMetric|\[in\] 将获取的指标。  这对应于特定值名称。|  
|dwValue|\[in\] 值的存储位置。的指标。  可以存储 DWORD SetMetric 的几个类似 \(在此示例中为\)， BSTR、 GUID 或数组 GUID。|  
|fUserSpecific|\[in\] 则为 true，则指标用户特定信息，并且，如果应向用户的项编写而不是本地计算机项。|  
|pszAltRoot|\[in\] 使用的备用注册表根。  设置为 `NULL` 使用默认值。|  
  
### RemoveMetric 方法  
 从注册表中移除指定的指标。  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|说明|  
|---------------|--------|  
|pszType|\[in\] 一个度量类型。|  
|guidSection|\[in\] 特定引擎、计算器、异常等的 GUID。  这指定小节在一个度量类型下为特定元素。|  
|pszMetric|\[in\] 要移除的指标。  这对应于特定值名称。|  
|pszAltRoot|\[in\] 使用的备用注册表根。  设置为 `NULL` 使用默认值。|  
  
### EnumMetricSections 方法  
 枚举在注册表的各种规格部分。  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|说明|  
|---------------|--------|  
|pszMachine|\[in\] 注册要写入一个可以远程计算机的名称 \(`NULL` 表示本地计算机\)。|  
|pszType|\[in\] 一个度量类型。|  
|rgguidSections|\[in, out\] 将填充的预分配的数组 GUID。|  
|pdwSize|\[in\] 在 `rgguidSections` 数组可以存储 GUID 的最大数目。|  
|pszAltRoot|\[in\] 使用的备用注册表根。  设置为 `NULL` 使用默认值。|  
  
## 表达式计算器功能  
  
|功能|说明|  
|--------|--------|  
|GetEEMetric|从注册表中检索一个指标。|  
|SetEEMetric|设置在注册表中指定的指标。|  
|RemoveEEMetric|从注册表中移除指定的指标。|  
|GetEEMetricFile|从指定的指标和加载获取文件名，它返回文件内容作为字符串。|  
  
## 异常功能  
  
|功能|说明|  
|--------|--------|  
|GetExceptionMetric|从注册表中检索一个指标。|  
|SetExceptionMetric|设置在注册表中指定的指标。|  
|RemoveExceptionMetric|从注册表中移除指定的指标。|  
|RemoveAllExceptionMetrics|从注册表中移除所有异常指标。|  
  
## 符号提供程序功能  
  
|功能|说明|  
|--------|--------|  
|GetSPMetric|从注册表中检索一个指标。|  
|SetSPMetric|设置在注册表中指定的指标。|  
|RemoveSPMetric|从注册表中移除指定的指标。|  
  
## 枚举函数  
  
|功能|说明|  
|--------|--------|  
|EnumMetricSections|枚举一个指定的指标类型的所有指标。|  
|EnumDebugEngine|枚举注册的调试引擎。|  
|EnumEEs|枚举注册的表达式计算器。|  
|EnumExceptionMetrics|枚举所有异常指标。|  
  
## 指标定义  
 这些定义可用于预定义的指标名称。  名称对应于各个注册表项和值名称是为宽字符字符串中定义的所有:例如， `extern LPCWSTR metrictypeEngine`。  
  
|预定义的指标类型|声明:基项为…|  
|--------------|-------------|  
|metrictypeEngine|所有调试引擎指标。|  
|metrictypePortSupplier|任何端口提供指标。|  
|metrictypeException|所有异常指标。|  
|metricttypeEEExtension|任何表达式计算器扩展。|  
  
|调试引擎属性|说明|  
|------------|--------|  
|metricAddressBP|设置为非零指示出地址断点支持。|  
|metricAlwaysLoadLocal|设置为非零以便始终加载调试引擎局部。|  
|metricLoadInDebuggeeSession|不使用|  
|metricLoadedByDebuggee|设置为非零指示调试引擎始终填充或将被调试的程序。|  
|metricAttach|设置为非零指示为现有程序的附件支持。|  
|metricCallStackBP|设置为非零指示支持调用堆栈断点。|  
|metricConditionalBP|设置为非零指示用于设置条件断点支持。|  
|metricDataBP|设置为非零指示用于将更改的断点支持数据中。|  
|metricDisassembly|设置为非零指示用于反汇编列表的生产支持。|  
|metricDumpWriting|设置为非零指示用于转储语、果转储输出设备的内存支持\)。|  
|metricENC|设置为非零指示用于 " 编辑并继续 " 支持。 **Note:**  自定义调试引擎永远不应将此或应始终将其设置为 0。|  
|metricExceptions|设置为非零指示为异常支持。|  
|metricFunctionBP|设置为非零指示为名为断点 \(中断的断点支持，当某个函数名调用\) 时。|  
|metricHitCountBP|设置为非零指示用于设置 “命中支持指向”断点 \(触发，在命中一定的次数\) 之后的断点。|  
|metricJITDebug|设置为非零指示用于实时调试支持 \(调试器，便会产生异常在运行时处理时\)。|  
|metricMemory|不使用|  
|metricPortSupplier|，如果已实现，它设置为端口提供程序的 CLSID。|  
|metricRegisters|不使用|  
|metricSetNextStatement|设置为非零指示用于设置跳过中间语句执行\) 的下一条语句支持 \(。|  
|metricSuspendThread|设置为非零指示用于挂起线程执行的支持。|  
|metricWarnIfNoSymbols|设置为非零指示用户应该得到通知，如果没有符号。|  
|metricProgramProvider|设置为程序提供程序的 CLSID。|  
|metricAlwaysLoadProgramProviderLocal|设置为非零指示应始终加载程序提供程序局部。|  
|metricEngineCanWatchProcess|设置为非零指示调试引擎将监视处理事件而不是过程提供程序。|  
|metricRemoteDebugging|设置为非零指示用于远程调试支持。|  
|metricEncUseNativeBuilder|设置为非零指示编辑并继续 " 管理器应使用调试引擎的 encbuild.dll 为 " 编辑并继续 " 生成。 **Note:**  自定义调试引擎永远不应将此或应始终将其设置为 0。|  
|metricLoadUnderWOW64|设置为非零指示在调试对象应加载调试引擎处理在 WOW 下，在调试 64 位进程时;否则，将使用在 Visual Studio 中将加载进程 \(运行在 WOW64 下\)。|  
|metricLoadProgramProviderUnderWOW64|设置为非零指示何时在调试对象应加载程序提供程序处理调试 64 位进程在 WOW 之下;否则，在 Visual Studio 将加载处理。|  
|metricStopOnExceptionCrossingManagedBoundary|设置为非零指示进程应停止，如果未经处理的异常跨托管\/非托管代码边界时引发。|  
|metricAutoSelectPriority|设置为调试引擎的自动选择的优先级 \(下限等于较高优先级\)。|  
|metricAutoSelectIncompatibleList|包含指定 GUID 项的注册表项调试在自动选择要忽略的引擎。  这些项是一个数字 \(0， 1， 2，依此类推\) 以及是以字符串 GUID。|  
|metricIncompatibleList|包含指定 GUID 项的注册表项进行调试此不兼容的引擎调试引擎。|  
|metricDisableJITOptimization|设置为非零指示实时优化 \(对于托管代码\) 应禁用在调试过程中。|  
  
|表达式计算器属性|说明|  
|--------------|--------|  
|metricEngine|这保存数字调试支持指定的表达式计算器的引擎。|  
|metricPreloadModules|设置为非零指示应预加载模块时，表达式计算器生成过程时。|  
|metricThisObjectName|设置为 “this”对象名。|  
  
|表达式计算器扩展属性|说明|  
|----------------|--------|  
|metricExtensionDll|支持此扩展 DLL 的名称。|  
|metricExtensionRegistersSupported|支持的列表注册。|  
|metricExtensionRegistersEntryPoint|对于访问的注册入口点。|  
|metricExtensionTypesSupported|支持的类型列表。|  
|metricExtensionTypesEntryPoint|为访问类型入口点。|  
  
|端口提供属性|说明|  
|------------|--------|  
|metricPortPickerCLSID|端口选择器 \(用户可以选择使用端口和添加端口用于调试的对话框\) CLSID。|  
|metricDisallowUserEnteredPorts|非零，如果用户输入的端口不能添加到端口提供程序 \(从本质上讲使端口选择器对话框只读\)。|  
|metricPidBase|，在将进程 ID 时，基本处理端口提供程序使用的 ID。|  
  
|预定义的 SP 存储类型|说明|  
|------------------|--------|  
|storetypeFile|符号在单独的文件中。|  
|storetypeMetadata|符号存储为元数据程序集中。|  
  
|其他属性|说明|  
|----------|--------|  
|metricShowNonUserCode|设置为非零显示非用户代码。|  
|metricJustMyCodeStepping|设置为非零指示单步执行用户代码可以仅发生。|  
|metricCLSID|特定度量类型的对象的 CLSID。|  
|metricName|用户友好名称。特定度量类型的对象。|  
|metricLanguage|语言名称。|  
  
## 注册表位置  
 度量读取并写到注册表中，特别是在 `VisualStudio` 子级。  
  
> [!NOTE]
>  大多数情况下，该度量到 HKEY\_LOCAL\_MACHINE 密钥将编写。  但是，有时 HKEY\_CURRENT\_USER 将是目标键。  Dbgmetric.lib 处理全部密钥。  在获取指标时，它首先搜索 HKEY\_CURRENT\_USER，然后 HKEY\_LOCAL\_MACHINE。  当设置指标时，参数指定要使用的顶级项。  
  
 *\[\] 注册表项*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[版本根\]*\\  
  
 *\[指标根\]*\\  
  
 *\[度量类型\]*\\  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[\] 注册表项*|`HKEY_CURRENT_USER`或 `HKEY_LOCAL_MACHINE`。|  
|*\[版本根\]*|Visual Studio 的版本 \(例如， `7.0`、 `7.1`或 `8.0`\)。  但是，使用到 **devenv.exe**，的**\/rootsuffix** 开关此根还可以修改。  对于 VSIP，此修饰符通常是 Exp，因此，版本根是，例如， 8.0Exp。|  
|*\[指标根\]*|这是 `AD7Metrics` 或 `AD7Metrics(Debug)`，具体取决于是否使用 dbgmetric.lib 的调试版本。 **Note:**  是否使用 dbgmetric.lib，此命名约定都应遵循，如果您对该注册表必须反映的区别调试版本和发布版本。|  
|*\[度量类型\]*|将写入的类型的度量值: `Engine`、 `ExpressionEvaluator`、 `SymbolProvider`等。  这些都在 dbgmetric.h 定义为，为给定类型名称。|  
|*\[指标\]*|将被赋予项的名称值来设置指标。  该度量的物理组织取决于该度量类型。|  
|*\[指标\]*|值赋给指标。  该值应具有的类型 \(字符串、数字、\) 取决于指标。|  
  
> [!NOTE]
>  所有 GUID 在 `{GUID}`格式存储。  例如 `{123D150B-FA18-461C-B218-45B3E4589F9B}`。  
  
### 调试引擎  
 下面是调试引擎指标的组织在注册表中。  `Engine` 是调试引擎的指标类型名称并对应于上面的注册表子树的 *\[度量类型\]* 。  
  
 `Engine`\\  
  
 *\[引擎 guid\]*\\  
  
 `CLSID` \= *\[类 guid\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[端口提供 guid\]*  
  
 `1` \= *\[端口提供 guid\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[引擎 guid\]*|调试引擎的 GUID。|  
|*\[类 guid\]*|实现此类的 GUID 调试引擎。|  
|*\[端口提供 guid\]*|端口提供程序的 GUID，因此，如果有的话\)。  许多调试引擎使用默认端口提供程序并不指定其提供程序。  在这种情况下，子 `PortSupplier` 将不存在。|  
  
### 端口提供程序  
 下面是端口提供指标的组织在注册表中。  `PortSupplier` 为端口提供程序的指标类型名称并对应于 *\[度量类型\]*。  
  
 `PortSupplier`\\  
  
 *\[端口提供 guid\]*\\  
  
 `CLSID` \= *\[类 guid\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[端口提供 guid\]*|端口提供程序的 GUID|  
|*\[类 guid\]*|实现此端口提供程序类的 GUID|  
  
### 符号提供程序  
 下面是符号提供指标的组织在注册表中。  `SymbolProvider` 是符号提供程序的指标类型名称并对应于 *\[度量类型\]*。  
  
 `SymbolProvider`\\  
  
 *\[符号提供程序 GUID\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[类 guid\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[类 guid\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[符号提供程序 GUID\]*|符号提供程序的 GUID|  
|*\[类 guid\]*|实现此符号提供程序类的 GUID|  
  
### 表达式计算器  
 下面是表达式计算器指标的组织在注册表中。  `ExpressionEvaluator` 是表达式计算器的指标类型名称并对应于 *\[度量类型\]*。  
  
> [!NOTE]
>  `ExpressionEvaluator` 的指标类型在 dbgmetric.h 未定义，，因为假定，表达式计算器的所有指标更改将通过适当的表达式计算器指标功能 \( `ExpressionEvaluator` 子级的格式是一些复杂的，因此，详细信息会隐藏 dbgmetric.lib 中\)。  
  
 `ExpressionEvaluator`\\  
  
 *\[语言 guid\]*\\  
  
 *\[供应商 guid\]*\\  
  
 `CLSID` \= *\[类 guid\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 `Engine`\\  
  
 `0` \= *\[调试引擎 guid\]*  
  
 `1` \= *\[调试引擎 guid\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[语言 guid\]*|语言的 GUID|  
|*\[供应商 guid\]*|供应商的 GUID|  
|*\[类 guid\]*|实现此表达式计算器类的 GUID|  
|*\[调试引擎 guid\]*|使用此表达式计算器调试引擎的 GUID|  
  
### 表达式计算器扩展  
 下面是表达式计算器扩展指标的组织在注册表中。  `EEExtensions` 是表达式计算器扩展的指标类型名称并对应于 *\[度量类型\]*。  
  
 `EEExtensions`\\  
  
 *\[扩展 guid\]*\\  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[扩展 guid\]*|表达式计算器扩展的 GUID|  
  
### 异常  
 下面是异常指标的组织在注册表中。  `Exception` 是异常的指标类型名称并对应于 *\[度量类型\]*。  
  
 `Exception`\\  
  
 *\[调试引擎 guid\]*\\  
  
 *\[异常类型\]*\\  
  
 *\[\] 异常*\\  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 异常*\\  
  
 *\[\] 指标 \= \[指标\]*  
  
 *\[\] 指标 \= \[指标\]*  
  
|占位符|说明|  
|---------|--------|  
|*\[调试引擎 guid\]*|支持异常调试引擎的 GUID。|  
|*\[异常类型\]*|标识可以处理异常的类子级的常规前缀。  典型的名称为 **C\+\+ Exceptions**、 **Win32 Exceptions**、 **Common Language Runtime Exceptions**和 **Native Run\-Time Checks**。  这些名称还用于标识特定异常类给用户。|  
|*\[\] 异常*|一个名称异常:例如， **\_com\_error** 或 **Control\-Break**。  这些名称还用于标识特定异常给用户。|  
  
## 要求  
 这些文件位于 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK 安装目录 \(默认情况下， *\[drivers\]*\\Program Files\\Microsoft Visual Studio 2010 SDK \\\)。  
  
 标题:include \\ dbgmetric.h  
  
 库:lib \\ ad2de.lib， lib \\ dbgmetric.lib  
  
## 请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)