# VS Code config

个人[VS Code](https://code.visualstudio.com/) 偏好配置文件，
用于保存配置，方便多台电脑间同步。

## How to use

```sh
cd "$HOME/Library/Application Support/Code/User"   # only for macOS
git init
git remote add origin https://github.com/able8/vscode-config.git
git pull origin master
sh import.sh        # 安装插件
```

## Customizing

If you want to customize something, you should add your git remote:

```sh
git remote add my-remote https://my.repo.com/my-repo.git
git add .
git commit -m "Added some snippets."
git push -u my-remote master
sh export.sh         # 安装 卸载 插件后，需要重新导出，再push
```

## 资源链接

- [vscode 快捷键](https://segmentfault.com/a/1190000012811886)
- [Git 基础 - 远程仓库的使用](https://git-scm.com/book/zh/v2/Git-基础-远程仓库的使用)
- [vscode Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

## 常用快捷键

按键 | 功能
----- | ---
⌘ b  | 切换隐藏左边拦
⌘ t  | 切换隐藏终端
⌘ j  | 切换 面板
⌘ `+／-`  | 放大／缩小
⌘ o | 跳转到某个文件
⌘ p | 打开文件
⌘ shift p | 输入命令，如git push, snippet
⌘ shift e | 打开左边文件管理器
⌘ shift g | 输入git commit 信息
⌘ shift f | 全局搜索
⌘ shift t | 重新打开关闭的文件
⌘ shift r | 预览markdown文件
⌘ shift x | 打开扩展
⌘ shift h | 文件中替换
⌘ + k  v  | 分栏预览markdown文件
⌘ K ⌘ X   | 修剪尾随空白
⌘ K P     | 复制当前文件的路径
⌘ K R     | 在Finder中显示当前文件
⌘ K O     | 在新窗口显示当前文件
⌘ shift k | 删除一行
⌘ shift u | 打开 输出
⌘ shift m | 查看错误提示  问题
⌘ + D | 向下选中相同内容
⌘ + K  ⌘ + D |移除前一个向下选中相同内容
⌘ + Enter  |下一行插入
⌘ + Shift + Enter |上一行插入
⌘ + Shift + \ | **跳转到匹配的括号**
⌘ + Up | 跳转至文件开头
⌘ + Down | 跳转至文件结尾
⌘ I	| 选择当前行
⌘ U | 回到上次光标位置
⌘ X | Cut line (empty selection)
⌘ C | Copy line (empty selection)
⌘ / | 注释
⌘ i | 选择当前行
⌘K ⌘S | 打开快捷键设置
ctrl + g  | 跳转至某行
Option + Cmd  + [ | 折叠代码
Option + Cmd  + ] | 展开代码
Option + Up | 向上移动行
Option + Down | 向下移动行
Option + Shift + Up | 向上复制行
Option + Shift + Down | 向下复制行
Option + 点击 | 插入多个光标  多行编辑
Option + shift+ 鼠标拖拽 |块选择
code . | 打开当前目录
code -r . | 在当前窗口打开当前目录

## 其它

- git

```py
cat <<'EOF' >> .zshrc
alias gcl='git clone'
alias gcm='git commit -am'
alias gs='git status'
alias gl='git log'
alias gd='git diff'
alias gpl='git pull'
alias gph='git push'
EOF
source .zshrc
```

- vscode 设置

```sh
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

# vscode  md 插入导航目录
- []()  自动TOC
ysiw  '  用引号包围
```

- vim

```text
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

多行选择后  J 把所有的行连接起来（变成一行）
被选择的行后加上点东西: ctrl+v 选择列  $ 行尾巴  A插入

b	跳到前一个单词的开头
e	跳到下一个单词的结尾
w	跳到下一个单词的开头

vim 正常模式下:
ctrl f 向前翻页
ctrl b 向后翻页
v+i+w	放在一个单词的任意位置时均可选中本单词
v+e	    光标放在一个单词的开头时可选中本单词

光标移动：
{ 移到段落的开头
} 移到下一个段落的开头
% : 匹配括号移动，包括 (  ) {     }  [  ] （你需要把光标先移到括号上）
* 和 #:  匹配光标当前所在的单词，（*是下一个，#是上一个） ，移动光标到下一个（或上一个）匹配单词
able

able
able

ta 跳到下一个a 前面
fa 跳到下一个a
大写的意思相反
跳转引号  f"  F"    "able"

综合起来
dt) 一直删除到这行的)    sdfasdfasdf)  )  "asdfasdf"  asdfd }
另外 懂了跳转键后 那删除或是复制时就不再是以行为单位了 可以指定到某个条件

ctrl+i 向前跳到前几次光标位置
ctrl+o 向后跳到后几次光标位置

区域选择 <action>a<object> 或 <action>i<object>
在visual 模式下，这些命令很强大，其命令格式为
<action>a<object> 和 <action>i<object>
action 可以是任何的命令，如 d (删除), y (拷贝), v (可以视模式选择)。
object 可能是： w 一个单词， W 一个以空格为分隔的单词， s 一个句字， p 一个段落。也可以是一个特别的字符："、 '、 )、 }、 ]。
假设你有一个字符串(map (+) ("foo")).而光标键在第一个 o 的位置。
vi" → 会选择 foo.
va" → 会选择 "foo".
vi) → 会选择 "foo".
va) → 会选择("foo").

s 默认删除光标所在字符，输入内容插入之= xi
S 默认删除当前行内容，输入内容作为当前行新内容= dd+o

z 命令会把当前行置为屏幕正中央(z字取其象形意义模拟一张纸的折叠及变形位置重置)
zt 命令会把当前行置于屏幕顶端(top)
zb 命令会把当前行置于屏幕底端(bottom)

cw 快速更改一个单词
ncw 删除当前字及其后的n-1个字，并进入输入模式 修改指定数目的字
cc 删除当前行，并进入输入模式
ncc 删除当前行及其后的n-1行，并进入输入模式
guw 光标下的单词变为小写
gUw 光标下的单词变为大写
xp 左右交换光标处两字符的位置
~ 改变当前光标下字符的大小写

插入模式中删除操作
^U 删除当前行
^H 删除前一个字符
^W 删除前一个词

normal模式下
u   撤销上一步的操作
Ctrl+r 恢复上一步被撤销的操作

.	重复上一个操作

#

```

- 多光标模式 Multi-Cursor Mode
    - 按住 `alt` + 点击, 实现选择多个光标位置，可以同时编辑
    - 插入模式， `cmd+d`, 添加下一个匹配项，`cmd+k cmd+d` 跳过一个匹配项，`cmd+shift+L` 选择所以匹配项
    - 正常模式下类似，注意点是先选择，然后按esc结束选择，即进入多光标编辑模式
