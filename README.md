# VS Code config 

个人[VS Code](https://code.visualstudio.com/) 偏好配置文件，
用于保存配置，方便多台电脑间同步。

## How to use

```sh
cd "$HOME/Library/Application Support/Code/User"   # only for macOS
git init
git remote add origin https://github.com/able8/vscode-config.git
git pull origin master
sh import.sh         # 安装插件
```

## Customizing

If you want to customize something, you should add your git remote:

```sh
git remote add my-remote https://my.repo.com/my-repo.git
git add .
git commit -m "Added some snippets."
git push -u my-remote master
sh export.sh         # 安装、卸载 插件后，需要重新导出，再push
```

## 常用快捷键

| 按键 | 功能 |
| --- | --- |
| cmd + b  | 切换隐藏左边拦  |
| cmd + t  | 切换隐藏终端 |
| cmd + j  | 切换 面板 |
| cmd + `+／-`  | 放大／缩小 |
cmd + p | 快速打开文件
cmd shift p | 输入命令，如git push
cmd shift e | 打开左边文件管理器
cmd shift g | 输入git commit 信息
cmd shift f | 全局搜索
cmd shift t | 重新打开关闭的文件


  
```sh
# open code with current directory
code .
# open the current directory in the most recently used code window
code -r .
cmd /  注释
cmd p 快速打开文件
Select current line  cmd i
cspell check   
pylint     cmd shift m  查看错误提示
cmd shif k  删除一行


# markdown
cmd + shift + r   打开预览窗口
cmd + k  v        侧边栏预览

#  移动代码和快速复制
alt 上下   移动行      
alt shift 上下  复制行
vim v 进入块选择 

cmd+shift+p git push 方便快速推送代码
cmd+shiff+p snippet  便捷自动补全 

Option + Up 向上移动行
Option + Down 向下移动行
Option + Shift + Up 向上复制行
Option + Shift + Down 向下复制行
Command + Shift + K 删除行

Option + 点击 插入多个光标  多行编辑
Command + D 向下选中相同内容
Command + K Command + D 移除前一个向下选中相同内容

Ctrl + G 跳转至某行
Command + P 跳转到某个文件

Command + Enter 下一行插入
Command + Shift + Enter 上一行插入
Command + Shift + \ 跳转到匹配的括号

Command + Up 跳转至文件开头
Command + Down 跳转至文件结尾

⌘I	选择当前行

# 转到函数定义处
F12 跳转到声明位置    
按 esc退出速览
Option + F12 查看具体声明    映射为 shift + 空格
Shift + F12 显示引用    映射为 shift + option + 空格

# esc退出速览 改成按 tab
{
    "key": "tab", "command": "closeReferenceSearch",
    "when": "referenceSearchVisible && !config.editor.stablePeek"
},

# ff 退出visal模式的选择
"vim.visualModeKeyBindings": [
    {   "before": ["f", "f"],
        "after": [ "<Esc>" ] },
],


# vim 列编辑 块选择(Visual Block)
v	    字符选择，将光标经过的字符选择
V 大写	 行选择，将光标经过的行选择
Ctrl+v	矩形选择，可以用矩形的方式选择数据
y   	将选中地方复制起来
d   	将选中地方删除
ctrl+v  进入模式，hjkl选择列，
A       光标后插入模式
I       大写光标前前插入，
r替换，d删除，
完成后按esc退出模式，再按esc完成所有修改。
ESC 按两次，会在每行的选定的区域出现插入的内容
```


## 资源链接

- [vscode 快捷键](https://segmentfault.com/a/1190000012811886)
- [Git 基础 - 远程仓库的使用](https://git-scm.com/book/zh/v2/Git-基础-远程仓库的使用)
