# APP development--Calculator*

## Layout design

设计的界面布局如图所示，采用GridLayout网格布局进行排列。

![](D:\Sustech\2022Spring\InnovativeExperiment\report\proj1\QQ图片20220313160108.png)

页面布局的代码如下

```java
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:paddingBottom="10dp"
    android:paddingLeft="10dp"
    android:paddingRight="10dp"
    android:paddingTop="10dp"
    tools:context="com.example.lenovo.project1_calculator.MainActivity">

    <EditText
        android:id="@+id/et_result"
        android:layout_width="match_parent"
        android:layout_height="107dp"
        android:layout_gravity="right"
        android:gravity="bottom"
        android:textSize="20sp" />

    <GridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:columnCount="4"
        android:paddingBottom="5dp"
        android:paddingLeft="20dp"
        android:paddingTop="5dp"
        android:rowCount="5">

        <Button
            android:id="@+id/btn_clear"
            android:text="AC"
            android:background="@drawable/bg"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:textSize="30sp" />

        <Button
            android:id="@+id/btn_left"
            android:text="("
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:textSize="30sp" />

        <Button
            android:id="@+id/btn_right"
            android:text=")"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:textSize="30sp" />
        <Button
            android:id="@+id/btn_divide"
            android:text="÷"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:textSize="30sp" />
        <Button
            android:id="@+id/btn_7"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="7"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_8"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="8"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_9"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="9"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_mul"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="×"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_4"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="4"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_5"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="5"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_6"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="6"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_min"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="−"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_1"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="1"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_2"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="2"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_3"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="3"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_add"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="+"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_backspace"
            android:text="←"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:textSize="30sp" />

        <Button
            android:id="@+id/btn_0"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="0"
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_dot"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="."
            android:textSize="25sp" />

        <Button
            android:id="@+id/btn_equal"
            android:layout_width="80dp"
            android:layout_height="75dp"
            android:background="@drawable/bg"
            android:text="="
            android:textSize="25sp" />

    </GridLayout>


</LinearLayout>

```



## Logic Implementation

### basic design ideas

计算器逻辑的实现主要通过 `Calculate` 方法实现，该方法由 `=` 按钮驱动，其余按键只改变计算器显示界面所呈现的字符串内容。

在 `Calculate` 方法中实现将字符串转化为算术表达式进行运算，并输出最终的结果。这是本次计算器逻辑设计的核心和关键所在，该函数将实现基本的异常处理，即在遇到错误输入格式时，不进行运算，提示错误信息；以及正确计算出正确输入的算术表达式的结果。该部分将在 `basic requirement` 部分展示；

此外，在设计程序的过程中遇到的一些影响计算答案准确性的一些问题，例如精度丢失、数据溢出等问题，以及尽可能的提高程序效率、运算速度的问题将在 `improved development` 中进行讨论。

### basic requirement

#### 字符串修正

对于符合算术表达式的字符串再根据人们使用的习惯以及程序的逻辑进行修正。

`.` 点号的修正：例如，在运算式`1-.3`将其修正为`1-0.3`，而对于`1+2.2`不做修正；即将点号前后为非数字或为空的情况在此前做添零操作。

`-`负号的修正：例如，在运算式`-3+2`将其修正为`0-3+2`,而对于`2-3`不做修正；即将负号前为非数字或为空的情况下在此前做添零操作。

```java
    public String rectify(String str) {
        String patternString1 = "\\.";
        String patternString2 = "\\-";
        String insertString = "0";
        StringBuilder sb = new StringBuilder(str);
        sb.insert(0, " ");
        sb.append(" ");
        String str1 = sb.toString();
        StringBuilder sb1 = new StringBuilder(str1);
        Pattern p1 = Pattern.compile(patternString1);
        Matcher m1 = p1.matcher(str1);
        int offset1 = 0;
        while (m1.find()) {
            if (flag(str1.charAt(m1.start() - 1)) != 0) {
                sb1.insert(m1.start() + offset1, insertString);
                offset1++;
                if (flag(str1.charAt(m1.start() + 1)) != 0) {
                    sb1.insert(m1.start() + 1 + offset1, insertString);
                    offset1++;
                }
            } else if (flag(str1.charAt(m1.start() + 1)) != 0) {
                sb1.insert(m1.start() + 1 + offset1, insertString);
                offset1++;
            }
        }

        String str2 = sb1.toString();
        StringBuilder sb2 = new StringBuilder(str2);
        Pattern p2 = Pattern.compile(patternString2);
        Matcher m2 = p2.matcher(str2);
        int offset2 = 0;
        while (m2.find()) {
            if (flag(str2.charAt(m2.start() - 1)) != 0) {
                sb2.insert(m2.start() + offset2, insertString);
                offset2++;
            }
        }
        String result = sb2.toString();
        result = result.substring(1, result.length() - 1);
        return result;
    }

```

