---
title: "演练：用 C# 编写可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "可视化工具, 编写"
  - "演练 [Visual Studio], 可视化工具"
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 演练：用 C# 编写可视化工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何使用 C\# 编写简单的可视化工具。  本演练中创建的可视化工具使用 Windows 窗体消息框显示字符串的内容。  这个简单的字符串可视化工具本身并不是十分有用，但它演示了为其他数据类型创建更有用的可视化工具所必须遵循的基本步骤。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您的当前设置或版本。  若要更改设置，请转到**“工具”**菜单，然后选择**“导入和导出设置”**。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 可视化工具代码必须放置在 DLL 中，调试器将读取此 DLL。  因此，第一步是为 DLL 创建类库项目。  
  
#### 创建类库项目  
  
1.  在**“文件”**菜单上选择**“新建”**，然后单击**“新建项目”**。  
  
2.  在**“新建项目”**对话框中**“项目类型”**下，选择**“Visual C\#”**。  
  
3.  在**“模板”**框中选择**“类库”**。  
  
4.  在**“名称”**框中，为类库键入一个适当的名称，例如 MyFirstVisualizer。  
  
5.  单击“确定”。  
  
 创建了类库后，必须添加对 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的引用，以便可以使用其中定义的类。  但在添加引用前，必须对某些类重命名，以使其名称有意义。  
  
#### 重命名 Class1.cs 并添加 Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  在**“解决方案资源管理器”**中右击 Class1.cs，然后从快捷菜单中选择**“重命名”**。  
  
2.  将名称从 Class1.cs 更改为有意义的名称，例如 DebuggerSide.cs。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会自动更改 DebuggerSide.cs 中的类声明，以与新文件名匹配。  
  
3.  在**“解决方案资源管理器”**中右击**“引用”**，然后从快捷菜单中选择**“添加引用”**。  
  
4.  在**“添加引用”**对话框的**“.NET”**选项卡上，选择“Microsoft.VisualStudio.DebuggerVisualizers.DLL”。  
  
5.  单击“确定”。  
  
6.  在 DebuggerSide.cs 中，向 `using` 语句添加以下语句：  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 现在已经准备好创建调试器端代码了。  这是运行在调试器中以显示要可视化的信息的代码。  首先，必须更改 `DebuggerSide` 对象的声明，以便从基类 `DialogDebuggerVisualizer` 继承。  
  
#### 从 DialogDebuggerVisualizer 继承  
  
1.  在 DebuggerSide.cs 中，转到以下代码行：  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  将代码更改为：  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` 有一个抽象方法 \(`Show`\) 是必须重写的。  
  
#### 重写 DialogDebuggerVisualizer.Show 方法  
  
-   在 `public class DebuggerSide` 中添加下面的方法：  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show` 方法包含实际创建可视化工具对话框或其他用户界面，并显示从调试器传递到可视化工具的信息的代码。  您必须添加创建该对话框并显示该信息的代码。  在本演练中，将使用 Windows 窗体消息框执行此操作。  首先，必须为 System.Windows.Forms 添加引用和 `using` 语句。  
  
#### 添加 System.Windows.Forms  
  
1.  在**“解决方案资源管理器”**中右击**“引用”**，然后从快捷菜单中选择**“添加引用”**。  
  
2.  在**“添加引用”**对话框的**“.NET”**选项卡上，选择 System.Windows.Forms.DLL。  
  
3.  单击“确定”。  
  
4.  在 DebuggerSide.cs 中，向 `using` 语句添加以下语句：  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 现在，为可视化工具添加一些代码，以创建和显示用户界面。  由于这是第一个可视化工具，因此，我们保持用户界面简单，并使用消息框。  
  
#### 在对话框中显示可视化工具输出  
  
1.  在 `Show` 方法中，添加以下代码行：  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     此代码示例中不包含错误处理。  但在实际的可视化工具或任何其他类型的应用程序中，应当包含错误处理。  
  
2.  在**“生成”**菜单中选择**“生成 MyFirstVisualizer”**。  该项目应能成功生成。  在继续前更正所有生成错误。  
  
 这是调试器端代码的结尾部分。  但是还有一步操作：添加用于通知调试对象端哪些类集合构成可视化工具的特性。  
  
#### 添加调试对象端代码  
  
1.  将以下特性代码添加到 DebuggerSide.cs，放置在 `using` 语句之后，`namespace MyFirstVisualizer` 之前：  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  在**“生成”**菜单中选择**“生成 MyFirstVisualizer”**。  该项目应能成功生成。  在继续前更正所有生成错误。  
  
 这时，第一个可视化工具就完成了。  如果您已正确地按照每一步操作，您可以生成该可视化工具，并将其安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  但在将可视化工具安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中之前，应对其进行测试以确保它能够正常运行。  您现在将创建一个测试套以在没有将可视化工具安装到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的情况下运行它。  
  
