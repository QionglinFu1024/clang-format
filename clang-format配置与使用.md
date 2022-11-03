# clang-format配置与使用

## 安装步骤：

1、安装clang-format

```ruby
brew install clang-format
```

查看是否安装成功

```ruby
clang-format --version
```

2、添加自动化服务

![1.png](https://devfutao.com/usr/uploads/2022/02/2280749423.png)

选择快速操作

![2.png](https://devfutao.com/usr/uploads/2022/02/2233056075.png)

将shell拖拽到右侧

![3.png](https://devfutao.com/usr/uploads/2022/02/1720226373.png)

添加内容并勾选，**保存**并命名为`CodeFormat`

![4.png](https://devfutao.com/usr/uploads/2022/02/2701569200.png)

```ruby
export PATH=/usr/local/bin:$PATH
clang-format
```

查看文件保存的位置：

```ruby
open ~/Library/Services
```

3、创建 `.clang-format` 文件并放到根目录

创建 `.clang-format` 文件：

```ruby
touch .clang-format
```

`.clang-format` 文件内容：

```ruby
# 工具 https://github.com/mapbox/XcodeClangFormat(需要添加签名使用)
# 函数名详细地址 英文 http://clang.llvm.org/docs/ClangFormatStyleOptions.html
# 函数名详细地址 中文 https://www.cnblogs.com/PaulpauL/p/5929753.html

# OC语言
Language: ObjC

# 基于LLVM格式
# BasedOnStyle: LLVM

# 对齐注释
AlignTrailingComments: true

# 指针和引用的对齐方式
PointerAlignment: Right

# 用于缩进的列数
IndentWidth: 4

# 针对OC的block的缩进宽度
ObjCBlockIndentWidth: 4

# OC的block嵌套参数不换行
ObjCBreakBeforeNestedBlockParam: false

# switch的case缩进
IndentCaseLabels: true

# OC里面，在@property后加空格
ObjCSpaceAfterProperty: true

# 括号中的(),{},[]代码对齐方式
AlignAfterOpenBracket: Align

#ContinuationIndentWidth: 0

# 赋值=对齐
AlignConsecutiveAssignments: false

# 声明参数对齐
AlignConsecutiveDeclarations: false

# 运算符位置
BreakBeforeBinaryOperators: None

# 如果为真（true）, 三元运算符将被放置在换行后
BreakBeforeTernaryOperators: false

# 总是在逗号和对齐逗号跟冒号前把构造函数初始化式换行
BreakConstructorInitializersBeforeComma: false

# 允许短的函数放在同一行
#AllowShortFunctionsOnASingleLine: None

# 允许case在同一行
AllowShortCaseLabelsOnASingleLine: false

# OC里面，在Protocol前后加空格
ObjCSpaceBeforeProtocolList: true

# 单行注释前的空格数
SpacesBeforeTrailingComments: 1

# 连续的空行保留几行
MaxEmptyLinesToKeep: 2

# 保留block里面的空行
KeepEmptyLinesAtTheStartOfBlocks: false

# 每行字符的限制，0表示没有限制
ColumnLimit: 0

# []中添加空格
SpacesInSquareBrackets: false

# ()中添加空格
SpacesInParentheses : false

# @[]里面两边空格，默认true
SpacesInContainerLiterals: false

# 赋值运算符前加空格
SpaceBeforeAssignmentOperators: true

# 在空括号中加空格
SpaceInEmptyParentheses: false

# 在<>中间插入空格
SpacesInAngles: false

# 换行的时候对齐操作符
AlignOperands: true

# 允许if在同一行
AllowShortIfStatementsOnASingleLine: true

# 允许while在同一行
AllowShortLoopsOnASingleLine: false

# 允许将简单的语句块放到同一行
AllowShortBlocksOnASingleLine: true

#缩进函数名
IndentWrappedFunctionNames: false

# 形参 如果为false要么都在同一行，要么各有一行
BinPackParameters: false

# 实参 如果为false要么都在同一行，要么各有一行
BinPackArguments: false

# 大括号换行
BreakBeforeBraces: Custom
BraceWrapping:
  # class定义后面
  AfterClass: true
  # 控制语句后面
  AfterControlStatement: false
  # enum定义后面
  AfterEnum: false
  # 函数定义后面
  AfterFunction: false
  # 命名空间定义后面
  AfterNamespace: false
  # struct定义后面
  AfterStruct: false
  # union定义后面
  AfterUnion: false
  # catch之前
  BeforeCatch: false
```

打开根目录

```ruby
open ~
```

4、设置快捷键：
系统偏好->键盘->快捷键->app快捷键->选择Xcode->设置快捷键按钮

![image-20221102104026409](/Users/bear/Library/Application Support/typora-user-images/image-20221102104026409.png)

5、查看效果：

快捷键按钮方式：重新打开Xcode->选中需要格式化的代码->按下之前设置的快捷键按钮
手动选择方式：选中需要格式化的代码->右键->`Services`->`CodeFormat`
![check.png](https://devfutao.com/usr/uploads/2022/07/2459538858.png)

## 可能出现的问题

1. clang-format, bash 命令未找到

   需要修改bash_profile文件，添加运行路径。具体为vim ~/.bash_profile, 在文件内添加clang-format存放路径，保存后退出。 source ~/.bash_profile

2. zsh:2: command not found: clang-format

   ```shell
   cp -R /opt/homebrew/Cellar/clang-format/14.0.6/bin/clang-format /usr/local/bin
   ```

