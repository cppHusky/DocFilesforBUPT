# 给BUPT学生的电子版资料

## 若您使用Debian，可以通过以下方式打包/处理文件。

为发送至QQ群之便，可以在Terminal中针对某个文件夹使用 `for dir in */; do zip -rv "${dir%/}.zip" "$dir" && rm -rv "$dir"; done` 指令，来把所有二级文件夹变成压缩文件。

如要压缩PDF文件，可以使用 `gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf` 指令。其中的 `output.pdf` 和 `input.pdf` 应换成具体的文件名。
