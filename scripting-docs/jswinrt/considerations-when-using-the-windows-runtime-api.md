---
title: "使用 Windows 运行时 API 时的注意事项 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="considerations-when-using-the-windows-runtime-api"></a>使用 Windows 运行时 API 时的注意事项
可以在 JavaScript 中使用 Windows 运行时 API 的几乎所有元素。 但是，应谨记 Windows 运行时元素的 JavaScript 表示形式的某些方面。  
  
> [!IMPORTANT]
>  有关使用 C++、C# 或 Visual Basic 创建 Windows 运行时组件并在 JavaScript 中使用这些组件的信息，请参阅[使用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)和[使用 C# 和 Visual Basic 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Windows 运行时类型的 JavaScript 表示形式中的特殊情况  
  
-   字符串：未初始化的字符串作为“未定义”字符串传递到 Windows 运行时方法，并将设置为 `null` 的字符串作为“null”字符串传递。 （这在将 `null` 或 `undefined` 值强制转换为字符串时为 true。）在将字符串传递给 Windows 运行时方法之前，应将其初始化为空字符串 ("")。  
  
-   接口：无法在 JavaScript 中实现 Windows 运行时接口。  
  
-   数组：Windows 运行时数组不能调整大小，因此可在 JavaScript 中调整数组大小的方法在 Windows 运行时数组中不起作用。  
  
-   数组：如果将 JavaScript 数组值传递给 Windows 运行时方法，则会复制该数组。 Windows 运行时方法无法修改数组或其成员，并将其返回到 JavaScript 应用。 但是，可以使用不会进行复制的类型化数组（例如 [Int32Array 对象](../javascript/reference/int32array-object.md)）。  
  
-   结构：Windows 运行时结构是 JavaScript 中的对象。 如果要将 Windows 运行时结构传递给 Windows 运行时方法，请不要使用 `new` 关键字实例化该结构。 而应创建一个对象并添加相关成员及其值。 成员的名称应采用 camel 形式：`SomeStruct.firstMember`。  
  
-   对象：JavaScript 对象与托管代码对象 (`System.Object`) 不同。 不能将 JavaScript 对象传递到需要 `System.Object` 的 Windows 运行时方法。  
  
-   对象标识：在大多数情况下，在 Windows 运行时和 JavaScript 之间来回传递的对象不会更改。 JavaScript 引擎会保留已知对象的映射。 当从 Windows 运行时返回对象时，它与映射匹配，如果该对象不存在，则会创建一个新对象。 表示 Windows 运行时方法返回的接口的对象要遵循相同的过程。 存在两种例外情况：  
  
    -   从 Windows 运行时调用返回、然后添加了新 (expando) 属性的对象在传递回 Windows 运行时时不保留其新属性。 但是，当它们返回到 JavaScript 应用时，由于它们与现有对象相匹配，返回的对象会具有 expando 属性。  
  
    -   Windows 运行时中的结构和委托不能视为与以前使用的结构或委托相同。 每次返回结构或委托时，它都会获取一个新引用。  
  
-   名称冲突：多个 Windows 运行时接口可能具有名称相同的成员。 如果它们在单个 JavaScript 对象（可以是运行时类或接口的表示形式）中进行组合，那么成员将以完全限定的名称来表示。 可以使用以下语法来调用这些成员：`Class["MemberName"](parameter)`。  
  
     在下面的代码中，两个接口都具有 Draw 方法，并且一个运行时类实现了两个接口。  
  
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
  
     以下介绍了如何在 JavaScript 中调用上述代码。  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` 参数：如果 Windows 运行时方法具有多个 `out` 参数，则在 JavaScript 中，该方法将 JavaScript 对象作为其返回值，且该对象具有与 `out` 参数对应的属性。 例如，请考虑以下使用 C++ 的 Windows 运行时签名。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     此签名的 JavaScript 版本为：  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     在此例中，`returnValue` 是 JavaScript 对象，它有两个字段：`first` 和 `second`。  
  
-   静态成员：Windows 运行时定义静态成员和实例成员。 在 JavaScript 中，将静态成员添加到与 Windows 运行时类或接口关联的对象中。  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 有关 Windows 运行时基本类型的 JavaScript 表示形式的详细信息，请参阅 [Windows 运行时类型的 JavaScript 表示形式](../jswinrt/javascript-representation-of-windows-runtime-types.md)。
