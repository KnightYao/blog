# linux 动态库的符号冲突问题
### 最近，给同事定位了一个符号表的冲突问题，简单记录一下。
### A代码作为静态链接库，被包含进了B代码，然后编译成了动态链接库B.so， A代码同时作为静态链接库，被编译进入了main的主代码。main函数调用B.so里面的函数，同时B.so里面的函数调用了A代码，结果进程异常退出了。

### 查看符号表，发现调用的A代码，其实运行的是直接编译进入main主函数的代码，而不是B.so里面包含的A代码。

### 而且比较凑巧的是，符号名称是相同的，但是代码逻辑却不相同，由于是arm的嵌入式单板，所有的空间被设置成了只读，导致无法生成core文件，还花了几个小时去分析。

### 那么，怎么避免这种情况？
### 1.如果我们要求so文件优先使用自己的库文件内的符号，需要在编译时使用-Wl,-Bsymbolic参数，这是个链接参数，会被传递给连接器ld使用，告诉so，优先使用库内符号。
### 2.我们还要考虑我们自身库的符号先得到加载的话，不会去覆盖其他库或者程序的符号，因此这里需要将不必导出的符号进行隐藏，只导出外部需要使用的符号。
### 3.这里我们在编译时使用-fvisibility=hidden参数来隐藏符号，但是只这样的话会把库内的所有的符号都隐藏了，包括调用者需要的函数，于是我们在需要导出的的函数和变量前加上 __attribute__ ((visibility ("default")))属性，这样就可以使用导出的函数了。