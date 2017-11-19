---
title: "如何： 提供适用于 Windows 的自动化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 945eeb8b81ecb26d43da9528db154d133c4f868c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-automation-for-windows"></a>如何： 提供适用于 Windows 的自动化
你可以提供自动化文档和工具窗口。 提供自动化是明智的每当你想要使自动化对象在一个窗口，并且环境不提供现成的自动化对象，它与任务列表。  
  
## <a name="automation-for-tool-windows"></a>工具窗口的自动化  
 通过返回一个标准的工具窗口上环境提供自动化<xref:EnvDTE.Window>对象中的以下过程所述：  
  
#### <a name="to-provide-automation-for-tool-windows"></a>提供自动化工具窗口  
  
1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>通过环境使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>作为`VSFPROPID`参数，以获取`Window`对象。  
  
2.  当调用方请求通过工具窗口的特定于 VSPackage 的自动化对象<xref:EnvDTE.Window.Object%2A>，环境调用`QueryInterface`为`IExtensibleObject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，或`IDispatch`接口。 同时`IExtensibleObject`和`IVsExtensibleObject`提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>方法。  
  
3.  当环境然后调用`GetAutomationObject`方法并传递`NULL`，通过传递响应备份你的 VSPackage 特定对象。  
  
4.  如果调用`QueryInterface`为`IExtensibleObject`和`IVsExtensibleObject`失败，则环境将调用`QueryInterface`为`IDispatch`。  
  
## <a name="automation-for-document-windows"></a>文档窗口的自动化  
 一个标准<xref:EnvDTE.Document>对象也是可从环境中，虽然编辑器可以有其自己的实现的`T:EnvDTE.Document`对象通过实现`IExtensibleObject`接口和响应`GetAutomationObject`。  
  
 此外，编辑器可以提供特定于 VSPackage 的自动化对象，通过检索<xref:EnvDTE.Document.Object%2A>方法，通过实现`IVsExtensibleObject`或`IExtensibleObject`接口。 [VSSDK 示例](http://aka.ms/vs2015sdksamples)做出了贡献 RTF 特定文档的自动化对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>