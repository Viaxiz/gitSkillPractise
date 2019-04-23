# 场景重现
come from:https://github.com/airuikun/blog/issues/5

------------
## 大致就是：
    现在做了3个功能，每个功能对应着一个commit的提交，分别是feature-1到feature-3
    然后执行了强行回滚到第一个
    > git reset --hard feature-1的序号
    然后又提交了一个新的功能feature-4
## 问题：
	如何找回之前的feature-2和feature-3，并保留feature-1和feature-4

## 做法:
	现在提交了feature-1 和 feature-4
	那么我们首先用
	>git reflog
	查看已经执行的操作
	然后找到feature-3的提交时候的hash值
	然后回滚到feature-3的时候
	>git reset --hard 该hash值
	这时没有feature-4
	所以看看feature-4提交时候的hash值后
	>git cherry-pick 该hash值
	然后就Ok了
