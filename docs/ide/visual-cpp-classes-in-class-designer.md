---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

类设计器支持 C\+\+ 类，并使用与可视化 Visual Basic 和 Visual C\# 类形状相同的方法可视化本地 C\+\+ 类，只不过 C\+\+ 类可以具有多重继承关系。  可以展开类形状以显示类中的更多字段和方法，也可以折叠类形状以节省空间。  
  
> [!NOTE]
>  类设计器不支持联合（一种特殊类型的类，在其中仅分配联合的最大数据成员所需的内存量）。  
  
## 简单继承  
 当您将多个类拖动到类关系图上，且这些类之间具有类继承关系时，将用箭头连接这些类。  箭头指向基类的方向。  例如，当类关系图中显示以下类时，将用一个箭头连接这些类，并且从 B 指向 A：  
  
```  
class A {};  
class B : A {};  
```  
  
 也可以仅将类 B 拖动到类关系图上，再右击 B 的类形状，然后单击**“显示基类”**。  这将显示其基类：A。  
  
## 多重继承  
 类设计器支持对多个类的继承关系进行可视化。  当派生类具有多个基类的特性时，将使用多重继承。  下面是多重继承的示例：  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 当您将多个类拖动到类关系图上，且这些类之间具有多类继承关系时，将用箭头连接这些类。  箭头指向基类的方向。  
  
 右击类形状，然后单击**“显示基类”**以显示选定类的基类。  
  
> [!NOTE]
>  C\+\+ 代码不支持**“显示派生类”**命令。  可以通过以下方式显示派生类：转到类视图，展开类型节点，展开**“派生类型”**子文件夹，然后将这些类型拖动到类关系图中。  
  
 有关多类继承的更多信息，请参见[多重继承](http://msdn.microsoft.com/zh-cn/3b74185e-2beb-4e29-8684-441e51d2a2ca)和[多个基类](/visual-cpp/cpp/multiple-base-classes)。  
  
## 抽象类  
 类设计器支持抽象类（也称为“抽象基类”）。  这些类无法实例化，但可以从这些类派生其他类。  利用本文档前面“多重继承”部分中的示例，您可以将 `Bird` 类实例化为各个对象，如下所示：  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 但是，您可能并不打算将 `Swimmer` 类实例化为各个对象。  您可能只打算从此类派生其他类型的动物类，例如 `Penguin`、`Whale` 和 `Fish`。  在这种情况下，您会将 `Swimmer` 类声明为抽象基类。  
  
 若要将一个类声明为抽象类，您可以使用 `abstract` 关键字。  标记为抽象成员或包含在抽象类中的成员为虚拟成员，必须通过从该抽象类派生的类实现。  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 您还可以通过包含至少一个纯虚函数将一个类声明为抽象类：  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 当您在类关系图中显示这些声明时，类名 `Swimmer` 及其纯虚函数 `swim` 会以斜体形式显示在抽象类形状中，并带有**“抽象类”**标记。  请注意，抽象类的类型形状与常规类的类型形状相同，只不过其边框为虚线。  
  
 派生自抽象基类的类必须重写基类中的每个纯虚函数，否则无法实例化所派生的类。  因此，举例来说，如果从 `Swimmer` 类派生 `Fish` 类，则 `Fish` 必须重写 `swim` 方法：  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 当您在类关系图中显示此代码时，类设计器会绘制一条从 `Fish` 到 `Swimmer` 的继承连线。  
  
## 匿名类  
 类设计器支持匿名类。  匿名类类型是在未使用标识符的情况下声明的类。  它们不能具有构造函数或析构函数，也不能作为参数传递给函数且不能作为返回值从函数中返回。  可以使用匿名类来替换带有 typedef 名称的类名称，如以下示例中所示：  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 结构也可以是匿名的。  类设计器使用显示其他类型时所使用的相同方式显示匿名类和结构。  虽然您可以声明和显示匿名类和结构，但类设计器将不会使用您指定的标记名称。  它将使用类视图生成的名称。  类或结构在类视图和类设计器中显示为名称为**“\_\_unnamed”**的元素。  
  
 有关匿名类的更多信息，请参见[匿名类类型](/visual-cpp/cpp/anonymous-class-types)。  
  
## 模板类  
 类设计器支持对模板类进行可视化。  支持嵌套的声明。  下表显示了一些典型的声明。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> 模板类|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 模板类|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> 模板类|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 模板类|  
  
 下表显示了部分专用化的一些示例。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 模板类|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> 模板类|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> 模板类|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> 模板类|  
  
 下表显示了部分专用化中的一些继承示例。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> 模板类<br /><br /> `B`<br /><br /> 类<br /><br /> （指向类 A）<br /><br /> `C`<br /><br /> 类<br /><br /> （指向类 A）|  
  
 下表显示了部分专用化模板函数的一些示例。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U\> \(\+ 1 overload\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> 模板类<br /><br /> `B<T2>`<br /><br /> 模板类<br /><br /> （B 包含在**“嵌套类型”**下的类 A 中）|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> 类<br /><br /> \-\> C\<int\><br /><br /> `C<T>`<br /><br /> 模板类|  
  
 下表显示了模板继承的一些示例。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> 类<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> 类<br /><br /> （B 包含在**“嵌套类型”**下的类 C 中）<br /><br /> `C<T>`<br /><br /> 模板类|  
  
 下表显示了规范专用类连接的一些示例。  
  
|代码元素|类设计器视图|  
|----------|------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> 类<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> 类<br /><br /> `C<T>`<br /><br /> 模板类<br /><br /> `D`<br /><br /> 类<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## 请参阅  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [类和结构](/visual-cpp/cpp/classes-and-structs-cpp)   
 [匿名类类型](/visual-cpp/cpp/anonymous-class-types)   
 [多重继承](http://msdn.microsoft.com/zh-cn/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [多个基类](/visual-cpp/cpp/multiple-base-classes)   
 [模板](/visual-cpp/cpp/templates-cpp)