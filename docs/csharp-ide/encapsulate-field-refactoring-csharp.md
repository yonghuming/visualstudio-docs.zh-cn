---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "封装字段重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>封装字段重构 (C#)
**封装字段**重构操作，可从现有字段，快速创建一个属性，然后对新属性的引用无缝地更新你的代码。  
  
 当[字段](/dotnet/csharp/programming-guide/classes-and-structs/fields)是[公共](/dotnet/csharp/language-reference/keywords/public)，其他对象可以直接访问该字段，并且可以修改它不会察觉拥有该字段的对象。 通过使用[属性](/dotnet/csharp/programming-guide/classes-and-structs/properties)封装该字段，可以禁止对字段的直接访问。  
  
 若要创建新的属性，**封装字段**操作将会更改你想要封装到字段的访问修饰符[私有](/dotnet/csharp/language-reference/keywords/private)，，然后生成[获取](/dotnet/csharp/language-reference/keywords/get)和[设置](/dotnet/csharp/language-reference/keywords/set)该字段的访问器。 在某些情况下，仅生成 `get` 访问器（如当字段声明为只读时）。  
  
 重构引擎对中指定的区域中的新属性的引用更新你的代码**更新引用**部分**封装字段**对话框。  
  
### <a name="to-create-a-property-from-a-field"></a>从字段创建属性  
  
1.  创建名为 `EncapsulateFieldExample` 的控制台应用程序，然后将 `Program` 替换为下面的示例代码。  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  在[代码编辑器](../ide/writing-code-in-the-code-and-text-editor.md)，将光标放在声明中，你希望将封装的字段的名称。 在下面的示例中，将光标置于单词 `width` 上：  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  上**重构**菜单上，单击**封装字段**。  
  
     **封装字段**对话框随即出现。  
  
     此外可以键入键盘快捷键 CTRL + R、 E 以显示**封装字段**对话框。  
  
     此外可以右键单击将光标置于，指向**重构**，然后单击**封装字段**以显示**封装字段**对话框。  
  
4.  指定设置。  
  
5.  按 enter 键，或单击**确定**按钮。  
  
6.  如果你选择**预览引用更改**选项，则**预览引用更改**窗口随即打开。 单击**应用**按钮。  
  
     源文件中会显示以下 `get` 和 `set` 访问器代码：  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     `Main` 方法中的代码也将更新为新的 `Width` 属性名称。  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>备注  
 **封装字段**操作时，才可以将光标置于与字段声明位于同一行时。  
  
 对于声明声明多个字段，**封装字段**使用逗号作为字段之间的边界，并开始重构和光标所在的行上最接近的光标的字段。 还可以通过在声明中选择字段的名称来指定想要封装的字段。  
  
 通过此重构操作生成的代码将由封装字段代码片段功能来建模。 代码片段是可修改的。 有关详细信息，请参阅[代码片段](../ide/visual-csharp-code-snippets.md)。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)   
 [Visual C# 代码片段](../ide/visual-csharp-code-snippets.md)