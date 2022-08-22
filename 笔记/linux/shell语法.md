# shell

- [shell](#shell)
  - [运行方式](#运行方式)
  - [变量](#变量)
    - [定义](#定义)
    - [使用](#使用)
    - [只读变量](#只读变量)

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