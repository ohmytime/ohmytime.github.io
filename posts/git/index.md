# Git



## Git log

让log显示成一行

```bash
git log --pretty=oneline 
```
 
格式化log
```bash
git log --pretty=format:&#34;%h - %an, %ar : %s&#34;
```

&lt;!--more--&gt;

## 分支管理

- #### Git新建分支

``` c
新建分支：
git checkout -b my-new-branch

删除分支：
git branch -d my-new-branch

新建分支也可以简写成：
git branch my-new-branch
git checkout my-new-branch

```


- #### Git删除分支

```c

显示所有分支
git branch -a

删除本地分支
git branch -d branch-name

删除远程分支：
git push origin -d remote-branch-name

```

- #### 分支改名

``` c
git branch -m new-name
```



## Git stash


- #### 临时保存

比如Dev分支，活干一半的时候，需要临时开一个Bugfix分支来修补bug

``` bash

//缓存当前编辑
git stash 
git stash save &#39;for name&#39;

// 显示缓存列表
git stash list

// 删除编号为3的缓存
git stash drop -q stash@{3}

// 删除所有缓存
git stash clear


// 弹出最新缓存
git stash pop

//然后再将缓存POP出来(最近的一个)
git stash pop  
# 恢复指定编号的 WIP，同时从列表中移除
git stash pop stash@{num}

# 恢复指定编号的 WIP，但不从列表中移除
git stash apply stash@{num} 


```

- #### 误删之后怎么恢复

如果不小心执行了： 
``` bash
git stash clear
```

把缓存的全部清除了，那么可以使用如下命令，找出历史缓存

``` bash
git log --oneline --decorate  $( git fsck --no-reflog | awk &#39;/dangling commit/ {print $3}&#39; )
```

然后会看到很多历史ID，执行

``` bash
git stash apply XXXX
```


## Git patch 打补丁


- #### 正常打patch

``` c
// 将更改打包成patch
git diff &gt; test.patch 

// 检查patch的情况
git apply --stat test.patch

会有如下输出：
 src/tuner-filters.c   |    4 &#43;&#43;--
 src/tuner.h           |    5 &#43;&#43;&#43;&#43;-
 src/ui-input.c        |   21 &#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;--
 src/ui-tuner-update.c |   20 &#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;-
 src/ui.c              |   21 &#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;&#43;--
 5 files changed, 63 insertions(&#43;), 8 deletions(-)
 
// 然后应用patch
git apply test.patch

// 最后检查结果：
git apply --check test.patch
// 如果没有任何输出，证明打patch成功

```




---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/git/  

