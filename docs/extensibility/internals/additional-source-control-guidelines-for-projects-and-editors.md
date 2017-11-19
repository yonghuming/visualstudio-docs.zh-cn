---
title: "项目和编辑器的其他源控件准则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ed84b4b1bf6c974f22682dcb8d899208c653ebc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>项目和编辑器的其他源控制指南
有大量的项目和编辑器应遵循为了支持源代码管理的准则。  
  
## <a name="guidelines"></a>准则  
 你的项目或编辑器还应执行以下操作来支持源代码管理：  
  
|区域|Project|编辑器|详细信息|  
|----------|-------------|------------|-------------|  
|文件的私有副本|X||环境支持文件的私有的副本。 即，在项目中登记每个人具有该项目中的文件他/她自己的私有副本。|  
|ANSI/Unicode 持久性|X|X|如果您编写的持久性代码，保持 ANSI 表单中的文件，因为大多数源控件程序当前不支持 Unicode。|  
|枚举文件|X||项目必须包含其中的所有文件的特定列表，并且必须能够枚举的使用的文件列表<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。 项目还应提供项名称通过其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>实施和支持名称查找 （包括特殊文件） 通过其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>实现。|  
|文本格式|X|X|如果可能，应为文本格式，以支持不同版本的合并文件。 不是以文本格式的文件不能在以后合并与其他版本的文件。 首选的文本格式为 XML。|  
|引用基于|X||在源代码管理中轻松地支持基于引用的项目。 但是，源代码管理，只要项目可以生成其点播情况下，无论这些文件是否存在于磁盘上的文件的列表还支持基于目录的项目。 当从源代码管理打开项目，会在之前其任何文件的第一个中关闭项目文件。|  
|保留可预测的顺序中的对象和属性|X|X|保留可预测的顺序，如字母顺序排列，以便合并中的文件。|  
|重新加载|X|X|当在磁盘上文件更改时，你的编辑器必须能够重新加载它。 当您参与源代码管理时，环境将重新加载数据为你通过调用你<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>实现。 调用了 IVsQueryEditQuerySave 时发生签出时难度最大重新加载用例::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和正在处理信息。 但是，你重新加载的代码必须能够在此情况下运行。<br /><br /> 环境将自动重新加载项目文件。 但是，项目必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>如果它有嵌套层次结构以支持重新加载嵌套项目文件。|  
  
## <a name="see-also"></a>另请参阅  
 [支持源代码管理](../../extensibility/internals/supporting-source-control.md)