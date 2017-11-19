---
title: "演练： 为 SharePoint 创建 Web 部件 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3293382ffc0c36fb78bb115d0f38c311278a7151
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>演练：为 SharePoint 创建 Web 部件
  Web 部件使用户能够使用浏览器直接修改内容、 外观和行为的 SharePoint 网站页。 本演练演示如何通过使用创建 Web 部件**Web 部件**Visual Studio 2010 中的项模板。  
  
 Web 部件显示在数据网格中的员工。 用户指定包含雇员数据的文件的位置。 用户还可以筛选数据网格，以便显示在列表中只是经理的员工。  
  
 本演练阐释了以下任务：  
  
-   通过使用 Visual Studio 中创建 Web 部件**Web 部件**项模板。  
  
-   可以通过 Web 部件的用户设置创建的属性。 此属性指定员工数据文件的位置。  
  
-   通过将控件添加到 Web 部件中呈现 Web 部件中的内容控件集合。  
  
-   创建一个新的菜单项，称为*谓词，*呈现的 Web 部件的谓词菜单中显示。 谓词使用户能够修改在 Web 部件中显示的数据。  
  
-   在 SharePoint 中测试 Web 部件。  
  
    > [!NOTE]  
    >  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]或某一版本的 Visual Studio 应用程序生命周期管理 (ALM)。  
  
## <a name="creating-an-empty-sharepoint-project"></a>创建空 SharePoint 项目  
 首先，创建空 SharePoint 项目。 稍后，你将添加 Web 部件到项目通过使用**Web 部件**项模板。  
  
#### <a name="to-create-an-empty-sharepoint-project"></a>若要创建空 SharePoint 项目  
  
1.  启动[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用**以管理员身份运行**选项。  
  
2.  在菜单栏上，选择**文件**，**新建**，**项目**。  
  
3.  在**新项目**对话框框中，展开**SharePoint**你想要使用，然后选择的语言下节点**2010年**节点。  
  
4.  在**模板**窗格中，选择**SharePoint 2010 项目**，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。 此向导，可选择将用于调试项目和解决方案的信任级别的站点。  
  
5.  选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮以接受默认的本地 SharePoint 站点。  
  
## <a name="adding-a-web-part-to-the-project"></a>将 Web 部件添加到项目  
 添加**Web 部件**到项目的项。 **Web 部件**项将添加 Web 部件代码文件。 更高版本，你会将代码添加到 Web 部件的代码文件，以呈现的 Web 部件的内容。  
  
#### <a name="to-add-a-web-part-to-the-project"></a>若要将 Web 部件添加到项目  
  
1.  在菜单栏上，选择**项目**，**添加新项**。  
  
2.  在**添加新项**对话框中，在**已安装的模板**窗格中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在 SharePoint 模板列表中，选择**Web 部件**模板，然后选择**添加**按钮。  
  
     **Web 部件**中将出现项**解决方案资源管理器**。  
  
## <a name="rendering-content-in-the-web-part"></a>呈现在 Web 部件中的内容  
 你可以指定你想要通过将它们添加到 Web 部件类的控件集合显示在 Web 部件中的控件。  
  
#### <a name="to-render-content-in-the-web-part"></a>若要呈现在 Web 部件中的内容  
  
1.  在**解决方案资源管理器**，打开 WebPart1.vb （在 Visual Basic 中) 或 WebPart1.cs （在 C# 中)。  
  
     Web 部件的代码文件将在代码编辑器中打开。  
  
2.  将以下语句添加到 Web 部件的代码文件的顶部。  
  
     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]  
  
3.  向 `WebPart1` 类添加下面的代码。 此代码声明了以下字段：  
  
    -   数据网格显示 Web 部件中的员工。  
  
    -   用于筛选数据网格控件显示的文本。  
  
    -   显示错误，如果数据网格是无法显示数据标签。  
  
    -   包含员工数据文件的路径的字符串。  
  
     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]  
  
4.  向 `WebPart1` 类添加下面的代码。 此代码将添加名为的自定义属性`DataFilePath`到 Web 部件。 自定义属性是一个属性，可以在 SharePoint 中由用户设置。 此属性会获取和设置用于填充数据网格的 XML 数据文件的位置。  
  
     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]  
  
