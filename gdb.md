# gdb 调试

| 命令        | 简写 | 功能                               |
| ----------- | ---- | ---------------------------------- |
| list        | l    | 列出源码                           |
| break       | b    | 设置断点                           |
| run         | r    | 从头看是run程序                    |
| continue    | c    | 从停止处继续run程序                |
| next        | n    | 向前执行一句（不可进入被调用函数） |
| step        | s    | 向前执行一句（可以进入被调用函数） |
| return      | ret  | 从当前函数返回                     |
| print       | p    | 显示变量或者表达式                 |
| x           | x    | 显示内存值                         |
| backtrace   | bt   | 显示调用栈                         |
| quit        | q    | 退出gdb                            |
| symbol-file | sy   | 从可执行文件中加载符号表           |

`info threads`显示当前进程中的线程