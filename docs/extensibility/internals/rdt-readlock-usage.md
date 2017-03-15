---
title: "RDT_ReadLock 用法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
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
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用情况

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>是标志，它提供了逻辑来锁定文档中运行的文档表 (RDT)，这 Visual Studio IDE 中当前打开的所有文档的列表。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 此标志确定何时打开的文档，以及文档是否是在用户界面中可见或不可见的方式在内存中保持。

通常，您将使用<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>下列任一条件为 true 时︰</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- 如果想要不可见的方式打开的文档和只读的但它尚未建立哪些<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>应拥有它。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- 当您希望用户会提示您保存用户名之前不可见的方式打开的文档显示在 UI 中，然后尝试将其关闭。

## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可见并不可见的文档

当用户在用户界面中，打开的文档<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必须建立文档所有者和<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>标志必须设置。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 如果没有<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>可以建立所有者，则将不保存文档，当用户单击**全部保存**或关闭 IDE。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 这意味着如果文档打开时不可见的方式在修改在内存中，且用户是系统提示您将文档保存在关闭，或如果保存**全部保存**选择，则`RDT_ReadLock`不能使用。 相反，您必须使用`RDT_EditLock`并注册<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>时<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>标志。</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 和文档修改

前面提到的标志指示不可见打开该文档将产生其`RDT_EditLock`到一个可见由用户打开文档时**DocumentWindow**。 当发生这种情况时，则用户看到其中**保存**时提示可见**DocumentWindow**已关闭。 <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>使用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服务最初工作时仅`RDT_ReadLock`（即，当打开文档时不可见的方式来分析信息） 执行。</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> 更高版本，如果必须修改该文档，然后该锁升级到弱**RDT_EditLock**。 如果用户然后打开该文档中的可见**DocumentWindow**、`CodeModel`的弱`RDT_EditLock`被释放。

如果用户然后关闭**DocumentWindow**并选择**否**当系统提示您保存打开的文档，则`CodeModel`实现文档中的所有信息将都释放和重新打开文档从磁盘不可见的方式在下次的详细信息时所必需的文档。 种微妙的此行为是在用户打开其中一个实例**DocumentWindow**不可见的打开文档，对其进行修改，将其关闭，并选择**否**当系统提示您保存文档。 在此情况下，如果该文档具有`RDT_ReadLock`，该文档实际上不会关闭，然后修改的文档将保持打开状态不可见的方式在内存中，即使用户已选择不保存文档。

如果不可见的文档打开使用弱`RDT_EditLock`，则它将产生其锁定，当用户打开文档明显但没有其他锁。 当此用户关闭**DocumentWindow**并选择**否**当系统提示保存文档，然后该文档必须关闭从内存。 这意味着不可见的客户端必须侦听 RDT 事件来跟踪此匹配项。 下次该文档是必需的该文档必须重新打开。
