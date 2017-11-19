---
title: "RDT_ReadLock 使用情况 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1bf4165340266d36535a1ad18336b74df84264e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用情况

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>是标志，它提供逻辑以锁定文档中运行的文档表 (RDT)，即当前打开的 Visual Studio IDE 的所有文档的列表。 此标志确定当打开文档，以及文档是否是在用户界面中可见或保持不可见的方式在内存中。

通常情况下，将使用<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>满足下列情况之一时：

- 如果想要不可见的方式打开的文档和只读的但它尚不建立其<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>应拥有它。

- 当您希望用户，会提示您保存用户名之前不可见的方式打开的文档显示在 UI 中，并尝试以将其关闭。

## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可见的且不可见的文档

当用户在 UI 中，打开的文档<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必须建立文档的所有者和<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>必须设置标志。 如果没有<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>可以建立所有者，则将不保存文档，当用户单击**保存所有**或关闭 IDE。 这意味着如果文档打开时不可见的方式，它将修改在内存中，并提示保存文档，在关闭或保存如果用户**保存所有**选择，则`RDT_ReadLock`不能使用。 相反，你必须使用`RDT_EditLock`并注册<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>时<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>标志。

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 和文档修改

前面提到的标志指示不可见的打开的文档将产生其`RDT_EditLock`到可见用户打开文档时**新建窗口**。 当发生这种情况时，则用户会看到与**保存**提示时可见**新建窗口**已关闭。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`使用实现，<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服务最初工作时仅`RDT_ReadLock`（即时不可见的方式打开该文档进行分析信息） 执行。 更高版本，如果必须修改该文档，然后锁升级到为弱**RDT_EditLock**。 如果用户然后打开该文档中的可见**新建窗口**、`CodeModel`的弱`RDT_EditLock`释放。

如果用户然后关闭**新建窗口**并选择**否**当系统提示保存打开的文档，则`CodeModel`实现释放文档中的所有信息并重新打开从磁盘不可见的方式的详细信息，才能使用该文档的下一步时间的文档。 种微妙的此行为是在用户打开其中一个实例**新建窗口**的不可见打开的文档中，对其进行修改，将其关闭，然后选择**否**当系统提示保存文档。 在此情况下，如果该文档具有`RDT_ReadLock`，文档实际上不会关闭，然后经过修改的文档将保持打开状态不可见的方式在内存中，即使用户选择不保存文档。

如果不可见的打开的文档使用为弱`RDT_EditLock`，则它将产生其锁定，当用户打开文档这并不持有任何其他锁。 当用户关闭**新建窗口**并选择**否**当系统提示保存文档，然后文档必须关闭从内存。 这意味着不可见的客户端必须侦听 RDT 事件，以跟踪此匹配项。 下次文档是必需的必须打开文档。