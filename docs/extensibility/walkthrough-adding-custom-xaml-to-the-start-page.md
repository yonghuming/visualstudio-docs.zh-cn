---
title: "演练： 将自定义 XAML 添加到开始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 924a6e2640002bc47eb75c903c46b5a170a9c308
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>演练： 将自定义 XAML 添加到开始页
本演练演示如何创建自定义 Visual Studio 起始页，其中包含 Web 浏览器。  
  
## <a name="adding-custom-xaml"></a>添加自定义 XAML  
  
1.  按照中的说明创建起始页[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在 MainWindow.xaml 文件中查找\<网格 > 部分。  
  
3.  添加\<TabControl > 元素和\<TabItem > 内\<网格 > 元素，如下面的示例中所示。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  添加第二个\<TabItem >，使用\<按钮 > 打开一个新项目的元素：  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>测试自定义起始页  
  
1.  按 F5。  
  
     使用自定义起始页安装但未选择打开 Visual Studio 的实验实例。  
  
2.  在 Visual Studio 的实验实例中，打开**工具/选项 / 环境**页。  
  
3.  选择**启动**。 上**自定义起始页**列表中，选择.xaml 文件，然后单击**确定**。  
  
4.  在“视图”  菜单上，单击“起始页” 。  
  
5.  单击**Bing**选项卡。  
  
     你应看到 Bing web 页。  
  
6.  单击**MyButton**选项卡。  
  
     你应该会看到**MyProject**按钮，这将打开**新项目**对话框。  
  
7.  关闭实验实例。  
  
## <a name="applying-the-custom-start-page"></a>应用自定义起始页  
  
#### <a name="to-test-the-custom-start-page"></a>若要测试自定义起始页  
  
1.  在**工具 / 选项 / 环境**，选择**启动**。 上**自定义起始页**列表中，选择.xaml 文件，然后单击**确定**。  
  
## <a name="next-steps"></a>后续步骤  
 Visual Studio 起始页现在包含一个 Web 浏览器选项卡和 MyButton 选项卡上显示的选项卡。你可以创建通过使用具有其他功能的自定义起始页*代码隐藏*模型中所示添加自定义的.dll，[将用户控件添加到起始页](../extensibility/adding-user-control-to-the-start-page.md)。 通过发布到生成的.vsix 文件，可以与其他用户共享自定义起始页[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，或到另一个网站或网络共享。 有关详细信息，请参阅[部署自定义起始页](../extensibility/deploying-custom-start-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF 容器控件](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)