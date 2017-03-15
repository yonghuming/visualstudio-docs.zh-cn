---
title: "如何：使用向导来处理项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard 接口"
  - "项目模板 [Visual Studio], 向导"
  - "模板 [Visual Studio], 向导"
  - "Visual Studio 模板, 向导"
  - "向导 [Visual Studio], 项目模板"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：使用向导来处理项目模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio提供了 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 该接口后，您可以在用户根据模板创建项目时运行自定义代码。  
  
 项目模板的自定义可用于：  
  
-   显示收集用户输入以参数化模板的自定义 UI。  
  
-   添加要在模板中使用的参数值。  
  
-   向模板添加其他文件。  
  
-   执行项目的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动化对象模型允许的几乎任何操作。  
  
 在创建项目过程中的各个时间（从用户单击**“新建项目”**对话框上的**“确定”**开始）都会调用 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口方法。  接口的每个方法都被命名以描述调用该方法的时刻。  例如，当 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 开始创建项目时，它立即调用 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>，这使其成为编写自定义代码以收集用户输入的一个良好位置。  
  
 为自定义向导编写的大多数代码将使用 <xref:EnvDTE.DTE> 对象（它是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自动化对象模型中的主对象）来自定义项目。  有关自动化对象模型的更多信息，请参见[扩展 Visual Studio 环境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)和[自动化与扩展性参考](../Topic/Automation%20and%20Extensibility%20Reference.md)。  
  
## 创建自定义模板向导  
 本主题显示如何创建一个自定义向导，该向导在创建项目之前打开一个 Windows 窗体。  此窗体允许用户添加自定义参数值，此值随后在创建项目的过程中被添加到源代码中。  主要步骤如下所示，其中每一步都有详细解释。  
  
#### 创建自定义模板向导  
  
1.  创建实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口的程序集。  
  
2.  将此程序集安装到全局程序集缓存中。  
  
3.  创建一个项目并使用**“导出模板”**向导根据该项目创建模板。  
  
4.  通过在 .vstemplate 文件中添加 `WizardExtension` 元素来修改模板，以将此模板链接到实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的程序集。  
  
5.  使用自定义向导创建新项目。  
  
## 实现 IWizard  
 此过程的第一步是创建实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的程序集。  此程序集使用 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法显示一个 Windows 窗体，该窗体允许用户添加一个自定义参数值，随后将在创建项目的过程中使用此值。  
  
> [!NOTE]
>  本示例使用 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>，但您也可以使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]。  
  
#### 实现 IWizard  
  
1.  创建一个新类库项目。  
  
2.  创建实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口的类。  请参见下面的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 示例的代码，该示例完全实现了 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口。  
  
 本示例包含两个代码文件：`IWizardImplementation`，它是一个实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口的类；以及 `UserInputForm`，它是用于获得用户输入的 Windows 窗体。  
  
### IWizardImplementation 类  
 `IWizardImplementation` 类包含 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的每个成员的方法实现。  在本示例中，只有 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法执行任务。  所有其他方法要么不执行任何任务，要么返回 `true`。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法接受四个参数：  
  
-   <xref:System.Object> 参数，可强制转换为根 <xref:EnvDTE._DTE> 对象，以使您能够自定义项目。  
  
-   <xref:System.Collections.Generic.Dictionary%602> 参数，它包含模板中所有预定义参数的集合。  有关模板参数的更多信息，请参见 [模板参数](../ide/template-parameters.md)。  
  
-   <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> 参数，它包含有关所使用的模板种类的信息。  
  
-   <xref:System.Object> 数组，它包含通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 传递给向导的一组参数。  
  
 本示例将一个来自用户输入窗体的参数值添加到 <xref:System.Collections.Generic.Dictionary%602> 参数中。  项目中 `$custommessage$` 参数的每个实例都将替换为用户输入的文本。  您必须将以下组件添加到您的项目：  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  本示例中 UserInputForm 在下一节中进行定义。  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
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
  
                customMessage = inputForm.get_CustomMessage();  
  
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
  
