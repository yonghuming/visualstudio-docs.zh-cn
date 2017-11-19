---
title: "空间选项卡上，进程属性对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70f9805f0868c7afec70fdda26ff97766281d9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="space-tab-process-properties-dialog-box"></a>“进程属性”对话框 ->“空间”选项卡
使用**空间**选项卡以检查进程的地址空间。 若要显示[过程属性对话框中](../debugger/process-properties-dialog-box.md)，焦点移到[进程视图](../debugger/processes-view.md)窗口。 在树中，选择任何进程节点，然后选择**属性**从**视图**菜单。  
  
 以下设置子网上有**空间**选项卡：  
  
|条目|描述|  
|-----------|-----------------|  
|**显示标记的空间**|使用此列表框中选择的空间 （映像，映射、 保留或未分配） 的类别。|  
|**可执行文件的字节数**|对于所选类别，此进程正在使用的所有地址空间之和。 可执行的内存是可执行程序，但不是能读取或写入的内存。|  
|**仅限 exec 读取的字节数**|对于所选的类别中，在使用此过程的只读属性中使用的所有地址空间之和。 仅限 exec 读取内存是指可以执行和读取。|  
|**Exec 读写字节**|对于所选的类别中，在使用此过程的读写属性中使用的所有地址空间之和。 Exec 读写内存是可由程序执行，以及读取和修改的内存。|  
|**Exec 写入复制字节**|对于所选类别，可由程序执行，以及读取和写入所有地址空间之和。 当需要进程间共享内存时，使用此类型的保护。 如果共享进程只读取内存，那么它们全部使用相同的内存。 如果共享进程需要写访问权限，然后将为该进程生成一份此内存。|  
|**无访问权限字节**|对于所选的类别中，从使用它可以防止一个处理的所有地址空间之和。 尝试读取或如果编写，则会生成访问冲突。|  
|**只读字节**|对于所选的类别中，指可以执行和读取所有地址空间之和。|  
|**读写字节**|对于所选类别，允许读取和写入的所有地址空间之和。|  
|**写副本字节**|针对所选的类别中，所有的地址空间的总和允许共享内存以进行读取，但不是用于写入。 当进程正在读取此内存时，它们可以共享相同的内存。 但是，当某个共享进程想要对此共享内存进行读/写访问，一份该内存专为写入。|