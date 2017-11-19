---
title: "计算和自定义存储属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 0be1527c82264ef388eb01d3a06702c1c4bb4f7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="calculated-and-custom-storage-properties"></a>计算的和自定义的存储属性
域特定语言 (DSL) 中的所有域属性可对用户在关系图上并在你语言资源管理器，显示，并可以由程序代码访问。 但是，其值将存储的方式不同属性。  
  
## <a name="kinds-of-domain-properties"></a>类型的域属性  
 在 DSL 定义中，您可以将**类型**的 domain 属性下, 表中所示：  
  
|域属性类型|描述|  
|--------------------------|-----------------|  
|**标准**（默认）|一个域属性，保存在*存储*和序列化为文件。|  
|**计算**|一个只读的域属性，则不保存在存储中，但是根据其他值来计算。<br /><br /> 例如，`Person.Age`无法从计算`Person.BirthDate`。<br /><br /> 你必须提供执行的计算的代码。 通常情况下，你将计算来自其他域属性的值。 但是，你还可以使用外部资源。|  
|**自定义存储**|一个域属性，直接在存储中，不会对其进行保存，但可以是 get 和 set。<br /><br /> 你必须提供用于获取和设置值的方法。<br /><br /> 例如，`Person.FullAddress`可存储在`Person.StreetAddress`， `Person.City`，和`Person.PostalCode`。<br /><br /> 你还可以访问外部资源，例如，若要获取和设置从数据库的值。<br /><br /> 你的代码不应在存储中设置值时`Store.InUndoRedoOrRollback`为 true。 请参阅[事务和自定义 Setter](#setters)。|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>算出的或自定义存储属性提供的代码  
 如果你设置域属性的类型为 Calculated 或自定义存储，你必须提供访问方法。 当你创建解决方案时，错误报告将告诉你的要求。  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>若要定义的计算或自定义存储属性  
  
1.  在 DslDefinition.dsl，选择域属性关系图中或在**DSL 资源管理器**。  
  
2.  在**属性**窗口中，设置**类型**字段**计算**或**自定义存储**。  
  
     请确保还设置其**类型**到所需。  
  
3.  单击**转换所有模板**工具栏中**解决方案资源管理器**。  
  
4.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     你收到以下错误消息:"*YourClass*不包含定义 get*YourProperty*。"  
  
5.  双击该错误消息。  
  
     Dsl\GeneratedCode\DomainClasses.cs 或 DomainRelationships.cs 将打开。 上面突出显示的方法调用中，注释将提示你提供一个实现 get*YourProperty*（)。  
  
    > [!NOTE]
    >  此文件是从 DslDefinition.dsl 生成的。 如果编辑此文件时，所做的更改将会丢失你所单击的下一步时间**转换所有模板**。 相反，请在单独的文件添加所需的方法。  
  
6.  在创建或打开类文件单独的文件夹，例如自定义代码\\*YourDomainClass*。 cs。  
  
     请确保命名空间是与生成的代码中的相同。  
  
7.  在类文件中，编写域类的一个部分实现。 在类中，编写的定义。 缺少`Get`方法类似于下面的示例：  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  如果你设置**类型**到**自定义存储**，你还需要提供`Set`方法。 例如:   
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     你的代码不应在存储中设置值时`Store.InUndoRedoOrRollback`为 true。 请参阅[事务和自定义 Setter](#setters)。  
  
9. 生成和运行解决方案。  
  
10. 测试属性。 请确保你尝试**撤消**和**重做**。  
  
##  <a name="setters"></a>事务和自定义的 Setter  
 中的自定义存储属性的 Set 方法中，你无需打开事务，因为通常在活动事务内调用该方法。  
  
 但是，如果用户调用撤消或重做，或者如果正在回滚事务可能也称为 Set 方法。 当<xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>为 true，Set 方法的行为，如下所示：  
  
-   它不应在存储中，例如将值分配给其他域属性进行更改。 撤消管理器将设置其值。  
  
-   但是，它应更新任何外部资源，如数据库或文件内容或 store 外的对象。 这将确保使它们保持在 synchronism 中存储的值。  
  
 例如:   
  
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
  
 有关事务的详细信息，请参阅[导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## <a name="see-also"></a>另请参阅  
 [导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [域属性的属性](../modeling/properties-of-domain-properties.md)   
 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)