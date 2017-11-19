---
title: "Visual Basic 6.0 的支持语句 |Microsoft 文档"
ms.date: 08/28/2017
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.openlocfilehash: bdfe33cac19d488bc7763f3c61c518093d8afffa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Visual Basic 6.0 在 Windows 上的支持声明


## <a name="executive-summary"></a>高级管理人员摘要

Visual Basic 团队提交到"它只需工作"Visual Basic 6.0 应用程序兼容性在以下的 Windows 支持操作系统上： 

- Windows 10
- Windows 8.1
- Windows 7
- Windows 2016 Server
- Windows Server 2012 R2 包括
- Windows Server 2008 R2 包括

Visual Basic 团队的目标是 Visual Basic 6.0 应用程序继续运行受支持的 Windows 版本上。 如本文档中所述，Visual Basic 6.0 核心运行时将支持的完整的生存期内的受支持的 Windows 版本，即五年的五年的扩展支持 (http://support.microsoft.com/gp/lifepolicy) 后跟的主流支持。 支持栏将限制为严重衰退和现有应用程序的关键安全问题。

## <a name="technical-summary"></a>技术摘要

Visual Basic 6.0 组成这些密钥可交付结果：
- Visual 基本 6.0 IDE （集成的开发环境）。
- Visual Basic 6.0 运行时： 基库和用于运行 VB 6.0 应用程序的执行引擎。
- Visual Basic 6.0 运行时扩展文件： 选择 ActiveX 控件 OCX 文件、 库和工具传送与 IDE 媒体和作为联机版本。

## <a name="the-visual-basic-60-ide"></a>Visual 基本 6.0 IDE

Visual Basic 6.0 IDE 不再支持截至 2008 年 4 月 8 日。 此外，Windows 和 Visual Basic 团队已测试在 Windows Vista、 Windows 7、 Windows Server 2008、 Windows 8 和 Windows 8.1，若要了解并缓解 （如果适用） 上的 Visual Basic 6.0 IDE 在 32 位版本的 Windows （请参阅的兼容性问题[64 位 Windows](#62-bit-windows)节有关 64 位系统的详细信息)。 此公告不会更改 ide 的支持策略。

## <a name="the-visual-basic-60-runtime"></a>Visual Basic 6.0 中运行时

Visual Basic 6.0 中运行时定义为最初包含 Visual Basic 6.0 中重新分发列表的已编译二进制文件。 这些文件已标记为可在原始的 Visual Basic 6.0 许可证分发。 这些文件的示例包括 Visual Basic 6.0 中运行时库 (`msvbvm60.dll`)，控件 (即， `msflxgrd.ocx`) 以及运行时的其他主要功能区域 (即 MDAC) 支持文件。

运行时划分为三个组：

- 支持运行时文件-传送的操作系统中

   大多数应用程序方案中使用的密钥 Visual Basic 6.0 中运行时文件中传送和支持的 Windows 版本的生存期支持。 此生存期为 5 年的主流支持和五年的延长支持从给定的版本的 Windows 附带的时间。 作为我们测试的受支持的 Windows 版本上运行的 Visual Basic 6.0 应用程序的一部分的兼容性已测试过这些文件。 

   > [!NOTE]
   > 所有受支持的 Windows 版本包含几乎完全相同的文件列表，并且包含这些文件的应用程序的 redist 要求应几乎完全相同。 一个主要区别在于`TriEdit.dll`已从 Windows Vista 和更高版本中删除。

- 支持运行时文件 –-扩展和你的应用程序一起分发的文件

   此扩展的列表组成控件、 库和进行到开发人员计算机中安装从 IDE 媒体或从 Microsoft.com 的工具。 通常情况下，VB6 IDE 这些控件到开发人员计算机默认情况下安装。 开发人员仍需要将这些文件与应用程序重新分发。 支持的文件有可用版本联机 Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927)。

- 不受支持的运行时文件

   或者有超出主流落后，而某些文件支持或从来都不包含在运行时 redist (例如，它们已包含在`\Tools`IDE 媒体以支持旧版 VB4/VB5 应用程序上的文件夹或它们是第三方控件)。 在 Windows; 上不支持这些文件相反，它们是受任何支持协议是应用于它们所提供的媒体。 这意味着围绕支持和维护不做任何保证。 在某些情况下，支持更高版本的这些库。 下面提供了向后兼容性或迁移到受支持版本的详细信息。

有关每个支持组中包含的文件的特定详细信息，请参阅[运行时定义](#runtime-definition)下面一节。

## <a name="the-visual-basic-60-support-lifetime"></a>Visual Basic 6.0 支持生存期

支持和/或受支持的 Windows 版本上传送 Visual Basic 6.0 中运行时二进制文件不会更改的支持策略为 Visual Basic 6.0 IDE 或 Visual Studio 6.0 IDE 作为一个整体。 这些产品移出 2008 年 4 月 8 日的扩展支持。

Http://support.microsoft.com/gp/lifepolicy 处找不到的 Microsoft 产品支持生命周期的详细信息。 作为此支持生命周期的一部分，Microsoft 将继续受支持的 Windows 版本上支持 Visual Basic 6.0 中运行时，这些操作系统的支持生存期内。 例如，这意味着，将为主流支持，2008 年 6 月和扩展的支持，2013 年 6 月之前在 Windows Server 2003 上中支持 Visual Basic 6.0 中运行时。
有关支持生命周期，或要了解有关其他支持选项的详细信息，请访问我们支持页在 http://www.microsoft.com/support。

## <a name="64-bit-windows"></a>64 位 Windows

Visual Basic 6.0 中运行时文件是 32 位。 这些文件提供在 64 位 Windows 操作系统在下表中引用。 在 WOW 仿真环境中仅支持 32 位 VB6 应用程序和组件。 32 位组件也必须在 32 位应用程序进程中托管。

Visual Basic 6.0 IDE 具有永远不会向提供了在本机 64 位版本中，也已在 64 位 Windows 上支持 32 位 IDE。 在 64 位 Windows 或 32 位以外的任何本机体系结构上 VB6 开发并不将不受支持。

## <a name="windows-7"></a>Windows 7

此支持声明初始版本，以来已发布 Windows 7 操作系统。 本文档已更新以阐明 VB6 在 Windows 7 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows 7 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。

## <a name="windows-81"></a>Windows 8.1

此支持声明初始版本，以来已发布 Windows 8.1 操作系统。 本文档已更新以阐明 VB6 Windows 8.1 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows 8.1 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以看作支持情景为 Windows 8.1 也是如此，因为它是适用于 Windows 7。

## <a name="windows-10"></a>Windows 10

此支持声明初始版本，以来已发布 Windows 10 操作系统。 本文档已更新以阐明 VB6 Windows 10 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows 10 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以将支持情景于 Windows 10 视为与对 Windows 8.1 也是如此。

## <a name="windows-server-2008"></a>Windows Server 2008

此支持声明初始版本，以来已发布 Windows Server 2008 操作系统。 本文档已更新以阐明 VB6 Windows Server 2008 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows Server 2008 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

此支持声明初始版本，以来已发布 Windows Server 2008 R2 操作系统。 本文档已更新以阐明 VB6 Windows Server 2008 R2 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows Server 2008 R2 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以将支持情景 for Windows Server 2008 R2 视为与对 Windows Server 2008 也是如此。

## <a name="windows-server-2012"></a>Windows Server 2012

此支持声明初始版本，以来已发布 Windows Server 2012 操作系统。 本文档已更新以阐明 VB6 Windows Server 2012 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows Server 2012 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以将支持情景为 Windows Server 2012 视为也是如此，因为它是 Windows Server 2008 r2。

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

此支持声明初始版本，以来已发布 Windows Server 2012 R2 操作系统。 本文档已更新以阐明 VB6 Windows Server 2012 R2 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows Server 2012 R2 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以将支持文章针对 Windows Server 2012 R2 视为也是如此，因为它是 Windows Server 2012。

## <a name="windows-server-2016"></a>Windows 2016 Server

此支持声明初始版本，以来已发布 Windows Server 2016 操作系统。 本文档已更新以阐明 VB6 Windows Server 2016 上的 Microsoft 的支持。

VB6 运行时将提供，会在 Windows Server 2016 支持的操作系统的生存期。 Visual Basic 6.0 中运行时文件继续只提供 32 位，并且所有组件必须都承载在 32 位应用程序进程。 开发人员可以将支持情景 for Windows Server 2016 视为也是如此，因为它是 Windows Server 2012 r2。

## <a name="supported-windows-operating-system-versions"></a>支持的 Windows 操作系统版本

本部分提供有关提供一定程度的 VB6 的支持的操作系统的其他信息。 

|Windows 操作系统|VB6 支持的运行时</br>在 Windows 中传送的文件具有支持？|VB6 支持 Rutime</br>扩展文件</br>要与你的应用程序分发具有支持？| VB6 IDE 提供支持？|
|---|---|---|---|
|Windows 10 中，所有的 32 位版本|是 *|是 *|No|
|Windows 10 中，所有 64 位版本 (仅 WOW)|是 * </br> 仅在 WOW 中运行的 32 位应用程序|是* </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows 8.1，所有的 32 位版本|是 *|是 *|No|
| Windows 8.1，所有 64 位版本 (仅 WOW)|是 * </br> 仅在 WOW 中运行的 32 位应用程序|是* </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows 7 中，所有的 32 位版本|是 *|是 *|No|
|Windows 7 中，所有 64 位版本 (仅 WOW)|是 * </br> 仅在 WOW 中运行的 32 位应用程序|是 * </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows Server 2016，所有 64 位版本 (仅 WOW)|是* </br> 仅在 WOW 中运行的 32 位应用程序|是* </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows Server 2012 R2，所有 64 位版本 (仅 WOW)<br>Windows Server 2012，所有 64 位版本 (仅 WOW)|是* </br> 仅在 WOW 中运行的 32 位应用程序|是* </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows Server 2008 R2，所有 x64 版本 (仅 WOW)</br>Windows Server 2008 中，所有 x64 版本 (仅 WOW)|是 * </br> 仅在 WOW 中运行的 32 位应用程序|是 * </br> 仅在 WOW 中运行的 32 位应用程序|No|
|Windows Server 2008 中，所有的 32 位版本|是 *|是 *|No|


> [!NOTE]
> &#42; VB6 运行时支持受限制的 Windows 支持生命周期。  例如，如果将目标操作系统处于外延支持，VB6 不能有比的延长支持较高级别的支持。  [Windows 支持生命周期事实表](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet)包含其他生命周期有关先前和当前 Windows 版本的信息。

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Visual Basic 6.0 中运行时在 VBA 和 Office 内的使用情况

Visual Basic 应用程序，或 VBA，是一种不同技术，通常用于应用程序自动化和其他应用程序，通常在 Microsoft Office 应用程序内的宏。 VBA 附带作为 Office 的一部分，因此 VBA 的支持受 Office 的支持策略。 但是，在其中使用 VBA 调用或承载 Visual Basic 6.0 中运行时二进制文件和控件的情况。 在这些情况下，Visual Basic 6.0 中的操作系统支持运行时文件和在支持的 VBA 环境中使用时，还支持扩展的文件列表。

对于 VB6 运行时方案，必须支持在 VBA 内，以下所有条件，必须为 true:

- VB 运行时主机 OS 版本仍受支持。
- 适用于 VBA Office 的主机版本仍受支持。
- 问题的运行时文件仍受支持。

## <a name="visual-basic-script-vbscript"></a>Visual Basic 脚本 (VBScript)

VBScript 与 Visual Basic 6.0 及此支持声明无关。 但是，VBScript 将当前发布的 Windows 7、 Windows 8.1、 Windows 10、 Windows Server 2008 R2、 Windows Server 2012 R2 和 Windows Server 2016 包括包括一部分，受操作系统支持生命周期。

## <a name="third-party-components"></a>第三方组件

Microsoft 不能以提供针对第三方组件，如 OCX/ActiveX 控件支持。 建议联系原始控件供应商联系以寻求支持这些组件的详细信息的客户。

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>与在 Windows 上运行的 VB 6.0 应用程序报告问题

计划使用 Visual Basic 6.0 带有列出的 Windows 操作系统之一的开发人员应将该操作系统安装和开始使用原始应用程序验收测试的应用程序兼容性测试。

如果与列出的 Windows 操作系统之一上运行的 Visual Basic 6.0 应用程序发现问题，请按照正常支持渠道报告此问题。

## <a name="supported-and-shipping-in-windows"></a>支持和传送中的 Windows

| | | | |
|---|---|---|---|
|atl.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    Msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|Ds16gt.dll|      msadrh15.dll|    Odbc16gt.dll|   olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    所用的 Odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      Odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   rpcrt4.dll|
|imagehlp.dll|    msdaora.dll|     Odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   secur32.dll|
|itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|itss.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>支持的运行时文件和你的应用程序一起分发

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>不受支持，但支持的和兼容的更新或升级可用

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>不受支持的运行时文件

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  rpcss.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>本地化支持二进制文件

以下二进制文件所需的支持本地化版本的 Windows 操作系统上运行的 Visual Basic 6.0 应用程序。 它们支持，但未随附在 Windows。 系统将要求随应用程序安装程序将这些文件。

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>支持的运行时文件和你的应用程序一起分发

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

