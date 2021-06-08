git branch | grep -v "master" | grep -v "test" | xargs git branch -D

删除本地除了master和test之外的其他分支



git config core.ignorecase false

git无法检测到文件名大小写的更改

