---
title: "确定哪种编辑器在项目中打开文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc0105b56f0a33a86953c95e3d36f5d7f00bcd37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>确定编辑器打开一个项目中的文件
当用户打开的项目中的某个文件时，环境都要通过轮询处理过程，最终打开适当的编辑器或设计器中的为该文件。 由环境使用的初始过程是相同的标准和自定义编辑器。 该环境使用不同的条件时轮询的编辑器，用于打开文件并与环境，VSPackage 必须协调在此过程。  
  
 例如，当用户选择**打开**命令**文件**菜单，然后选择`filename`.rtf （或任何其他文件扩展名.rtf），环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>对于每个项目，最终循环运行解决方案中的所有项目实例实现。 项目返回一组按优先级别标识声明在文档上的标志。 使用最高优先级，则环境将调用相应<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 有关进一步信息轮询处理过程，[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
 杂项文件项目声明未声明的其他项目的所有文件。 这样一来，在标准编辑器打开它们之前，自定义编辑器可以打开文档。 如果杂项文件项目声明一个文件，则环境将调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法以使用标准编辑器打开文件。 环境会检查个处理.rtf 文件的已注册编辑器其内部列表。 此列表位于在注册表中的以下项：  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 环境还会检查有子项 DocObject 的任何对象的 HKEY_CLASSES_ROOT\CLSID 键中的类标识符。 如果在其中找到的文件扩展名，则嵌入的应用程序的版本，如 Microsoft Word 中，是 Visual Studio 中创建的就地。 这些文档对象必须实现的复合文件<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>接口或该对象必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>接口。  
  
 如果在注册表中的.rtf 文件未编辑器工厂，则环境会在注册表中查找\\.rtf 密钥，将打开编辑器中指定。 如果在注册表中未找到文件扩展名，环境将使用 Visual Studio 核心文本编辑器打开文件，如果它是一个文本文件。  
  
 如果核心文本编辑器失败，出现这种情况如果文件不是一个文本文件，然后该环境使用其二进制编辑器的文件。  
  
 如果环境未找到编辑器.rtf 扩展在其注册表中，它将加载 VSPackage 实现此编辑器工厂。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>上新的 VSPackage 的方法。 VSPackage 调用`QueryService`为`SID_SVsRegistorEditor`，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法随环境注册编辑器工厂。  
  
 环境现在重新检查已注册的编辑器中，查找.rtf 文件的新注册的编辑器工厂其内部列表。 环境调用你实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，并传递在要创建的文件名称和视图类型。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>