#### 异常处理-合法性检测

在计算结果之前，需要提前对字符串进行一个算术表达式的合法检测，对于不符合规则的运算式，返回错误信息，以节约计算的空间；

分为以下几种情况进行讨论：

一、若字符串为空，返回空字符串；

二、算术表达式不合法

1.左括号与右括号不匹配；

2.出现连续运算符；

3.运算符出现在字符串的头或尾；

```java
   public int ExprValid(String ex) {//1表示合法，0表示语法错误
        int valid = 1;
        if (flag(ex.charAt(0)) == OP || flag(ex.charAt(ex.length() - 1)) == OP) {
            valid = 0;
        } else {
            Stack<Character> match = new Stack<>();
            for (int i = 0; i < ex.length() - 1; i++) {
                if (flag(ex.charAt(i)) == flag(ex.charAt(i + 1)) && flag(ex.charAt(i)) == OP) {
                    valid = 0;
                    break;
                }
                if (ex.charAt(i) == '(') {
                    if (ex.charAt(i + 1) == ')') {
                        valid = 0;
                        break;
                    }
                    match.push(ex.charAt(i));
                } else if (ex.charAt(i) == ')') {
                    if (match.empty()) {
                        valid = 0;
                        break;
                    } else if (match.peek() == '(') {
                        match.pop();
                    }
                }

            }
            if (ex.charAt(ex.length() - 1) == '(') {
                match.push(ex.charAt(ex.length() - 1));
            } else if (ex.charAt(ex.length() - 1) == ')') {
                if (match.empty()) {
                    valid = 0;
                } else if (match.peek() == '(') {
                    match.pop();
                }
            }
            if (!match.empty()) {
                valid = 0;
            }
        }
        return valid;
    }

```

#### 计算过程-逆波兰表达式

日常使用的计算表达式为中缀表达式，即二元运算符总是位于两个对象之间。但是这种表示方法对于人来说比较好理解，但对于计算机来说并不好理解。

将中缀表达式转化为后缀表达式，创建两个stack,分别用于存储数值元素和符号元素，具体操作如下：

> 1、从左往右扫描中缀表达式。
>
> 2、如果是数字那么将其直接入栈到**Nums**中。
>
> 3、如果是操作符，需要进一步判断:
>
> （1）如果是左括号'('直接入栈到**Ops**中。
>
> （2）如果是运算符（'+'、'-'、'*'、'/'），如果是空栈那么直接入栈到**Ops** ;如果栈顶是运算符，且栈顶运算符的优先级大于该运算符,那么将栈顶的运算符出栈，并入栈到**Nums**;如果栈顶运算符优先级小于该运算符，那么直接将该运算符入栈到**Ops**中。
>
> （3）如果是右括号')'，在表达式合法的前提下，将**Ops**中的运算符依次出栈，并入栈到**Nums**中，直到遇到左括号'('。

然后进行后缀表达式的计算

> 对储存的后缀表达式的栈**Nums**从**栈底到栈顶**开始扫描，创建另一个数组**result_array**。
>
> 1、如果是数字，那么直接添加到**result_array**之中。
>
> 2、如果是运算符，将**result_array**末尾的两个数字出栈（考虑到运算符加、减、乘、除都是双目运算符，只需要两个操作数），出栈后对两个数字进行相应的运算，并将运算结果加入**result_array**；

代码实现：

