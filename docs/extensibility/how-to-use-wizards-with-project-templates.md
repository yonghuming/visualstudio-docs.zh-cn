---
title: "如何： 使用向导来处理项目模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecbf4b95689d760a58e00a65671c13c4c0807b51
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-wizards-with-project-templates"></a>如何：使用向导来处理项目模板
Visual Studio 提供了 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口，可实现该接口来在用户从模板创建项目时运行自定义代码。  
  
 项目模板自定义可以用于显示项目中收集用户输入以自定义模板，将其他文件添加到模板或允许的任何其他操作的自定义 UI。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口方法称为在不同时间而在创建项目，从开始就立即用户单击**确定**上**新项目**对话框。 名为接口的每个方法来描述中调用的点。 例如，Visual Studio 会调用<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>立即当它启动创建项目时，使其用于编写自定义代码来收集用户输入的正确位置。  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>使用 VSIX 项目创建一个项目模板项目  
 你开始使用项目模板项目。，是 Visual Studio SDK 的一部分创建的自定义模板。 在此过程中，我们将使用 C# 项目模板项目，但还没有 Visual Basic 项目模板项目。 然后将 VSIX 项目添加到包含项目模板项目的解决方案。  
  
1.  创建 C# 项目模板项目 (在 Visual Studio 中，**文件 / 新建 / 项目 / Visual C# / 可扩展性 / C# 项目模板**)。 将其命名为**MyProjectTemplate**。  
  
    > [!NOTE]
    >  可能要求你安装 Visual Studio SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  添加新的 VSIX 项目 (**文件 / 新建 / 项目 / Visual C# / 扩展性 / VSIX 项目**) 项目模板项目与同一解决方案中 (中**解决方案资源管理器**，选择解决方案节点中，右键单击，并选择**添加 / 新建项目**)。 将其命名为**MyProjectWizard。**  
  
3.  将 VSIX 项目设置为启动项目。 在**解决方案资源管理器**，选择 VSIX 项目节点，右键单击，并选择**设为启动项目**。  
  
4.  将模板项目添加为 VSIX 项目的资产。 在**解决方案资源管理器**，在 VSIX 项目节点下找到**source.extension.vsixmanifest**文件。 双击它以在清单编辑器中打开它。  
  
5.  在清单编辑器中，选择**资产**窗口左侧的选项卡。  
  
6.  在**资产**选项卡上，选择**新建**。 在**添加新资产**窗口中的，为类型字段中，选择**Microsoft.VisualStudio.ProjectTemplate**。 在**源**字段中，选择**当前解决方案中的项目**。 在**项目**字段中，选择**MyProjectTemplate**。 然后单击“确定” 。  
  
7.  生成解决方案并启动调试。 将出现 Visual Studio 的第二个实例。 （这可能需要几分钟）。  
  
8.  在 Visual Studio 的第二个实例中，尝试使用你的新模板创建新项目。 (**文件 / 新建 / 项目 / Visual C# / MyProject 模板**)。 新项目应显示名为的类与**Class1**。 现在已创建自定义项目模板 ！ 立即停止调试。  
  
## <a name="creating-a-custom-template-wizard"></a>创建自定义模板向导  
 本主题演示如何创建自定义向导创建项目之前打开 Windows 窗体。 该窗体允许用户添加一个自定义参数值，在项目创建期间添加到源代码。  
  
1.  将 VSIX 项目设置为允许它创建一个程序集。  
  
2.  在**解决方案资源管理器**，选择 VSIX 项目节点。 以下解决方案资源管理器，你应看到**属性**窗口。 如果不这样做，则选择**视图 / 属性窗口**，或按**F4**。 在属性窗口中，选择以下字段以`true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  将为资产的程序集添加到 VSIX 项目中。 打开 source.extension.vsixmanifest 文件并选择**资产**选项卡。在**添加新资产**窗口中，为**类型**选择**Microsoft.VisualStudio.Assembly**，为**源**选择**A当前解决方案中的项目**，和**项目**选择**MyProjectWizard**。  
  
4.  添加到 VSIX 项目的以下引用。 (在**解决方案资源管理器**，在 VSIX 项目节点，请选择**引用**，右键单击，并选择**添加引用**。)在**添加引用**对话框，请在**Framework**选项卡上，查找**System.Windows 窗体**程序集，然后选择它。 现在选择**扩展**选项卡。 查找**EnvDTE**程序集，然后选择它。 此外可以找到**Microsoft.VisualStudio.TemplateWizardInterface**程序集，然后选择它。 单击“确定”。  
  
5.  将向导实现的类添加到 VSIX 项目。 (在解决方案资源管理器，右键单击 VSIX 项目节点，然后选择**添加**，然后**新项**，然后**类**。)将类**WizardImplementation**。  
  
6.  中的代码替换**WizardImplementationClass.cs**文件替换为以下代码：  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
        {  
            private UserInputForm inputForm;  
            private string customMessage;  
  
            // This method is called before opening any item that   
            // has the OpenInEditor attribute.  
            public void BeforeOpeningFile(ProjectItem projectItem)  
            {  
            }  
  
            public void ProjectFinishedGenerating(Project project)  
            {  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public void ProjectItemFinishedGenerating(ProjectItem   
                projectItem)  
            {  
            }  
  
            // This method is called after the project is created.  
            public void RunFinished()  
            {  
            }  
  
            public void RunStarted(object automationObject,  
                Dictionary<string, string> replacementsDictionary,  
                WizardRunKind runKind, object[] customParams)  
            {  
                try  
                {  
                    // Display a form to the user. The form collects   
                    // input for the custom message.  
                    inputForm = new UserInputForm();  
                    inputForm.ShowDialog();  
  
                    customMessage = UserInputForm.CustomMessage;  
  
                    // Add custom parameters.  
                    replacementsDictionary.Add("$custommessage$",   
                        customMessage);  
                }  
                catch (Exception ex)  
                {  
                    MessageBox.Show(ex.ToString());  
                }  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public bool ShouldAddProjectItem(string filePath)  
            {  
                return true;  
            }          
        }  
    }  
    ```  
  
     **UserInputForm**引用在此代码将在稍后实现。  
  
     `WizardImplementation`类包含的每个成员的方法实现<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>。 在此示例中，仅<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法执行任务。 所有其他方法不执行任何操作或返回`true`。  
  
     <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法接受四个参数：  
  
    -   <xref:System.Object>参数可强制转换为根<xref:EnvDTE._DTE>对象，以使你可以自定义项目。  
  
    -   A<xref:System.Collections.Generic.Dictionary%602>参数，其中包含模板中的所有预定义参数的集合。 有关模板参数的详细信息，请参阅[模板参数](../ide/template-parameters.md)。  
  
    -   A<xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>参数，其中包含有关使用哪种类型的模板的信息。  
  
    -   <xref:System.Object>数组，其中包含一组参数传递到向导的 Visual Studio。  
  
     此示例将参数值添加到窗体用户输入从<xref:System.Collections.Generic.Dictionary%602>参数。 每个实例`$custommessage$`项目中的参数将替换为用户输入的文本。 必须将以下程序集添加到你的项目：**系统**和**System.Drawing**。
  
7.  现在创建**UserInputForm**。 在**WizardImplementation.cs**文件中，将以下代码添加在结束后**WizardImplementation**类。  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
            }  
        }  
    ```  
  
     用户输入窗体提供了一种简单形式输入自定义参数。 包含一个名为文本框的窗体`textBox1`和名为的按钮`button1`。 单击该按钮，从文本框中的文本存储在`customMessage`参数。  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>连接到自定义模板的向导  
 为了使你的自定义项目模板，以使用自定义向导，您需要向导程序集签名并将某些行添加到你的自定义项目模板，让它知道在何处可以找到向导实现，创建新项目时。  
  
1.  程序集签名。 在**解决方案资源管理器**，选择 VSIX 项目，右键单击，并选择**项目属性**。  
  
2.  在**项目属性**窗口中，选择**签名**中的选项卡。**签名**选项卡上，选中**对程序集签名**。 在**选择强名称密钥文件**字段中，选择**\<新建 >**。 在**创建强名称密钥**窗口，请在**密钥文件名称**字段中，键入**key.snk**。 取消选中**保护我使用密码的密钥文件**字段。  
  
3.  在**解决方案资源管理器**、 选择 VSIX 项目，然后查找**属性**窗口。  
  
4.  设置**复制生成输出到输出目录**字段**true**。 这样，要重新生成解决方案，则会复制到输出目录的程序集。 它仍包含在.vsix 文件。 你需要查看若要找出其签名密钥的程序集。  
  
5.  重新生成解决方案。  
  
6.  你现在可以 MyProjectWizard 项目目录中找到的 key.snk 文件 (**\<磁盘位置 > \MyProjectTemplate\MyProjectWizard\key.snk**)。 将复制的 key.snk 文件。  
  
7.  转到输出目录，查找程序集 (**\<磁盘位置 > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**)。 粘贴此处的 key.snk 文件。 （这不是绝对必需，但它将使以下步骤更容易。）  
  
8.  打开一个命令窗口，并将更改为在其中创建程序集的目录。  
  
9. 查找**sn.exe**签名工具。 例如，在 Windows 10 64 位操作系统系统中，典型的路径将为以下：  
  
     **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools**  
  
     如果找不到该工具，请尝试在运行**其中 /R。 sn.exe**命令窗口中。 记下的路径。  
  
10. 从命名为 key.snk 文件提取公钥。 在命令窗口中，键入  
  
     **\<sn.exe 的位置 > \sn.exe-p key.snk outfile.key。**  
  
     不要忘记括起来的路径用引号引起来的 sn.exe，如果目录名称中有空格 ！  
  
11. 从 outfile 中获取的公钥令牌：  
  
     **\<sn.exe 的位置 > \sn.exe-t outfile.key。**  
  
     同样，不要忘记引号引起来。 你应看到如下输出中的行  
  
     **公钥标记是<token>**  
  
     记下此值。  
  
12. 将对自定义向导的引用添加到项目模板的.vstemplate 文件。 在解决方案资源管理器，找到名为 MyProjectTemplate.vstemplate，该文件并打开它。 结束后\<TemplateContent > 部分中，添加以下节：  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     其中**MyProjectWizard**是程序集的名称和**令牌**是你在上一步中复制的令牌。  
  
13. 在项目中保存的所有文件并重新生成。  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>将自定义的参数添加到模板  
 在此示例中，用作模板的项目显示的自定义向导的用户输入窗体中指定的消息。  
  
1.  在解决方案资源管理器，转到**MyProjectTemplate**项目，然后打开**Class1.cs**。  
  
2.  在`Main`应用程序，方法添加以下代码行。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     参数`$custommessage$`将替换为从模板创建一个项目时在用户输入窗体中输入的文本。  
  
 下面是完整的代码文件之前导出到模板。  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>使用自定义向导  
 现在可以从你的模板创建项目，并使用自定义向导。  
  
1.  重新生成解决方案并启动调试。 将显示 Visual Studio 的第二个实例。  
  
2.  创建新的 MyProjectTemplate 项目。 (**文件 / 新建 / 项目 / Visual C# / MyProjectTemplate**)  
  
3.  在**新项目**对话框中，找到你的模板，键入一个名称，并单击**确定**。  
  
     将打开向导的用户输入的表单。  
  
4.  键入自定义参数的值，然后单击按钮。  
  
     向导用户输入窗体关闭，并且从模板创建一个项目。  
  
5.  在**解决方案资源管理器**，右键单击源代码文件，然后单击**查看代码**。  
  
     请注意，`$custommessage$`已替换为在向导用户输入窗体中输入的文本。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [自定义模板](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 元素（Visual Studio 模板）](../extensibility/wizardextension-element-visual-studio-templates.md)
