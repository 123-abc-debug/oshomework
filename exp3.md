
Task
Lear shell programming by following the instructions inshell script.pdf
Please use shel to traverse the contents of a folder andrename the files inside according to certain rules.


一、实验目的
掌握 Shell 脚本的基本结构与执行方式。
学会定义和使用 Shell 变量（ scalar 变量与数组变量）。
熟悉 Shell 支持的算术运算符、布尔运算符和关系运算符的使用。
理解并运用 Shell 决策语句（if...else、case...esac）和循环语句（for 循环）。
掌握 Shell 输出重定向功能的使用方法。


三、实验内容与步骤
（一）Shell 脚本基础结构与执行
新建文本文件，命名为test_basic.sh，在文件中编写如下脚本：
sh
#!/bin/sh
# Author: 实验者姓名
# 脚本功能：获取用户输入并输出问候语
echo "What is your name?"
read PERSON
echo "Hello, $PERSON"
保存文件后，通过命令chmod +x test_basic.sh为脚本添加执行权限。
在终端中执行脚本./test_basic.sh，输入姓名并观察输出结果，记录运行过程与最终输出。
（二）Shell 变量的定义与使用
1. 标量变量的定义与访问
创建脚本test_scalar.sh，内容如下：
sh
#!/bin/sh
# 定义标量变量
NAME="Zara Ali"
VAR2=100
# 访问变量值并输出
echo "Name: $NAME"
echo "Number: $VAR2"
赋予执行权限后运行脚本，观察变量值的输出结果，验证标量变量的存储与访问功能。
2. 数组变量的定义与访问
创建脚本test_array.sh，内容如下：
sh
#!/bin/sh
# 定义数组变量
NAME[0]="Zara"
NAME[1]="Qadir"
NAME[2]="Mahnaz"
NAME[3]="Ayan"
NAME[4]="Daisy"
# 访问数组元素并输出
echo "First Index: ${NAME[0]}"
echo "Second Index: ${NAME[1]}"
echo "Third Index: ${NAME[2]}"
echo "All Elements: ${NAME[@]}"  # 输出数组所有元素
运行脚本，观察数组元素的输出结果，理解数组变量的索引访问和批量访问方式。
（三）Shell 运算符的使用
创建脚本test_operators.sh，内容如下：
sh
#!/bin/sh
# 定义测试变量
a=10
b=20

# 算术运算符测试
echo "Arithmetic Operators:"
echo "a + b = $(expr $a + $b)"
echo "a - b = $(expr $a - $b)"
echo "a * b = $(expr $a \* $b)"  # 注意乘法运算符需转义
echo "b / a = $(expr $b / $a)"
echo "b % a = $(expr $b % $a)"

# 关系运算符测试
echo -e "\nRelational Operators:"
[ $a -eq $b ] && echo "$a -eq $b : True" || echo "$a -eq $b : False"
[ $a -ne $b ] && echo "$a -ne $b : True" || echo "$a -ne $b : False"
[ $a -gt $b ] && echo "$a -gt $b : True" || echo "$a -gt $b : False"
[ $a -lt $b ] && echo "$a -lt $b : True" || echo "$a -lt $b : False"

# 布尔运算符测试
echo -e "\nBoolean Operators:"
[ ! $a -eq $b ] && echo "! (a == b) : True" || echo "! (a == b) : False"
[ $a -lt 20 -o $b -gt 100 ] && echo "a < 20 -o b > 100 : True" || echo "a < 20 -o b > 100 : False"
[ $a -lt 20 -a $b -gt 100 ] && echo "a < 20 -a b > 100 : True" || echo "a < 20 -a b > 100 : False"
运行脚本，对比输出结果与预期，验证各类运算符的功能正确性。
（四）Shell 决策语句的应用
1. if...elif...else 语句
创建脚本test_if.sh，内容如下：
sh
#!/bin/sh
# 输入一个数字，判断其大小范围
echo "Enter a number:"
read NUM
if [ $NUM -gt 100 ]; then
    echo "The number is greater than 100"
elif [ $NUM -eq 100 ]; then
    echo "The number is equal to 100"
else
    echo "The number is less than 100"
fi
运行脚本，分别输入大于 100、等于 100 和小于 100 的数字，观察判断结果是否正确。
2. case...esac 语句
创建脚本test_case.sh，内容如下：
sh
#!/bin/sh
# 输入字符，判断其类型
echo "Enter a character (a-z, A-Z, 0-9):"
read CHAR
case $CHAR in
    [a-z]) echo "You entered a lowercase letter";;
    [A-Z]) echo "You entered an uppercase letter";;
    [0-9]) echo "You entered a digit";;
    *) echo "Invalid character";;
esac
运行脚本，输入不同类型的字符，验证 case 语句的分支匹配功能。
（五）Shell for 循环的使用
创建脚本test_for.sh，内容如下：
sh
#!/bin/sh
# 循环输出数字列表
echo "Numbers 0-9:"
for var in 0 1 2 3 4 5 6 7 8 9
do
    echo $var
done

# 循环输出指定格式的文件
echo -e "\nFiles starting with .bash in home directory:"
for FILE in $HOME/.bash*
do
    echo $FILE
done
运行脚本，观察数字的循环输出结果和家目录下.bash开头的文件列表，理解 for 循环对列表项的遍历功能。
（六）输出重定向的使用
在终端中执行如下命令，将who命令的输出重定向到users.txt文件：
sh
who > users.txt
执行cat users.txt命令，查看文件内容，验证重定向是否成功。
执行如下命令，覆盖users.txt文件内容：
sh
echo "line1" > users.txt
再次查看users.txt文件，观察内容变化，理解输出重定向的覆盖特性。
四、实验结果与分析
记录每个脚本的运行命令、输入数据（若有）和输出结果，整理成表格形式。
分析实验过程中遇到的问题及解决方法，例如脚本执行权限不足、运算符使用错误、语法格式错误等。
验证 Shell 脚本各功能模块（变量、运算符、流程控制、重定向）的实际效果是否与理论预期一致。
五、实验总结
总结本次实验中掌握的 Shell 脚本核心知识点，包括变量定义、运算符使用、流程控制语句和输出重定向。
反思实验过程中的难点与易错点，例如 Shell 语法中空格的要求、运算符的转义、数组的访问格式等。
简述 Shell 脚本在 Unix/Linux 系统中的应用场景，以及本次实验对后续学习的帮助。



任务内容一：学习 Shell 脚本编程

你需要根据提供的文档 《shell script.pdf》 来学习 Shell 编程的基础内容。
（文档一般会包含变量、if、for、while、函数、文件操作等基础知识。）

任务内容二：编写一个 Shell 脚本程序

你要自己写一个 Shell 脚本，实现以下功能：

✔ 使用 Shell 遍历某个文件夹（目录）

也就是用脚本自动读取目录中的所有文件，例如：

for file in /path/to/folder/*
do
    ...
done

✔ 按照“某种规则”重命名目录中的文件

“某种规则”一般包括以下几类，你可以任选一种或按老师要求来写：

给所有文件加上前缀（如 file → new_file）

给所有文件加上序号（如 img1.jpg、img2.jpg …）

替换文件名中的某些字符

统一改为小写/大写

统一扩展名（如 *.TXT → *.txt）

例如，将目录中的文件依次改名为：

file_1.jpg
file_2.jpg
file_3.jpg


或者：

2025_原文件名

任务目的（报告需要写）

理解并掌握 Shell 脚本的基本语法

学会操作文件、遍历文件夹

学会使用脚本批量处理文件（如自动重命名）
