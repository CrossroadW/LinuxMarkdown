**Linux 命令行中的单横线、双横线，我们称之为命令行选项，命令行选项后面可能会带有参数值。**

单横线
## 单横线选项后面跟的参数必须是单字符参数，一个字符表示一个参数，可以多个参数写在同一个横线后面。

tar -xcvf ×××
1
## 在选项需要加参数的时候，参数可以紧跟在选项后面，也可以使用空格分隔。

mysql -u root -p
mysql -uroot -p
1
2
双横线
双横线选项后面跟的参数必须是多字符参数（单词），双横线后只能跟一个参数。

```console
tar --help
```

## 在选项需要加参数的时候，参数可以使用“=”分隔，也可以使用空格分隔。

git branch --set-upstream-to origin/remote_branch  your_branch
git branch --set-upstream-to=origin/remote_branch  your_branch