---
title: "如何： 指定通过 ClickOnce 发布的文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 68773435bc35a93ab49189306db532c68e2b8dad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>如何：指定通过 ClickOnce 发布的文件
发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]与应用程序一起部署的项目中的应用程序、 所有非代码文件。 在某些情况下，可能不希望或需要发布某些文件，或者你可能想要安装基于条件对某些文件。 Visual Studio 提供的功能，若要排除的文件，将文件标记为数据文件或必备组件，并创建用于条件安装的文件组。  
  
 文件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在中管理应用程序**应用程序文件**对话框中，可从访问**发布**页**项目设计器**。  
  
 最初，没有名为的单个文件组**（必需）**。 你可以创建其他文件组并向它们分配文件。 无法更改**下载组**的应用程序运行所需的文件。 例如，应用程序的.exe 或文件标记为数据文件必须属于**（必需）**组。  
  
 默认发布状态值文件值的标记为**（自动）**。 例如，应用程序的.exe 的发布状态为**包括 （自动）**默认情况下。  
  
 文件都具有**生成操作**属性设置为**内容**指定为应用程序文件并将其标记为默认情况下包含。 它们可以为包含、 排除，或标记为数据文件。 例外情况包括，如下所示：  
  
-   默认情况下，如 SQL 数据库 （.mdf 和.mdb） 文件和 XML 文件的数据文件将被标记为数据文件。  
  
-   添加引用时，将按以下方式指定引用程序集 （.dll 文件）： 如果**Copy Local**是**False**，默认情况下作为系统必备程序集标记 (**先决条件 (自动）**) 安装应用程序之前，必须位于 gac。 如果**Copy Local**是**True**，该程序集标记为应用程序程序集的默认情况下 (**包括 （自动）**) 并将复制到在安装的应用程序文件夹。 COM 引用将出现在**应用程序文件**对话框中 （如.ocx 文件） 仅当其**Isolated**属性设置为**True**。 默认情况下，它将为包含。  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>将文件添加到应用程序的文件对话框  
  
1.  选择数据文件中的**解决方案资源管理器**。  
  
2.  在属性窗口中，更改**生成操作**属性**内容**值。  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>若要从 ClickOnce 发布中排除文件  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**应用程序文件**按钮以打开**应用程序文件**对话框。  
  
4.  在**应用程序文件**对话框框中，选择你想要排除的文件。  
  
5.  在**发布状态**字段中，选择**排除**从下拉列表。  
  
### <a name="to-mark-files-as-data-files"></a>若要将文件标记为数据文件  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**应用程序文件**按钮以打开**应用程序文件**对话框。  
  
4.  在**应用程序文件**对话框框中，选择你想要将标记为数据的文件。  
  
5.  在**发布状态**字段中，选择**数据文件**从下拉列表。  
  
### <a name="to-mark-files-as-prerequisites"></a>若要将文件标记为系统必备组件  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**应用程序文件**按钮以打开**应用程序文件**对话框。  
  
4.  在**应用程序文件**对话框框中，选择你想要将标记为系统必备组件的应用程序程序集 （.dll 文件）。 请注意你的应用程序，必须以使其显示在列表中应用程序程序集的引用。  
  
5.  在**发布状态**字段中，选择**先决条件**从下拉列表。  
  
### <a name="to-add-a-new-file-group"></a>若要添加新的文件组  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**应用程序文件**按钮以打开**应用程序文件**对话框。  
  
4.  在**应用程序文件**对话框中，选择**组**字段中为你想要在新的组中包含的文件。  
  
    > [!NOTE]
    >  文件必须具有**生成操作**属性设置为**内容**文件名称出现在之前**应用程序文件**对话框。  
  
5.  在**下载组**字段中，选择**\<新建 … >**从下拉列表。  
  
6.  在**新建组**对话框中，输入组的名称，然后单击**确定**。  
  
### <a name="to-add-a-file-to-a-group"></a>若要将文件添加到组  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**应用程序文件**按钮以打开**应用程序文件**对话框。  
  
4.  在**应用程序文件**对话框中，选择**组**字段中为你想要在新的组中包含的文件。  
  
5.  在**下载组**字段中，从下拉列表中选择一个组。  
  
    > [!NOTE]
    >  无法更改**下载组**的应用程序运行所需的文件。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)