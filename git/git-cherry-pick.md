# Git 高级使用技巧 - cherry-pick

在开发过程中很容易出现改错分支的情况，例如，本来应该在 `dev` 分支上修改的内容，却在 `test` 分支上做了修改并且进行了多次提交，这种情况可能处理起来比较麻烦了，但是有了 `cherry-pick` 一样很轻松解决。

> cherry 是樱桃的意思，pick 是选择，挑选的意思。

### 1. cherry-pcik 语法

```git
$ git cherry-pick commit-id             #将某个提交应用到当前所在的分支。
```

### 2. 使用案例

场景: 将代码错误修改到 `dev` 分支，需要应用到 `master` 分支，并恢复 `dev` 分支。

1. 创建一个 `git` 仓库，在 `master` 分支上进行一次提交。
 
```git
$ mkdir git_cherry-pick && cd git_cherry-pick
$ git init
$ touch Test.java
```

`Test.java` 的内容如下：

```java
public class Test {

    public static void main(String[] args) {

    }

    public int sum(int x, int y) {
        return x + y;
    }
}
```

```git
$ git add .
$ git commit -m "init project"
```
2. 创建 dev 分支，并且进行两次修改两次提交

```git
$ git checkout -b dev   # 创建并切换分支
```
第一次修改是添加了 `substract` 方法，第二次修改是添加了 `multip` 方法，修改后 `Test.java` 内容如下：

```java
public class Test {

    public static void main(String[] args) {

    }

    public int sum(int x, int y) {
        return x + y;
    }

    public int subtract(int x, int y) {
        return x - y;
    }

    public int multip(int x, int y) {
        return x * y;
    }
}
```

此时的提交记录分别如下：

* master
```git
28192af init project
```

* dev

```git
81f5f1c add multip method
024108f add substract method
28192af init project
```

3. 此时发现 `substract` 和 `multip` 方法应该在 `master` 分支上提交。此时使用 `cherry-pick` 进行处理。

```git
$ git co master
$ git cherry-pick 024108f
$ git cherry-pick 81f5f1c
```

此时两分支的提交记录分别如下：

* master
```git
442a332 add multip method
c5517d9 add substract method
28192af init project
```

* dev

```git
81f5f1c add multip method
024108f add substract method
28192af init project
```
此时两分支 `Test.java` 的内容完全一致，但是两个分支的提交记录 ID 不一样，当执行 `cherry-pick` 的时候，`git` 会产生新的提交 ID。

4. 恢复 `dev` 分支修改前的状态。

此时可以使用 `git reset` 来实现，也可以使用如下方法。

```git
$ git checkout 28192af          # 切换到修改前的提交
$ git branch -D dev             # 强制删除 dev 分支
$ git checkout -b dev           # 重新创建 dev 分支
```

> 注意

`cherry-pick` 只是应用某次提交的内容到对应分支。以上示例默认是按提交顺序应用到 `master` 分支，也可以单独选择某个提交应用到对应主干。例如，可以选择最后一次提交，这样之前提交的内容就不会应用到 `master` 分支。







