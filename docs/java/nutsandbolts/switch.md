# switch 语句
[[toc]]

不同于 if-then 和 if-then-else 语句，switch 语句可以有多个可能的执行路径。

一个 switch 用 byte，short，char，和 int 原始数据类型。它还可以与枚举类型（讨论 [枚举类型](../javaoo/enum.md)），String 类。以及一些特殊的类来封装某些基本类型： Character、Byte、Short 和 Integer（在讨论 [数字和字符串](../data/)）。

以下代码示例， SwitchDemo 声明一个 int 名称 month 的值表示一个月。代码根据 month 使用该 switch 语句的值显示月份的名称。

```java
public class SwitchDemo {
    public static void main(String[] args) {

        int month = 8;
        String monthString;
        switch (month) {
            case 1:  monthString = "January";
                     break;
            case 2:  monthString = "February";
                     break;
            case 3:  monthString = "March";
                     break;
            case 4:  monthString = "April";
                     break;
            case 5:  monthString = "May";
                     break;
            case 6:  monthString = "June";
                     break;
            case 7:  monthString = "July";
                     break;
            case 8:  monthString = "August";
                     break;
            case 9:  monthString = "September";
                     break;
            case 10: monthString = "October";
                     break;
            case 11: monthString = "November";
                     break;
            case 12: monthString = "December";
                     break;
            default: monthString = "Invalid month";
                     break;
        }
        System.out.println(monthString);
    }
}
```

一个 switch 语句的主体被称为一个开关块。switch 块中的语句可以标记一个或多个 case 或d efault 标签。该 switch 语句评估其表达式，然后执行匹配 case 标签后面的所有语句。

您还可以使用 if-then-else 语句显示月份的名称

```java
int month = 8;
if (month == 1) {
    System.out.println("January");
} else if (month == 2) {
    System.out.println("February");
}
...  // and so on
```

决定是否使用 if-then-else 语句或 switch 语句是基于可读性和语句正在测试的表达式。一个 if-then-else 语句可以测试基于值或条件的范围的表达式，而 switch 语句测试仅基于一个整数，枚举值或表达式 String 对象。

另一个兴趣点是 break 声明。每个 break 语句都会结束封闭 switch 语句。控制流继续跟随该 switch 块后的第一个语句。这些 break 语句是必要的，因为没有这些语句，switch 块中的语句落空：匹配 case 标签之后的所有语句都将按顺序执行，而不管后续 case 标签的表达，直到遇到 break 语句。该程序 SwitchDemoFallThrough 显示一个 switch 块中的语句。该程序显示与 month 年份相关的整数和以下月份的月份：

```java
public class SwitchDemoFallThrough {

    public static void main(String[] args) {
        java.util.ArrayList<String> futureMonths =
            new java.util.ArrayList<String>();

        int month = 8;

        switch (month) {
            case 1:  futureMonths.add("January");
            case 2:  futureMonths.add("February");
            case 3:  futureMonths.add("March");
            case 4:  futureMonths.add("April");
            case 5:  futureMonths.add("May");
            case 6:  futureMonths.add("June");
            case 7:  futureMonths.add("July");
            case 8:  futureMonths.add("August");
            case 9:  futureMonths.add("September");
            case 10: futureMonths.add("October");
            case 11: futureMonths.add("November");
            case 12: futureMonths.add("December");
                     break;
            default: break;
        }

        if (futureMonths.isEmpty()) {
            System.out.println("Invalid month number");
        } else {
            for (String monthName : futureMonths) {
               System.out.println(monthName);
            }
        }
    }
}
```

这是输出

```java
August
September
October
November
December
```

该语句按照 case 的顺序进行判定，直到匹配上，如果没有 break 声明，那么后面的 case 将被直接执行，而不管是否匹配

在技​​术上，最终 break 不是必需的，因为流程不在 switc h声明之内。建议使用 break，以便修改代码更容易，更不容易出错。 default 部分处理其中一个 case 部分未明确处理的所有值。

以下代码示例 SwitchDemo2 显示语句如何具有多个 case 标签。代码示例计算特定月份的天数：

```java
class SwitchDemo2 {
    public static void main(String[] args) {

        int month = 2;
        int year = 2000;
        int numDays = 0;

        switch (month) {
            case 1: case 3: case 5:
            case 7: case 8: case 10:
            case 12:
                numDays = 31;
                break;
            case 4: case 6:
            case 9: case 11:
                numDays = 30;
                break;
            case 2: // 如果是2月则判定当年是否是闰年
                if (((year % 4 == 0) &&
                     !(year % 100 == 0))
                     || (year % 400 == 0))
                    numDays = 29;
                else
                    numDays = 28;
                break;
            default:
                System.out.println("Invalid month.");
                break;
        }
        System.out.println("Number of Days = "
                           + numDays);
    }
}
```

代码输出
```java
Number of Days = 29
```


## 在 switch 中使用 String

在 Java SE 7 及更高版本中，您可以在 switch 语句的表达式中使用 String 对象。以下代码示例， StringSwitchDemo 根据 String 命名的值显示月份的数量 month：

```java
public class StringSwitchDemo {

    public static int getMonthNumber(String month) {

        int monthNumber = 0;

        if (month == null) {
            return monthNumber;
        }

        switch (month.toLowerCase()) {
            case "january":
                monthNumber = 1;
                break;
            case "february":
                monthNumber = 2;
                break;
            case "march":
                monthNumber = 3;
                break;
            case "april":
                monthNumber = 4;
                break;
            case "may":
                monthNumber = 5;
                break;
            case "june":
                monthNumber = 6;
                break;
            case "july":
                monthNumber = 7;
                break;
            case "august":
                monthNumber = 8;
                break;
            case "september":
                monthNumber = 9;
                break;
            case "october":
                monthNumber = 10;
                break;
            case "november":
                monthNumber = 11;
                break;
            case "december":
                monthNumber = 12;
                break;
            default:
                monthNumber = 0;
                break;
        }

        return monthNumber;
    }

    public static void main(String[] args) {

        String month = "August";

        int returnedMonthNumber =
            StringSwitchDemo.getMonthNumber(month);

        if (returnedMonthNumber == 0) {
            System.out.println("Invalid month");
        } else {
            System.out.println(returnedMonthNumber);
        }
    }
}
```

程序输出：8

将表达式 String 与每个标签相关联的 switch 表达式进行比较，case 就像使用该 String.equals 方法一样。为了让 StringSwitchDemo示 例接受任何一个月，无论情况如何，month 都将转换为小写（使用 toLowerCase 方法），并且与 case 标签关联的所有字符串都是小写的。

::: tip
此示例检查 switch 语句中的表达式是否为 null。确保任何 switch 语句中的表达式不为 null 以防止 NullPointerException 抛出。
:::