```java
  public String PexpretoSexpre(String ex) {
        Stack<Object> Nums = new Stack<>();
        Stack<Object> Ops = new Stack<>();
        int NumStart = 0;
        int NumEnd = 0;
        char temp_char = ' ';
        for (int i = 0; i < ex.length(); i++) {
            temp_char = ex.charAt(i);
            if (flag(temp_char) != 0 && flag(temp_char) != 1) {
                NumEnd = i;
                if (flag(ex.charAt(NumStart)) == 0 && NumEnd > NumStart) {
                    BigDecimal temp_num = new BigDecimal(ex.substring(NumStart, NumEnd));
                    Nums.push(temp_num);
                }
                NumStart = i + 1;
                switch (temp_char) {
                    case '+':
                    case '-':
                    case '×':
                    case '÷': {
                        if (Ops.empty()) {
                            Ops.push(temp_char);
                        } else if (priority((Character) Ops.peek()) <= priority(temp_char)) {
                            Ops.push(temp_char);
                        } else if (priority((Character) Ops.peek()) > priority(temp_char)) {
                            Nums.push(Ops.peek());
                            Ops.pop();
                            Ops.push(temp_char);
                        }
                        break;
                    }
                    case '(': {
                        Ops.push(temp_char);
                        break;
                    }
                    case ')': {
                        while ((Character) Ops.peek() != '(') {
                            Nums.push(Ops.peek());
                            Ops.pop();
                        }
                        Ops.pop();
                        break;
                    }
                    default: {

                    }

                }
            }

        }

        if (NumStart < ex.length() && flag(ex.charAt(NumStart)) == 0) {
            BigDecimal temp_num = new BigDecimal(ex.substring(NumStart, ex.length()));
            Nums.push(temp_num);
        }
        while (!Ops.empty()) {
            Nums.push(Ops.peek());
            Ops.pop();
        }
        //中缀转后缀
        ArrayList<Object> Num_array = new ArrayList<>(Nums);
        ArrayList<BigDecimal> result_array = new ArrayList<>();
        int index_array = 0;
        for (int i = 0; i < Num_array.size(); i++) {
            if (Num_array.get(i) instanceof BigDecimal) {
                result_array.add((BigDecimal) Num_array.get(i));
                index_array++;
            } else if (Num_array.get(i) instanceof Character) {
                switch ((Character) Num_array.get(i)) {
                    case '+': {
                        result_array.set(index_array - 2, result_array.get(index_array - 1).add(result_array.get(index_array - 2)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '-': {
                        result_array.set(index_array - 2, result_array.get(index_array - 2).subtract(result_array.get(index_array - 1)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '×': {
                        result_array.set(index_array - 2, result_array.get(index_array - 1).multiply(result_array.get(index_array - 2)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '÷': {
                        if(result_array.get(index_array-1).compareTo(BigDecimal.ZERO) == 0){
                            return "Math Error";
                        }
                        result_array.set(index_array - 2, result_array.get(index_array - 2).divide(result_array.get(index_array - 1), 8, BigDecimal.ROUND_HALF_UP));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }

                }
            }
        }

        return result_array.get(0).toString();

    }
```

其中对于被除数为零的情形，返回”Math Error“;

最终的code放于页末。

### improved development

#### 使用BigDemical解决浮点数精度丢失问题

**double**和**float**都是浮点数类型。在计算机中采用二进制进行存储。

浮点数在内存中的存储方式，其原理就是将浮点数通过用尾数和指数来表示。 即 a = m × b^e（其中a表示为浮点数，m为尾数，b为选取的基数，e是指数） 

**float**数据类型长度为32位，其中最高位为符号位，中间8位为指数位，最后23位作为尾数位。而**double** 数据类型长度为64位，与**float**类似，但指数位扩展到11位，尾数位也扩展到52位。**float**表示范围为 (-3.4E+38)~(3.4E+38)，**float**的精度由其尾数位来控制，它的尾数位可以表示最大的数为2^23-1，故 **float**最多能够表示小于8388607的小数点后7位，**double**表示范围与其原理相近似，但它的精度最高位扩展到了16位。

尽管如此，两者表示小数的个数都是有限的，对于总个数为无穷的小数，很多情形下是无法精确表示的。而计算器的设计有一个重要要求为精确性，在一些情形下**float**和**double**存在精度丢失问题，甚至在某些特殊运算表达式中，会造成很严重的误差放大。

为了更加精确表示，java提供了**BigDecimal类**来解决浮点数精度丢失的问题。

> BigDecimal的高精度的原理：浮点型数值运算时发生精度丢失的原因是，在二进制存储中，整数部分其存储单元并非相连的，而是随着数值的增大，存储位置也在变大，这样在整数运算中由于二进制占有的部分的增多，就会导致其出现运算误差，但如果将其小数部分转换成整数，通过整数进行运算，其占用存储空间又会变为整数的存储，这样连续的存储单元在运算时不会发生精度丢失。

