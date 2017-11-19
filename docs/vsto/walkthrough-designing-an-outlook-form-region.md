---
title: "演练： 设计 Outlook 窗体区域 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: form regions [Office development in Visual Studio], creating
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f2d8e1f8ad116bd6db12eca288e567a652e502a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>演练：设计 Outlook 窗体区域
  自定义窗体区域扩展标准或自定义 Microsoft Office Outlook 窗体。 在本演练中，你将设计作为新页出现在联系人项目的检查器窗口中的自定义窗体区域。 通过将地址信息发送到 Windows Live 本地搜索网站，此窗体区域将显示为联系人列出的每个地址的映射。 有关窗体区域的信息，请参阅[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 本演练阐释了以下任务：  
  
-   创建新的 Outlook VSTO 外接程序项目。  
  
-   将窗体区域添加到 VSTO 外接程序项目。  
  
-   设计窗体区域的布局。  
  
-   自定义窗体区域的行为。  
  
-   测试 Outlook 窗体区域。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")本主题的视频版本，请参阅[视频帮助： 设计 Outlook 窗体区域](http://go.microsoft.com/fwlink/?LinkID=140824)。  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>创建新的 Outlook VSTO 外接程序项目  
 首先创建基本的 VSTO 外接程序项目。  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>创建新的 Outlook VSTO 外接程序项目  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，创建 Outlook VSTO 外接程序项目名**MapItAddIn**。  
  
2.  在 **“新建项目”** 对话框中，选择 **“创建解决方案的目录”**。  
  
3.  将项目保存到任一目录。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>向 Outlook VSTO 外接程序项目添加窗体区域  
 Outlook VSTO 外接程序解决方案可包含一个或多个 Outlook 窗体区域项。 通过将窗体区域项添加到你的项目**新建 Outlook 窗体区域**向导。  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>向 Outlook VSTO 外接程序项目添加窗体区域  
  
1.  在**解决方案资源管理器**，选择**MapItAddIn**项目。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
3.  在**添加新项**对话框中，选择**Outlook 窗体区域**，命名该文件**命名为 MapIt**，然后单击**添加**。  
  
     **NewOutlook 窗体区域**向导将启动。  
  
4.  上**选择你想要创建窗体区域**页上，单击**设计新的窗体区域**，然后单击**下一步**。  
  
5.  上**选择你想要创建的窗体区域类型**页上，单击**单独**，然后单击**下一步**。  
  
     A*单独*窗体区域将一个新页面添加到 Outlook 窗体。 有关窗体区域类型的更多信息，请参阅 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)。  
  
6.  上**提供说明性文本并选择显示首选项**页上，键入**Map It**中**名称**框。  
  
     打开联系人项目时，此名称将显示在检查器窗口的功能区中。  
  
7.  选择**检查器中撰写模式**和**读取模式下的检查器**，然后单击**下一步**。  
  
8.  上**标识将显示此窗体区域的邮件类**页上，清除**邮件**，选择**联系人**，然后单击**完成**.  
  
     MapIt.cs 或 MapIt.vb 文件将添加到项目中。  
  
## <a name="designing-the-layout-of-the-form-region"></a>设计窗体区域的布局  
 通过使用直观地开发窗体区域*窗体区域设计器*。 可将托管的控件拖到窗体区域设计器图面。 使用设计器和**属性**窗口来调整控件的布局和外观。  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>设计窗体区域的布局  
  
1.  在**解决方案资源管理器**，展开**MapItAddIn**项目，，然后双击 MapIt.cs 或 MapIt.vb 以打开窗体区域设计器。  
  
2.  右键单击设计器中，并依次**属性**。  
  
3.  在**属性**窗口中，设置**大小**到**664、 469**。  
  
     这可确保窗体区域的大小足以显示映射。  
  
4.  在 **“视图”** 菜单上单击 **“工具箱”**。  
  
5.  从**公共控件**选项卡**工具箱**，添加**WebBrowser**到窗体区域。  
  
     **WebBrowser**将显示为联系人列出的每个地址的映射。  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>自定义窗体区域的行为  
 将代码添加到窗体区域事件处理程序，从而自定义窗体区域在运行时的行为方式。 对于此窗体区域而言，代码将检查 Outlook 项的属性，并确定是否显示 Map It 窗体区域。 如果它显示该窗体区域，代码将导航到 Windows Live 本地搜索并加载 Outlook 联系人项目中列出的每个地址的映射。  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>自定义窗体区域的行为  
  
1.  在**解决方案资源管理器**，MapIt.cs 或 MapIt.vb，右键单击，然后单击**查看代码**。  
  
     MapIt.cs 或 MapIt.vb 将在代码编辑器中打开。  
  
2.  展开**窗体区域工厂**代码区域。  
  
     将公开名为 `MapItFactory` 的窗体区域工厂类。  
  
3.  将以下代码添加到 `MapItFactory_FormRegionInitializing` 事件处理程序中。 将在用户打开联系人项目时调用此事件处理程序。 下面的代码确定联系人项目是否包含地址。 如果联系人项目不包含地址，此代码将设置<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>类到**true** ，并且不显示窗体区域。 否则，VSTO 外接程序将引发 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，并显示窗体区域。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  将以下代码添加到 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件处理程序中。 这段代码执行下列任务：  
  
    -   将联系人项目中的每个地址连接起来，并创建一个 URL 字符串。  
  
    -   调用 <xref:System.Windows.Forms.WebBrowser> 对象的 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法，并将 URL 字符串作为参数传递。  
  
     本地搜索网站将在 Map It 窗体区域中出现，并在便笺本中显示每个地址。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>测试 Outlook 窗体区域  
 运行项目时，Visual Studio 将打开 Outlook。 打开联系人项目以查看 Map It 窗体区域。 Map It 窗体区域显示为包含地址的任何联系人项目的窗体中的页面。  
  
#### <a name="to-test-the-map-it-form-region"></a>测试 Map It 窗体区域  
  
1.  按 F5 运行项目。  
  
     Outlook 将打开。  
  
2.  在 Outlook 中，在**主页**选项卡上，单击**新项**，然后单击**联系人**。  
  
3.  在联系人窗体中，键入**Ann Beebe**为联系人名称，然后指定以下三个地址。  
  
    |地址类型|Address|  
    |------------------|-------------|  
    |**业务**|**4567 Main St.东城，NY**|  
    |**主页**|**1234 北部 St.东城，NY**|  
    |**其他**|**3456 Main St.西雅图，WA**|  
  
4.  保存并关闭联系人项目。  
  
5.  重新打开**Ann Beebe**联系人项目。  
  
6.  在**显示**组项的功能区中，单击**Map It**以打开 Map It 窗体区域。  
  
     Map It 窗体区域出现，并显示本地搜索网站。 **业务**，**主页**，和**其他**地址将出现在便笺本。 在便笺本中，选择需映射的地址。  
  
## <a name="next-steps"></a>后续步骤  
 可从以下主题了解有关如何自定义 Outlook 应用程序 UI 的详细信息：  
  
-   若要了解如何自定义 Outlook 项的功能区，请参阅 [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)   
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [Outlook 窗体区域创建准则](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [演练： 导入在 Outlook 中设计的窗体区域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [如何： 向 Outlook 外接程序项目添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [将窗体区域与 Outlook 邮件类关联](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook 窗体区域中的自定义操作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [如何：防止 Outlook 显示窗体区域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  