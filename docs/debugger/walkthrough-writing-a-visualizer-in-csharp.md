---
title: "演练： 用 C# 编写可视化工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd63f183d42111cfb8381b5fee86debbca6cd04e
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>演练：用 C# 编写可视化工具 #
本演练演示如何使用 C# 编写简单的可视化工具。 将在本演练中创建的可视化工具显示使用的 Windows 窗体消息框字符串内容。 此简单字符串可视化工具不是本身而言，尤其有用，但它演示创建其他数据类型的更多有用可视化工具时必须遵循的基本步骤。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你的当前设置或版本。 若要更改设置，请转到**工具**菜单，然后选择**导入和导出设置**。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 可视化工具代码必须放置在一个 DLL，将由调试器读取。 因此，第一步是创建 DLL 的类库项目。  

## <a name="create-a-visualizer-manually"></a>手动创建可视化工具

请按照下面创建可视化工具的任务。
  
#### <a name="to-create-a-class-library-project"></a>创建类库项目  
  
1.  上**文件**菜单上，选择**新建 > 项目**。  
  
2.  在**新项目**对话框中，在**Visual C#**，选择**.NET 标准**。  
  
3.  在中间窗格中，选择**类库**。  
  
4.  在**名称**框中，键入类库，例如 MyFirstVisualizer 正确的名称。  
  
5.  单击“确定”。  
  
 创建类库后，你必须添加对 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的引用，以便才能在此处使用定义的类。 添加引用之前，但是，你必须重命名某些类以使它们具有有意义的名称。  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要将 Class1.cs 重命名并添加 Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  在**解决方案资源管理器**，右键单击 Class1.cs，然后选择**重命名**快捷菜单上。  
  
2.  将名称从 Class1.cs 更改为有意义的名称，如 debuggerside.cs。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自动更改的类声明，在 debuggerside.cs 中，以便与新文件名匹配。  
  
3.  在**解决方案资源管理器**，右键单击**引用**选择**添加引用**快捷菜单上。  
  
4.  在**添加引用**对话框中，在**.NET**选项卡上，选择 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
5.  单击“确定”。  
  
6.  在 DebuggerSide.cs 中，将下面的语句添加到 `using` 语句中：  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 现在你已准备好创建调试器端代码。 这是运行在调试器中以显示要可视化的信息的代码。 首先，你必须更改的声明`DebuggerSide`对象，以便从基类继承`DialogDebuggerVisualizer`。  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>从 DialogDebuggerVisualizer 继承  
  
1.  在 debuggerside.cs 中，转到下面的代码行：  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  更改到的代码：  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`具有一个抽象方法 (`Show`)，必须重写。  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>重写 DialogDebuggerVisualizer.Show 方法  
  
-   在`public class DebuggerSide`，添加以下**方法：**  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show`方法包含实际创建可视化工具对话框或其他用户界面，并显示已从调试器传递到可视化工具的信息的代码。 您必须添加创建该对话框并显示该信息的代码。 在此演练中，你将执行此操作使用的 Windows 窗体消息框。 首先，必须添加的引用和`using`System.Windows.Forms 的语句。  
  
#### <a name="to-add-systemwindowsforms"></a>添加 System.Windows.Forms  
  
1.  在**解决方案资源管理器**，右键单击**引用**选择**添加引用**快捷菜单上。  
  
2.  在**添加引用**对话框中，在**.NET**选项卡上，选择 System.Windows.Forms.DLL。  
  
3.  单击“确定”。  
  
4.  在 DebuggerSide.cs 中，将下面的语句添加到 `using` 语句中：  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 现在，你将添加一些代码以创建和显示可视化工具用户界面。 由于这是你的第一个可视化工具，我们将简化用户界面，并使用一个消息框。  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>若要在对话框中显示可视化工具输出  
  
1.  在 `Show` 方法中，添加以下代码行：  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     此代码示例中不包含错误处理。 应包含实际的可视化工具或任何其他类型的应用程序中的错误处理。  
  
2.  上**生成**菜单上，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。  
  
 这是调试器端代码的结尾。 但是; 还有一步该属性用于通知调试对象端哪些类集合构成可视化工具。  
  
#### <a name="to-add-the-debuggee-side-code"></a>若要添加调试对象端代码  
  
1.  后向 debuggerside.cs 中，添加以下特性代码`using`语句之前`namespace MyFirstVisualizer`:  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  上**生成**菜单上，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。  
  
 这时，第一个可视化工具就完成了。 如果您已正确地按照每一步操作，您可以生成该可视化工具，并将其安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。 但在将可视化工具安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中之前，应对其进行测试以确保它能够正常运行。 您现在将创建一个测试套以在没有将可视化工具安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的情况下运行它。  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>添加测试方法以显示可视化工具  
  
