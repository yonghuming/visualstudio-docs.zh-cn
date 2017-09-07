---
title: "将跟踪属性添加到的域特定语言定义 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 22
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ef5f86cb3b41af6cc9e7432cdbfb7365471320b8
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>向域特定语言定义中添加跟踪属性
本演练演示如何向域模型中添加跟踪属性。  
  
 A*跟踪域*属性是的属性，用户可以更新，但具有一个默认值，通过使用其他域属性或元素的值来计算。  
  
 例如，在域特定语言工具 （DSL 工具），属性的域类具有一个默认值，通过使用域类，而是用户的名称来计算的显示名称可以在设计时更改的值或其重置为计算值。  
  
 在本演练中，你将创建具有跟踪具有基于模型的默认 Namespace 属性的默认值的属性的 Namespace 的域特定语言 (DSL)。 有关跟踪属性的详细信息，请参阅[定义跟踪属性](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be)。  
  
-   跟踪属性描述符 DSL 工具支持。 但是，DSL 设计器不能用于将跟踪属性添加到一种语言。 因此，你必须添加自定义代码以定义和实现跟踪属性。  
  
 跟踪属性有两种状态： 跟踪，并更新用户。 跟踪属性具有以下功能：  
  
-   当跟踪状态中，跟踪属性的值计算，且值更新为模型更改中的其他属性。  
  
-   在更新时由用户状态时，跟踪属性的值保留为其用户上次设置的属性的值。  
  
-   在**属性**窗口中，**重置**命令属性是在更新后才可以启用跟踪属性通过用户状态。 **重置**命令将跟踪属性设置为跟踪状态。  
  
-   在**属性**窗口中，当跟踪属性处于跟踪状态，其值显示在正则字体。  
  
-   在**属性**窗口中，跟踪属性为在更新时由用户状态，以粗体显示其值。  
  
## <a name="prerequisites"></a>先决条件  
 在开始本演练之前，您必须首先安装这些组件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>创建 DSL 项目  
 创建你的域特定语言的项目。  
  
#### <a name="to-create-the-project"></a>创建项目  
  
1.  创建域特定语言设计器项目。 将其命名为 `TrackingPropertyDSL`。  
  
2.  在**域特定语言设计器向导**，设置以下选项：  
  
    1.  选择**MinimalLanguage**模板。  
  
    2.  使用域特定语言中，默认名称`TrackingPropertyDSL`。  
  
    3.  设置到的模型文件的扩展名`trackingPropertyDsl`。  
  
    4.  用于模型文件的默认模板图标。  
  
    5.  设置到的产品的名称`Product Name`。  
  
    6.  设置为公司的名称`Company Name`。  
  
    7.  默认值用于在解决方案中，项目的根命名空间`CompanyName.ProductName.TrackingPropertyDSL`。  
  
    8.  允许向导为你的程序集创建强名称密钥文件。  
  
    9. 查看该解决方案的详细信息，然后单击**完成**创建 DSL 定义项目。  
  
## <a name="customizing-the-default-dsl-definition"></a>自定义默认的 DSL 定义  
 在此部分中，你自定义 DSL 定义以包含以下项：  
  
-   跟踪模型的每个元素的属性的 Namespace。  
  
-   模型的每个元素的布尔 IsNamespaceTracking 属性。 此属性将指示跟踪属性是否跟踪状态或处于已更新的用户状态。  
  
-   该模型默认 Namespace 属性。 此属性将用于计算 Namespace 跟踪属性的默认值。  
  
-   CustomElements 计算模型的属性。 此属性将指示具有自定义的命名空间的元素的比例。  
  
#### <a name="to-add-the-domain-properties"></a>若要添加的域属性  
  
1.  在 DSL 设计器中，右键单击**ExampleModel**域类，指向**添加**，然后单击**DomainProperty**。  
  
    1.  命名新属性`DefaultNamespace`。  
  
    2.  在**属性**窗口中为新的属性中，设置**默认值**到`DefaultNamespace`，并设置**类型**到**字符串**。  
  
2.  到**ExampleModel**域类中，添加名为的域属性`CustomElements`。  
  
     在**属性**窗口中为新的属性中，设置**类型**到**计算**。  
  
3.  到**ExampleElement**域类中，添加名为的域属性`Namespace`。  
  
     在**属性**窗口中为新的属性中，设置**是可浏览**到**False**，并设置**类型**到**CustomStorage**.  
  
4.  到**ExampleElement**域类中，添加名为的域属性`IsNamespaceTracking`。  
  
     在**属性**窗口中为新的属性中，设置**是可浏览**到**False**，将其设置**默认值**到`true`，并设置**类型**到**布尔**。  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>若要更新的图表元素和 DSL 详细信息  
  
