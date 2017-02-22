---
title: "定义锁定策略以创建只读段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
caps.handback.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 定义锁定策略以创建只读段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可视化和建模 SDK 的不变性 API 允许程序锁定部分或全部一个域特定语言 \(DSL\)模型，以便可以读取，但不能更改它。  可以使用此只读选项，如，因此，用户可以调用同事说明和查看 DSL 模型，但可能不允许其从更改原始文件。  
  
 此外，作为 DSL 的作者，您可以定义一个 *锁定的策略。*一个锁定的策略定义了哪些锁允许，不允许使用，或者必须。  例如，那么，当您发布 DSL 时，可以鼓励第三方开发人员对它进行扩展新的命令。  但是，您也可以使用一个锁定的策略防止它们修改模型的指定部分的只读状态。  
  
> [!NOTE]
>  使用反射，一个锁定的策略可避免。  它为第三方开发人员提供了一种明确的边界，但是，不提供强有力的安全防护措施。  
  
 更多信息和示例可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) 网站。  
  
## 设置和获取锁  
 可以设置锁定存储，分区中，或者在各个元素。  例如，此语句将会阻止一个模型元素被删除但也可以防止其属性更改:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 其他锁值在角色可用于阻止在关系，元素创建，在分区和重新排序链接之间的移动的更改。  
  
 锁定应用于用户操作和于程序代码。  如果程序代码尝试进行更改， `InvalidOperationException` 将引发异常。  锁定取消忽略或重做操作。  
  
 可以查看元素是否有任何锁中给出的设置将使用 `IsLocked(Locks)` ，并且可以获取当前设置对元素的锁。使用 `GetLocks()`。  
  
 可以设置锁，而无需使用事务。  锁定数据库不是存储的一部分。  如果将锁定响应值的更改在存储中，如 OnValueChanged，您应当允许是取消操作的一部分的更改。  
  
 这些方法是在 <xref:Microsoft.VisualStudio.Modeling.Immutability> 命名空间中定义的扩展方法。  
  
### 在分区和存储的锁  
 锁还会应用于分区和存储。  分区中设置的锁定应用于分区中的所有元素。  因此，例如，下面的语句将会阻止分区中的所有删除组件，而不考虑其锁定状态。  但是，其他锁例如 `Locks.Property` 在单独的组件仍可以设置:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 在存储设置的锁定应用于其所有元素，不考虑该锁将分区和元素。  
  
### 使用锁  
 您可以使用锁来实现模式 \(如以下示例:  
  
-   禁止对所有元素的 \(表示注释的那些的更改和关系。  这使得用户批注模型，而无需更改它。  
  
-   禁止在默认分区中的更改，但是，允许在关系图分区中的更改。  用户重新排列关系图，但是，不能修改基础模型。  
  
-   禁止到中存储的更改但在单独的数据库中注册用户组。  对于其他用户，关系图和模型是只读的。  
  
-   ，如果关系图的布尔属性设置为 true，请禁止对设计的更改。  提供一个菜单命令更改该属性。  这有助于确保不会意外提交更改的用户。  
  
-   禁止元素的添加和特殊类、删除和关系，但是，允许属性更改。  为用户提供可当在其中可以填充属性。  
  
## 锁定值  
 锁定存储、分区或单个 ModelElement 进行设置。  锁定是 `Flags` 枚举:您可以合并其值使用 “&#124;”。  
  
-   ModelElement 的锁始终包括其分区锁。  
  
-   分区的锁始终包括存储的锁。  
  
 可以在单个元素不能在分区的锁或存储同时禁用锁。  
  
|值|这意味着 `IsLocked(Value)` 是否为 true|  
|-------|-------------------------------------|  
|无|没有限制。|  
|属性|不可更改元素字段的特性。  这不适用于由域类的效果会在关系的属性。|  
|添加|新元素和链接不能在分区或存储区中创建。<br /><br /> 不适用于 `ModelElement`。|  
|移动|元素不能移动分区中之间，如果 `element.IsLocked(Move)` 为 true，或者，如果 `targetPartition.IsLocked(Move)` 为 true。|  
|Delete|元素在删除操作将传播的不能删除，则此锁将元素，或任何元素，如嵌入元素和形状。<br /><br /> 可以使用 `element.CanDelete()` 查看元素是否能删除。|  
|重新排序|不能更改排序。 roleplayer 的链接。|  
|RolePlayer|的设置 LINK 未能更改是源此元素。  例如，新元素不能嵌入在此元素下。  这不会影响此元素为目标的链接。<br /><br /> 如果此元素为链接，其源和目标不受影响。|  
|全部|按位或其他值。|  
  
## 锁定策略  
 作为 DSL 的作者，您可以定义一个 *锁定的策略*。  一个锁定的策略减轻 SetLocks\(\) 的操作，因此，您可以禁止特定锁定设置或要求必须设置特定的锁。  通常，会使用一个锁定的策略从意外冲突到 DSL 的用途不鼓励用户或开发人员类似，可以声明变量的 `private`。  
  
 也可以使用一个锁定的策略将任何元素的锁根据元素类型。  这是因为， `SetLocks(Locks.None)` 始终调用，将元素从文件时首先创建或反序列化。  
  
 但是，在其生存期内，不能使用策略更改在元素的锁。  若要实现该角色，则应使用调用 `SetLocks()`。  
  
 若要定义一个锁定的策略，必须:  
  
-   创建实现的类 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>。  
  
-   将此类添加到通过 DSL 的 DocData 可用的服务。  
  
### 定义一个锁定的策略  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 具有以下定义:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 ，当调用已 `SetLocks()` 在存储、分区或 ModelElement 时，这些方法调用。  在每个方法，则提供建议设置锁定。  可以返回建议的设置，也可以增加和减少锁。  
  
 例如：  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 确保，用户始终可以删除元素，因此，即使其他代码调用 `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 禁止在 MyClass 的每个元素上所有属性的更改:  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### 使策略可用作服务  
 在 `DslPackage` 项目中，添加包含代码类似于下面的示例的新文件:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```