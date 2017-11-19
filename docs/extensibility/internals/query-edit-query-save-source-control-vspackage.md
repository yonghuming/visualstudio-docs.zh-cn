---
title: "查询 (源控件 VSPackage) 保存的编辑查询 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0aeb24f52b1b6b719e81dcd1a9bd93bd5822f8e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>(源控件 VSPackage) 保存的查询编辑查询
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]编辑器可以广播保存查询编辑查询 (QEQS) 事件。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]源存根 （stub） 实现 QEQS 服务，以便它 QEQS 事件的接收方。 然后，这些事件可以委派给的当前处于活动状态的源控件 VSPackage。 VSPackage 实现该活动的源控件<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>及其方法。 方法`IVsQueryEditQuerySave2`接口通常称为第一次和之前保存文档在编辑文档前立即。  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 事件  
 源代码管理 VSPackage 必须通过实现处理 QEQS 事件`IVsQueryEditQuerySave2`接口和所需的方法。 下面是 VSPackage 必须实现至少两个方法的简要说明。 实际实现必须根据源控件模型的逻辑。  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>任何项目或编辑器想要修改的文件时调用。 理想情况下，此方法称为*之前*文件将修改并保存文件时。 调用时，`IVsQueryEditQuerySave2::QueryEditFiles`方法检查给定的文件是否在源代码管理下，它们是否需要被签出，以及是否它们可以重新加载。 如果情况下可防止文件被编辑，`IVsQueryEditQuerySave2::QueryEditFiles`方法通知调用的程序来取消编辑。 还有可能为使调用方指定的调用模式。 在"静默"模式下，此方法采用操作，仅当它不会导致显示任何 UI。 如果 UI 是不可避免地，必须返回一个标志以指示问题。  
  
 该方法的行为以事务性方式运行;也就是说，如果单个文件取消了编辑，则对于的所有文件将被取消编辑。 相反，如果允许编辑，则允许所有文件。 如果此方法允许一次编辑给定的一组文件，它必须始终允许在后续调用相同的一系列文件上的编辑。 允许编辑循环将继续，直到关闭、 保存，和重新加载; 文件除非更改其属性 （属性）;或在更改源代码管理包之前。 在实现时需要考虑的情况下`IVsQueryEditQuerySave2::QueryEditFiles`方法包括多个文件，特殊文件，取消从用户和内存中的编辑。  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>任何项目或编辑器需要保存一组文件时调用。 调用时，`IVsQueryEditQuerySave2::QuerySaveFiles`方法检查如果给定的文件是只读的并且它们是否在源代码管理下。 如果需要对这些文件被签出，则将调用委托给源代码管理包。 如果情况下从正在保存，防止文件`IVsQueryEditQuerySave2::QuerySaveFiles`方法必须告知编辑器取消保存。 与`IVsQueryEditQuerySave2::QueryEditFiles`方法，它是可能为使调用方指定的调用模式。 在"静默"模式下，此方法采用操作，仅当它不会导致显示任何 UI。 如果 UI 是不可避免地，必须返回一个标志以指示问题。  
  
 此方法必须在事务性方式; 中的行为也就是说，如果保存已取消在单个文件，保存取消了对所有文件。 相反，如果允许保存，则它必须允许所有文件。 与`IVsQueryEditQuerySave2::QueryEditFiles`方法时，需要考虑实现情况`IVsQueryEditQuerySave2::QuerySaveFiles`方法包括多个文件，特殊文件，取消从用户和内存中的编辑。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>