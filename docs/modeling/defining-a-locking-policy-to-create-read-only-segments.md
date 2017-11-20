---
title: "定义要创建只读的段的锁定策略 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: "12"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 0ac8ba75920c4b3b8964d473258c162c256139ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>定义锁定策略以创建只读段
不可变性 API[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可视化和建模 SDK 允许一个程序对锁定部分或全部域特定语言 (DSL) 模型，以便它可以读取但未更改。 无法使用此只读选项，例如，以便用户可以要求同事添加批注并查看 DSL 模型，但可以更改原始禁止它们。  
  
 此外，作为 DSL 的作者可以定义*锁定策略。* 锁定的策略定义的锁是允许、 不允许，或强制。 例如，DSL 发布时，你可以鼓励第三方开发人员可以使用新的命令对它进行扩展。 但你无法使用锁定的策略来防止它们被更改的模型的指定部分的只读状态。  
  
> [!NOTE]
>  通过使用反射，可以绕过锁定策略。 它为第三方开发人员提供了清除边界，但不是提供强大的安全性。  
  
 详细信息和示例位于[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][可视化和建模 SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Web 站点。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>设置和获取锁  
 存储区、 一个分区，或单个元素，可以设置锁。 例如，此语句将阻止删除，将模型元素，并将还防止更改其属性：  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 其他锁值可用来防止关系、 元素创建、 分区和角色中的重新排序链接之间移动中的更改。  
  
 锁将应用同时向用户操作和程序代码。 如果程序代码尝试进行更改，`InvalidOperationException`将引发。 撤消或重做操作情况下，锁将被忽略。  
  
 你可以发现是否元素通过使用给定的一组中具有的任何锁定`IsLocked(Locks)`，并可以通过使用获得当前集元素上的锁`GetLocks()`。  
  
 你可以设置锁，而使用事务。 锁定数据库不是存储的一部分。 如果在存储中值的更改的响应中设置锁，例如在 OnValueChanged，你应允许属于撤消操作的更改。  
  
 这些方法是在中定义的扩展方法<xref:Microsoft.VisualStudio.Modeling.Immutability>命名空间。  
  
### <a name="locks-on-partitions-and-stores"></a>对分区和存储的锁  
 锁也可以应用于分区和存储。 设置每个分区的锁将应用到分区中的所有元素。 因此，例如，以下语句将阻止在一个分区中的所有元素删除，而不考虑其自己持有的锁的状态。 不过，其他锁如`Locks.Property`仍然无法设置对单独的元素：  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 锁定状态的存储区设置适用于所有元素，而不考虑该锁分区和元素上的设置。  
  
### <a name="using-locks"></a>使用锁  
 你无法使用锁来实现方案，如下面的示例：  
  
-   不允许对所有元素和关系，表示注释除外的更改。 这样用户就可以对模型进行批注而不能更改。  
  
-   不允许更改在默认分区中，但允许在关系图分区中的更改。 用户可以重新排列关系图中，但不能更改基础模型。  
  
-   禁止对除外的在单独的数据库中注册的用户组的存储区的更改。 对于其他用户，关系图和模型中都是只读的。  
  
-   禁止对模型的更改，如果关系图的布尔属性设置为 true。 提供菜单命令来更改该属性。 这有助于确保它们无法表达的用户意外更改。  
  
-   禁止添加和删除的元素和关系的特定类，但允许属性更改。 这使用户有固定的窗体，它们可以在其中填充属性。  
  
## <a name="lock-values"></a>锁值  
 可以在应用商店、 分区或单独的模型元素上设置锁。 锁是`Flags`枚举： 你可以组合使用其值 &#124;。  
  
-   锁的模型元素始终包含其分区的锁。  
  
-   锁分区始终包含存储的锁。  
  
 无法在分区上设置锁定或存储，并且在同一时间禁用对单个元素的锁定。  
  
|值|这意味着如果`IsLocked(Value)`为 true|  
|-----------|------------------------------------------|  
|无|没有限制。|  
|属性|不能更改域属性的元素。 这不适用于生成的域类关系中的角色的属性。|  
|添加|不在分区中创建新的元素和链接或存储。<br /><br /> 不适用于`ModelElement`。|  
|移动|如果无法将元素移动分区之间`element.IsLocked(Move)`为 true，或者如果`targetPartition.IsLocked(Move)`为 true。|  
|删除|无法删除元素，如果此锁设置于元素自身，或在任何到元素上删除将传播，例如嵌入的元素和形状。<br /><br /> 你可以使用`element.CanDelete()`来发现是否可删除一个元素。|  
|重新排序|无法更改排序 roleplayer 方式的链接。|  
|RolePlayer|对于来源于此元素的链接集不能更改。 例如，无法将新元素嵌入在此元素下。 这不会影响此元素为其为目标的链接。<br /><br /> 如果此元素是一个链接，其源和目标不受影响。|  
|全部|其他值的按位或。|  
  
## <a name="locking-policies"></a>锁定策略  
 作为 DSL 的作者，你可以定义*锁定策略*。 锁定的策略，以便你可以防止特定锁设置或强制，必须设置特定的锁减少 SetLocks()，该操作。 通常情况下，你将使用锁定策略仅用户或开发人员能够从意外相同的方式，可以声明一个变量中 contravening DSL 的预期的用途`private`。  
  
 锁定策略还可用于设置在所有元素上的锁依赖于元素的类型。 这是因为`SetLocks(Locks.None)`始终元素是首次创建或从文件反序列化时调用。  
  
 但是，你无法使用策略来改变其生命周期内的元素上的锁。 若要实现该效果，应使用调用`SetLocks()`。  
  
 若要定义锁定策略，必须：  
  
-   创建用于实现 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 的类。  
  
-   将此类添加到可通过 DSL 的 DocData 的服务。  
  
### <a name="to-define-a-locking-policy"></a>若要定义锁定策略  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>具有以下定义：  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 为进行调用时调用这些方法`SetLocks()`上应用商店、 分区或模型元素。 每个方法，你将获得锁的建议设置。 你可以返回建议的组，或者可以将添加减去锁。  
  
 例如:   
  
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
  
 若要确保用户始终可以删除元素，即使其他代码调用`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 若要禁用的 MyClass 的每个元素的所有属性中的行为更改：  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>用于使你的策略可用作服务  
 在你`DslPackage`项目中，添加包含类似于下面的示例代码的新文件：  
  
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
