# shell

- [shell](#shell)
  - [运行方式](#运行方式)
  - [变量](#变量)
    - [定义](#定义)
    - [使用](#使用)
    - [只读变量](#只读变量)
    - [删除变量](#删除变量)
    - [变量类型](#变量类型)
    - [Shell 字符串](#shell-字符串)
      - [单引号](#单引号)
      - [双引号](#双引号)
      - [获取字符串长度](#获取字符串长度)
      - [提取子字符串](#提取子字符串)
      - [查找子字符串](#查找子字符串)
    - [shell 数组](#shell-数组)
      - [数组定义](#数组定义)
      - [读取数组](#读取数组)
      - [获取数组的长度](#获取数组的长度)
      - [获取数组中的所有元素](#获取数组中的所有元素)
    - [shell 注释](#shell-注释)
  - [Shell 的传递参数](#shell-的传递参数)
  - [shell的运算符](#shell的运算符)
    - [算术运算符](#算术运算符)
    - [关系运算符](#关系运算符)
    - [布尔运算符](#布尔运算符)
    - [逻辑运算符](#逻辑运算符)
    - [字符串运算符](#字符串运算符)
    - [文件测试运算符](#文件测试运算符)
  - [Shell echo命令](#shell-echo命令)
  - [Shell printf命令](#shell-printf命令)
  - [Shell test命令](#shell-test命令)
  - [流程控制](#流程控制)
  - [Shell 函数](#shell-函数)
  - [Shell 输入/输出重定向](#shell-输入输出重定向)
  - [Shell 文件包含](#shell-文件包含)

## 运行方式

- 方式一：作为可执行程序

```shell
chmod +x ./test.sh
./test.sh
```

- 方式二：作为解释器参数

```shell
/bin/sh test.sh
```

## 变量

### 定义

```shell
var="hello world"
```

- 等号左右不能有空格
- 已经定义的变量可以被重新定义

### 使用

- 在变量名之前加上美元符号
- 可以在变量外加上花括号，帮助辨识

```shell
my_name="liude"
echo $my_name
echo ${my_name}
```

### 只读变量

- **readonly**命令可以将变量定义为只读变量，其值不能改变
- 只读变量不能被删除

```shell
readonly myUrl
```

### 删除变量

- **unset**

```shell
unset var
```

### 变量类型

1. **局部变量**
2. **环境变量**
3. **shell 变量**

### Shell 字符串

#### 单引号

```shell
str='this is a  string'
str1='noob'
str2='hello,'$str''
str3='hello,${str1}'
```

- 单引号里的任何字符都会原样输出，变量也是无效的
- 单引号字串里面不能出现一个单独的单引号(即使是使用转义符号), 但可以成对出现，作为字符串拼接使用

#### 双引号

```shell
str1="noob"
str"hello,i know your are \"$str1\"! \n"
echo -e $str
```

- 双引号之中可以有变量
- 双引号里可以出现转义字符

#### 获取字符串长度

```shell
string="abcd"
echo ${#string} #变量为数组时 ${#string}等价${#string[0]}
```

#### 提取子字符串

```shell
string="hello world"
echo ${string:1:4} #第一个字符索引为0
```

#### 查找子字符串

```shell
string="hello wrold"
echo `expr index "$string" io` # ` 是反引号
```

### shell 数组

#### 数组定义

```shell
array_name=(value0,value2......)

array_name=(
    value0
    value1
    ....
)

array_name[0]=value0
array_name[1]=value1
array_name[n]=valuen
```

#### 读取数组

```shell
valuen=${array_name[n]}
```

- 使用`@`符号可以获取数组的所有元素

```shell
echo ${array_name[@]}
```

#### 获取数组的长度

- 与获取字符串长度相同

```shell
length=${#array_name[@]} #获取数组元素个数
length=${#arrar_name[*]}
length=${#array_name[n]} #获取数组单个元素的长度
```

#### 获取数组中的所有元素

- 使用 '@' '*'
```shell
echo "数组的元素为：${my_array[*]}"
echo "数组的元素为：${my_array[@]}"
```

### shell 注释

```shell
#单行注释
```

## Shell 的传递参数

- 脚本内获取参数的格式是: **$n** n 代表数字
  - n 为 0：代表执行的文件名(包含文件路径)
  - n 为 1，2，3.....:依次代表第一，二，三，....个参数

```shell
echo "文件名: $0"
echo "第一个参数: $1"
echo "第二个参数: $2"
echo "第三个参数: $3"
echo "第四个参数: $4"
```

| 参数处理字符 | 说明                                     |
| ------------ | ---------------------------------------- |
| $#           | 传到脚本的参数个数                       |
| $\*          | 以一个单字符串显示所有向脚本传递的参数。 |
| $$           | 脚本运行的当前进程ID号|
| $!           | 后台运行的最后一个进程的id号|
| $@           | 返回所有的参数，以单个的形式|
| $-           | 显示Shell使用的当前选项，与set命令相同|
| $?           | 显示最后命令的退出状态,0代表没有错误|

## shell的运算符

- 原生bash不支持简单的数学运算，可以通过其他命令来实现如'awk','expr'

```shell
val = `expr 2 + 2`
echo "两数之和为：$val"
```

- 注意是使用的是 **``** 反引号，不是 **''** 单引号,且表达式要被反引号完整包住
- 表达式和运算符之间要有空格

### 算术运算符

### 关系运算符

### 布尔运算符

### 逻辑运算符

### 字符串运算符

### 文件测试运算符

## Shell echo命令

## Shell printf命令

## Shell test命令

## 流程控制

## Shell 函数

## Shell 输入/输出重定向

## Shell 文件包含