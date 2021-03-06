Linux 系统内文件有三种身份(拥有者、群组与其他人)，每种身份都有三种权限
(rwx)， 已知道能够使用 `chown`, `chgrp`, `chmod `去修改这些权限与属性，
当然，利用` ls -l `去观察文件也没问题。那么，这些文件权限对于一般文件与
目录文件有何不同呢？

### 权限对文件的重要性

文件是实际含有数据的地方，包括一般文本文件、数据库内容文件、二进制可执行文件(binary program)
等等。 因此，权限对于文件来说，他的意义是这样的：

- r (read)：可读取此一文件的实际内容，如读取文本文件的文字内容等；
- w (write)：可以编辑、新增或者是修改该文件的内容(但不含删除该文件)；
- x (eXecute)：该文件具有可以被系统执行的权限。

### 权限对目录的重要性

文件是存放实际数据的所在，那么目录主要是储存啥玩意啊？目录主要的内容在记录文件名列表，文
件名与目录有强烈的关连啦！ 所以如果是针对目录时，那个 r, w, x 对目录是什么意义呢？

- r (read contents in directory)：表示具有读取目录结构列表的权限，所以当你具有读取(r)一个目录的权限时，表示你可以查询该目录下的
文件名数据。 所以你就可以利用 ls 这个指令将该目录的内容列表显示出来！
- w (modify contents of directory)：这个可写入的权限对目录来说，是很了不起的！ 因为他表示你具有异动该目录结构列表的权限，也就是底
下这些权限：

    - 建立新的文件与目录；
    - 删除已经存在的文件与目录(不论该文件的权限为何！)
    - 将已存在的文件或目录进行更名；
    - 将已存在的文件或目录进行更名；
    
    总之，目录的 w 权限就与该目录底下的文件名异动有关就对了啦！
    
- x (access directory)：目录的执行权限有啥用途啊？目录只是记录文件名而已，总不能拿来执行吧？没错！目录不可以被执
行，目录的 x 代表的是用户能否进入该目录成为工作目录的用途！ 所谓的工作目录(work directory)就是你
目前所在的目录啦！举例来说，当你登入 Linux 时， 你所在的家目录就是你当下的工作目录。而变换目录
的指令是『cd』(change directory)啰！

### 总结

| 组件 | 内容 | 迭代物件 | r | w | x |
|---|---|---|---|---|---|
| 文件 | 详细资料 data | 文件内容 | 读到文件内容 | 修改文件内容 | 执行文件内容 |
| 目录 | 档名 | 可分类抽屉 | 读到档名 | 修改档名 | 进入该目录的权限(key) |

根据上述的分析，你可以看到，对一般文件来说，rwx 主要是针对『文件的内容』来设计权限，对目
录来说，rwx 则是针对『目录内的文件名列表』来设计权限。 其中最有趣的大概就属目录的 x 权限
了！『档名怎么执行』？没道理嘛！其实，这个 x 权限设计，就相当于『该目录，也就是该抽屉的 "
钥匙" 』啦！ 没有钥匙你怎么能够打开抽屉呢？对吧！