5.  将 `CreateChildControls` 方法替换为以下代码。 这段代码执行下列任务：  
  
    -   上一步中添加数据网格和你声明的标签。  
  
    -   将数据网格绑定到一个包含雇员数据的 XML 文件。  
  
     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]  
  
6.  将以下方法添加到 `WebPart1` 类。 这段代码执行下列任务：  
  
    -   创建所呈现的 Web 部件的 Web 部件谓词菜单中显示的谓词。  
  
    -   处理在用户选择谓词菜单中的谓词时所引发的事件。 此代码将筛选显示在数据网格中的员工列表。  
  
     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]  
  
## <a name="testing-the-web-part"></a>测试 Web 部件  
 运行项目时，会打开 SharePoint 站点。 Web 部件自动添加到在 SharePoint Web 部件库中。 可以将 Web 部件添加到任何 Web 部件页。  
  
#### <a name="to-test-the-web-part"></a>若要测试 Web 部件  
  
1.  将下面的 XML 粘贴到记事本文件。 此 XML 文件包含将显示在 Web 部件的示例数据。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
           <employee>  
               <name>David Hamilton</name>  
               <hireDate>2001-05-11</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Karina Leal</name>  
               <hireDate>1999-04-01</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Nancy Davolio</name>  
               <hireDate>1992-05-01</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Steven Buchanan</name>  
               <hireDate>1955-03-04</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Suyama Michael</name>  
               <hireDate>1963-07-02</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
        </employees>  
    ```  
  
2.  在记事本中，在菜单栏上，选择**文件**，**另存为**。  
  
3.  在**另存为**对话框中，在**另存为类型**列表中，选择**所有文件**。  
  
4.  在**文件名**框中，输入**data.xml**。  
  
5.  通过选择任意文件夹**浏览文件夹**按钮，，然后选择**保存**按钮。  
  
6.  在 Visual Studio 中，选择**F5**密钥。  
  
     打开 SharePoint 站点。  
  
7.  上**站点操作**菜单上，选择**更多选项**。  
  
8.  在**创建**页上，选择**Web 部件页**类型，然后选择**创建**按钮。  
  
9. 在**新建 Web 部件页**页上，将该页命名为**SampleWebPartPage.aspx**，然后选择**创建**按钮。  
  
     显示该 Web 部件页。  
  
10. 选择 Web 部件页上的任何区域。  
  
11. 在页面顶部，选择**插入**选项卡上，然后选择**Web 部件**按钮。  
  
12. 在**类别**窗格中，选择**自定义**文件夹中，选择**WebPart1** Web 部件，然后选择**添加**按钮。  
  
     Web 部件显示在此页。  
  
## <a name="testing-the-custom-property"></a>测试自定义属性  
 若要填充的数据网格中显示在 Web 部件中，指定包含有关每个雇员的数据的 XML 文件的路径。  
  
#### <a name="to-test-the-custom-property"></a>若要测试自定义属性  
  
1.  选择显示 Web 部件中，右侧的箭头，然后选择**编辑 Web 部件**从显示的菜单中。  
  
     包含 Web 部件的属性窗格中出现在页面的右侧。  
  
2.  在窗格中，展开**杂项**节点，输入前面创建的 XML 文件的路径，选择**应用**按钮，，然后选择**确定**按钮。  
  
     确认的员工列表显示在 Web 部件。  
  
## <a name="testing-the-web-part-verb"></a>测试 Web 部件谓词  
 显示和隐藏通过单击 Web 部件谓词菜单中显示的项不是经理的员工。  
  
#### <a name="to-test-the-web-part-verb"></a>若要测试的 Web 部件谓词  
  
1.  选择显示 Web 部件中，右侧的箭头，然后选择**仅显示经理**从显示的菜单中。  
  
     只有是经理的员工将显示在 Web 部件中。  
  
2.  同样，选择箭头，然后选择**显示所有员工**从显示的菜单中。  
  
     在 Web 部件中显示所有员工。  
  
## <a name="see-also"></a>另请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何： 创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何： 使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [演练：使用设计器为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  