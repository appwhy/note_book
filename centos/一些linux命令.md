

## dd：创建指定大小的文件

`dd`： Copy a file, converting and formatting according to the operands.

`dd if=/dev/zero of=sample.txt bs=1M count=50` : 输入文件（input file）为zero，输出文件（output file）为sample.txt，大小为50M

参数说明:

* `bs`: bytes 同时设置读/写缓冲区的字节数（等于设置ibs和obs）

## dmesg： 显示开机信息

dmesg（英文全称：display message）命令用于显示开机信息。

kernel 会将开机信息存储在 ring buffer 中。您若是开机时来不及查看信息，可利用 dmesg 来查看。开机信息亦保存在 `/var/log` 目录中，名称为 dmesg 的文件里。

