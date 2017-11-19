---
title: "如何： 向实体类添加验证 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 7110fed065816c6d6843e9ed6f95d2da2d6f4851
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-add-validation-to-entity-classes"></a>如何： 向实体类添加验证
*验证*实体类是输入到数据对象的值符合在对象的架构中，以及应用程序建立的规则的约束的确认过程。 在将更新发送到基础数据库之前对数据进行验证是一种很好的做法，这样可以减少错误。 还可以减少应用程序和数据库之间的潜在往返行程次数。  
  
 [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供使用户能够扩展运行期间插入、 更新和删除操作的完整实体，并还期间和之后单独的列的设计器生成的代码的分部方法更改。  
  
> [!NOTE]
>  本主题提供了使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]将验证添加到实体类的基本步骤。 因为它可能难以执行这些通用步骤不参考特定实体类，具有已提供一个使用实际数据的演练。  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>添加对特定列值更改的验证  
 此过程演示当列中的值更改时如何验证数据。 由于验证在类定义（而不是用户界面）中执行，因此如果值导致验证失败将引发异常。 请为应用程序中试图更改列值的代码实现错误处理。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>在列值更改过程中验证数据  
  
1.  打开或创建一个新的 LINQ to SQL 类文件 (**.dbml**文件) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (双击**.dbml**文件中**解决方案资源管理器**。)  
  
2.  在 O/R 设计器中，右键单击你想要添加验证，然后单击的类**查看代码**。  
  
     将打开代码编辑器，其中显示所选实体类的分部类。  
  
3.  将光标放在该分部类中。  
  
4.  对于 Visual Basic 项目：  
  
    1.  展开**方法名称**列表。  
  
    2.  找到**OnCOLUMNNAMEChanging**的列，你想要添加到验证方法。  
  
    3.  `OnCOLUMNNAMEChanging`方法添加到该分部类。  
  
    4.  添加下列代码，以首先确认是否已输入了值，然后确保为该列输入的值可被你的应用程序接受。 `value` 参数包含建议的值，因此添加逻辑以确认它是否为有效值：  
  
        ```vb  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
    对于 C# 项目：  
  
    由于 C# 项目不会自动生成事件处理程序，你可以使用 IntelliSense 创建列更改分部方法。 键入 `partial` 和空格以访问可用分部方法的列表。 单击要为其添加验证的列的列更改方法。 下面的代码类似于您选择列更改分部方法时生成的代码：  
  
    ```csharp  
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
        {  
           throw new System.NotImplementedException();  
        }  
    ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>添加对实体类更新的验证  
 除了可以在更改过程中检查值之外，还可以在尝试更新完整实体类时验证数据。 在尝试进行更新操作的过程中进行的验证可以比较多个列中的值（如果业务规则要求这样做）。 下面的过程演示在尝试更新完整实体类时如何进行验证。  
  
> [!NOTE]
>  更新完整实体类的验证代码是在分部 <xref:System.Data.Linq.DataContext> 类（而不是在特定实体类的分部类）中执行的。  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>在实体类更新过程中验证数据  
  
1.  打开或创建一个新的 LINQ to SQL 类文件 (**.dbml**文件) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (双击**.dbml**文件中**解决方案资源管理器**。)  
  
2.  右击 O/R 设计器上的空白区域，单击**查看代码**。  
  
     将打开代码编辑器，其中显示 `DataContext` 的一个分部类。  
  
3.  将光标放在 `DataContext` 的分部类上。  
  
4.  对于 Visual Basic 项目：  
  
    1.  展开**方法名称**列表。  
  
    2.  单击**UpdateENTITYCLASSNAME**。  
  
    3.  `UpdateENTITYCLASSNAME`方法添加到该分部类。  
  
    4.  使用 `instance` 参数访问各个列值，如下面的代码所示：  
  
        ```vb  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
    对于 C# 项目：  
  
    由于 C# 项目不会自动生成事件处理程序，你可以使用 IntelliSense 创建分部`UpdateCLASSNAME`方法。 键入 `partial` 和空格以访问可用分部方法的列表。 单击要为其添加验证的类的更新方法。 下面的代码类似于你选择时生成的代码`UpdateCLASSNAME`分部方法：  
  
    ```csharp  
    partial void UpdateCLASSNAME(CLASSNAME instance)  
    {  
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
        {  
            string ErrorMessage = "Invalid data!";  
            throw new System.Exception(ErrorMessage);  
        }  
    }  
    ```  
  
## <a name="see-also"></a>请参阅
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[验证数据](../data-tools/validate-data-in-datasets.md)  
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)  