但是值得注意的是，通过**String**类型构造的**BigDecimal类**是精准的，建议使用**String**类型进行构造。

#### 使用大数算法解决数据溢出问题

在计算某些比较大的值时，特别是乘法运算，可能会使结果超出int或者long所能够表示的范围，从而导致数据溢出。

如![](D:\Sustech\2022Spring\InnovativeExperiment\report\proj1\QQ图片20220313130919.png)

该大数相乘的算法具体如下，以`23*41`为例；

1.将23和41倒序存入两个数组中： array1: {3 ,2} array2: {1,4} 

2.按照列竖式做乘法的规则就有3* 1个1，（3* 4+2* 1）个10和2* 4个100 

3.将他们存在array3:{3,14,8} 然后再进行进位得到{3，4，9} 

4.所得数组倒序得到运算结果943 

```c++
string result(string m ,string n){
bool sign = false;
string out = "";
if(m[0] == '-'){
m.erase(0,1);
sign = (1-sign);
}
if(n[0] == '-'){
n.erase(0,1);
sign = (1-sign);
}
if(sign){
out = "-";
}
long long int l1 = m.length();
long long int l2 = n.length();
int a[l1] = {0};
int b[l2] = {0};
int result[l1+l2] = {0};
long long int index = 0;
for(int i = l1 - 1, j = 0; i >= 0; i--, j++){
a[j] = m[i] - '0';
}
for(int i = l2 - 1, j = 0; i >= 0; i--, j++){
b[j] = n[i] - '0';
}
for(int i = 0; i < l1; i++){
for(int j = 0; j < l2; j++){
result[i + j] += a[i] * b[j];
}
}
for(int i = 0; i < (l1+l2); i++){
if(result[i] > 9){
result[i+1] += result[i]/10;
result[i] %= 10;
}
}
for(int i = l1+l2-1; i > 0; i--){
if(result[i] != 0){
index = i;
break;
}
}
for(int i = index; i >= 0; i--){
out += to_string(result[i]);
}
return out;
}
```

### Evaluation of results

该设计可以处理只含有数字、`+`,`-`,`×`,`÷`，`(`,`)`的算术式。

1.能够判断算术式的合理性，如`(1+3))*5`返回`Syntax Error`

2.对于小数点的某些式子能够计算，如`1+.2 = 1.2`

3.计算含负数的形式的表达式。

4.对于被除数为零的表达式，返回`Math Error`

### Residual issues

由于时间等诸多方面的限制，该计算器的实现仍然存在一下几个方面的问题，亟待解决

1.使用BigDemical类进行迭带运算时，且运算包含除法运算时，可能会出现精度丢失的问题。例如`3*3.3/(1+8)`，这是由于在除法运算时，对BigDemical进行了四舍五入，保留小数的操作。

2.由于时间限制，未能够将大数乘法成功应用于该算法中，主要在于与BigDemical的冲突导致，一个在于精度，另一个则是数据大小溢出的情况；可能需要切换mode进行安排。

### Reference