### 用户输入窗体  
 用户输入窗体提供一个用于输入自定义参数的简单窗体。  该窗体包含一个名为 `textBox1` 的文本框和一个名为 `button1` 的按钮。  单击此按钮时，文本框中的文本将存储在 `customMessage` 参数中。  
  
##### 向解决方案添加 Windows 窗体  
  
1.  将以下代码添加到向导实现的文件中。  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## 将程序集安装到全局程序集缓存中  
 必须用强名称对实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的程序集进行签名，并将该程序集安装到全局程序集缓存中。  
  
#### 将程序集安装到全局程序集缓存中  
  
1.  用强名称对程序集进行签名。  有关更多信息，请参见[如何：使用强名称为程序集签名](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)或[How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/f468a7d3-234c-4353-924d-8e0ae5896564)。  
  
2.  将强名称程序集安装到全局程序集缓存中。  有关详细信息，请参阅[如何：将程序集安装到全局程序集缓存](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md)。  
  
## 创建要用作模板的项目  
 在本示例中，用作模板的项目是一个控制台应用程序，它显示在自定义向导的用户输入窗体中指定的消息。  
  
#### 创建示例项目  
  
1.  创建一个新的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 控制台应用程序。  
  
2.  在应用程序的 `Main` 方法中，添加以下代码行。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     当根据模板创建项目时，参数 `$custommessage$` 将替换为在用户输入窗体中输入的文本。  
  
3.  在**“文件”**菜单上单击**“导出模板”**。  
  
4.  在**“导出模板”**向导中，单击**“项目模板”**，选择正确的项目，然后单击**“下一步”**。  
  
5.  在**“导出模板”**向导中，输入关于该模板的描述性信息，选择**“自动将模板导入到 Visual Studio 中”**复选框，然后单击**“完成”**。  
  
     现在，模板显示在**“新建项目”**对话框中，但没有使用自定义向导。  
  
 下面的示例显示导出到模板之前的完整代码文件。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## 修改模板  
 现在，模板已被创建并显示在**“新建项目”**对话框中，必须对其进行修改，以便它使用在前面步骤中创建的程序集。  
  
#### 向模板添加自定义向导  
  
1.  找到包含该模板的 .zip 文件。  
  
    1.  在**“工具”**菜单上，单击**“选项”**。  
  
    2.  单击**“项目和解决方案”**。  
  
    3.  读取**“Visual Studio 用户项目模板位置”**文本框。  
  
     默认情况下，此位置为 My Documents\\Visual Studio *Version*\\Templates\\ProjectTemplates。  
  
2.  解压缩该 .zip 文件。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开 .vstemplate 文件。  
  
4.  在 `TemplateContent` 元素后，添加具有自定义向导程序集的强名称的 [WizardExtension 元素（Visual Studio 模板）](../extensibility/wizardextension-element-visual-studio-templates.md) 元素。  有关查找程序集的强名称的更多信息，请参见[如何：查看全局程序集缓存的内容](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md)和[如何：引用具有强名称的程序集](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md)。  
  
     下面的示例显示一个 `WizardExtension` 元素。  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## 使用自定义向导  
 现在，您可以根据自己的模板创建项目并使用自定义向导。  
  
#### 使用自定义向导  
  
1.  在**“文件”**菜单上，单击**“新建项目”**。  
  
2.  在**“新建项目”**对话框中，定位您的模板，键入名称，然后单击**“确定”**。  
  
     向导用户输入窗体将打开。  
  
3.  为自定义参数键入一个值并单击按钮。  
  
     向导用户输入窗体将关闭，并且根据模板创建了一个项目。  
  
4.  在**“解决方案资源管理器”**中，右击源代码文件并单击**“查看代码”**。  
  
     请注意，`$custommessage$` 已替换为在向导用户输入窗体中输入的文本。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [自定义模板](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 元素（Visual Studio 模板）](../extensibility/wizardextension-element-visual-studio-templates.md)