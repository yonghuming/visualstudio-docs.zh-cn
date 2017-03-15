---
title: "Visual C++ 2015 Update 2 中的重大更改 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Visual C++ 2015 Update 2 中的重大更改
当升级到 Visual C\+\+ 2015 Update 2 CTP 后，之前编译并正常运行的代码中可能会出现编译和\/或运行时错误。 编译器和运行时行为中会引起这类问题的更改称为*重大更改*，通常，修改 C\+\+ 语言标准、函数签名或内存中的对象布局时需要进行这种更改。  
  
 本文的其余部分介绍了 Visual C\+\+ 2015 Update 2 CTP 中具体的重大更改，并且在本文中，术语“新行为”或“现在”均指该版本。 术语“旧行为”和“早前\/之前”指 Visual C\+\+ 2015 Update 1 和早期版本。 有关 Visual C\+\+ 2015 初始版本和 Visual C\+\+ 2015 Update 1 之间的重大更改的详细信息，请参阅 [更新 1 中的重大更改](../misc/breaking-changes-in-visual-cpp-2015-update-1.md)。 有关 Visual C\+\+ 2013和 Visual C\+\+ 2015 之间的重大更改的详细信息，请参阅 [Visual C\+\+ 2015 中的重大更改](/visual-cpp/porting/visual-cpp-change-history-2003-20151)。  
  
-   [编译器的重大更改](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 编译器  
  
-   **可能会因对表达式 SFINAE 的部分支持而发出其他警告和错误**  
  
     由于缺少对表达式 SFINAE 的支持，编译器的早期版本未能分析 `decltype` 说明符中特定类型的表达式。 这种旧行为不正确，也不符合 C\+\+ 标准。 由于持续的一致性改进，此编译器现已可分析这些表达式，并能为表达式 SFINAE 提供部分支持。 因此，此编译器现在可发出在编译器的早期版本无法分析的表达式中找到的警告和错误。  
  
     这一新行为分析包含尚未声明类型的 `decltype` 表达式时，将导致编译器发出编译器错误 C2039。  
  
 **错误 C2039：*“type”*：不是*“global namespace”*的成员**     示例 1：使用未声明的类型（之前）  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     示例 1（之后）  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     当这一新行为分析 `decltype` 表达式时（该表达式缺少将依赖名称指定为类型所必须使用的关键字 `typename`），编译器将发出编译器警告 C4346 和编译器错误 C2923。  
  
 **警告 C4346：*'S2\<T\>::Type'*：依赖名称不是类型 错误 C2923：对参数 *“T”* 而言，*“s1”*:*“S2\<T\>::Type”*不是有效的模版类型参数**     示例 2：依赖名称不是类型（之前）  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     示例 2（之后）  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile` **成员变量将防止出现隐式定义的构造函数和赋值运算符**  
  
     编译器的早期版本允许具有 `volatile` 成员变量的类自动生成默认复制\/移动构造函数和默认复制\/移动赋值运算符。 这种旧行为不正确，也不符合 C\+\+ 标准。 编译器现在认为拥有可变成员变量的类具有非常用构造函数和赋值运算符，这将防止自动生成这些运算符的默认实现。  当此类为某一联合（或类中的匿名联合）的成员时，会将联合（或包含匿名联合的类）的复制\/移动构造函数和复制\/移动赋值运算符的隐式定义为已删除。 尝试构造或复制联合（或包含匿名联合的类）而不显式定义它们是错误的，将导致编译器发出编译器错误 C2280。  
  
 **错误 C2280：*“B::B\(const B &\)”*：尝试引用已删除的函数**     示例（之前）  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     示例（之后）  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **静态成员函数不支持 cv 限定符。**  
  
     Visual C\+\+ 2015 的早期版本允许静态成员函数具有 cv 限定符。 此行为是由于 Visual C\+\+ 2015 和 Visual C\+\+ 2015 Update 1 中的回归而导致的；Visual C\+\+ 2013 和 Visual C\+\+ 的早期版本拒绝接受以这种方式编写的代码。 Visual C\+\+ 2015 和 Visual C\+\+ 2015 Update 1 的行为不正确且不符合 C\+\+ 标准。  Visual Studio 2015 Update 2 拒绝接受以这种方式编写的代码，并改为发出编译器错误 C2511。  
  
 **错误 C2511：“void A::func\(void\) const”：在“A”中找不到重载成员函数**     示例（之前）  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     示例（之后）  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **WinRT 代码中不允许枚举的前向声明**（仅影响 \/ZW）  
  
     为 Windows 运行时 \(WinRT\) 编译的代码不允许前向声明 `enum` 类型，这与使用 \/clr 编译器开关为 .Net Framework 编译托管 C\+\+ 代码时相似。 此行为可确保枚举大小始终为已知，并可将其正确映射到 WinRT 类型系统。 编译器将拒绝接受以这种方式编写的代码，并发出编译器错误 C2599 和编译器错误 C3197。  
  
 **错误 C2599：*“CustomEnum”*：不允许 WinRT 枚举的前向声明 错误 C3197：*“public”*：只能在定义中使用**     示例（之前）  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     示例（之后）  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **重载的非成员运算符 new 和运算符 delete 可能不是以内联方式声明的**（默认开启等级 1 \(\/W1\)）  
  
     当以内联方式声明非成员运算符 new 和运算符 delete 函数时，编译器的早期版本不会发出警告。 以这种方式编写的代码格式不正确（无需诊断），并且可能由于不匹配的 new 和 delete 运算符（尤其是与调整了大小的释放共同使用时）而导致难以诊断的内存问题。   编译器现将发出编译器警告 C4595 以帮助识别以这种方式编写的代码。  
  
 **警告 C4595：*“operator new”*：无法以内联方式声明非成员运算符 new 或 delete 函数**     示例（之前）  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     修复以这种方式编写的代码可能需要将运算符定义从头文件移动到相应的源文件中。