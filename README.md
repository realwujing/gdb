# linux-learning

This is a collection of notes and resources for learning Linux.

## git submodules

- 自动初始化并更新仓库中的每一个子模块， 包括可能存在的嵌套子模块。

    1. 方式1

        ```bash
        git clone --recurse-submodules https://github.com/realwujing/linux-learning.git
        ```

    2. 方式2

        ```bash
        git clone https://github.com/realwujing/linux-learning.git
        git submodule update --init --recursive
        ```

- 递归地抓取子模块的更改并更新当前仓库中的每一个子模块， 包括可能存在的嵌套子模块。

    1. 方式1

        ```bash
        git pull --recurse-submodules
        ```

    2. 方式2

        ```bash
        git pull
        git submodule update --init --recursive
        ```

- 推送当前仓库中的每一个子模块， 包括可能存在的嵌套子模块。

    1. 方式1

        ```bash
        git push --recurse-submodules=on-demand
        ```

    2. 方式2(方式1报错情况下使用)

        ```bash
        git submodule foreach --recursive 'git push' && git push
        ```

- 更改submodule分支

    ```bash
    git config -f .gitmodules submodule.assembly.branch main
    ```

    ```bash
    git submodule update --remote
    ```

- 在你拉取的提交中， 可能 .gitmodules 文件中记录的子模块的 URL 发生了改变。 比如，若子模块项目改变了它的托管平台，就会发生这种情况

    ```bash
    # 将新的 URL 复制到本地配置中
    git submodule sync --recursive
    ```

    ```bash
    # 从新 URL 更新子模块
    git submodule update --init --recursive
    ```

## More

- [7.11 Git 工具 - 子模块](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)