---
title: "确定哪种编辑器在项目中打开文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>确定哪个编辑器随即打开，在项目中的文件
当用户在项目中打开某个文件时，该环境都要通过轮询过程中，最终打开适当的编辑器或设计器中的为该文件。 受雇于环境的初始过程是相同的标准和自定义编辑器。 在环境中轮询的编辑器，用于打开文件时使用不同的条件和 VSPackage 在此过程中必须有环境协调。  
  
 例如，如果用户选择**打开**命令**文件**菜单上，并选择`filename`.rtf （或任何其他文件扩展名为.rtf） 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>最终循环运行解决方案中的所有项目实例的每个项目的实现。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 项目返回一组按优先级别确定对文档的声明的标志。 使用最高的优先级，该环境调用相应<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 有关详细信息的轮询过程中，[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
 杂项文件项目声明未声明的其他项目的所有文件。 这样一来，标准编辑器打开它们之前，自定义编辑器可以打开文档。 杂项文件项目声明一个文件，如果环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法，以使用标准编辑器打开该文件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 环境检查其内部列表的已注册的编辑器的一种处理.rtf 文件。 此列表位于注册表的以下项︰  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`1> \Editors\\{`editor factory guid`1>} \Extensions]  
  
 该环境还会检查 HKEY_CLASSES_ROOT\CLSID 项具有子项 DocObject 任意对象中的类标识符。 如果在其中找到的文件扩展名，该应用程序，如 Microsoft Word 的嵌入式的版本是 Visual Studio 中创建在原位。 这些文档对象必须实现的复合文件<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>接口或该对象必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 如果在注册表中的.rtf 文件无编辑器工厂则环境会在注册表中查找\\.rtf 键，然后打开编辑器中指定。 如果在注册表中找不到的文件扩展名，然后在环境中使用 Visual Studio 核心文本编辑器打开该文件，如果它是一个文本文件。  
  
 如果核心文本编辑器中失败，出现这种情况如果该文件不是一个文本文件，然后在环境中使用其二进制编辑器的文件。  
  
 如果环境未找到编辑器.rtf 扩展在其注册表中，它将加载 VSPackage 实现此编辑器工厂。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>上新的 VSPackage 的方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage 调用`QueryService`为`SID_SVsRegistorEditor`，并使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法以向环境中注册编辑器工厂。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 现在，该环境重新检查已注册的编辑器中，查找.rtf 文件的新注册的编辑器工厂其内部列表。 环境调用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，传入要创建的文件名称和视图类型。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
