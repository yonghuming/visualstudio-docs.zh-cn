---
title: "演练：对托管代码进行代码缺陷分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析, 演练"
  - "托管代码, 分析"
  - "代码分析工具, 演练"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：对托管代码进行代码缺陷分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本演练中，您可以通过使用代码分析工具分析托管的项目进行代码缺陷。  
  
 本演练将指导您完成使用代码分析来分析你的.NET 托管代码程序集，为了符合 Microsoft.NET Framework 设计准则的过程。  
  
 在本演练中，您︰  
  
-   分析和更正代码缺陷警告。  
  
## <a name="prerequisites"></a>先决条件  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]。  
  
## <a name="create-a-class-library"></a>创建一个类库  
  
#### <a name="to-create-a-class-library"></a>若要创建一个类库  
  
1.  在 **文件** 菜单 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], ，请单击 **新建** ，然后单击 **项目**。  
  
2.  在 **新项目** 对话框中，在 **项目类型**, ，请单击 **Visual C#**。  
  
3.  在下 **模板**, ，选择 **类库**。  
  
4.  在 **名称** 文本框中，键入 **CodeAnalysisManagedDemo** ，然后单击 **确定**。  
  
5.  创建项目后，打开 Class1.cs 文件。  
  
6.  用下面的代码替换 Class1.cs 的现有文本︰  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  将 Class1.cs 文件保存。  
  
## <a name="analyze-the-project"></a>分析项目  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析托管的项目进行代码缺陷分析  
  
1.  选择在 CodeAnalysisManagedDemo 项目 **解决方案资源管理器**。  
  
2.  在 **项目** 菜单上，单击 **属性**。  
  
     CodeAnalysisManagedDemo 属性页将显示。  
  
3.  单击 **Code_analysis**。  
  
4.  请确保  **生成时启用代码分析 (定义 CODE_ANALYSIS 常量**) 检查。  
  
5.  从 **运行此规则集** 下拉列表中，选择 **Microsoft 的所有规则**。  
  
6.  在 **文件** 菜单上，单击 **保存选定项**, ，，然后关闭 ManagedDemo 属性页。  
  
7.  在 **生成** 菜单上，单击 **生成 ManagedDemo**。  
  
     CodeAnalysisManagedDemo 项目生成警告报告在 **代码分析** 和 **输出** windows。  
  
     如果 **代码分析** 窗口未显示，在 **分析** 菜单上，选择 **Windows** 然后 **选择代码分析**。  
  
## <a name="correct-the-code-analysis-issues"></a>更正代码分析问题  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>若要更正代码分析规则冲突  
  
1.  在 **视图** 菜单上，单击 **错误列表**。  
  
     根据您选择的开发人员配置文件，您可能需要指向 **其他窗口** 上 **视图** 菜单，然后再单击 **错误列表**。  
  
2.  在 **解决方案资源管理器**, ，请单击 **显示所有文件**。  
  
3.  接下来，展开属性节点，然后打开 AssemblyInfo.cs 文件。  
  
4.  使用以下方法来更正警告︰  
  
-   [CA1014︰ 用 CLSCompliantAttribute 的程序集标记](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design︰ 用 CLSCompliantAttribute，应标记为 demo，其值应为，则返回 true。  
  
    -   将代码添加 `using``System;` 到 AssemblyInfo.cs 文件。  
  
         接下来，将代码添加 `[assembly: CLSCompliant(true)]` 到 AssemblyInfo.cs 文件的末尾。  
  
         重新生成项目。  
  
-   [CA1032︰ 实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 与此类添加下面的构造函数︰ 公用 demo(String)  
  
    -   添加该构造函数 `public demo (String s) : base(s) { }` 到类 `demo`。  
  
-   [CA1032︰ 实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 与此类添加下面的构造函数︰ 公用演示 （String，异常）  
  
    -   添加该构造函数 `public demo (String s, Exception e) : base(s, e) { }` 到类 `demo`。  
  
-   [CA1032︰ 实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 将下面的构造函数添加到此类︰ 受保护的演示 （SerializationInfo，StreamingContext）  
  
    -   将代码添加 `using System.Runtime.Serialization;` Class1.cs 文件的开头。  
  
         接下来，添加该构造函数 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         重新生成项目。  
  
-   [CA1032︰ 实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 与此类添加下面的构造函数︰ 公用 demo()  
  
    -   添加该构造函数 `public demo () : base() { }` 到类 `demo`**。**  
  
         重新生成项目。  
  
-   [CA1709︰ 标识符应采用正确的大小写](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 更正命名空间名称 testCode' 的大小写更改为 TestCode。  
  
    -   命名空间的大小写更改 `testCode` 到 `TestCode`。  
  
-   [CA1709︰ 标识符应采用正确的大小写](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 更正其更改为 Demo 的类型名称 demo 的大小写。  
  
    -   更改的成员名称 `Demo`。  
  
-   [CA1709︰ 标识符应采用正确的大小写](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 更正其更改为 Item 的成员名称 item 的大小写。  
  
    -   更改的成员名称 `Item`。  
  
-   [CA1710︰ 标识符应具有正确的后缀](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming︰ 重命名 testCode.demo 以 Exception 结尾。  
  
    -   将类和为其构造函数的名称更改 `DemoException`。  
  
-   [CA2210︰ 程序集应具有有效的强名称](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)︰ 使用强名称密钥进行签名 ManagedDemo。  
  
    -   在 **项目** 菜单上，单击 **ManagedDemo 属性**。  
  
         显示项目属性。  
  
         单击 **签名**。  
  
         选择 **为程序集签名** 复选框。  
  
         在 **选择强名称密钥文件** 列表中，选择 **\< 新建 … >**。  
  
          **创建强名称密钥** 对话框随即出现。  
  
         在 **密钥文件名称**, ，键入为 TestKey。  
  
         输入密码，然后单击 **确定**。  
  
         在 **文件** 菜单上，单击 **保存选定项**, ，然后关闭属性页。  
  
         重新生成项目。  
  
-   [CA2237︰ 以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage︰ 添加要键入演示是此类型实现 ISerializable 的 [Serializable] 属性。  
  
    -   添加 `[Serializable ()]` 到类属性 `demo`。  
  
         重新生成项目。  
  
 在完成更改后，Class1.cs 文件应如下所示：  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>排除代码分析警告  
  
#### <a name="to-exclude-code-defect-warnings"></a>若要排除代码缺陷警告  
  
1.  对于每一个剩余警告，请执行以下操作：  
  
    1.  在“代码分析”窗口中，选择警告。  
  
    2.  选择 **操作**, ，然后选择 **禁止显示消息**, ，然后选择 **在项目禁止显示文件**。  
  
     有关详细信息，请参阅 [如何︰ 通过使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  重新生成项目。  
  
     生成项目，并且没有任何警告或错误。