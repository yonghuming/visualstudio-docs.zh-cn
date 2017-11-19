---
title: "运行 Document 表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf66dce40cda2d72757c3a2fe141ed023b286d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="running-document-table"></a>正在运行的文档表
IDE 维护称为正在运行的文档表 (RDT) 的内部结构中的所有当前打开的文档的列表。 此列表包括所有打开的文档在内存中，而不考虑是否当前正在编辑这些文档。 文档是保持不变，包括在项目或主项目文件 （例如，.vcxproj 文件） 的文件的任何项。  
  
## <a name="elements-of-the-running-document-table"></a>运行文档表元素  
 正在运行的文档表包含以下条目。  
  
|元素|描述|  
|-------------|-----------------|  
|文档标记|一个字符串，唯一标识文档数据对象。 这是一个管理文件 (例如，C:\MyProject\MyFile) 的项目系统的绝对文件路径。 此字符串还用于保存在文件系统，如在数据库中的存储过程以外的存储中的项目。 在这种情况下，项目系统可以创建的唯一字符串，它可以识别和可能分析来确定如何将文档存储。|  
|层次结构所有者|拥有该文档，所表示的层次结构对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>接口。|  
|项 ID|层次结构中的特定项的项标识符。 此值是唯一的而拥有本文档的层次结构中的所有文档，但此值不一定是唯一的不同的层次结构。|  
|文档数据对象|最小值，这是`IUnknown`<br /><br /> 的名称。 IDE 不需要任何特定界面超出`IUnknown`为自定义编辑器的文档数据对象的接口。 但是，对于标准编辑器中，编辑器的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>需要接口来处理文件从项目的持久性调用。 有关详细信息，请参阅[保存标准文档](../../extensibility/internals/saving-a-standard-document.md)。|  
|Flags|条目添加到 RDT 时，可以指定可控制是否保存文档后，是否将应用的读取或编辑锁，标志等。 有关详细信息，请参见 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 枚举。|  
|编辑锁计数|编辑锁的计数。 编辑锁指示某些编辑器打开以便进行编辑的文档。 当编辑锁的计数转换为零时，用户是系统提示保存文档时，如果修改它。 例如，每次在使用编辑器中打开文档时**新窗口**命令时，编辑锁添加 RDT 中该文档。 要设置的编辑锁的顺序，该文档必须具有层次结构或项 id。|  
|读取锁计数|读取锁的计数。 读取的锁定指示文档正在通读如向导某种机制。 读取的锁定包含 RDT 中处于活动状态时，该值指示不能编辑文档的文档。 你可以设置读取的锁定，即使该文档不具有层次结构或项 id。 此功能，可在内存中打开文档，并将其填入 RDT 而无需拥有的任何层次结构的文档。 很少使用此功能。|  
|锁的持有者|实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>接口。 锁的持有者实现的功能，如的向导的打开和编辑在编辑器之外的文档。 锁的持有者允许的功能将添加到要防止仍编辑时关闭该文档的文档的编辑锁。 通常情况下，编辑锁仅能通过文档窗口 （即，编辑器） 的代码来添加。|  
  
 RDT 中的每个条目都有唯一的层次结构或与之关联，通常对应于项目中的一个节点的项 ID。 通常由层次结构拥有可用于编辑的所有文档。 在 RDT 中所做的条目控制哪些项目，或-更准确地-的层次结构中，当前拥有正在编辑的文档数据对象。 在 RDT 中使用的信息，IDE 可以避免文档中，在一次打开由多个项目。  
  
 层次结构还控制数据的持久性，并使用在 RDT 中的信息来更新**保存**和**另存为**对话框。 当用户修改文档，然后选择**退出**命令**文件**菜单上，IDE 将提示他们提供**保存更改**对话框中，可以显示它们的所有项目和当前修改的项目项。 这允许用户选择哪个要保存的文档。 若要保存的文档的列表 （即，会发生变化，这些文档） 从 RDT 生成。 你会看到在任何项**保存更改**对话框中，在退出应用程序时应具有 RDT 中的记录。 RDT 协调是否已保存的文档，并且是否保存有关提示用户使用针对每个文档的标志条目中指定的值的操作。 RDT 标志的详细信息，请参阅<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>枚举。  
  
## <a name="edit-locks-and-read-locks"></a>编辑锁和读取锁  
 编辑锁定和读的锁定驻留在 RDT。 文档窗口递增和递减编辑锁定。 因此，当用户打开新的文档窗口，编辑锁计数递增 1。 当编辑锁的数目达到零时，层次结构处于有信号状态保存或保存的数据关联的文档。 层次结构然后可以将任何方式，包括持久保存为文件或存储库中的项中的数据持久保存。 你可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>中的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>界面来添加编辑锁和读锁定，和<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法来删除这些锁。  
  
 通常情况下，实例化编辑器的文档窗口时，窗口框架中自动添加文档的编辑锁 RDT。 但是，如果你创建文档的自定义视图，不使用标准的文档窗口 (即，它未实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>接口)，则需要设置你自己编辑锁定。 例如，在向导中，文档只编辑而不在编辑器中打开。 在文档锁，以打开通过向导和类似的实体的顺序，必须实现这些实体<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>接口。 若要注册你文档锁的持有者，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法，并传入你<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>实现。 这样将文档锁的持有者添加到 RDT。 实现文档锁的持有者的另一种情况是如果你打开通过特殊工具窗口的文档。 在此情况下，你不能有关闭文档工具窗口。 但是，通过将注册为 RDT 中的文档锁的持有者，IDE 可以调用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>方法提示文档的关闭。  
  
## <a name="other-uses-of-the-running-document-table"></a>运行 Document 表的其他用法  
 在 IDE 中的其他实体使用 RDT 来获取有关文档的信息。 例如，源控制管理器使用 RDT 告诉系统之后，它获取最新版本的文件重新加载编辑器中的文档。 若要执行此操作，源代码控制管理器查找中 RDT 其中任何打开的文件。 如果它们是，则源代码控制管理器首先检查以查看层次结构实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 如果项目不实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法，则源控制管理器有关的实现会检查<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>上文档数据对象直接的方法。  
  
 IDE 还使用 RDT resurface （置于顶层） 未打开的文档中，如果用户请求该文档。 有关详细信息，请参阅[通过使用打开文件命令显示文件](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 若要确定文件是否在 RDT 中打开，执行下列操作之一。  
  
-   要查看项是否打开的文档名字对象 （即，完整的文档路径） 的查询。  
  
-   使用层次结构或项 ID 请项目系统要求的完整文档路径，然后在 RDT 中查找项。  
  
## <a name="see-also"></a>另请参阅  
 [RDT_ReadLock 使用情况](../../extensibility/internals/rdt-readlock-usage.md)   
 [持久性和正在运行的文档表](../../extensibility/internals/persistence-and-the-running-document-table.md)