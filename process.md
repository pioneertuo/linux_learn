#### 进程的由来
# 程序
- 静态文件
- 
# 进程
- 运行着的实体

# 查看进程之间的关系
- pstree

# 操作系统如何区分进程
- PID:进程的身份证
- 使用 ps -ef 命令来查看进程
- 使用 ps -ef | more   时输出的进程内容只输出一页,不要输出那么多


#### 创建一个进程
# fork函数
头文件：
    #include <unistd.h>
函数原型：
    pid_t fork(void);
返回值：
    成功：子进程0 / 父进程正整数
    失败：-1

# fork函数特性
- 执行fork函数之后，fork函数会返回两次
- 在旧进程中返回时，返回值？
  
# fork函数要点总结
- 在执行fork函数之前，操作系统只有一个进程，fork函数之前的代码只会被执行一次。
- 在执行fork函数之后，操作系统有两个几乎一样的进程，fork函数之后的代码会被执行两次。

#### 子进程偷梁换柱
# exec函数族
- 常用后缀
  l:代表以列表形式传参
  v:代表以矢量数组形式传参(vector)
  p:代表使用环境变量Path来寻找指定执行文件
  e:代表用户提供自定义的环境变量

- 头文件：
  #include <unistd.h>

- 函数原型：具体可在man手册中字节查看
    int execl(const char *path, const char *arg, ...
                       /* (char  *) NULL */);
    int execlp(const char *file, const char *arg, ...
                       /* (char  *) NULL */);

    int execv(const char *path, char *const argv[]);
    int execvp(const char *file, char *const argv[]);
    int execvpe(const char *file, char *const argv[],
                       char *const envp[]);



