---
title: "演练： 在数据集设计器中创建数据表 |Microsoft 文档"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 0e1328eda7974b7e4ec04df0c4f5bd969cf09de6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>演练：在数据集设计器中创建数据表
本演练说明了如何创建<xref:System.Data.DataTable>（不带 TableAdapter) 使用**数据集设计器**。 有关创建包括 Tableadapter 的数据表的信息，请参阅[创建和配置 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 本演练涉及以下任务：  
  
-   创建新的 Windows 窗体应用程序项目  
  
-   将新的数据集添加到应用程序  
  
-   将提供新数据表添加到数据集  
  
-   向数据表添加列  
  
-   设置表的主键  
  
## <a name="creating-a-new-windows-forms-application"></a>创建新的 Windows 窗体应用程序  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>若要创建新的 Windows 窗体应用程序项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**DataTableWalkthrough**，然后选择**确定**。 
  
     **DataTableWalkthrough**项目时创建，并添加到**解决方案资源管理器**。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>将新的数据集添加到应用程序  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>若要向项目添加新的数据集项  
  
1.  上**项目**菜单上，选择**添加新项...**.  
  
     添加新项对话框。  
  
2.  在左侧窗格中，选择**数据**，然后选择**数据集**在中间窗格中。  
  
3.  选择“添加”。  
  
     Visual Studio 将添加名为的文件**dataset1.xsd**到项目并将其在打开**数据集设计器**。  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>将新数据表添加到数据集  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>若要将提供新数据表添加到数据集  
  
1.  拖动**DataTable**从**数据集**选项卡**工具箱**到**数据集设计器**。  
  
     名为的表**DataTable1**添加到数据集。  
   
2.  单击的标题栏**DataTable1**和将其重命名`Music`。  
  
## <a name="adding-columns-to-the-data-table"></a>向数据表添加列  
  
#### <a name="to-add-columns-to-the-data-table"></a>将列添加到数据表  
  
1.  右键单击**音乐**表。 指向**添加**，然后单击**列**。  
  
2.  名称列`SongID`。  
  
3.  在**属性**窗口中，设置<xref:System.Data.DataColumn.DataType%2A>属性<xref:System.Int16?displayProperty=fullName>。  
  
4.  重复此过程，并添加以下各列：  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>设置表的主键  
数据的所有表应都具有主键。 为主键唯一标识数据表中的特定记录。  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>若要设置的数据表的主键  
  
-   右键单击**SongID**列，，然后单击**设置主键**。  
  
     密钥图标旁边将出现**SongID**列。  
  
## <a name="saving-your-project"></a>保存你的项目  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>保存 DataTableWalkthrough 项目  
  
-   上**文件**菜单上，单击**保存所有**。  
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中创建和配置数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[验证数据](../data-tools/validate-data-in-datasets.md)   
[保存数据](../data-tools/saving-data.md)   