1.  将下面的方法添加到类 `public DebuggerSide`：  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  上**生成**菜单上，选择**生成 MyFirstVisualizer**。 该项目应能成功生成。 在继续前更正所有生成错误。  
  
 然后，您必须创建一个可执行项目以调用可视化工具 DLL。 为简单起见，我们将使用一个控制台应用程序项目。  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>将控制台应用程序项目添加到解决方案中  
  
1.  上**文件**菜单上，选择**添加**，然后单击**新项目**。  
  
2.  在**添加新项目**对话框中，在**模板**框中，选择**控制台应用程序**。  
  
3.  在**名称**框中，键入有意义的名称，控制台应用程序，如`MyTestConsole`。  
  
4.  单击“确定”。  
  
 现在，必须添加必要的引用，以便 MyTestConsole 能够调用 MyFirstVisualizer。  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>添加对 MyTestConsole 的必需引用  
  
1.  在**解决方案资源管理器**，右键单击**MyTestConsole**选择**添加引用**快捷菜单上。  
  
2.  在**添加引用**对话框中， **.NET**选项卡上，选择 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
3.  单击“确定”。  
  
4.  右键单击**MyTestConsole**选择**添加引用**试。  
  
5.  在**添加引用**对话框中，单击**项目**选项卡，然后单击 MyFirstVisualizer。  
  
6.  单击“确定”。  
  
 现在，你将添加代码以完成测试套。  
  
#### <a name="to-add-code-to-mytestconsole"></a>将代码添加到 MyTestConsole  
  
1.  在**解决方案资源管理器**，右键单击 Program.cs，然后选择**重命名**快捷菜单上。  
  
2.  编辑从 Program.cs 到有意义的名称，如 TestConsole.cs 的名称。  
  
     **请注意** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] TestConsole.cs 以便与新文件名匹配中的类声明也会自动更改。  
  
3.  在 TestConsole.cs，添加以下代码到`using`语句：  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  在方法 `Main` 中，添加以下代码：  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 现在，你已准备好测试你的第一个可视化工具。  
  
#### <a name="to-test-the-visualizer"></a>测试可视化工具  
  
1.  在**解决方案资源管理器**，右键单击**MyTestConsole**选择**设为启动项目**快捷菜单上。  
  
2.  上**调试**菜单上，选择**启动**。  
  
     在控制台应用程序启动和可视化工具随即出现并显示字符串"Hello，World"。  
  
 祝贺您！ 您刚刚生成了第一个可视化工具并进行了测试。  
  
 如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用可视化工具，而不是只从测试工具中调用它，则需要安装它。 有关详细信息，请参阅[如何： 安装可视化工具](../debugger/how-to-install-a-visualizer.md)。  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>创建可视化工具使用可视化工具项模板  
 到目前为止，本演练说明了如何手动创建可视化工具。 作为练习执行此操作。 既然你知道简单的可视化工具的工作原理，没有更简单的方法创建一个： 使用可视化工具项模板。  
  
 首先，你必须创建一个新的类库项目。  
  
#### <a name="to-create-a-new-class-library"></a>若要创建新的类库  
  
1.  上**文件**菜单上，选择**新建 > 项目**。  
  
2.  在**新项目**对话框中，在**Visual C#**，选择**.NET 标准**。  
  
3.  在中间窗格中，选择**类库**。   
  
4.  在**名称**框中，键入类库，如 MySecondVisualizer 正确的名称。  
  
5.  单击“确定”。  
  
 现在，你可以向其添加可视化工具项：  
  
#### <a name="to-add-a-visualizer-item"></a>若要添加的可视化工具项  
  
1.  在**解决方案资源管理器**，右键单击 MySecondVisualizer。  
  
2.  在快捷菜单上，选择**添加**，然后单击**新项**。  
  
3.  在**添加新项**对话框中，在**Visual C# 项**，选择**调试器可视化工具**。  
  
4.  在**名称**框中，键入适当的名称，如 SecondVisualizer.cs。  
  
5.  单击 **“添加”**。  
  
 这是向其所有没有。 看一下 SecondVisualizer.cs 的文件，并查看该模板添加为你的代码。 请继续并该代码。 既然你知道基础知识，你可以在你创建更复杂和有用可视化工具你自己。  
  
## <a name="see-also"></a>另请参阅  
 [可视化工具体系结构](../debugger/visualizer-architecture.md)   
 [如何： 安装可视化工具](../debugger/how-to-install-a-visualizer.md)   
 [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)
