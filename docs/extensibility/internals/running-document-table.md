---
title: "正在运行的 Document 表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "读锁定"
  - "正在运行的 document 表 (RDT) IVsDocumentLockHolder 接口"
  - "正在运行的 document 表 (RDT)"
  - "正在运行的 document 表 (RDT) 编辑锁"
  - "运行 document 表的文档数据对象"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 正在运行的 Document 表
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 将称为运行文档表 \(RDT\) 的内部结构中的所有当前打开的文档的列表来维护。 此列表包括所有打开的文档在内存中，而不考虑是否当前正在编辑这些文档。 文档是保留不变，项目或主项目文件 （例如，.vcxproj 文件） 中包括的文件的任何项。  
  
## 运行 Document 表中的元素  
 正在运行的 document 表包含以下各项。  
  
|元素|描述|  
|--------|--------|  
|文档名字对象|一个字符串，唯一标识文档的数据对象。 这是项目系统中管理文件 \(例如，C:\\MyProject\\MyFile\) 的绝对文件路径。 此字符串还用于保存在文件系统，如在数据库中的存储过程之外的存储区中的项目。 在这种情况下，项目系统可以创造的唯一字符串，它可以识别和可能分析以确定如何将文档存储。|  
|层次结构所有者|层次结构中拥有对象的文档中，由表示 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 接口。|  
|项 ID|层次结构中特定项的的项的标识符。 此值是唯一的而拥有本文档的层次结构中的所有文档，但不是保证此值在不同的层次结构是唯一的。|  
|文档数据对象|最低保护措施，这是 `IUnknown`<br /><br /> 的名称。 IDE 不需要任何特定的接口之外 `IUnknown` 自定义编辑器的文档的数据对象的接口。 但是，对于标准编辑器中，编辑器的实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 处理从项目文件持久性调用所需的接口。 有关详细信息，请参阅[保存标准文档](../../extensibility/internals/saving-a-standard-document.md)。|  
|Flags|标志，用于控制是否保存文档时，是否将应用的读取或编辑锁，以此类推，可在项添加到 RDT 时指定。 有关详细信息，请参阅 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 枚举。|  
|编辑锁计数|编辑锁的计数。 编辑锁表示某种编辑器打开以便进行编辑的文档。 当编辑锁的计数转换为零时，被提示用户保存文档时，如果它已被修改。 例如，每次您在使用的编辑器中打开文档 **新窗口** 命令时，编辑锁添加 RDT 中该文档。 要设置一个编辑锁，该文档必须有一个层次结构或项 id。|  
|读取锁计数|读取锁的计数。 读取的锁定指示某种机制，如的向导通过读取该文档。 读取的锁定将文档保留在 RDT 中处于活动状态时，该值指示不能编辑该文档。 可以将设置读的锁定，即使该文档不会有一个层次结构或项 id。 此功能允许您打开的文档在内存中并将其填入 RDT 而无需拥有的任何层次结构的文档。 很少使用此功能。|  
|锁的持有者|一个实例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 接口。 锁的持有者是通过打开和编辑文档在编辑器之外的向导等功能实现的。 锁的持有者允许将添加到文档，以防止从正在关闭时仍编辑文档的编辑锁的功能。 通常情况下，编辑由文档窗口 （也就是说，编辑器） 仅添加锁。|  
  
 RDT 中的每个条目都有唯一的层次结构或与之关联，它通常与项目中的一个节点相对应的项 ID。 通常由层次结构中拥有所有文档进行编辑。 在 RDT 中所做的条目控制哪些项目，或\-\-更准确地 — 的层次结构中，当前拥有所编辑的文档数据对象。 在 RDT 中使用的信息，IDE 可以避免文档中，在每次打开多个项目。  
  
 层次结构还控制数据的持久性，并在 RDT 中使用的信息来更新 **保存** 和 **另存为** 对话框。 当用户修改文档，然后选择 **退出** 命令 **文件** 菜单上，IDE 会提示他们提供 **保存更改** 对话框中显示的项目和项目项的当前修改所有这些内容。 这允许用户选择一种要保存的文档。 若要保存的文档的列表 （只有更改这些文档） 从 RDT 生成的。 您会看到在任何项目 **保存更改** 对话框中，在退出该应用程序时应 RDT 中有记录。 RDT 协调是否已保存的文档和是否提示用户一次保存有关使用针对每个文档的标志条目中指定的值的操作。 RDT 标志的详细信息，请参阅 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 枚举。  
  
## 编辑锁和读取锁  
 编辑锁和读的锁定驻留在 RDT。 文档窗口递增和递减编辑锁定。 因此，当用户在打开新文档窗口中，编辑锁计数递增 1。 当编辑锁的数目为零时，层次结构是指示实时编码器持久保存或保存的数据关联的文档。 层次结构然后可以将以任何方式，包括持久保存为文件或存储库中的项的数据持久保存。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> 中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 界面来添加编辑锁和读锁定和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 方法来移除这些锁。  
  
 通常情况下，实例化一个编辑器的文档窗口时，该窗口框架中自动添加该文档的编辑锁 RDT。 但是，如果您创建文档的自定义视图，不使用标准的文档窗口 \(也就是说，它不实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 接口\)，则您需要设置您自己编辑的锁。 例如，在向导中，编辑了的文档而无需在编辑器中打开。 为了使文档锁定要打开的向导和类似的实体，这些实体必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 接口。 若要注册文档锁持有者，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 方法，并传入你 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 实现。 这样做会向 RDT 文档锁持有者。 实现文档锁持有者的另一种情况是如果您打开通过特殊工具窗口的文档。 在此情况下，您不能具有工具窗口中关闭该文档。 但是，通过将注册为在 RDT 文档锁的持有者，IDE 可以调用的实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 方法提示文档的结束。  
  
## 运行 Document 表的其他用法  
 在 IDE 中的其他实体使用 RDT 来获取有关文档的信息。 例如，源代码控制管理器使用 RDT 告知系统后，它获取最新版本的文件重新加载编辑器中的文档。 若要执行此操作，源代码控制管理器查找中 RDT 以查看其中的任何已打开的文件。 如果它们是的则源代码控制管理器首先检查以查看层次结构实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 如果项目未实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法，则源控制管理器有关的实现会检查 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 文档的数据对象直接的方法。  
  
 IDE 还使用 RDT resurface （使在最前面） 打开的文档，如果用户请求该文档。 有关详细信息，请参阅[通过使用打开文件命令显示文件](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 若要确定是否在 RDT 中打开文件，请执行下列操作之一。  
  
-   若要查找该项目已打开的文档名字对象 （即完整的文档路径） 的查询。  
  
-   使用层次结构或项目 ID 请项目系统要求的完整的文档路径，然后 RDT 中查找项。  
  
## 请参阅  
 [RDT\_ReadLock 使用情况](../../extensibility/internals/rdt-readlock-usage.md)   
 [持久性和运行 Document 表](../../extensibility/internals/persistence-and-the-running-document-table.md)