1.[逆波兰表达式——中缀表达式转后缀表达式 - 蓝海人 - 博客园 (cnblogs.com)](https://www.cnblogs.com/lanhaicode/p/10776166.html)

2.[(77条消息) 用Java进行算数表达式的运算(合法性、负数运算、多位数运算)_小于学编程.的博客-CSDN博客](https://blog.csdn.net/weixin_50600369/article/details/122420307?ops_request_misc=%7B%22request%5Fid%22%3A%22164708409916780269827682%22%2C%22scm%22%3A%2220140713.130102334.pc%5Fall.%22%7D&request_id=164708409916780269827682&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-122420307.pc_search_result_control_group&utm_term=算术表达式合法性判断java&spm=1018.2226.3001.4187)

3.[(71条消息) Java运算如何确保精度(BigDecimal)_醺泽的博客-CSDN博客_bigdecimal如何保证精度的](https://blog.csdn.net/qq_45722267/article/details/113307053?ops_request_misc=%7B%22request%5Fid%22%3A%22164714101216781685375903%22%2C%22scm%22%3A%2220140713.130102334.pc%5Fall.%22%7D&request_id=164714101216781685375903&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-113307053.pc_search_result_control_group&utm_term=bigdecimal实现连续运算精度丢失&spm=1018.2226.3001.4187)

4.[(71条消息) C++ 大数相乘算法_吴斌的博客-CSDN博客_c++大数乘法](https://blog.csdn.net/weixin_41376979/article/details/79197186)

### Code

```java
package com.example.lenovo.project1_calculator;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.text.TextUtils;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import java.math.BigDecimal;
import java.util.ArrayList;
import java.util.Stack;
import java.util.regex.Matcher;
import java.util.regex.Pattern;


public class MainActivity extends AppCompatActivity {

    private Button btn_0,btn_1,btn_2,btn_3,btn_4,btn_5,btn_6,btn_7,btn_8,btn_9,btn_dot;
    private Button btn_add,btn_min,btn_mul,btn_divide;
    private Button btn_left,btn_right;
    private Button btn_clear,btn_backspace,btn_equal;
    private EditText result;
    double num1,num2,num_result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //get component
        btn_0 = findViewById(R.id.btn_0);
        btn_1 = findViewById(R.id.btn_1);
        btn_2 = findViewById(R.id.btn_2);
        btn_3 = findViewById(R.id.btn_3);
        btn_4 = findViewById(R.id.btn_4);
        btn_5 = findViewById(R.id.btn_5);
        btn_6 = findViewById(R.id.btn_6);
        btn_7 = findViewById(R.id.btn_7);
        btn_8 = findViewById(R.id.btn_8);
        btn_9 = findViewById(R.id.btn_9);
        btn_add = findViewById(R.id.btn_add);
        btn_min = findViewById(R.id.btn_min);
        btn_mul = findViewById(R.id.btn_mul);
        btn_divide = findViewById(R.id.btn_divide);
        btn_left = findViewById(R.id.btn_left);
        btn_right = findViewById(R.id.btn_right);
        btn_clear = findViewById(R.id.btn_clear);
        btn_backspace = findViewById(R.id.btn_backspace);
        btn_dot = findViewById(R.id.btn_dot);
        btn_equal = findViewById(R.id.btn_equal);
        result = findViewById(R.id.et_result);
        //click event
        btn_0.setOnClickListener(new Click());
        btn_1.setOnClickListener(new Click());
        btn_2.setOnClickListener(new Click());
        btn_3.setOnClickListener(new Click());
        btn_4.setOnClickListener(new Click());
        btn_5.setOnClickListener(new Click());
        btn_6.setOnClickListener(new Click());
        btn_7.setOnClickListener(new Click());
        btn_8.setOnClickListener(new Click());
        btn_9.setOnClickListener(new Click());
        btn_add.setOnClickListener(new Click());
        btn_min.setOnClickListener(new Click());
        btn_mul.setOnClickListener(new Click());
        btn_divide.setOnClickListener(new Click());
        btn_left.setOnClickListener(new Click());
        btn_right.setOnClickListener(new Click());
        btn_clear.setOnClickListener(new Click());
        btn_backspace.setOnClickListener(new Click());
        btn_dot.setOnClickListener(new Click());
        btn_equal.setOnClickListener(new Click());
    }
    class Click implements View.OnClickListener {
        String temp;
        @Override
        public void onClick(View view) {
        switch (view.getId()){
            case R.id.btn_0:
                temp = result.getText().toString();
                temp += "0";
                result.setText(temp);
                break;
            case R.id.btn_1:
                temp = result.getText().toString();
                temp += "1";
                result.setText(temp);
                break;
            case R.id.btn_2:
                temp = result.getText().toString();
                temp += "2";
                result.setText(temp);
                break;
            case R.id.btn_3:
                temp = result.getText().toString();
                temp += "3";
                result.setText(temp);
                break;
            case R.id.btn_4:
                temp = result.getText().toString();
                temp += "4";
                result.setText(temp);
                break;
            case R.id.btn_5:
                temp = result.getText().toString();
                temp += "5";
                result.setText(temp);
                break;
            case R.id.btn_6:
                temp = result.getText().toString();
                temp += "6";
                result.setText(temp);
                break;
            case R.id.btn_7:
                temp = result.getText().toString();
                temp += "7";
                result.setText(temp);
                break;
            case R.id.btn_8:
                temp = result.getText().toString();
                temp += "8";
                result.setText(temp);
                break;
            case R.id.btn_9:
                temp = result.getText().toString();
                temp += "9";
                result.setText(temp);
                break;
            case R.id.btn_dot:
                temp = result.getText().toString();
                temp += ".";
                result.setText(temp);
                break;
            case R.id.btn_add:
                temp = result.getText().toString();
                temp += "+";
                result.setText(temp);
                break;
            case R.id.btn_min:
                temp = result.getText().toString();
                temp += "-";
                result.setText(temp);
                break;
            case R.id.btn_mul:
                temp = result.getText().toString();
                temp += "×";
                result.setText(temp);
                break;
            case R.id.btn_divide:
                temp = result.getText().toString();
                temp += "÷";
                result.setText(temp);
                break;
            case R.id.btn_left:
                temp = result.getText().toString();
                temp += "(";
                result.setText(temp);
                break;
            case R.id.btn_right:
                temp = result.getText().toString();
                temp += ")";
                result.setText(temp);
                break;
            case R.id.btn_clear:
                temp = "";
                result.setText(temp);
                break;
            case R.id.btn_backspace:
                temp = result.getText().toString();
                temp =temp.substring(0,temp.length()-1);
                result.setText(temp);
                break;
            case R.id.btn_equal:
                temp = result.getText().toString();
                if (! TextUtils.isEmpty(temp) ){

                if(NonDoubleDot(temp)){
                    temp = rectify(temp);
                    if(ExprValid(temp) == 1){
                        temp =PexpretoSexpre(temp);
                        result.setText(temp);
                    }
                    else {
                         result.setText("Syntax Error");
                    }
                }
                else {
                    result.setText("Syntax Error");
                }
                }
                break;
            default:
                break;

        }
        }
    }

    public final int NUM = 0;//0-9,
    public final int DOT = 1;//.
    public final int OP = 2;//+,-,cheng,chu
    public final int BRACKET = 3;//()
    public final int FIRST = 5;
    public final int SECOND = 4;

    public int flag(char c) {
        if (Character.isDigit(c)) {
            return NUM;
        } else if (c == '.') {
            return DOT;
        } else if (c == '+' || c == '-' || c == '×' || c == '÷') {
            return OP;
        } else {
            return BRACKET;
        }
    }

    public int priority(char c) {

        if (c == '×' || c == '÷') {
            return FIRST;
        }
        if (c == '+' || c == '-') {
            return SECOND;
        } else
            return -1;
    }

    public boolean NonDoubleDot(String str) {
        boolean result = true;
        for (int i = 0; i < str.length() - 1; i++) {
            if (str.charAt(i) == '.' && str.charAt(i + 1) == '.') {
                result = false;
                break;
            }
        }
        return result;
    }

    public String rectify(String str) {
        String patternString1 = "\\.";
        String patternString2 = "\\-";
        String insertString = "0";
        StringBuilder sb = new StringBuilder(str);
        sb.insert(0, " ");
        sb.append(" ");
        String str1 = sb.toString();
        StringBuilder sb1 = new StringBuilder(str1);
        Pattern p1 = Pattern.compile(patternString1);
        Matcher m1 = p1.matcher(str1);
        int offset1 = 0;
        while (m1.find()) {
            if (flag(str1.charAt(m1.start() - 1)) != 0) {
                sb1.insert(m1.start() + offset1, insertString);
                offset1++;
                if (flag(str1.charAt(m1.start() + 1)) != 0) {
                    sb1.insert(m1.start() + 1 + offset1, insertString);
                    offset1++;
                }
            } else if (flag(str1.charAt(m1.start() + 1)) != 0) {
                sb1.insert(m1.start() + 1 + offset1, insertString);
                offset1++;
            }
        }

        String str2 = sb1.toString();
        StringBuilder sb2 = new StringBuilder(str2);
        Pattern p2 = Pattern.compile(patternString2);
        Matcher m2 = p2.matcher(str2);
        int offset2 = 0;
        while (m2.find()) {
            if (flag(str2.charAt(m2.start() - 1)) != 0) {
                sb2.insert(m2.start() + offset2, insertString);
                offset2++;
            }
        }
        String result = sb2.toString();
        result = result.substring(1, result.length() - 1);
        return result;
    }

    public int ExprValid(String ex) {//1表示合法，0表示语法错误
        int valid = 1;
        if (flag(ex.charAt(0)) == OP || flag(ex.charAt(ex.length() - 1)) == OP) {
            valid = 0;
        } else {
            Stack<Character> match = new Stack<>();
            for (int i = 0; i < ex.length() - 1; i++) {
                if (flag(ex.charAt(i)) == flag(ex.charAt(i + 1)) && flag(ex.charAt(i)) == OP) {
                    valid = 0;
                    break;
                }
                if (ex.charAt(i) == '(') {
                    if (ex.charAt(i + 1) == ')') {
                        valid = 0;
                        break;
                    }
                    match.push(ex.charAt(i));
                } else if (ex.charAt(i) == ')') {
                    if (match.empty()) {
                        valid = 0;
                        break;
                    } else if (match.peek() == '(') {
                        match.pop();
                    }
                }

            }
            if (ex.charAt(ex.length() - 1) == '(') {
                match.push(ex.charAt(ex.length() - 1));
            } else if (ex.charAt(ex.length() - 1) == ')') {
                if (match.empty()) {
                    valid = 0;
                } else if (match.peek() == '(') {
                    match.pop();
                }
            }
            if (!match.empty()) {
                valid = 0;
            }
        }
        return valid;
    }


    public String PexpretoSexpre(String ex) {
        Stack<Object> Nums = new Stack<>();
        Stack<Object> Ops = new Stack<>();
        int NumStart = 0;
        int NumEnd = 0;
        char temp_char = ' ';
        for (int i = 0; i < ex.length(); i++) {
            temp_char = ex.charAt(i);
            if (flag(temp_char) != 0 && flag(temp_char) != 1) {
                NumEnd = i;
                if (flag(ex.charAt(NumStart)) == 0 && NumEnd > NumStart) {
                    BigDecimal temp_num = new BigDecimal(ex.substring(NumStart, NumEnd));
                    Nums.push(temp_num);
                }
                NumStart = i + 1;
                switch (temp_char) {
                    case '+':
                    case '-':
                    case '×':
                    case '÷': {
                        if (Ops.empty()) {
                            Ops.push(temp_char);
                        } else if (priority((Character) Ops.peek()) <= priority(temp_char)) {
                            Ops.push(temp_char);
                        } else if (priority((Character) Ops.peek()) > priority(temp_char)) {
                            Nums.push(Ops.peek());
                            Ops.pop();
                            Ops.push(temp_char);
                        }
                        break;
                    }
                    case '(': {
                        Ops.push(temp_char);
                        break;
                    }
                    case ')': {
                        while ((Character) Ops.peek() != '(') {
                            Nums.push(Ops.peek());
                            Ops.pop();
                        }
                        Ops.pop();
                        break;
                    }
                    default: {

                    }

                }
            }

        }

        if (NumStart < ex.length() && flag(ex.charAt(NumStart)) == 0) {
            BigDecimal temp_num = new BigDecimal(ex.substring(NumStart, ex.length()));
            Nums.push(temp_num);
        }
        while (!Ops.empty()) {
            Nums.push(Ops.peek());
            Ops.pop();
        }
        //中缀转后缀
        // System.out.println(Nums);
        ArrayList<Object> Num_array = new ArrayList<>(Nums);
        ArrayList<BigDecimal> result_array = new ArrayList<>();
        int index_array = 0;
        for (int i = 0; i < Num_array.size(); i++) {
            if (Num_array.get(i) instanceof BigDecimal) {
                result_array.add((BigDecimal) Num_array.get(i));
                index_array++;
            } else if (Num_array.get(i) instanceof Character) {
                switch ((Character) Num_array.get(i)) {
                    case '+': {
                        result_array.set(index_array - 2, result_array.get(index_array - 1).add(result_array.get(index_array - 2)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '-': {
                        result_array.set(index_array - 2, result_array.get(index_array - 2).subtract(result_array.get(index_array - 1)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '×': {
                        result_array.set(index_array - 2, result_array.get(index_array - 1).multiply(result_array.get(index_array - 2)));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }
                    case '÷': {
                        if(result_array.get(index_array-1).compareTo(BigDecimal.ZERO) == 0){
                            return "Math Error";
                        }
                        result_array.set(index_array - 2, result_array.get(index_array - 2).divide(result_array.get(index_array - 1), 8, BigDecimal.ROUND_HALF_UP));
                        result_array.remove(index_array - 1);
                        index_array--;
                        break;
                    }

                }
            }
        }

        return result_array.get(0).toString();

    }


}

```

