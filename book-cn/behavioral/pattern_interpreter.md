# Interpreter模式

解释器模式(Interpreter Pattern): 给定一个语言，定义它的文法的一种表示，并定义一个解释器，这个解释器使用该表示来解释语言中的句子。

Interpreter模式属于行为型模式。行为型模式涉及到算法和对象间职责的分配；行为型模式不仅描述对象或类的模式，还描述它们之间的通信模式。行为型模式刻划了在运行时难以跟踪的复杂的控制流；它们将你的注意力从控制流转移到对象间的联系方式上来。行为型模式主要包括：Chain of Responsibility模式、Command模式、Interpreter模式、Iterator模式、Mediator模式、Memento模式、Observer模式、State模式、Strategy模式、Template Method模式和Visitor模式。行为型模式在某种程度上具有相关性。

## 模式简介

GOF的《设计模式》指出Interpreter模式的意图是：  
给定一个语言，定义它的文法的一种表示，并定义一个解释器，这个解释器使用该表示来解释语言中的句子。

如果一种特定类型的问题发生的频率足够高 , 那么可能就值得将该问题的各个实例表述为一个简单语言中的句子。这样就可以构建一个解释器, 该解释器通过解释这些句子来解决该问题。

Interpreter模式适用于以下场景：

- 当有一个语言需要解释执行, 并且你可将该语言中的句子表示为一个抽象语法树时，可使用解释器模式。
- 该文法简单对于复杂的文法, 文法的类层次变得庞大而无法管理。此时语法分析程序生成器这样的工具是更好的选择。它们无需构建抽象语法树即可解释表达式, 这样可以节省空间而且还可能节省时间。
- 最高效的解释器通常不是通过直接解释语法分析树实现的, 而是首先将它们转换成另一种形式。例如，正则表达式通常被转换成状态机。

## 模式图解

Interpreter模式的UML示例如下：

![Interpreter模式示例](../images/behavioral_interpreter.jpg)

Interpreter模式的工作过程如下：

- AbstractExpression类声明一个抽象的解释操作，这个接口为抽象语法树中所有的节点所共享。
- TerminalExpression类实现与文法中的终结符相关联的解释操作。
- NonTerminalExpression类.文法中的所有规则{R1...R2},均包含NonTerminalExpression实例，并维护AbstractExpression的指针，解释器(Interpreter)递归地调用表示R1到Rn的那些对象的解释操作。
- Context类包含解释器之外的一些全局信息。
- Client类构建表示该文法定义的语言中一个特定的句子的抽象语法树。该抽象语法树由NonTerminalExpression和TerminalExpression的实例装配而成。
- 每一节点的解释操作用上下文来存储和访问解释器的状态。

Interpreter模式的有益效果如下：

- 易于扩展文法：该模式使用类来表示文法规则 , 你可使用继承来改变或扩展该文法。
- 易于实现文法：定义抽象语法树中各个节点的类的实现大体类似。可以用编译器或语法分析程序生成器自动生成。
- 复杂的文法难以维护：解释器模式为文法中的每一条规则至少定义了一个类。
- 易于扩展解释器解释新的表达式。

Composite模式: 抽象语法树是一个复合模式的实例。Flyweight模式：说明了如何在抽象语法树中共享终结符。Iterator模式：解释器可用一个迭代器遍历该结构。Visitor模式：可用来在一个类中维护抽象语法树中的各节点的行为。

## 模式实例

[TODO]

## 系列文章

- [CSDN专栏: 设计模式(UML/23种模式)](https://blog.csdn.net/column/details/27399.html)
- [Github专栏: 设计模式(UML/23种模式)](https://github.com/media-tm/MTDesignPattern)

## 参考文献

- [GOF的设计模式：可复用面向对象软件的基础](http://item.jd.com/10057319.html)
- [设计模式之禅](http://item.jd.com/11414555.html)
- [图说设计模式](https://github.com/me115/design_patterns)