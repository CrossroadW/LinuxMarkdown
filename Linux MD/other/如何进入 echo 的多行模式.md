通过在命令行中输入 `echo`，然后按下回车键进入单行模式，在单行模式下可以使用反斜杠(`\`)来换行，例如：

```shell

`echo "Hello World! \ This is a new line."`
输出结果为：
`Hello World! This is a new line.`

除此之外还可以使用 `echo` 命令的 `-e` 选项进入多行模式，例如：
`echo -e "Hello World!\nThis is a new line."`

输出结果为：
`Hello World! This is a new line.`
其中`\n`表示换行符。

```
**如何退出 echo 的多行模式：**

在使用 `\` 进行换行的时候，如果没有使用`\`来**转义**回车键(即直接按下回车键)，bash会认为你已经完成了一整条命令，因此你可以直接按下回车键来退出多行模式。

而在使用 `-e` 开启的多行模式中，不需要退出多行模式。