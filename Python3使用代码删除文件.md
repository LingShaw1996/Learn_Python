## Python3使用代码删除文件

在阅读《爱上python》时，“8.6 删除和重命名文件”提到一个知识，“在处理文件时，我们需要学习的另外两个有用的函数是remove()和rename()。**这两个函数在os模块里面，在使用它们之前，我们需要在程序中引入它们。**”

个人不是非常理解这句话，而书中也没有实例。因此在网上找了几个示例，笔记如下。

#### 删除文件

使用Python代码删除文件，有两种方式，分别是os.unlink()和os.remove().

```python
# 导入os模块来删除文件
# 使用os.remove()和os.remove()删除文件

import os

# 标准格式为：os.remove(path or '文件名')
os.remove('123.jpg')  # 删除成功
os.unlink('123.png')  # 删除成功

# 注意文件的路径一定要正确
```

* [`os.unlink(path,*,dir_fd=None)`](https://docs.python.org/3/library/os.html#os.unlink):Remove (delete) the file *path*. This function is semantically identical to [`remove()`](https://docs.python.org/3/library/os.html#os.remove); the `unlink` name is its traditional Unix name. Please see the documentation for [`remove()`](https://docs.python.org/3/library/os.html#os.remove) for further information.

* [`os.remove(*path*, ***, *dir_fd=None*)`](https://docs.python.org/3/library/os.html#os.remove):Remove (delete) the file *path*. If *path* is a directory, [`OSError`](https://docs.python.org/3/library/exceptions.html#OSError) is raised. Use [`rmdir()`](https://docs.python.org/3/library/os.html#os.rmdir) to remove directories.

  This function can support [paths relative to directory descriptors](https://docs.python.org/3/library/os.html#dir-fd).

  On Windows, attempting to remove a file that is in use causes an exception to be raised; on Unix, the directory entry is removed but the storage allocated to the file is not made available until the original file is no longer in use.（如果尝试删除一个正在使用的文件，在Windows系统中，会返回异常；在Unix系统中，目录条目虽被删除，但仍给该文件分配内存，且在该内存停止使用之前，这个内存不可用。）

  This function is semantically identical to [`unlink()`](https://docs.python.org/3/library/os.html#os.unlink).

注意：删除之后，文件不会存放在回收站，而是直接删除。类似于火绒安全提供的“文件粉碎”功能。

#### 参考链接

[python 删除文件、目录 - MuWinter的博客 - CSDN博客](https://blog.csdn.net/MuWinter/article/details/77196261)

[os — Miscellaneous operating system interfaces — Python 3.7.1 documentation](https://docs.python.org/3/library/os.html)