1.  在 DSL 设计器中，右键单击**ExampleShape**几何形状，指向**添加**，然后单击**文本修饰器**。  
  
    1.  命名新文本修饰器`NamespaceDecorator`。  
  
    2.  在**属性**窗口中的文本修饰器，设置**位置**到**InnerBottomLeft**。  
  
2.  在 DSL 设计器中，选择连接的行**ExampleElement**类到**ExampleShape**形状。  
  
    1.  在**DSL 详细信息**窗口中，选择**修饰器地图**选项卡。  
  
    2.  在**修饰符**列表中，选择**NamespaceDecorator**，选中其复选框，然后在**显示属性**列表中，选择**Namespace**.  
  
3.  在**DSL 资源管理器**，展开**域类**文件夹中，右键单击**ExampleElement**节点，，然后单击**添加新域类型描述符**.  
  
    1.  展开**ExampleElement**节点，然后选择**自定义类型描述符 （域类型描述符）**节点。  
  
    2.  在**属性**域类型描述符，窗口中将设置**自定义编码**到**True**。  
  
4.  在**DSL 资源管理器**，选择**Xml 序列化行为**节点。  
  
    1.  在**属性**窗口中，设置**自定义 Post 负载**到**True**。  
  
## <a name="transforming-templates"></a>转换模板  
 现在，你已为 DSL 定义的域类和属性，可以验证，DSL 定义可以转换正确重新生成你的项目的代码。  
  
#### <a name="to-transform-the-text-templates"></a>转换文本模板  
  
1.  上**解决方案资源管理器**工具栏上，单击**转换所有模板**。  
  
2.  系统将重新生成解决方案的代码，并将保存 DslDefinition.dsl。 有关 XML 格式的定义文件的信息，请参阅[DslDefinition.dsl 文件](../modeling/the-dsldefinition-dsl-file.md)。  
  
## <a name="creating-files-for-custom-code"></a>为自定义代码中创建文件  
 当转换所有模板时，系统将生成的 Dsl 和 DslPackage 项目中定义你的域特定语言的源代码。 以便你可以避免干扰生成的文本，不同于生成的代码文件的文件中编写自定义代码。  
  
 用于维护值和跟踪属性的状态，必须提供代码。 若要帮助你区分你自定义代码与生成的代码，并避免命名冲突的文件，将自定义代码文件放置在一个单独的子文件夹。  
  
#### <a name="to-create-the-code-files"></a>若要创建的代码文件  
  
1.  在**解决方案资源管理器**，右键单击**DSL**项目，指向**添加**，然后单击**新文件夹**。 将新文件夹命名`CustomCode`。  
  
2.  右键单击新**自定义代码**文件夹，指向**添加**，然后单击**新项**。  
  
3.  选择**代码文件**设置模板，**名称**到`NamespaceTrackingProperty.cs`，然后单击**确定**。  
  
     创建 NamespaceTrackingProperty.cs 文件并将其打开以进行编辑。  
  
4.  在文件夹中，创建以下的代码文件： `ExampleModel.cs,``HelperClasses.cs`， `Serialization.cs`，和`TypeDescriptor.cs`。  
  
5.  在**DslPackage**项目中，还创建`CustomCode`文件夹，并向其中添加`Package.cs`代码文件。  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>添加帮助器类以支持跟踪属性  
 到 HelperClasses.cs 文件中，添加`TrackingHelper`和`CriticalException`类，如下所示。 将引用这些类稍后在本演练。  
  
#### <a name="to-add-the-helper-classes"></a>若要添加的帮助程序类  
  
1.  将以下代码添加到 HelperClasses.cs 文件中。  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>自定义类型描述符添加自定义代码  
 实现`GetCustomProperties`方法的类型描述符`ExampleModel`域类。  
  
> [!NOTE]
>  DSL 工具生成的自定义类型描述符的代码`ExampleModel`调用`GetCustomProperties`; 但是，DSL 工具也不会生成实现该方法的代码。  
  
 定义此方法将创建跟踪 Namespace 跟踪属性的属性描述符。 此外，提供跟踪属性的属性允许**属性**窗口以正确显示属性。  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>若要修改 ExampleModel 域类的类型描述符  
  
1.  将以下代码添加到 TypeDescriptor.cs 文件中。  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>包中添加自定义代码  
 生成的代码定义的类型说明提供程序 ExampleElement 域类;但是，你必须添加代码以指示 DSL 以使用此类型描述提供程序。  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>若要更新要使用自定义类型描述符的 DSL 包  
  
1.  将以下代码添加到 Package.cs 文件中。  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>模型中添加自定义代码  
 实现`GetCustomElementsValue`方法`ExampleModel`域类。  
  
