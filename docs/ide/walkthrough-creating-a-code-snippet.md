---
title: "演练：创建代码段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码段, 创建"
  - "代码段, 导入"
  - "代码段, 引用"
  - "代码段, 替换"
  - "代码段, 快捷方式"
  - "代码段, 模板"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 演练：创建代码段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只需几步操作即可创建代码片段。  您需要做就是创建 XML 文件，填充适当的元素并添加代码。  您还可以将引用和替换参数添加到代码中。  您可以通过在代码片段管理器（“工具\/代码片段管理器”）中使用导入按钮来将这段代码添加到您安装的 Visual Studio 中。  
  
> [!TIP]
>  有关如何更轻松地写入代码片段的信息，请搜索 CodePlex 网站获取相关社区工具，如[Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033)（代码片段编辑器。  
  
## 代码片段模板  
 下面是基本代码片段模板：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title></Title>  
        </Header>  
        <Snippet>  
            <Code Language="">  
                <![CDATA[]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
  
```  
  
### 创建代码片段  
  
1.  在 Visual Studio 中创建新的 XML 文件，然后添加如上所示的模板。  
  
2.  在“标题”元素中填充代码片段的标题，例如“Hello World VB”。  
  
3.  在“代码”元素“语言”特性中填充代码片段的语言。  对于此示例，使用“VB”。  
  
4.  添加 CDATA 段中的某些代码到代码元素内，例如：  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  将代码片段保存为 VBCodeSnippet.snippet。  
  
### 向 Visual Studio 添加代码片段  
  
1.  您可以使用代码片段管理器将自己的代码片段添加到安装的 Visual Studio 中。  打开代码片段管理器（“工具\/代码片段管理器”）。  
  
2.  单击“导入”按钮。  
  
3.  转到您在前面的过程中保存代码片段的位置，选择该位置，然后单击“打开”。  
  
4.  “导入代码片段”对话框打开，要求你从右窗格中选择要添加此代码片段的地方。  “我的代码片段”是选择之一。  选择它并单击“完成”，然后单击“确定”。  
  
5.  此代码片段复制到以下位置：  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  通过打开 Visual Basic 项目并打开代码文件测试你的代码片段。  在文件中，单击上下文菜单上的“插入代码片段”，然后单击“我的代码片段”。  你应看到名为**我的 Visual Basic 代码片段**的代码片段。  双击它。  
  
7.  你应看到代码中插入的`Console.WriteLine("Hello, World!")`。  
  
### 添加说明和快捷字段  
  
1.  如果在代码片段管理器中进行查看，说明字段可提供有关代码片段的详细信息。  快捷方式是用户可键入以插入自己的代码片段的标记。  编辑已添加的片段，方法是打开文件 `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`。  
  
2.  添加作者和说明元素到标头元素，然后进行填充。  
  
3.  标头元素看上去像下面这样：  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  打开代码片段管理器并选择您的代码片段。  在右窗格中，您应该看到“说明”和“作者”字段现在已经得到填充。  
  
5.  要添加快捷键，则一并添加快捷方式元素和作者及说明元素。  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  请再次保存代码片段文件。  
  
7.  要测试快捷方式，请打开 Visual Basic 项目并打开代码文件。  在文件中键入`您好`并按 TAB。  应插入代码片段。  
  
### 添加引用和导入  
  
1.  借助 Visual Basic 代码片段，您可以使用引用元素向项目添加引用，也可以使用导入元素添加导入声明。（其他语言的代码片段没有此功能。）例如，如果将代码示例中的 `Console.WriteLine` 更改为  `MessageBox.Show`，则您可能需要将 System.Windows.Forms.dll 程序集添加到该项目。  
  
2.  打开您的代码片段。  
  
3.  在代码片段元素下添加引用元素：  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  在代码片段元素下添加导入元素：  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  将 CDATA 部分更改为以下：  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  保存代码片段。  
  
7.  打开 Visual Basic 项目并添加代码片段。  
  
8.  你将在代码文件的顶部看到 Imports 语句：  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. 查看项目属性。  “引用”选项卡包括对 System.Windows.Forms.dll 的引用。  
  
### 添加替换  
  
1.  您可能希望代码片段中的部分由用户替换，例如，您添加了一个变量后，希望用户以当前项目中的变量将其替换。  您可以提供两种替换类型：文本和对象。  文本为某种类型的字符串\(字符串文本、变量名称或数值的字符串表示形式\)。  对象为某种类型的实例而非字符串。  在此过程中，您将声明一个文本替换和一个对象替换，并更改代码以引用这些替换。  
  
2.  打开您的代码片段。  
  
3.  此示例使用 SQL 连接字符串，因此，你需要更改导入和引用元素以添加适当的引用：  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  要声明 SQL 连接字符串的文本替换，请在代码片段元素下添加声明元素，并在其中添加带有 ID 子元素的文本元素以及替换的默认值：  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  要声明 SQL 连接的对象替换，请在声明元素内添加一个对象元素，并添加 ID 子元素、对象的类型，工具提示和默认值的子元素。  结果声明元素看上去像下面这样：  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  在代码部分，您可使用 $ 符号包围替换内容进行引用，例如 `$replacement$`：  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  保存代码片段。  
  
8.  打开 Visual Basic 项目并添加代码片段。  
  
9. 代码应如下所示，其中替换 `SQL 连接字符串`和 `dcConnection` 以淡橙色高亮显示。  按 TAB 键可在各项之间导航。  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## 请参阅  
 [代码段架构参考](../ide/code-snippets-schema-reference.md)