# C#语言简介
C#（发音为“C sharp”）是一种现代的、面向对象的编程语言，主要用于开发Windows平台上的应用程序，也可用于跨平台开发。
C# 是一种编译型语言，它需要通过编译器将源代码转换为可以运行的目标代码。

# C#程序基本语法结构
```csharp
using System; // 引用命名空间

namespace HelloWorld // 定义命名空间
{
    class Program // 定义类
    {
        static void Main(string[] args) // 主方法，程序入口
        {
            Console.WriteLine("Hello, World!"); // 输出语句
            Console.WriteLine("welcome to C Sharp studying.");
            Console.Write("are you ok?");
            Console.Write("I'm fine.\n");
            Console.WriteLine("sum:" + (3 + 5));
        }
    }
}
```

# 类和对象
**类和对象是面向对象编程（OOP）中的两个基本概念，它们是构建软件应用程序的核心。**
- 1. 类（Class）
    类是对象的模板或蓝图，是对一类事物的抽象描述。它定义了对象的属性（成员变量）和行为（方法或函数）。可以理解为类是一个“类型”，它描述了对象应具备什么特性和功能，但类本身不占用内存，只有创建对象时才会分配内存。
    - **类的主要组成**：
        - 字段（Field）：类中的变量，通常用来描述对象的属性。
        - 方法（Method）：类中的函数或操作，定义对象的行为。
        - 构造函数（Constructor）：用于初始化对象的一种特殊方法。
        - 属性（Property）：为类中的字段提供一种更灵活的访问方式，通常包含 get 和 set 访问器。它提供了对类内部字段（通常是私有字段）的访问控制机制。通过属性，我们可以控制字段的读取和修改权限，通常通过 get 和 set 方法来实现。
    ```csharp
        public class Car
        {
            // 字段
            public string Model;
            public string Color;
            
            // 构造函数
            public Car(string model, string color)
            {
                Model = model;
                Color = color;
            }
            
            // 方法
            public void Drive()
            {
                Console.WriteLine("The car is driving.");
            }
        }
    ```

- 2. 对象（Object）
    对象是类的实例。类只是一个模板，而对象是通过这个模板实际创建的实例。对象在内存中占有空间，它包含类中定义的字段，并且能够执行类中定义的方法。每个对象都有自己独立的状态。
    ```csharp
    Car myCar = new Car("Tesla Model 3", "Red");  // 创建一个 Car 类型的对象
    myCar.Drive();  // 调用对象的方法
    ```
## 类和对象的关系
    类：是对象的蓝图，定义了对象应该有什么样的属性和行为。
    对象：是类的实例，类的实际表现形式。每个对象都占有内存，拥有自己的属性和方法。

# C#编译
## C#编译过程
1. 源代码编写
2. 将源代码编译成中间语言 (IL)
    使用 C# 编译器（csc）将代码编译为中间语言（Intermediate Language，简称 IL）。
    输出的文件是 .exe 或 .dll 文件，这是一种二进制形式，称为程序集（Assembly）。
3. 运行时解析（CLR 执行）
    在程序运行时，.NET 的公共语言运行时（Common Language Runtime，简称 CLR）会将 IL 转换为目标平台的机器代码。
    机器代码直接与操作系统和硬件交互，从而完成程序的实际执行。

 - 注意：
    1. 什么是 .exe 文件？
        .exe 是 可执行文件（Executable File）。
        通常用于生成独立运行的应用程序，双击即可执行。
        适用于控制台应用程序或Windows桌面应用程序。    
        - 特点：
            入口点：包含 Main 方法，程序从此处开始执行。
            独立性：可以直接运行，但可能依赖其他 .dll 文件。
            目标：通常生成一个最终的应用程序供用户使用。
            平台限制：特定于操作系统（如 Windows 的 .exe 文件不能直接运行在 Linux 或 macOS 上）。
        - 适用场景：
            创建一个完整的程序，例如：
                控制台应用程序。
                桌面应用程序。
                服务程序（如 Windows 服务）。
        - 生成.exe文件操作:
          - 1.1 创建一个项目
            1. 打开 Visual Studio。
            2. 点击 文件 -> 新建 -> 项目。
            3. 在项目模板中选择以下类型之一(这些会生成 .exe):
                控制台应用程序(Console App,适合命令行程序)。
                Windows 窗体应用程序(Windows Forms App)。
                WPF 应用程序（适合桌面应用程序）。
                确保项目类型为 Console App 或其他可执行类型。
            4. 编写代码
            5. 填写项目名称和保存位置，点击 创建。
            6. 点击 生成 -> 生成解决方案
            7. 编译完成后：
                在项目文件夹的 bin\Debug 或 bin\Release 目录下可以找到 .exe 文件。
    2. 什么是 .dll 文件？
        .dll 是 动态链接库(Dynamic Link Library)。
        用于存储共享代码，不能直接运行。
        通常用作被其他程序调用的库，可以包含一组功能、类或逻辑。
        - 特点：
            无入口点：没有 Main 方法，不能单独执行。
            共享性：可以被多个 .exe 或其他 .dll 文件引用和调用。
            模块化：支持代码复用，便于将应用程序拆分为多个模块。
            跨项目使用：可以将功能封装为库，供多个项目共享。
        - 适用场景：
            封装逻辑或功能模块，例如：
                工具库。
                第三方 API(如 Newtonsoft.Json.dll)。
                插件系统中的插件模块。
        - 生成.dll文件操作:
            1. 打开 Visual Studio。
            2. 点击 文件 -> 新建 -> 项目。
            3. 在项目模板中选择 类库(Class Library)。
                如果是 .NET Framework,请选择 类库 (.NET Framework)。
                如果是 .NET Core 或 .NET 6/7,请选择 类库 (.NET)。
            4. 填写项目名称和保存位置，点击 创建。
            5. 编写代码，添加要封装的逻辑。
            6. 点击 生成 -> 生成解决方案。

## C# 编译模式
  - 1. Debug 模式
    用于开发阶段，生成包含调试信息的程序集。
    - 优点：
        包含丰富的调试信息（例如变量、行号）。
        更容易定位错误。
    - 缺点：
        性能稍差，不适合用于发布。
  - 2. Release 模式
    用于发布阶段，生成优化后的程序集。
    - 优点：
        性能更优。
        体积更小。
    - 缺点：
        调试信息减少，不适合排查复杂问题。
        