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

## Shell 字符串

### 单引号

```shell
str='this is a  string'
str1='noob'
str2='hello,'$str''
str3='hello,${str1}'
```

- 单引号里的任何字符都会原样输出，变量也是无效的
- 单引号字串里面不能出现一个单独的单引号(即使是使用转义符号), 但可以成对出现，作为字符串拼接使用

### 双引号

```shell
str1="noob"
str"hello,i know your are \"$str1\"! \n"
echo -e $str
```

- 