> [!NOTE]
>  DSL 工具生成的代码`ExampleModel`调用`GetCustomElementsValue`; 但是，DSL 工具也不会生成实现该方法的代码。  
  
 定义`GetCustomElementsValue`方法提供逻辑的计算的 CustomElements 属性`ExampleModel`。 此方法对数进行计数`ExampleElement`具有跟踪属性，它具有用户更新的值，并返回一个字符串，表示此计数为模型中的总元素的比例 Namespace 的域类。  
  
 此外，添加`OnDefaultNamespaceChanged`方法`ExampleModel`，并重写`OnValueChanged`方法`DefaultNamespacePropertyHandler`嵌套的类`ExampleModel`调用`OnDefaultNamespaceChanged`。  
  
 因为 DefaultNamespace 属性用于计算跟踪属性，Namespace`ExampleModel`必须通知所有`ExampleElement`DefaultNamespace 的值已更改的域类。  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>若要修改的属性处理程序跟踪的属性  
  
1.  将以下代码添加到 ExampleModel.cs 文件中。  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>将自定义代码添加跟踪属性  
 添加`CalculateNamespace`方法`ExampleElement`域类。  
  
 定义此方法提供逻辑的计算的 CustomElements 属性`ExampleModel`。 此方法对数进行计数`ExampleElement`具有跟踪是在更新的属性的 Namespace 的域类通过用户状态，并返回表示此计数为模型中的总元素的比例的字符串。  
  
 此外，将添加存储和方法来获取和设置的 Namespace 自定义存储属性`ExampleElement`域类。  
  
> [!NOTE]
>  DSL 工具生成的代码`ExampleModel`调用 get 和 set 方法; 但是，DSL 工具不会生成实现的方法的代码。  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>若要添加自定义类型描述符方法  
  
1.  将以下代码添加到 NamespaceTrackingProperty.cs 文件中。  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>添加自定义代码，以支持序列化  
 添加代码以支持自定义后负载行为对于 XML 序列化。  
  
> [!NOTE]
>  DSL 工具生成调用的代码`OnPostLoadModel`和`OnPostLoadModelAndDiagram`方法; 但是，DSL 工具不会生成实现这些方法的代码。  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>若要添加代码以支持自定义的后加载行为  
  
1.  将以下代码添加到 Serialization.cs 文件中。  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>测试语言  
 下一步是生成并运行 DSL 设计器中的新实例[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]以便你可以验证是否跟踪属性是否正常工作。  
  
#### <a name="to-exercise-the-language"></a>若要执行语言  
  
1.  上**生成**菜单上，单击**重新生成解决方案**。  
  
2.  在“调试”菜单上，单击“启动调试”。  
  
     实验性生成[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]打开**调试**解决方案，其中包含一个空的测试文件。  
  
3.  在**解决方案资源管理器**，双击 Test.trackingPropertyDsl 文件以在设计器中打开它，然后单击设计图面。  
  
     请注意，在**属性**关系图中，窗口**默认 Namespace**属性是**DefaultNamespace**，和**自定义元素**属性是**0/0**。  
  
4.  拖动**ExampleElement**元素从**工具箱**到关系图图面。  
  
5.  在**属性**元素中，选择窗口**元素 Namespace**属性，并将值从**DefaultNamespace**到**OtherNamespace**。  
  
     请注意，值**元素 Namespace**现在以粗体显示。  
  
6.  在**属性**窗口中，右键单击**元素 Namespace**，然后单击**重置**。  
  
     属性的值更改为**DefaultNamespace**，和值显示在正则字体。  
  
     右键单击**元素 Namespace**试。 **重置**现在已禁用命令，因为该属性是当前在其跟踪状态。  
  
7.  将另一个**ExampleElement**从**工具箱**到关系图图面，并更改其**元素 Namespace**到**OtherNamespace**。  
  
8.  单击设计图面。  
  
     在**属性**为关系图的值的窗口**自定义元素**现**1/2**。  
  
9. 更改**默认 Namespace**从图表的**DefaultNamespace**到**NewNamespace**。  
  
     **Namespace**的第一个元素曲目**默认 Namespace**属性，而**Namespace**第二个元素保持其用户更新值**OtherNamespace**。  
  
10. 保存的解决方案，然后关闭实验性生成。  
  
## <a name="next-steps"></a>后续步骤  
 如果你打算使用多个跟踪属性，或在多个 DSL 中实现跟踪属性，可以创建文本模板生成的常见代码，以支持每个跟踪属性。 文本模板的详细信息，请参阅[代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [如何定义的域特定语言](../modeling/how-to-define-a-domain-specific-language.md)   
 [如何：创建域特定语言解决方案](../modeling/how-to-create-a-domain-specific-language-solution.md)   

