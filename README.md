# VS Code config and preferences
My personal configurations and preferences for [VS Code](https://code.visualstudio.com/).
It's an usefull repository to keep the same VS Code settings across many computers.

## How to use

```sh
# macOS
cd "$HOME/Library/Application Support/Code/User"  
git init
git remote add origin https://github.com/able8/vscode-config.git
git pull origin master
```

install the extensions:

```sh
sh import.sh
```

## Customizing
If you want to customize something, you should add your git remote after executing the steps on **How to use** section:

```sh
git remote add my-remote https://my.repo.com/my-repo.git
```

Now you can change the settings, snippets and keyboard shortcuts in VS Code and push the files to your repository:
```sh
git add .
git commit -m "Added some snippets."
git push -u my-remote master
```

If you add or remove a extension through VS Code, you will need to export it before pushing to your repo:

```sh
sh export.sh
```

## 资源链接

- [vscode 快捷键](https://segmentfault.com/a/1190000012811886)
- [Git 基础 - 远程仓库的使用](https://git-scm.com/book/zh/v2/Git-基础-远程仓库的使用)
