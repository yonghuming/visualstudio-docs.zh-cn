---
title: "演练︰ 将自定义 XAML 添加到开始页上 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c19658e44daf96b6db96c503de1b59127b673111
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>演练︰ 将自定义 XAML 添加到开始页
本演练演示如何创建自定义 Visual Studio 的起始页，其中包含 Web 浏览器。  
  
## <a name="adding-custom-xaml"></a>添加自定义 XAML  
  
1.  通过以下中的说明创建起始页[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在 MainWindow.xaml 文件中查找\<网格&1;> 部分。  
  
3.  添加\<TabControl&1;> 元素和一个\<TabItem&1;> 内\<网格&1;> 元素，如下面的示例中所示。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  添加第二个\<TabItem&1;>，与\<按钮&1;> 打开一个新项目的元素︰  
  
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
  
     将打开 Visual Studio 的实验实例，与自定义起始页安装但未选中。  
  
2.  在 Visual Studio 的实验实例中，打开**工具 /Options / 环境**页。  
  
3.  选择**启动**。 在**自定义起始页**列表，选择您的.xaml 文件，然后单击**确定**。  
  
4.  在“视图”  菜单上，单击“起始页” 。  
  
5.  单击**Bing**选项卡。  
  
     您应看到 Bing web 页面。  
  
6.  单击**MyButton**选项卡。  
  
     您应该看到**MyProject**按钮以打开**新项目**对话框。  
  
7.  关闭实验实例。  
  
## <a name="applying-the-custom-start-page"></a>应用自定义起始页  
  
#### <a name="to-test-the-custom-start-page"></a>若要测试自定义起始页  
  
1.  在**工具 / 选项 / 环境**，选择**启动**。 在**自定义起始页**列表，选择您的.xaml 文件，然后单击**确定**。  
  
## <a name="next-steps"></a>后续步骤  
 Visual Studio 起始页现在包含一个显示 Web 浏览器选项卡和 MyButton 选项卡上的选项卡。 您可以创建自定义起始页通过使用具有其他功能的*代码隐藏*模型中添加自定义.dll，如中所示[将用户控件添加到启动页](../extensibility/adding-user-control-to-the-start-page.md)。 通过将发布到生成的.vsix 文件，可与其他用户共享自定义起始页[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，或到另一个网站或网络共享位置。 有关详细信息，请参阅[部署自定义起始页](../extensibility/deploying-custom-start-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF 容器控件](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
