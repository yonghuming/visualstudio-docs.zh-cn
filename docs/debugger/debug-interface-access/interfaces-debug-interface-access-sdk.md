---
title: "接口 （调试接口访问 SDK） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 044c6ce1dafbd5ce753d9e3a98d41ed1963a77ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="interfaces-debug-interface-access-sdk"></a>接口（调试接口访问 SDK）
在中表的内容和 Vtable 顺序中的接口页上，每个接口下按字母顺序列出了方法。  
  
## <a name="in-this-section"></a>本节内容  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 提供控制 DIA SDK 如何计算调试对象的虚拟和相对虚拟地址。  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 启动的调试符号的源的访问。  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 提供对调试数据流中的记录的访问。  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 枚举数据源中包含的各种调试流。  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 枚举中的数据源包含的各种帧数据元素。  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 枚举数据源中包含的各种插入的源。  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 枚举数据源中包含的各种行号。  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 枚举数据源中包含的各个部分参与意见。  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 枚举数据源中包含的各个部分。  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 枚举中的数据源包含的各种源文件。  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 枚举各种可用的堆栈帧。  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 枚举数据源中包含的各种符号。  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 通过地址枚举数据源中包含的各种符号。  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 枚举各种数据源中包含的表。  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 公开堆栈帧的详细信息。  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 公开基位置和内存的偏移量的模块或图像的详细的信息。  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 访问程序源代码存储在 DIA 数据源中。  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 描述从字节映像文本块映射到源代码文件行号的过程的访问信息。  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 从 DIA 符号查找过程，从而使一个用户界面来报告的位置尝试进度接收回调。  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 从 DIA 符号查找过程的功能，允许要找到进程上施加限制接收回调。  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 可以用来读取 DIA 属性集的持久性属性。  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 允许客户端应用程序提供所指定的文件位置的可执行文件的字节。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 允许客户端应用程序提供所指定的相对虚拟地址的可执行文件的字节。  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 描述部分贡献检索数据，也就是说，连续的内存块的图像由提供编译单位。  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 将数据从节号线段的地址空间映射。  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 为调试符号提供查询上下文。  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 表示源文件。  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 显示堆栈帧的属性。  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 提供方法以执行堆栈引导使用 PDB 文件。  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 可维护的调用之间的堆栈上下文[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 便于审核堆栈使用程序调试数据库 (PDB) 文件。  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 描述符号实例的属性。  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 枚举 DIA 数据源表。  
  
## <a name="related-sections"></a>相关章节  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 描述枚举和结构由 DIA SDK 的各种接口。  
  
 [常量（调试接口访问 SDK）](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 描述在 DIA SDK 中可用的常量。  
  
## <a name="see-also"></a>另请参阅  
 [参考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)