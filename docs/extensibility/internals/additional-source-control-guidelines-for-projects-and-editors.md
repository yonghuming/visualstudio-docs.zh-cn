---
title: "为项目和编辑器的其他源控制指南 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
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
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>为项目和编辑器的其他源控制指南
有大量的项目和编辑器应遵循为了支持源代码管理的准则。  
  
## <a name="guidelines"></a>准则  
 您的项目或编辑器还应执行以下操作以支持源控件︰  
  
|区域|Project|编辑器|详细信息|  
|----------|-------------|------------|-------------|  
|文件的私有副本|x||环境支持文件的私有的副本。 也就是说，在项目中登记每个人都有他/她自己的私有副本，该项目中的文件。|  
|ANSI/Unicode 持久性|x|x|如果您编写的持久性代码，因为大多数源代码管理程序目前不支持 Unicode 保留 ANSI 表单中的文件。|  
|枚举的文件|x||项目必须包含其中的所有文件的特定列表，并且必须能够枚举的文件使用的列表<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 项目还应公开的项名称通过其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>实施和支持的名称查找 （包括特殊文件） 通过其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>实现。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|文本格式|x|x|如果可能，文件应以文本格式支持不同版本的合并。 不以文本格式的文件不能在以后合并与其他版本的文件。 首选的文本格式为 XML。|  
|基于引用的|x||在源代码管理中轻松地支持基于引用的项目。 但是，基于目录的项目也受源代码管理，只要该项目可以生成按需，而不考虑这些文件是否存在于磁盘上文件的列表。 当从源代码管理打开项目，项目文件是在停止之前其任何文件的第一个。|  
|保留在可预知的顺序中的对象和属性|x|x|保留可预测的顺序，如字母顺序排列，以便于合并文件。|  
|重新加载|x|x|当在磁盘上文件更改时，您的编辑器必须能够重新加载它。 当参与源代码管理时，环境将重新加载数据为您通过调用您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>实现。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 最困难的重新加载情况是签出过程中出现时调用了 IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和正在处理的信息。</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 但是，在重新加载代码必须能够在这种情况中运行。<br /><br /> 环境会自动重新加载项目文件。 但是，一个项目必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>如果有嵌套层次结构以支持重新加载嵌套项目文件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>另请参阅  
 [支持的源控件](../../extensibility/internals/supporting-source-control.md)
