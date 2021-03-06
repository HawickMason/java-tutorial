# 表达式、语句和块
[[toc]]

现在，您了解变量和运算符，现在该了解**表达式、语句和块**。运算符可用于构建表达式，其计算值；表达式是语句的核心组成部分; 语句可以分组成块。

## 表达式
一个**表达式**是变量、运算符和方法调用，他们根据语言的语法，计算结果为单个值，您已经看到了表达式的例子，如下所示：

```java
int cadence = 0;
anArray[0] = 100;
System.out.println("Element 1 at index 0: " + anArray[0]);

int result = 1 + 2; // result is now 3
if (value1 == value2)
    System.out.println("value1 == value2");
```

表达式返回的值的数据类型取决于表达式中使用的元素。该表达式 `cadence = 0` 返回一个 int，因为赋值运算符返回与其左侧操作数相同的数据类型的值；在这种情况下， cadence 是一个 int。从其他表达式可以看出，表达式也可以返回其他类型的值，例如 boolean 或 String。

Java 编程语言允许您从各种较小的表达式构造复合表达式，只要表达式中一部分所需的数据类型与其他表达式的数据类型相匹配。以下是复合表达式的示例：

```java
1 * 2 * 3
```

在这个特定的例子中，表达式被评估的顺序是不重要的，因为乘法的结果不依赖于顺序；结果总是相同的，无论你采用什么顺序进行乘法运算。但是，这并不是所有的表达式。例如，以下表达式给出不同的结果，具体取决于您是否先执行加法或除法操作：

```java
x + y / 100    // 不清晰的
```

你可以使用括号使表达式更清晰

```java
(x+y) / 100 // 明确，推荐
```

如果没有明确指出要执行的操作的顺序，则顺序由分配给表达式中正在使用的操作符的优先级决定。具有较高优先级的运算符首先得到评估。例如，除法运算符的优先级高于加法运算符。因此，以下两个语句是等价的：

```java
x + y / 100


x + (y / 100) // 无歧义，推荐
```

写入复合表达式时，应该是明确的，并用圆括号表示哪些运算符应该先被评估。这种做法使代码更容易阅读和维护。

## 语句

语句大致相当于自然语言中的句子。一个 **语句** 形成一个完整的执行单位。通过用分号（;）终止表达式，可以将以下类型的表达式形成为语句。

* 作业表达式
* 任何使用 ++ 或 --
* 方法调用
* 对象创建表达式

这样的语句叫做 **表达式语句** 。下面是一些表达式语句的例子。

```java
// 赋值语句
aValue = 8933.234;
// 自增语句
aValue++;
// 方法调用语句
System.out.println("Hello World!");
// 对象创建语句
Bicycle myBike = new Bicycle();
```

除表达式语句外，还有另外两种语句：**声明** 语句和 **控制流程** 语句。一个声明语句声明一个变量。你已经看到很多声明语句的例子：

```java
// 声明语句
double aValue = 8933.234;
```

最后，控制流程语句规定语句执行的顺序。您将在下一节 [控制流程语句](./flow.md) 中了解到

## 块
一个 **块是** 大括号之间的一组零个或多个语句，可以在允许单个语句的任何地方使用。以下示例 BlockDemo 说明了块的使用：

```java
class BlockDemo {
     public static void main(String[] args) {
          boolean condition = true;
          if (condition) { // 块1
               System.out.println("Condition is true.");
          } // end block one
          else { // 块2
               System.out.println("Condition is false.");
          } // 块3
     }
}
```