#### 添加测试方法以显示可视化工具  
  
1.  将下面的方法添加到类 `public DebuggerSide`：  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  在**“生成”**菜单中选择**“生成 MyFirstVisualizer”**。  该项目应能成功生成。  在继续前更正所有生成错误。  
  
 然后，您必须创建一个可执行项目以调用可视化工具 DLL。  为了简单起见，我们将使用控制台应用程序项目。  
  
#### 将控制台应用程序项目添加到解决方案中  
  
1.  在**“文件”**菜单上选择**“添加”**，然后单击**“新建项目”**。  
  
2.  在**“添加新项目”**对话框的**“模板”**框中，选择**“控制台应用程序”**。  
  
3.  在**“名称”**框中，为控制台应用程序键入一个有意义的名称，例如 `MyTestConsole`。  
  
4.  单击“确定”。  
  
 现在，必须添加必要的引用，以便 MyTestConsole 能够调用 MyFirstVisualizer。  
  
#### 添加对 MyTestConsole 的必需引用  
  
1.  在**“解决方案资源管理器”**中右击**“MyTestConsole”**，然后从快捷菜单中选择**“添加引用”**。  
  
2.  在**“添加引用”**对话框的**“.NET”**选项卡中，选择 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
3.  单击“确定”。  
  
4.  右击**“MyTestConsole”**，然后再次选择**“添加引用”**。  
  
5.  在**“添加引用”**对话框中单击**“项目”**选项卡，然后再单击“MyFirstVisualizer”。  
  
6.  单击“确定”。  
  
 现在，您将添加代码以完成测试套。  
  
#### 将代码添加到 MyTestConsole  
  
1.  在**“解决方案资源管理器”**中右击 Program.cs，然后从快捷菜单中选择**“重命名”**。  
  
2.  编辑名称，从 Program.cs 改为更有意义的名称，例如 TestConsole.cs。  
  
     **Note** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会自动更改 TestConsole.cs 中的类声明，以与新文件名匹配。  
  
3.  在 TestConsole.cs 中，向 `using` 语句添加以下代码：  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  在方法 `Main` 中，添加以下代码：  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 现在，即可测试第一个可视化工具。  
  
#### 测试可视化工具  
  
1.  在**“解决方案资源管理器”**中右击**“MyTestConsole”**，然后从快捷菜单中选择**“设为启动项目”**。  
  
2.  在**“调试”**菜单上选择**“启动”**。  
  
     控制台应用程序将会启动，可视化工具将出现并显示字符串“Hello, World”。  
  
 祝贺您！  您刚刚生成了第一个可视化工具并进行了测试。  
  
 如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用可视化工具，而不是只从测试工具中调用它，则需要安装它。  有关详细信息，请参阅[如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)。  
  
## 使用可视化工具项模板  
 到目前为止，此演练已演示了如何手动创建可视化工具。  这已作为练习完成了。  现在您知道简单的可视化工具是如何工作的，创建可视化工具还有一个更简单的方法：使用可视化工具项模板。  
  
 首先，必须创建一个新的类库项目。  
  
#### 创建新的类库  
  
1.  在**“文件”**菜单上选择**“添加”**，然后单击**“新建项目”**。  
  
2.  在**“添加新项目”**对话框的**“项目类型”**下，选择**“Visual C\#”**。  
  
3.  在**“模板”**框中选择**“类库”**。  
  
4.  在**“名称”**框中，为类库键入适当的名称，例如 MySecondVisualizer。  
  
5.  单击“确定”。  
  
 现在，即可向它添加可视化工具项：  
  
#### 添加可视化工具项  
  
1.  在**“解决方案资源管理器”**中右击 MySecondVisualizer。  
  
2.  从快捷菜单中选择**“添加”**，然后单击**“新建项”**。  
  
3.  在**“添加新项”**对话框的**“模板”**下的**“Visual Studio 已安装的模板”**中，选择**“调试器可视化工具”**。  
  
4.  在**“名称”**对话框中键入适当的名称，例如 SecondVisualizer.cs。  
  
5.  单击**“添加”**。  
  
 至此全部操作都已完成。  请浏览文件 SecondVisualizer.cs，并查看该模板为您添加的代码。  继续对代码进行试验。  现在，您了解了基础知识，即可创建您自己的更为复杂有用的可视化工具了。  
  
## 请参阅  
 [可视化工具体系结构](../debugger/visualizer-architecture.md)   
 [如何：安装可视化工具](../debugger/how-to-install-a-visualizer.md)   
 [可视化工具](../debugger/create-custom-visualizers-of-data.md)