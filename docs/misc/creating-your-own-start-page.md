---
title: "创建你自己的起始页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建起始页"
  - "自定义起始页"
  - "自定义起始页"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# 创建你自己的起始页
你可以通过使用“起始页”项目模板或通过创建一个空白“起始页”来创建自定义“起始页”。  
  
 由于 Visual Studio 应用程序模型上的依赖关系，XAML 设计器可能无法提供完全准确的自定义“起始页”的可视表示形式。  
  
## 使用项目模板  
 “起始页”项目模板创建的“起始页”项目是 Visual Studio 起始页的完整副本。 然后，你可以按你的规范编辑“起始页”。  
  
#### 若要通过使用“起始页”项目模板来创建自定义“起始页”  
  
1.  从 Visual Studio 库下载并安装[起始页项目模板](http://go.microsoft.com/fwlink/?LinkId=186204)。  
  
    > [!WARNING]
    >  此时 Visual Studio 2010 起始页项目模板尚未升级。 有关如何升级该模板的信息，请参阅 [如何：升级 Visual Studio 自定义起始页](../Topic/How%20to:%20Upgrade%20a%20Visual%20Studio%20Custom%20Start%20Page.md)。  
  
2.  安装模板后，使用它创建新的起始页项目。  
  
3.  在“新建项目”对话框的左窗格中，在“已安装的模板”下，展开“其他项目类型”节点，单击“扩展性”。  
  
4.  在中间窗格中，单击“自定义起始页”，然后命名项目并单击“确定”。  
  
     Visual Studio 创建的“起始页”项目是 Visual Studio 起始页的完整副本。  
  
5.  在“解决方案资源管理器”中，打开 **StartPage.xaml**。  
  
6.  编辑 StartPage.xaml。  
  
     在已安装自定义起始页的情况下，你可以按 F5 键打开 Visual Studio 的实验实例来查看所做的工作。  
  
## 创建一个空白起始页  
 创建空白“起始页”最简单的方法是使用“起始页”项目模板，然后删除其内容。  
  
#### 若要通过使用“起始页”项目模板来创建空白“起始页”  
  
1.  如前面过程中所述，通过使用“起始页”项目模板创建“起始页”项目。  
  
2.  打开 StartPage.xaml。  
  
3.  删除所有的页面内容，仅留下外部 xml 元素和所包含的网格 <xref:System.Windows.Controls.Grid> 元素，以使.xaml 文件类似于以下示例。  
  
     [!CODE [BlankStartPage#01](../CodeSnippet/VS_Snippets_VSSDK/blankstartpage#01)]  
  
4.  删除任何不想使用的支持文件。  
  
     你应该保留 .vsix 和 .pkgdef 文件以进行部署。  
  
 或者，你可以通过创建具有正确标记结构，Visual Studio 可以识别的 XAML 文件来创建一个空白“起始页”。 然后，你可以添加标记和代码隐藏以获得所需的外观和功能。 有关详细信息，请参阅[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)。  
  
## 测试并应用自定义起始页  
 在主实例经验证不会崩溃之前，请勿将其设置为运行自定义“起始页”。 测试自定义“起始页”后，你可以通过在 Visual Studio 的主实例中重复该过程的最后三个步骤以将其应用到你的系统。  
  
#### 若要测试自定义“起始页”  
  
1.  按 F5。  
  
     新“起始页”已安装但未选中的情况下，会打开 Visual Studio 实验实例。  
  
2.  在 Visual Studio 的实验实例中，在“工具”菜单上，单击“选项”。  
  
3.  在“选项”对话框中，在“环境”下，选择“启动”。 然后，在“自定义起始页”列表中，选择 .xaml 文件，然后单击“确定”。  
  
4.  在“视图”菜单上，单击“起始页”。  
  
     将显示正在工作的“起始页”。 必须关闭实验实例，重新复制任何已更改的文件，然后再重新打开实验实例，以查看新的更改。  
  
 你可以通过将 .vsix 文件从 bin\\debug 目录上载到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，或上载到另一个网站或 Intranet 共享，来共享你的自定义“起始页”。 有关更多信息，请参见[部署自定义起始页](../extensibility/deploying-custom-start-pages.md)。  
  
## 请参阅  
 [自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)   
 [演练: 将自定义 XAML 添加到开始页](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)