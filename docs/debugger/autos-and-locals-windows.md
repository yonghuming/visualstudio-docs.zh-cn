---
title: "检查自动和局部变量窗口中的变量 |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2504807bd4717ec7f42ed059e7ef4d962c7441e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="inspect-variables-in-the-autos-and-locals-windows-in-visual-studio"></a>检查自动中的变量和 Visual Studio 中的局部变量窗口
**自动**窗口 (调试时， **CTRL + ALT + V、 A**，或**调试 > Windows > 自动**) 和**局部变量**（时调试窗口**CTRL + ALT + V、 L**，或**调试 > Windows > 局部变量**) 是非常有用，当你想要在调试时，请参阅变量值。 “局部变量”  窗口显示在本地范围内定义的变量，它们通常为当前正在执行的函数或方法。 **“自动”** 窗口显示在当前行（调试器停止的位置）周围使用的变量。 在此窗口中显示哪些变量的完全是不同的语言。 请参阅下面的 [What variables appear in the Autos Window?](#bkmk_whatvariables) 下方。  
  
若需了解基本调试的详细信息，请参阅 [Getting Started with the Debugger](../debugger/getting-started-with-the-debugger.md)。  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>查看“自动”和“局部变量”窗口中的对象  
数组和对象在“自动”和“局部变量”窗口中显示为树控件。 单击变量名称左侧的箭头以展开显示字段和属性的视图。 以下是 [“局部变量”](http://msdn.microsoft.com/Library/a8737776-e545-4867-91ed-51c7f031fa19) 窗口中的 **FileStream** 对象的示例：  
  
![局部变量 &#45;FileStream](../debugger/media/locals-filestream.png "局部变量 FileStream")  
  
## <a name="bkmk_whatvariables"></a> “自动”窗口中显示了哪些变量？  
 你可以在 C#、Visual Basic 和 C++ 代码中使用 **“自动”** 窗口。 **“自动”** 窗口不支持 JavaScript 或 F#。  
  
 在 C# 和 Visual Basic 中，“自动”  窗口显示当前或前一行中使用的任何变量。 例如，如果声明四个变量并对它们进行如下设置：

```CSharp
    public static void Main()
    {
       int a, b, c, d;
       a = 1;
       b = 2;
       c = 3;
       d = 4;
    }
```

 如果在行 `c = 3`上设置了断点并运行调试器，当执行停止时，“自动”  窗口将如下所示：  

 ![自动 &#45;CSharp](../debugger/media/autos-csharp.png "自动 CSharp")  

 注意， `c` 的值为 0，因为行 `c = 3` 尚未执行。  

 在 C++ 中，“自动”  窗口将显示当前行（执行停止的行）前面至少三行使用的变量。 如果声明了六个变量：

```C++
    void main() {
        int a, b, c, d, e, f;
        a = 1;
        b = 2;
        c = 3;
        d = 4;
        e = 5;
        f = 6;
    }
```

 如果在行 `e = 5;` 上设置了断点并运行调试器，当执行停止时，“自动”  窗口将如下所示：  
  
 ![自动 &#45;Cplus](../debugger/media/autos-cplus.png "自动 Cplus")  
  
 请注意，此变量未初始化，因为行 `e = 5;` 上的代码尚未执行。  
  
 在某些情况下，你还可以看到函数和方法的返回值。 请参阅下面的 [View return values of method calls](#bkmk_returnValue) 。  
  
##  <a name="bkmk_returnValue"></a> View return values of method calls  
 在 .NET 和 C++ 代码中，当你单步执行或单步跳出方法调用时，可以检查返回值。 当方法调用的结果未存储在局部变量中时（例如，当方法用作另一个方法的参数或返回值时），此功能很有用。  
  
 下面的 C# 代码将添加两个函数的返回值：  

```CSharp
static void Main(string[] args)  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    int x = sumVars(a, b) + subtractVars(c, d);  
}  
  
private static int sumVars(int i, int j)  
{  
    return i + j;  
}  
  
private static int subtractVars(int i, int j)  
{  
    return j - i;  
}  
```

 在 `int x = sumVars(a, b) + subtractVars(c, d);` 行上设置断点。  
  
 开始调试，且当执行在第一个断点处中断时，按 **F10（跳过）**。 你应在 **“自动”** 窗口中看到如下内容：  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>为什么在“局部变量”窗口和“自动”窗口中变量值有时是红色的？  
你可能注意到，在“局部变量”  和“自动”  窗口中一个变量的值有时是红色的。 这些是自上次评估以来更改过的变量值。 此更改可能是在上一次调试会话中进行的，或者是因为在窗口中更改了该值。  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>更改变量窗口中的数字格式  
默认数字格式为十进制，但你可以将其更改为十六进制。 在“局部变量”  或“自动”  窗口内右键单击，然后选择“十六进制显示” 。 此更改将影响所有调试器窗口。  
  
## <a name="editing-a-value-in-a-variable-window"></a>在变量窗口中编辑值  
你可以编辑“自动” 、“局部变量” 、“监视” 和“快速监视”  窗口中出现的大多数变量的值。 有关“监视”  和“快速监视”  窗口的信息，请参阅 [Watch and QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)。 只需双击要更改并添加新值的值。  
  
你可以输入表达式作为一个值，例如 `a + b`。 调试器接受大多数合法的语言表达式。  
  
在本机 C++ 代码中，你可能需要限定变量名的上下文。 有关详细信息，请参阅 [Context Operator (C++)](../debugger/context-operator-cpp.md)。  
 
但是，更改值时应多加小心。 可能存在的问题如下：  
  
-   计算某些表达式可以更改变量的值，或会影响程序的状态。 例如，计算 `var1 = ++var2` 会更改 `var1` 和 `var2`的值。  
  
     会更改数据的表达式被视为具有 [副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))，如果你不了解这些表达式，则会产生意外的结果。 因此，在进行更改前，请确保你了解此更改的后果。  
  
-   编辑浮点值时，由于要将小数部分从十进制转换为二进制，因此所得的结果可能存在微小误差。 即使看起来无关紧要的编辑都会导致浮点变量中某些最不重要的数据位发生变化。  
  
## <a name="changing-the-window-context"></a>更改窗口上下文  
你可以使用**调试位置**工具栏来选择所需的函数、 线程或进程，这会更改变量窗口的上下文。 设置断点并开始调试。 （如果看不到此工具栏，你可以通过单击工具栏区域的空白部分启用它。 你应当看到工具栏的列表；选择“调试位置” ）。 当命中断点时，则将停止执行，你可以查看调试位置工具栏上，即下图底部的行。
  
![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")   
  
## <a name="see-also"></a>另请参阅  
 [调试器窗口](../debugger/debugger-windows.md)
