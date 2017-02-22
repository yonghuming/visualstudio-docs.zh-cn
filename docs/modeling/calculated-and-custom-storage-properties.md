---
title: "计算的和自定义存储属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言中，域属性进行编程"
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
caps.handback.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 计算的和自定义存储属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

域特定语言 \(DSL\) 中的所有域属性可以向关系图上用户语言资源管理器中显示的程序代码可以访问。 但是，属性中存储它们的值的方式不同。  
  
## 类型的域属性  
 在 DSL 定义中，您可以将 **种类** 域属性，如下面的表中列出︰  
  
|域的属性类型|描述|  
|------------|--------|  
|**标准** （默认值）|保存在一个域属性 *存储* 和序列化到文件。|  
|**计算**|一个只读的域属性，则不保存在存储中，但是计算从其他值。<br /><br /> 例如， `Person.Age` 可能会计算出从 `Person.BirthDate`。<br /><br /> 您必须提供执行计算的代码。 通常情况下，您可以计算从其他域属性的值。 但是，您还可以使用外部资源。|  
|**自定义存储**|域属性，直接在存储中，不会对其进行保存，但可以是 get 和 set。<br /><br /> 您必须提供用于获取和设置的值的方法。<br /><br /> 例如， `Person.FullAddress` 可存储在 `Person.StreetAddress`, ，`Person.City`, ，和 `Person.PostalCode`。<br /><br /> 此外可以访问外部资源，例如，若要获取和设置从数据库的值。<br /><br /> 您的代码不应在存储中设置值时 `Store.InUndoRedoOrRollback` 为 true。 请参阅 [事务和自定义 Setter](#setters)。|  
  
## 提供代码计算或自定义存储属性  
 如果对计算或自定义存储设置域属性的类型，您必须提供访问方法。 生成您的解决方案时，错误报告将告诉您的要求。  
  
#### 若要定义的计算值或自定义存储属性  
  
1.  在 DslDefinition.dsl 中，选择域属性关系图中或在 **DSL 资源管理器**。  
  
2.  在 **属性** 窗口中，设置 **种类** 字段拖至 **计算** 或 **自定义存储**。  
  
     请确保还设置其 **类型** 到所需。  
  
3.  单击 **转换所有模板** 的工具栏中的 **解决方案资源管理器**。  
  
4.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     您收到以下错误消息:"*YourClass* 不包含定义 get*YourProperty*。"  
  
5.  双击该错误消息。  
  
     将打开 Dsl\\GeneratedCode\\DomainClasses.cs 或 DomainRelationships.cs。 上方突出显示的方法调用中，注释将提示您提供一个实现进行 Get*YourProperty*（\)。  
  
    > [!NOTE]
    >  从 DslDefinition.dsl 生成此文件。 如果编辑此文件时，所做的更改将会丢失您单击下一次 **转换所有模板**。 相反，在单独的文件添加所需的方法。  
  
6.  创建或打开一个类文件在单独的文件夹，例如 CustomCode\\*YourDomainClass*。 cs。  
  
     请确保命名空间是生成的代码相同。  
  
7.  在类文件中，编写不同的域类的部分实现。 在类中，编写缺失的定义 `Get` 方法类似于下面的示例︰  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  如果您设置 **种类** 到 **自定义存储**, ，您还需要提供 `Set` 方法。 例如：  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     您的代码不应在存储中设置值时 `Store.InUndoRedoOrRollback` 为 true。 请参阅 [事务和自定义 Setter](#setters)。  
  
9. 生成和运行解决方案。  
  
10. 测试属性。 请确保您尝试 **撤消** 和 **重做**。  
  
##  <a name="setters"></a> 事务和自定义资源库  
 中的自定义存储属性的 Set 方法中，您无需打开一个事务，因为通常在活动事务内调用该方法。  
  
 但是，如果用户调用撤消或重做操作，或者如果正在回滚事务可能还调用 Set 方法。 当 <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> 为 true，Set 方法的行为，如下所示︰  
  
-   它不应在存储中，例如为其他域属性分配值进行更改。 撤消管理器将设置其值。  
  
-   但是，它应更新任何外部资源，如数据库或文件的内容或在存储外的对象。 这将确保使它们保持在 synchronism 存储区中的值。  
  
 例如：  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 有关事务的详细信息，请参阅 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## 请参阅  
 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [域属性的属性](../modeling/properties-of-domain-properties.md)   
 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)