### vim从.开始，这是vim思路的核心

首先需要明白VIM的基本命令；主要是位置移动，插入，删除，复制粘贴，查找

### 学习的方法

- ":help word"  进入文档说明

位置移动和搜索，需要重复加强练习，做到指哪打哪；

# 基本设置

- :set hlsearch     高亮显示查找结果
- :set nohlsearch   取消高亮
- :set nu           显示行号
- 在Mac下，shift可以切换中英输入法，在中文输入法下，命令会无效；
- Insert，切换光标为输入/替换模式，光标将变成竖线/下划线;在MAC下试了无效；
- ESC，退出输入模式，切换到命令模式

# 浏览
 
- ctrl+b\f  向上\下滚动一屏(before / after)
    - Page Up   -> 对应 ctrl+b
    - Page Down -> 对应 ctrl+f  这一组更加的顺手
- ctrl+u\d  向上\下滚动半屏(up / down) 我更喜欢用这个
- ctrl+e\y  向上\下滚动一行

- 50%  跳转到文件整体的百分之50部分

- `` 上次光标停靠的行 
- gd 移动到光标所处的函数或变量的定义处,配合 `` 可以回到上次光标停靠的行 

- zz:将当前行滚动于屏幕中间，方便查看上下文,这个命令非常的实用；这是非常实用的一个命令；如果ZZ就是写入缓冲区并退出
- zt置顶 top
- zb置尾 bottom

