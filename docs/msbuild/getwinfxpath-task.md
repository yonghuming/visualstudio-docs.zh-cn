---
title: "GetWinFXPath 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 45d07bf0834aa1488e8c2e3b22ee460eb629539e
ms.lasthandoff: 02/22/2017

---
# <a name="getwinfxpath-task"></a>GetWinFXPath 任务
<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 任务返回当前 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 运行时的目录。  
  
## <a name="task-parameters"></a>任务参数  
  
|参数|说明|  
|---------------|-----------------|  
|`WinFXPath`|可选的 **String** 输出参数。<br /><br /> 指定 [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] 运行时的实际路径。|  
|`WinFXNativePath`|必需的 **String** 参数。<br /><br /> 指定本机 [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] 运行时的路径。|  
|`WinFXWowPath`|必需的 **String** 参数。<br /><br /> 指定 64 位系统上 32 位 **Windows on Windows** 模块中的 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 程序集的路径。|  
  
## <a name="remarks"></a>备注  
 如果在 64 位处理器上执行 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 任务，则 **WinFXPath** 参数会设置为 **WinFXWowPath** 参数中存储的路径；否则，**WinFXPath** 参数会设置为 **WinFXNativePath** 参数中存储的路径。  
  
## <a name="example"></a>示例  
 如下示例演示了如何使用 **GetWinFXPath** 任务来检测 [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] 运行时的本机路径。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [WPF MSBuild 引用](../msbuild/wpf-msbuild-reference.md)   
 [任务参考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [Building a WPF Application (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)（生成 WPF 应用程序 (WPF)）
