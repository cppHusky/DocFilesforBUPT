# 给BUPT学生的电子版资料

## 若您使用Debian，可以通过以下方式打包/处理文件

为发送至QQ群之便，可以在Terminal中针对某个文件夹使用 `for dir in /source/directory/*/; do zip -rv "${dir%/}.zip" "$dir" && rm -rv "$dir"; done` 指令，来把所有二级文件夹变成压缩文件。

复制大于50MB的文件到接驳文件夹，可以使用 `find /source/directory -type f -size +50M -exec cp -v {} /destination/directory \;` 指令。其中的 `source/directory` 和 `/destination/directory` 应换成具体的路径名。

用Git LFS追踪所有大于50MB的文件，使用 `find /source/directory -size +50M | while read -r file; do git lfs track "$file"; done` 指令。

复制修改过的文件/文件夹到指定位置（并保留文件结构），可以用以下组合指令：

```
> filelist.txt
find /source/directory -type d -newermt 'YYYY-MM-DD HH:MM:SS' -exec sh -c 'find "$0" -type f' {} \; >> filelist.txt
rsync -av --files-from=filelist.txt --relative /source/directory /destination/directory
```

<!-- 如要压缩PDF文件，可以使用 `gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf` 指令。其中的 `output.pdf` 和 `input.pdf` 应换成具体的路径名。（暂不推荐使用，直到这个方法证实可靠） -->
<!-- 思修教材被我误删了。回头加上。 -->