- %：  匹配到相应括号处（），{}，[]，<>等,编程时常用(将光标放在 { 处，然后输入v%就可以把大括号中内容选定)
- [{  跳到本代码块的开头
- ]} 跳到本代码块的结尾
- ()  => )移动光标到下一个句子，(移动光标到上一个句
- {}  => {移动到段首，}是移动到段尾

# 位置移动

 这一步要多训练，可以做到最快的指哪打哪；

###  垂直移动，在不同行之间

- hjkl  左  下  上 右
    - 2j 向下移动2行；其他类似；
    - 一般用←键 也就是删除键来代替h来使用；
- Enter/回车键，功能和j是一样的，这也在IDEA里也可以下一行，一般是-和enter一起配合；正常用不到
- - 光标移动到非空格符的上一行（其他行 2- 光标向上移动2行,并位于行首）
    - + 光标移动到非空格符的下一行（其他行 2+ 光标向下移动2行,并位于行首））

- H 光标移至屏幕首行
- M 光标移至屏幕中间
- L 光标移至屏幕最末行

- gg 文档顶部 1G (goto first line)
- G  文档尾部    (goto last line)
- nG 跳到指定的行；比如12G跳转到12行，此时如果按两次`就会返回原来行；这个不如命令行模式看的直观，但是这个命令非常的方便；
- :n 跳到n行,比如到39行 :39 回车即可；一般和zz配合，移动到某行，在把当前的行放在屏幕的中间 ；

### 水平移动，在同一行里移动

- ^ 光标移到行首的第一个字符处(和0的区别需要明白)
    - 0 光标移至行首,
- $ 光标移至行尾(当前行,3$：移动到3行后的行尾,当前行是第一行)
- HOME END代替0代替$ 这个也是实用,不过不推荐

- w 跳到下一个词的词首，3w代表向后移动3个；( words forward 前进)
- b 跳到当前词的词首, （backward 向后），如果光标本身就在当前词的词首，则跳到前一词的词首 ，标点也算一个单词, 3b 代表向前移动3个；
- e 跳到当前词的词尾；end
- n<space>  : 按下数字后再按空格键，光标会向右移动这一行的 n 个字符。


# 选中

- v 字符选中
    - 剪切快 v
    - 剪切并进入插入模式 c
- V 行选择 

# 搜索

- * ：选中所有的当前字符,光标并跳到下一个所在单词
- # ：选中所有的当前字符,光标并跳到上一个所在单词

- /word  查找word，回车后，按n键可以跳到下一个，N上一个，
    - 另外按/键后，按上下键可以找到以前查找的记录，同样的 ：也有记录
    - 如果你输入 "/the"，你也可能找到 "there"。要找到以 "the" 结尾的单词，可以用：
        /the\> "\>" 是一个特殊的记号，表示只匹配单词末尾。类似地，"\<" 只匹配单词的开头。
        这样，要匹配一个完整的单词 "the"，只需：/\<the\>
- ?/word 同上，默认向上查找

- f 向后搜索 fx定位下一个x
- F 向前搜索 Fx定位上一个x

继续下一个用; , 来实现(;表示跳到下一个 ,表示跳到前一个)

# 关键字替换
- :%s/str1/str2/g       替换每一行的str1为str2
    - :%s/^ /- /g       把空格开头的行都替换成"- "这样的字符
    - :%s/^/+/g         把每一行的开头都加"+"这个字符

- :s/str1/str2          将下一个str1替换为str2
- :s/str1/str2/g        替换当前行的str1为str2；

- :10,20s/str1/str2/g    替换从行10到行20之间的str1为str2；
- :10,$s/str1/atr2/g    替换从行10到最后一行的str1为str2

- r word
- R word

# 复制

- yy  复制当前行 yank
- Y   复制当前行

- nyy 复制后面的n行
- ynj: 向下复制n行          
- ynk: 向上复制n行  

- y0：复制光标至行首
- y$：复制光标至行尾
- yG
- y1G/ygg

- yw   y like d
- yaw: 复制一个单词,光标在单词任意位置    
- ynw: 复制N个单词,     


# 粘贴
p：粘贴至光标后　　　　
P：粘贴至光标前　　　　
3P：粘贴3次      
- :reg 查看当前的剪切板,前面会显示剪切板对应的词条快捷方式；
"2p     粘贴最后第二次的剪切的内容

# 删除（严格来说是剪切，不是删除）

简单的说，d相关是剪切，

- dd: 剪切整行: 此命令一般和粘贴配合（p）使用，也可以作为剪切来使用；
    - 如果p的时候，会在下一行插入，如果P的时候，会在上一行插入；
- D : 剪切当前到行尾 这条命令也非常实用, 此命令复制是字符，不含回车的，粘贴的时候，不会有换行效果的；
- d0：剪切光标至行首
- d$：剪切光标至行尾 这条命令可以用D来代替
- dG
- d1G/dgg

- dw:删除一个单词；courent word
- cw:删除一个单词进入插入模式；

- s :剪切字符插入s， 
- S  剪切本行并插入
- cc 剪切本行并插入 -> ddi


- :2,10d  剪切第2-第10行(包含第2和第10行)；
- :10,2d  剪切第2-第10之间的（不包含第2-第10行,这条命令在vscode插件下无效,在wstorm的插件下可用

- x：剪切当前光标所在的字符,
- X：剪切前一个字符
- nx：剪切光标后面n个字符,剪切3个字符就是3x
- nX：剪切光标前面的n个字符
如果光标放在第一个s上，想剪切到“(”为止，则输入dt(就可以了，t(的作用是跳到下一个"("前。 

# 恢复/撤销

- u ：撤销上一次操作 (后退)
- ctrl+r:对撤消的撤消（前进）
- U : 撤销当前行的所有修改



# 插入

- a     在光标前插内内容  -> append
- i     在光标后插入内容  -> insert
- o     在所在行的下一行插入新行  -> open oen line
- c     删除光标所在位置周围某个范围的文本并进入插入模式。

- A     -> $a
- I     -> ^i
- O     -> 在所在行的上一行插入新行
- C  和D的效果是一样的, (相当于c$) 

- Esc   退出插入模式

- ciw - 删除一个单词并开始插入； 
- caw - 删除一个单词并开始插入,包括它后面的空格； 
- ci" - 删除一个字符串内部文本并开始插入； 
- c$ - 从光标位置删除到行尾并开始插入； 
- ct字符 - 从光标位置删除本行某个字符之前（保留该字符）并开始插入。

# 点命令

. 重复执行命令，这个命令包含了vim的精髓，需要非常的理解；有大能

# 窗口操作

- :split
- :vsplit
- :new
- :close
- :only
- ctrl+w 两次可以切换下一个窗口；
- :w [filename]	将编辑的数据储存成另一个档案（类似另存新档）

# 指令行的储存、离开等指令

注意一下啊，那个惊叹号 (!) 在 vi 当中，常常具有『强制』的意思～

- :w	将编辑的数据写入硬盘档案中(常用)
- :q	离开 vi (常用)  

- :w! 若文件属性为『只读』时，强制写入该档案。不过，到底能不能写入， 还是跟你对该档案的档案权限有关啊！
- :q! 若曾修改过档案，又不想储存，使用 ! 为强制离开不储存档案。

- :wq	储存后离开，若为 :wq! 则为强制储存后离开 (常用)
- ZZ  这是大写的 Z 喔！若档案没有更动，则不储存离开，若档案已经被更动过，则储存后离开！

- :w [filename]	将编辑的数据储存成另一个档案（类似另存新档）
- :r [filename]	在编辑的数据中，读入另一个档案的数据。亦即将 『filename』 这个档案内容加到游标所在行后面
- :n1,n2 w [filename]	将 n1 到 n2 的内容储存成 filename 这个档案。
- :! command		暂时离开 vi 到指令行模式下执行 command 的显示结果！例如
    - :! ls /home 即可在 vi 当中察看 /home 底下以 ls 输出的档案信息
    
# 格式化
- >>   向右移动本行一段距离     
- <<   向左移动本行一段距离    
- 3<<  把下面3行（包括本行），向左移动一段距离     
- :20,30>>  把20行到30行向右移动一段距离
- >G    
- J :合并两行
