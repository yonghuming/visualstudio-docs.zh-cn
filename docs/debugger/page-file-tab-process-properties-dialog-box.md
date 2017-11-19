---
title: "页面文件选项卡上，进程属性对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bf5215e7a6d4c4a4a0dac37a9bde2b15fb8f19a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="page-file-tab-process-properties-dialog-box"></a>“进程属性”对话框 ->“页文件”选项卡
使用**页面文件**选项卡上，若要检查进程的分页文件。 若要显示[过程属性对话框中](../debugger/process-properties-dialog-box.md)，焦点移到[进程视图](../debugger/processes-view.md)窗口。 在树中，选择任何进程节点，然后选择**属性**从**视图**菜单。  
  
 以下设置子网上有**页面文件**选项卡：  
  
|条目|描述|  
|-----------|-----------------|  
|**页面文件字节**|当前此进程正在使用的分页文件中的页面数。 分页文件存储的数据的进程使用，但不是包含其他文件中的页。 分页文件可供所有进程，并运行其他进程时，在分页文件的空间不足可能会导致错误。|  
|**峰值页面文件字节**|分页文件中使用此过程具有最大页数。|  
|**页错误**|在此进程中执行的线程的页面错误数。 当一个线程是指不在其工作集在主内存中的虚拟内存页面，页面错误时发生。 因此，页面将不会检索从磁盘是否在待机列表上，因此已在主内存中，或如果它正在由另一个过程与将页面共享。|