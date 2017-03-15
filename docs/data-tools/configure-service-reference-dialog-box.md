---
title: "“配置服务引用”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "WCF 服务，“配置服务引用”对话框"
  - "服务引用 [Visual Studio]，配置行为"
  - "“配置服务引用”对话框"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “配置服务引用”对话框
**“配置服务引用”**对话框使你能够配置 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 服务的行为。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。  若要更改设置，请在“工具”菜单上选择“导入和导出设置”。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 要访问“配置服务引用”对话框，请右击“解决方案资源管理器”中的一个服务引用，然后选择“配置服务引用”。  你还可以通过单击[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)中的**“高级”**按钮来访问该对话框。  
  
## 任务列表  
  
-   要更改承载 WCF 服务的地址，请在“地址”字段中输入新的地址。  
  
-   要更改 WCF 客户端中类的访问级别，请在“生成的类的访问级别”列表中选择一个访问级别关键字。  
  
-   要异步调用 WCF 服务的方法，请选中“生成异步操作”复选框。  
  
-   要在 WCF 客户端中生成消息约定类型，请选中“始终生成消息约定”复选框。  
  
-   要为 WCF 客户端指定列表集合类型或字典集合类型，请从“集合类型”和“字典集合类型”列表中选择类型。  
  
-   要禁用类型共享，请清除“重新使用引用的程序集中的类型”复选框。  要对引用的程序集的子集启用类型共享，请选中“重新使用引用的程序集中的类型”复选框，接着选中“重新使用所引用的指定程序集中的类型”，然后在“引用的程序集列表”中选择所需的引用。  
  
## UIElement 列表  
 **Address**  
 用于更新服务引用在其中查找服务的 Web 地址。  例如，在开发过程中服务可能承载在开发服务器上，之后又移到了生产服务器上，因而需要进行地址更改。  
  
> [!NOTE]
>  从[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)中显示**“配置服务引用”**对话框时，“地址”元素不可用。  
  
 **生成的类的访问级别**  
 确定 WCF 客户端类的代码访问级别。  
  
> [!NOTE]
>  对于网站项目，该选项将始终设置为 `Public`，并且无法更改。  有关详细信息，请参阅[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)。  
  
 **生成异步操作**  
 确定 WCF 服务的方法是同步调用（默认）还是异步调用。  
  
 **生成基于任务的操作**  
 编写异步代码时，此选项允许你使用随 .Net 4 一起推出的任务并行库 \(TPL\)。  请参阅[“任务并行库 \(TPL\)”](http://msdn.microsoft.com/library/dd460717.aspx)。  
  
 **始终生成消息约定**  
 确定是否将为 WCF 客户端生成消息约定类型。  有关消息约定的详细信息，请参阅[使用消息约定](../Topic/Using%20Message%20Contracts.md)。  
  
 **集合类型**  
 为 WCF 客户端指定列表集合类型。  默认类型为 <xref:System.Array>。  
  
 **字典集合类型**  
 为 WCF 客户端指定字典集合类型。  默认类型为 <xref:System.Collections.Generic.Dictionary%602>。  
  
 **重新使用引用的程序集中的类型**  
 确定在添加或更新服务时，WCF 客户端是否将设法重用引用的程序集中已经存在的类型，而不是生成新的类型。  默认情况下，此选项处于选中状态。  
  
 **重新使用所有引用的程序集中的类型**  
 如果选中此项，则会尽可能重用“引用的程序集列表”中的所有类型。  默认情况下，该选项是选中的。  
  
 **重新使用所引用的指定程序集中的类型**  
 如果选中此项，将只重用“引用的程序集列表”中选定的类型。  
  
 **引用的程序集列表**  
 包含一个列表，此列表针对项目或网站列出了引用的程序集。  如果选中“重新使用所引用的指定程序集中的类型”，则可选中或清除个别程序集。  
  
 **添加 Web 引用**  
 显示[“添加 Web 引用”对话框](http://msdn.microsoft.com/zh-cn/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)。  
  
> [!NOTE]
>  此选项只应该用于针对 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 版的项目。  
  
> [!NOTE]
>  仅在从[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)中显示**“配置服务引用”**对话框时，**“添加 Web 引用”**按钮才可用。  
  
## 请参阅  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/configure-service-reference-dialog-box.md)   
 [使用 ASMX 和 WCF 服务示例](http://msdn.microsoft.com/zh-cn/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)