---
title: "配置服务引用对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 26e74c43e79012adc6b241390cd463a35c9f58c1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="configure-service-reference-dialog-box"></a>“配置服务引用”对话框
**配置服务引用**对话框中，您可以配置的行为[!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]服务。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 访问**配置服务引用**对话框中，右击的服务引用中**解决方案资源管理器**选择**配置服务引用**。 此外可以通过单击访问对话框**高级**按钮**添加的服务引用对话框**。  
  
## <a name="task-list"></a>任务列表  
  
-   若要更改承载 WCF 服务的地址，输入中的新地址**地址**字段。  
  
-   若要更改 WCF 客户端中的类的访问级别，选择在访问级别关键字**访问生成的类级别**列表。  
  
-   若要以异步方式调用 WCF 服务的方法，选择**生成异步操作**复选框。  
  
-   若要在 WCF 客户端中生成消息协定类型，请选择**始终生成消息协定**复选框。  
  
-   若要为 WCF 客户端指定列表或字典集合类型，选择从类型**集合类型**和**字典集合类型**列出。  
  
-   若要禁用类型共享，请清除**重新使用引用的程序集中的类型**复选框。 若要启用类型共享引用的程序集的子集，请选择**重新使用引用的程序集中的类型**复选框，选择**重新使用类型指定引用的程序集中**，然后选择所需在引用**引用的程序集列表**。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **地址**  
 用于更新服务引用在其中查找服务的 Web 地址。 例如，在开发过程中服务可能承载在开发服务器上，之后又移到了生产服务器上，因而需要进行地址更改。  
  
> [!NOTE]
>  Address 元素不可用**配置服务引用**对话框中将显示从**添加的服务引用对话框**。  
  
 **生成的类的访问级别**  
 确定 WCF 客户端类的代码访问级别。  
  
> [!NOTE]
>  对于网站项目，该选项将始终设置为 `Public`，并且无法更改。 有关详细信息，请参阅[服务引用疑难解答](../data-tools/troubleshooting-service-references.md)。  
  
 **生成异步操作**  
 确定 WCF 服务的方法是同步调用（默认）还是异步调用。  
  
 **生成基于任务的操作**  
 编写异步代码时，此选项允许你使用随 .Net 4 一起推出的任务并行库 (TPL)。 请参阅[任务并行库 (TPL)](http://msdn.microsoft.com/library/dd460717.aspx)。  
  
 **始终生成消息协定**  
 确定是否将为 WCF 客户端生成消息约定类型。 有关消息约定的详细信息，请参阅[使用消息协定](/dotnet/framework/wcf/feature-details/using-message-contracts)。  
  
 **集合类型**  
 为 WCF 客户端指定列表集合类型。 默认类型为 <xref:System.Array>。  
  
 **字典集合类型**  
 为 WCF 客户端指定字典集合类型。 默认类型为 <xref:System.Collections.Generic.Dictionary%602>。  
  
 **重新使用引用的程序集中的类型**  
 确定在添加或更新服务时，WCF 客户端是否将设法重用引用的程序集中已经存在的类型，而不是生成新的类型。 默认情况下，此选项处于选中状态。  
  
 **重新使用所有引用的程序集中的类型**  
 如果选中中的所有类型**引用的程序集列表**将尽可能重用。 默认情况下，该选项是选中的。  
  
 **重新使用指定的引用程序集的类型**  
 如果选中中的所选的类型**引用的程序集列表**将重复使用。  
  
 **引用的程序集列表**  
 包含一个列表，此列表针对项目或网站列出了引用的程序集。 当**重新使用类型指定引用的程序集中**选择时，可以选择或清除个别程序集。  
  
 **添加 Web 引用**  
 显示[添加 Web 引用对话框](https://msdn.microsoft.com/en-us/library/8dcbc50t(v=vs.100).aspx)。  
  
> [!NOTE]
>  此选项只应该用于针对 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 版的项目。  
  
> [!NOTE]
>  **添加 Web 引用**按钮是时才可用**配置服务引用**对话框中将显示从**添加的服务引用对话框**。  
  
## <a name="see-also"></a>另请参阅  

 [如何： 添加对 Web 服务的引用](how-to-add-update-or-remove-a-wcf-data-service-reference.md)   
 [Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/configure-service-reference-dialog-box.md)