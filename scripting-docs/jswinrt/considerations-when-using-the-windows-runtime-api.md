---
title: "使用 Windows 运行时 API 时的注意事项 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 运行时 API"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 Windows 运行时 API 时的注意事项
在 JavaScript 可以使用 Windows 运行时 API 的几乎每一个元素。  但是，有的 Windows 运行时元素的 JavaScript 表示形式的某些方面您应谨记。  
  
> [!IMPORTANT]
>  有关在 C\+\+、C\# 或 Visual Basic 中创建 Windows 运行时组件的信息以及在 JavaScript 中简化它们，请参见 [创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components.md)。  
  
## 在 Windows 运行时类型的 JavaScript 表示形式的特殊情况  
  
-   字符串：一个未初始化的字符串将传递给 Windows 运行时方法作为字符串“undefined”，并且，字符串设置为 `null` 将作为该字符串“null”传递。（无论 `null` 或 `undefined` 值将其强制为字符串。）在将字符串传递到 Windows 运行时方法之前，应将其初始化为空字符串\(""\)。  
  
-   接口：您无法在 JavaScript 中实现 Windows 运行时接口。  
  
-   数组：Windows 运行时数组大小不可调，因此在 JavaScript 不会在 Windows 运行时数组上运行时调整数组大小的方法。  
  
-   数组：如果将 JavaScript 数组值传递给 Windows 运行方法，则将复制该数组。  Windows 运行时方法不可修改该数组或其成员并将其返回您的 JavaScript 应用程序。  但是，您可以使用不会复制的类型化数组（例如，[Int32Array 对象](../javascript/reference/int32array-object.md)）。  
  
-   结构：在 JavaScript 中 Windows 运行时结构是对象。  如果希望将 Windows 运行时结构传递给 Windows 运行时方法，则不要实例化 `new` 关键字的结构。  相反，创建一个对象并添加相关成员以及它们的值。  成员的名称应在大小写格式中：`SomeStruct.firstMember`。  
  
-   对象：JavaScript 对象与管理代码对象\(`System.Object`\)不相同。  不能将 JavaScript 对象传递给需要 `System.Object` 的 Windows 运行时方法。  
  
-   对象标识：在许多情况下，对象来回通过 Windows 运行时与 JavaScript 之间不更改。  JavaScript 引擎维护已知对象的映射。  当对象从 Windows 运行时返回其与映射匹配时，并且，如果它不存在，创建一个新对象。  表示通过 Windows 运行时方法返回的接口的对象遵循相同的过程。  共有两种异常：  
  
    -   在传递回 Windows 运行时，从 Windows 运行时调用返回的对象，然后向其中添加了新的 \(expando\) 属性，而不保留其新属性。  但是，当它们返回 JavaScript 应用程序时，因为它们都与现有对象匹配，则返回的对象具有 expando 属性。  
  
    -   在 Windows 运行时中结构和委托不能标识为与前面使用的结构或委托相同。  每次返回结构或委托时，它将获取一个新引用。  
  
-   名称冲突：多个 Windows 运行时接口可以具有相同名称的成员。  如果是在单个 JavaScript 对象中合并（运行时选件类或接口的表示形式\)，成员使用完全限定名来表示。  可使用以下语法调用这些成员：`Class["MemberName"](parameter)`。  
  
     在以下代码中，两个接口有绘图方法，因此，运行时选件类实现这两种接口。  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     这是对 JavaScript 中的上代码调用的方式。  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` 参数：如果 Windows 运行时方法具有多个 `out` 参数，则在 JavaScript 方法中具有一个 JavaScript 对象作为其返回值，因此，对象具有对应于 `out` 参数的属性。  例如，在 C\+\+ 中请考虑以下 Windows 运行时签名。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     此签名的 JavaScript 版本是：  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     在此示例中，`returnValue` 是具有两个字段的 JavaScript 对象：`first` 和 `second`。  
  
-   静态成员：Windows 运行时定义静态成员和实例成员。  在 JavaScript 中，静态成员将添加到与 Windows 运行时选件类或接口相关联的对象。  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 有关 Windows 运行时基类型的 JavaScript 表示形式的更多信息，请参见 [Windows 运行时类型的 JavaScript 表示形式](../jswinrt/javascript-representation-of-windows-runtime-types.md)。