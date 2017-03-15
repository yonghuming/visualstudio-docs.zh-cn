---
title: "关于异常的疑难解答：System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException 类"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.InvalidOperationException
当调用一个对象的一个方法且该对象的状态无法支持该方法调用时，将引发 <xref:System.InvalidOperationException?displayProperty=fullName>。 当一个方法尝试从一个线程操作 UI 且该线程不是主要或 UI 线程时，也将引发该异常。  
  
> [!IMPORTANT]
>  由于 <xref:System.InvalidOperationException> 可能在多种环境中引发，因此必须阅读并理解“异常助手”中显示的 <xref:System.Exception.Message%2A>。  
  
##  <a name="BKMK_In_this_article"></a> 本文内容  
 [在非 UI 线程上运行的方法会更新 UI](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [foreach（Visual Basic 中的 For Each）块中的语句会更改其循环访问的集合。](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [为 null 的 Nullable&lt;T&gt; 转换为 T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [对空集合调用了 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [相关文章](#BKMK_Related_articles)  
  
 本文中代码示例展示你的应用中可能发生的常见 <xref:System.InvalidOperationException> 异常。如何处理问题取决于具体情况。如果异常对于应用的功能来说是致命的，你可能希望使用 [try … catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements)（在在 Visual Basic 中为 [Try ..Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)）构造来捕捉异常并在退出时清理应用的状态。但其他 <xref:System.InvalidOperationException> 是可以预料并避免。修改后的方法示例向你展示其中一些技巧。  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> 在非 UI 线程上运行的方法会更新 UI  
 [从 UI 线程进行 UI 更新引发 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [避免在非 UI 线程上引发 InvalidOperationException](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 大多数 .NET GUI（图形用户界面）应用框架（如 Windows 窗体和 Windows Presentation Foundation \(WPF\)）只允许从创建和管理 UI 的线程（**主线程**或 **UI** 线程）访问 GUI 对象。 尝试从非 UI 线程访问 UI 元素时，将引发 <xref:System.InvalidOperationException>。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> 从 UI 线程进行 UI 更新引发 InvalidOperationException  
  
> [!NOTE]
>  以下示例使用 [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md) 来创建非 UI 线程。 但是，这些示例也与所有 .NET [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md) 相关。  
  
 在这些示例中，`ThreadsExampleBtn_Click` 事件处理程序两次调用 `DoSomeWork` 方法。 对方法的第一次调用 \(`DoSomeWork(20);`\) 同步运行并成功。 但第二次调用 `Task.Run( () => { DoSomeWork(1000);});` 则在应用的[线程池](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx)中的一个线程上运行。 由于此调用试图从非 UI 线程更新 UI，该语句将引发 <xref:System.InvalidOperationException>  
  
 **WPF 和 Store 应用**  
  
> [!NOTE]
>  在 Store Phone 应用中，将引发 <xref:System.Exception> 而非更为具体的 <xref:System.InvalidOperationException>。  
  
 **异常消息：**  
  
|||  
|-|-|  
|WPF 应用|附加信息: 调用线程无法访问此对象，因为另一个线程拥有该对象。|  
|应用商店应用|附加信息: 应用程序调用了为另一个线程封送的界面。 \(异常来自 HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Windows 窗体应用**  
  
 **异常消息：**  
  
-   附加信息: 线程间操作无效: 从不是创建控件“TextBox1”的线程访问它。  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在非 UI 线程上运行的方法会更新 UI](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> 避免在非 UI 线程上引发 InvalidOperationException  
 Windows UI 框架实现*“调度程序”*模式，此模式包含一种用以检查 UI 线程上当前是否正在执行对 UI 元素成员的调用的方法，还包含其他用以计划对 UI 线程的调用的方法。  
  
 **WPF 应用**  
  
 在 WPF 应用中，使用其中一种 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 在 UI 线程上执行委托。 如果必要，使用 <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> 方法确定一个方法是否正在非 UI 线程上运行。  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Windows 窗体应用**  
  
 在 Windows 窗体应用中，使用 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 方法执行更新 UI 线程的委托。 如果必要，使用 <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 属性确定一个方法是否正在非 UI 线程上运行。  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **应用商店应用**  
  
 在 Store 应用中，使用 <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> 方法执行更新 UI 线程的委托。 如果必要，使用 <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> 属性确定一个方法是否正在非 UI 线程上运行。  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在非 UI 线程上运行的方法会更新 UI](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> foreach（Visual Basic 中的 For Each）块中的语句会更改其循环访问的集合。  
 [使用 foreach 引发 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [在循环中避免 InvalidOperationException](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 语句（Visual Basic 中的 [For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)）重复数组或集合中每个元素的一组嵌入语句，该数组或集合可实现 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 界面。`foreach` 用于循环访问该集合以读取和修改元素，但它不能用于添加或删除集合中的项。 如果通过 foreach 语句从源集合添加项或删除其中的项，将引发 <xref:System.InvalidOperationException>。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> 使用 foreach 引发 InvalidOperationException  
 在本示例中，当 <xref:System.InvalidOperationException> 语句尝试在 foreach 块中修改列表时，将引发 `numList.Add(5);`。  
  
 **异常消息：**  
  
-   附加信息: 集合已修改；枚举操作无法执行。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [foreach（Visual Basic 中的 For Each）块中的语句会更改其循环访问的集合。](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> 在循环中避免 InvalidOperationException  
  
> [!IMPORTANT]
>  在循环访问集合的同时向列表添加元素或从列表中删除元素可能导致意外的和难以预料的副作用。 如果可能，应将操作移到循环访问之外。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 如果你的情况要求你在循环访问集合时向列表添加元素或从列表中删除元素，请使用 [for](/dotnet/csharp/language-reference/keywords/for)（Visual Basic 中的 [For](/dotnet/visual-basic/language-reference/statements/for-next-statement)）循环：  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [foreach（Visual Basic 中的 For Each）块中的语句会更改其循环访问的集合。](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> 为 null 的 Nullable\<T\> 转换为 T  
 [通过无效强制转换引发 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [避免错误的强制转换引发 InvalidOperationException](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 如果将 <xref:System.Nullable%601>（Visual Basic 中的 `null`）的 `Nothing` 结构强制转换为其基础类型，将引发 <xref:System.InvalidOperationException> 异常。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> 通过无效强制转换引发 InvalidOperationException  
 在此方法中，当 Select 方法将 dbQueryResults 的 null 元素强制转换为 int 时，将引发 <xref:System.InvalidOperationException>。  
  
 **异常消息：**  
  
-   附加信息: 可为空的对象必须具有一个值。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [为 null 的 Nullable&lt;T&gt; 转换为 T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> 避免错误的强制转换引发 InvalidOperationException  
 若要避免 <xref:System.InvalidOperationException>：  
  
-   使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> 属性以仅选择不为 null 的元素。  
  
-   使用其中一种重载的 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> 方法为 null 项提供默认值。  
  
 **Nullable\<T\>.HasValue 示例**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Nullable\<T\>.GetValueOrDefault 示例**  
  
 在本示例中，我们使用 <xref:System.Nullable%601.GetValueOrDefault%28%600%29> 指定一个默认值，此默认值在 `dbQueryResults` 返回的预期值之外。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [为 null 的 Nullable&lt;T&gt; 转换为 T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> 对空集合调用了 System.Linq.Enumerable 方法  
 <xref:System.Linq.Enumerable> 方法 <xref:System.Linq.Enumerable.Aggregate%2A>、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Last%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.First%2A>、<xref:System.Linq.Enumerable.Single%2A> 和 <xref:System.Linq.Enumerable.SingleOrDefault%2A> 对序列执行操作并返回单一结果。  
  
 当序列为空时，这些方法的一些重载会引发 <xref:System.InvalidOperationException> 异常（其他重载则返回 `null` （Visual Basic 中的 `Nothing`））。 当序列包含多个元素时，<xref:System.Linq.Enumerable.SingleOrDefault%2A> 也会引发 <xref:System.InvalidOperationException>。  
  
> [!TIP]
>  本节中讨论的大多 <xref:System.Linq.Enumerable> 方法都是重载方法。 确保你理解你选择的重载行为。  
  
 **异常消息：**  
  
 [Aggregate、Average、Last、Max 和 Min 方法](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [First 和 FirstOrDefault 方法](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Single 和 SingleOrDefault 方法](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Aggregate、Average、Last、Max 和 Min 方法  
  
-   附加信息: 序列不包含任何元素  
  
 **通过 Average 引发 InvalidOperationException**  
  
 在本示例中，当调用 <xref:System.InvalidOperationException> 方法时，以下方法将引发 <xref:System.Linq.Enumerable.Average%2A>，因为 Linq 表达式返回一个序列，该序列中不存在大于 4 的元素。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 在不检查空序列的情况下使用这些方法中的一种时，你默认假设该序列为空且空序列是意外的匹配项。 当假设序列不为空时，可以捕捉或引发异常。  
  
 **避免由空序列引发的 InvalidOperationException**  
  
 使用 <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> 方法之一检查序列是否为空。  
  
> [!TIP]
>  如果要平均的序列可能包含大量元素或如果生成该序列的操作十分昂贵，则使用 <xref:System.Linq.Enumerable.Any%2A> 可提高此检查的性能。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [对空集合调用了 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> First 和 FirstOrDefault 方法  
 <xref:System.Linq.Enumerable.First%2A> 返回序列中的第一项，如果序列为空，则引发 <xref:System.InvalidOperationException>。  你可以调用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法而非 <xref:System.Linq.Enumerable.First%2A> 以返回特定值或默认值，避免引发异常。  
  
> [!NOTE]
>  在 .NET Framework 中，类型具有默认值的概念。 例如，对于任何引用类型，默认值为 null，而整型的默认值为零。 请参见[默认值表](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **通过 First 引发 InvalidOperationException**  
  
 <xref:System.Linq.Enumerable.First%2A> 是一种优化方法，它返回满足指定条件的序列的第一个元素。 如果找不到满足条件的元素，这些方法将引发 <xref:System.InvalidOperationException> 异常。  
  
 在本示例中，`First` 方法引发异常，因为 `dbQueryResults` 不包含大于 4 的元素。  
  
 **异常消息：**  
  
-   附加信息: 序列不包含任何匹配元素  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **避免 FirstOrDefault 引发的异常**  
  
 你可以使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法之一替代 <xref:System.Linq.Enumerable.First%2A> 检查 `firstNum` 序列是否包含至少一个元素。 如果查询找不到满足条件的元素，它将返回指定值或默认值。 你可以检查返回值，确定是否找到任何元素。  
  
> [!NOTE]
>  如果类型的默认值是序列中的有效元素，则要实现使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 可能更为复杂。  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [对空集合调用了 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Single 和 SingleOrDefault 方法  
 <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> 方法返回序列的唯一元素，或者序列中满足指定测试的唯一元素。  
  
 如果序列中不存在元素，或者序列中有多个元素，该方法将引发 <xref:System.InvalidOperationException> 异常。  
  
 当序列不包含任何元素时，可以使用 <xref:System.Linq.Enumerable.SingleOrDefault%2A> 返回指定值或默认值以避免引发异常。 但是，如果序列包含多个与选定谓词匹配的元素，<xref:System.Linq.Enumerable.SingleOrDefault%2A> 仍会引发 <xref:System.InvalidOperationException>。  
  
> [!NOTE]
>  在 .NET Framework 中，类型具有默认值的概念。 例如，对于任何引用类型，默认值为 null，而整型的默认值为零。 请参见[默认值表](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **通过 Single 引发 InvalidOperationException**  
  
 在本示例中，`singleObject` 引发 <xref:System.InvalidOperationException>，因为 `dbQueryResults` 不包含大于 4 的元素。  
  
 **异常消息：**  
  
-   附加信息: 序列不包含任何匹配元素  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **通过 Single 或 SingleOrDefault 引发 InvalidOperationException**  
  
 在本示例中，`singleObject` 引发 <xref:System.InvalidOperationException>，因为 `dbQueryResults` 包含多个大于 2 的元素。  
  
 **异常消息：**  
  
-   附加信息: 序列包含一个以上的匹配元素  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **避免 Single 引发的 InvalidOperationException**  
  
 使用 <xref:System.Linq.Enumerable.Single%2A> 和 <xref:System.Linq.Enumerable.SingleOrDefault%2A> 也可作为对你目的的记录。<xref:System.Linq.Enumerable.Single%2A> 强烈暗示，在该条件下你预计仅返回一个结果。<xref:System.Linq.Enumerable.SingleOrDefault%2A> 声明你预计返回一个或零个结果，但不会有更多。 当这些条件无效时，可以引发或捕捉 <xref:System.InvalidOperationException>。 但是，如果你预计这些无效的条件将以某种频率发生，你应该考虑使用其他 <xref:System.Linq.Enumerable> 方法（如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Where%2A>）来生成你的结果。  
  
 开发过程中，你可以使用其中一种 <xref:System.Diagnostics.Debug.Assert%2A> 方法来核实你的假设。 在本示例中，突出显示的代码导致调试器在开发期间中断进程并显示一个断言对话框。 该断言在发行代码中被删除，如果结果无效，则将引发 <xref:System.Linq.Enumerable.Single%2A>。  
  
> [!NOTE]
>  使用 <xref:System.Linq.Enumerable.Take%2A> 并将其 `count` 参数设定为 2 会使返回的序列数目最多包含两个元素。 此序列包含你需要检查的所有情况（0 个、1 个和多个元素），并且当序列可能包含大量元素或生成的序列很昂贵时，它可以改善检查的性能。  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 如果你希望避免异常的同时仍在发行代码中处理无效状态，你可以修改上述技巧。 在此示例中，方法对应于 switch 语句中 `moreThan2` 返回的元素数目。  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [对空集合调用了 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> 相关文章  
 [异常设计准则（.NET Framework 设计准则）](http://msdn.microsoft.com/library/ms229014)  
  
 [处理和引发异常（.NET Framework 应用程序要点）](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [如何：接收首次异常通知（.NET Framework 开发指南）](http://msdn.microsoft.com/library/Dd997368)  
  
 [如何：处理 PLINQ 查询中的异常（.NET Framework 开发指南）](http://msdn.microsoft.com/library/Dd460712)  
  
 [托管线程中的异常（.NET Framework 开发指南）](http://msdn.microsoft.com/library/ms228965)  
  
 [异常和异常处理（C\# 编程指南）](http://msdn.microsoft.com/library/ms173160)  
  
 [异常处理语句（C\# 参考）](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally 语句 \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [异常处理 \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [C\+\+\/CLI 中的异常](http://msdn.microsoft.com/library/Hh875008)  
  
 [异常处理（任务并行库）](http://msdn.microsoft.com/library/Dd997415)  
  
 [异常处理（调试）](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [演练：处理并发异常（在 Visual Studio 中访问数据）](http://msdn.microsoft.com/library/ms171936)  
  
 [如何：处理因数据绑定而发生的错误和异常（Windows 窗体）](http://msdn.microsoft.com/library/k26k86tb)  
  
 [处理网络应用 \(XAML\) 中的异常 \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [本文内容](#BKMK_In_this_article)