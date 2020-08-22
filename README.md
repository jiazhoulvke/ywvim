This is a mirror of [http://www.vim.org/scripts/script.php?script_id=2662](http://www.vim.org/scripts/script.php?script_id=2662)

created by
Yue Wu
 
script type
utility
 
description
介绍： 
======= Chinese version ======= 
注意!!! 
======= 
如果你是 ywvim 的老用户, 在升级到新版本前, 请注意你的旧版本到新版本间*所有*的发布公告和已知 bugs, 然后查找对应设置的说明, 以免不兼容的改变给你带来不便. 
如果你在使用中发现了问题, 在报告之前, 请先查看下面的"已知问题"部分, 确定是否为已知 bug. 

下载最新脚本(1.31): https://www.vim.org/scripts/download_script.php?src_id=27223 
下载最新码表(1.15): https://www.vim.org/scripts/download_script.php?src_id=27224 

介绍: 
===== 
ywvim 是一款不依赖外部输入法的, 在 vim 里输入中文的工具. 支持在 vim 的所有模式下输入中文. 它面向的对象主要为形码用户, 对于拼音用户, 你可以试试有更多功能的 vimim[http://www.vim.org/scripts/script.php?script_id=2506]. 
坏消息: ywvim 和 vimim 的键绑定冲突, 你必须在两者中做出选择. 

.vimrc 里的设置: 
================ 
把下面的几行放到你的 .vimrc 中: 

----- 
let g:ywvim_ims=[ 
            \['wb', '五笔', 'wubi.ywvim'], 
            \['py', '拼音', 'pinyin.ywvim'], 
            \['cj', '仓颉', 'cangjie.ywvim'], 
            \['wb98', '五笔98', 'wubi98.ywvim'], 
            \['zm', '郑码', 'zhengma.ywvim'], 
            \['zy', '注音', 'zhuyin.ywvim'], 
            \['ar30', '行列', 'array30.ywvim'], 
            \] 

let g:ywvim_py = { 'helpim':'wb', 'gb':0 } 

let g:ywvim_zhpunc = 1 
let g:ywvim_listmax = 5 
let g:ywvim_esc_autoff = 0 
let g:ywvim_autoinput = 0 
let g:ywvim_intelligent_punc=1 
let g:ywvim_circlecandidates = 1 
let g:ywvim_helpim_on = 0 
let g:ywvim_matchexact = 0 
let g:ywvim_chinesecode = 1 
let g:ywvim_gb = 0 
let g:ywvim_preconv = 'g2b' 
let g:ywvim_conv = '' 
let g:ywvim_lockb = 1 
----- 

使用: 
===== 
<Ctrl-Space>, <Ctrl-Shift-Space>, <Ctrl-@>, <Ctrl-\> 输入法开关. 

;(分号) 临时英文. 

z, ` 临时拼音.（需要输入法变量 g:ywvim_ims 里有一个 'py' 拼音简称的码表） 

<Ctrl-^> 设置输入法: 
    码表切换. 
    中英标点切换. 
    候选项个数: 候选项个数. 
    最大词长: 你想输入的最长的词. 设为 1 为单字模试. 
    简繁转换开关. 
    只输入GB2312. 
    辅助编码提示开关. 

,.-=    上下翻页. 

空格或数字选字, 回车输英文. 
; 分号选择第二候选词. (感谢在 www.newsmth.net 的 vace 的建议.) 

注音用户注意!!!: 
两次空格为翻页. 
回车为输入默认汉字. 
默认没有绑任何键到临英和临拼(你可以更改). 

详情: 
===== 

所有变量中, 只有 g:ywvim_ims 是必须要设置的. 

1. g:ywvim_ims 是注册你的输入法的变量, 格式为: 

      \['输入法的拼音简称', '输入法的中文名称', '码表文件'] 
             
比如 \['wb', '五笔', 'wubi.ywvim'], 可以读为: 五笔输入法, 简称为 wb, 码表文件为 wubi.ywvim. 
ywvim 会自动扫描 ywvim.vim 的同一目录及其子目录, 如果有同名文件, 以第一个优先. 
第一行的为默认输入法. 
你可以把你不需要的输入法的行删去. 

2. let g:ywvim_py = { 'helpim':'wb', 'gb':0 } 

单独设置每个码表的参数, 码表级别优先于全局级别. 码表级别的参数设置格式是: 

    g:ywvim_{输入法的简称} = {'参数':'参数设置'} 

目前有这几个参数支持局部设置: 
listmax: 候选框数目. 
maxphraselength: 最大词长. 
helpim: 反查码表的简称. 
zhpunc: 中文标点开关. 
matchexact: 精确匹配开关. 
gb: 只输入 gb2312 范围汉字. 

比如你可以这样设: 

    let g:ywvim_zy = {'listmax':6, 'maxphraselength':1, 'gb':0} 

意思是, 对于注音(zy)输入法, 候选框个数(listmax)为 6, 最大词长(maxphraselength)为 1, 只输入在 gb2312 范围的汉字('gb':0). 

你也可以全局设置某个变量, 格式是 let g:ywvim_listmax = 5, 这样就不用为每个码表都设相同的设置了. 下面都是全局变量. 

3. g:ywvim_zhpunc: 设置默认中文标点输入开关, 1 为开, 默认打开拼音输入, 2 为关. 

4. g:ywvim_listmax: 候选项个数. 

5. g:ywvim_esc_autoff: 设置离开插入模式时是否自动关闭 ywvim. 1 为自动, 0 为手动. 
(感谢在 #arch-cn@irc.oftc.net 的 snow 提的要求.) 

6. let g:ywvim_autoinput = 1: 支持两种程度的自动模式. 设为 2 为重度自动, 任何单码字都自动上屏. 2 为中度自动, 只在翻页时出现的单码字才上屏. 
(感谢在 #arch-cn@irc.oftc.net 上的 medicalwei 提供的建议) 

7. let g:ywvim_circlecandidates = 1: 设为 1 表示可以在候选页中循环翻页. 
(感谢在 #arch-cn@irc.oftc.net 上的 medicalwei 提供的建议) 

8. let g:ywvim_helpim_on = 0: 设为 1 表示打开反查码表的功能. 

    警告: 对于大码表会导致其速度降低. 

9. let g:ywvim_matchexact = 0: 设为 1 表示只显示全码匹配的字. 
(感谢在 #arch-cn@irc.oftc.net 上的 medicalwei 提供的建议) 

10. let g:ywvim_chinesecode = 1: 对于有中文字母的输入法(比如注音, 仓颉), 
已键入的字母用中文字母来显示, 而不是英文字母. 比如在注音里, 你输入 ji3 后, 
显示的是 ㄨㄛˇ, 而不是 ji3 
(感谢在 #arch-cn@irc.oftc.net 上的 medicalwei 提供的建议) 

11. let g:ywvim_gb = 1, 设为 1 为只输入 gb2312 范围汉字. 

12. let g:ywvim_preconv = 'g2b', 默认简繁转换方向. 

13. let g:ywvim_conv = 'g2b', 設置簡繁轉換方向, 'g2b' 為簡軟繁, 'b2g' 為繁轉簡, ''(留空)為關閉 
(感谢在 www.newsmth.net 上的 vace 提供的建议) 

14. let g:ywvim_lockb = 0, 为 0 时, 在空码是不锁定键盘. 

15. let g:ywvim_theme = 'light', 设置输入栏主题颜色, 可选 'light' 或 'dark'. 

16. let g:ywvim_intelligent_punc=1，打开智能标点，在数字后输入标点，默认输入英文状态标点，快速再输入同一个标点时，会替换成中文标点。 
    let g:ywvim_intelligent_punclist='.,:' 设置支持智能标点的标点符号。 

17. let g:ywvim_popupwin=1 使用vim8.2以上的弹窗特性显示候选项。 
    let g:ywvim_popupwin_follow_cursor=1 设置候选项弹窗为光标跟随。 
    let g:ywvim_popupwin_horizontal=1 设置弹窗的候选项水平排列。 
    let g:ywvim_popupwin_force_cmdline 在cmdline时强制使用popupwin特性。 

已知问题: 
========= 
1. 反查码表对于大码表反应速度过慢. 临时解决方案, 换词汇量较小的码表或者把 listmax 设小一点. 

2. cmdline中无法正常关闭popupwin。 

3. 窗口布局变化时（如Ctrl-w o）不能更新输入法状态提示。 

问题与建议反馈: 
===== 
请发反馈, 补丁或建议到 ywupub AT 163 DOT com. 

待做: 
============ 

码表格式: 
========= 
ywvim 用的码表是最简单的普通文本, 所以你可以很容易的定制出自己的码表. 请确保你的码表以 utf-8 的编码保存.

分四部分:[Description], [CharDefinition], [Punctuation] 和 [Main]. 顺序不能颠倒: 
[Description]是输入法的一般参数. 
[CharDefinition] 是给像注音, 仓颉等有中文字母的输入法用的. 
[Punctuation]是标点, [Main]是主码表. 

[Description] 
Name=倉頡五代   <== 码表名称. 
MaxCodes=5      <== 最大码长. 
MaxElement=1  <== 最大词长. 感谢在 www.newsmth.net 的 vace 的建议. 
UsedCodes=abcdefghijklmnopqrstuvwxyz <== 输入法所用到的键位 
EnChar=;    <= 临时输入英文的切换键. 
PyChar=z    <= 临时输入拼音键. 
InputZhSecKeys=; <= 输入第二重码键. 
下面选项均为注音用户所设, 其他输入法不必设置. 
EndCodes=  <= 结束字码的键位. 
InputZhKeys=  <= 输入中文的按键 
InputEnKeys=  <= 输入英文的按键 
AltPageUpKeys= <= 其他上翻页键 
AltPageDnkeys= <= 其他下翻页键 

[CharDefinition] 
a 日  <== 中文字母的定义在这里定义. 如果没有, 留空即可. 

[Punctuation] 
{ 『 
" “ ” 

[Main] 
a 日 曰 <== 由字码和汉字组成一行. 

常见问题: 
============ 
Q: 增加模糊查找? 增加自动调频? 
A: 对于像作者一样的单字形码用户, 模糊查找是完全用不到的功能, 所以没有兴趣也没有时间开发. 如果你希望有该特性, 请发补丁给我. 
而自动调频对于形码来说, 简直就是灾难, 但对音码来说可能很有用. 如果你觉得有用, 你也可以发补丁给我. 谢谢. 

======= English version ======= 
======= 
NOTE!!! 
======= 
If you are a ywvim's old user, before upgrade to the latest version, please have a look at *all* of the release notes and known bugs then look for the more details about the corresponding part of them in the description, because maybe some imcompatible changes have been made between your old version and the latest one. 
If you find a bug when using, please look at the "known bugs" section to make sure whether it's a know bug before you report. 

Download the lastest script(1.31): https://www.vim.org/scripts/download_script.php?src_id=27223 
Download the lastest mabiao(1.15): https://www.vim.org/scripts/download_script.php?src_id=27224 

Introduce: 
========== 
ywvim is an input method for vim without the help of any external input method tools, it can input chinese in all modes of vim. Its target user is mainly of 形码, and lacks many fancy features for 拼音 users, for such a featureful IM, please have a look at vimim[http://www.vim.org/scripts/script.php?script_id=2506]. 
Bad news: ywvim's key mappings conflict with vimim, you have to make a choice between them. 

settings in .vimrc: 
=================== 
put some lines like the following into your ~/.vimrc: 

----- 
let g:ywvim_ims=[ 
            \['wb', '五笔', 'wubi.ywvim'], 
            \['py', '拼音', 'pinyin.ywvim'], 
            \['cj', '仓颉', 'cangjie.ywvim'], 
            \['wb98', '五笔98', 'wubi98.ywvim'], 
            \['zm', '郑码', 'zhengma.ywvim'], 
            \['zy', '注音', 'zhuyin.ywvim'], 
            \['ar30', '行列', 'array30.ywvim'], 
            \] 

let g:ywvim_py = { 'helpim':'wb', 'gb':0 } 
let g:ywvim_zhpunc = 1 
let g:ywvim_listmax = 5 
let g:ywvim_esc_autoff = 0 
let g:ywvim_autoinput = 1 
let g:ywvim_intelligent_punc=1 
let g:ywvim_circlecandidates = 1 
let g:ywvim_helpim_on = 0 
let g:ywvim_matchexact = 0 
let g:ywvim_chinesecode = 1 
let g:ywvim_gb = 0 
let g:ywvim_preconv = 'g2b' 
let g:ywvim_conv = '' 
let g:ywvim_lockb = 0 
----- 

Usage: 
====== 
<Ctrl-Space>, <Ctrl-Shift-Space>, <Ctrl-@>, <Ctrl-\>    Toggle ywvim between on and off. 

;(semicolon)    Temporary English key. 

z, `            Temporary pinyin input key. (need a abbrev name 'py' pinyin mabiao in g:ywvim_ims) 

<Ctrl-^> setup ywvim: 
    码表切换. 
    中英标点切换. 
    候选项个数: candidates number. 
    最大词长: max pharase length. 
    简繁转换开关. 
    只输入GB2312. 
    辅助编码提示开关. 

,.-=        Pageup/pagedown. 

space or num key for input Chinese, Enter inputs English. 
; Select the second candiate. Thanks for vace on www.newsmth.net's suggestion.) 

NOTE for zhuyin users!!!: 
two continual space is pagedown. 
Enter is to select the defaut Chinese charator. 
English key and Pinyin key don't be bond to any keys by default(you can configure it). 

Details: 
============ 

g:ywvim_ims is a must-have variable among so many options. 

1. g:ywvim_ims is the variable that registers your input methods, the format is: 

      \['English_abbreviation_for_IM', 'Chinese_name_of_IM', 'mabiao_file'] 

For example, \['wb', '五笔', 'wubi.ywvim'], can be described as: wubi input method, English abbreviation is wb, mabiao file is wubi.ywvim. 
ywvim will try to search the dir and subdirs under it, and use the first one if there are files shared with the same name.. 
the first one is the defaut one. 
You can delete the lines of IM that you don't need at all. 

2. let g:ywvim_py = { 'helpim':'wb', 'gb':0 } 

You can setup a parameter which only has effect on a particular IM, IM's has higher priority on global's. Its format is: 

    g:ywvim_{English_abbreviation_for_IM} = {'parameter':'setting'} 

These parameters support local effect: 
listmax: candidates max number. 
maxphraselength: max length of phrase. 
helpim: help IM's English abbreviation. 
zhpunc: Input Chinese punctuations. 
matchexact: show only the exact matched. 
gb: set it to 1 means only input Chinese in gb2312. 

For instance you can setup like this: 

    let g:ywvim_zy = {'listmax':6, 'maxphraselength':1, 'gb':0} 

it means, for zhuyin(zy) IM, candidates max rumber(maxlist) is 6, max phrase(maxphraselength) is 1, only input Chinese in gb2312('gb':0). 

You also can setup a parameter globally, format is let g:ywvim_listmax = 5, so you can setup a parameter easily for every IM. 

3. g:ywvim_zhpunc: toggle the default Chinese punctuation on(1) or off(0). 

4. g:ywvim_listmax: maxmum number of candidates. 

5. g:ywvim_esc_autoff: whether auto toggle ywvim to be off when escaping from insertmode, 1 means yes, 0 no. 
(Thanks to snow on #arch-cn@irc.oftc.net who gave this feature request.) 

6. let g:ywvim_autoinput = 1:  supports two extends of auto input, set it to 2 is high auto, every singe candiate is auto inputted, 1 is media auto, just auto input when pageup/down. 
(Thanks for medicalwei on #arch-cn@irc.oftc.net's suggestion.) 

7. let g:ywvim_circlecandidates = 1: set to 1 means circle pages when reaching the end. 
(Thanks for medicalwei on #arch-cn@irc.oftc.net's suggestion.) 

8. let g:ywvim_helpim_on = 0: set it to 1 means support of help mabiao. 

    Warn: The speed is terrible slow for extremly large mabiao. 

9. let g:ywvim_matchexact = 0: set to 1 means only show the exact matched Chinese. 
(Thanks for medicalwei on #arch-cn@irc.oftc.net's suggestion.) 

10. let g:ywvim_chinesecode = 1: when set, show the Chinese alphabets instead of English. 
(Thanks for medicalwei on #arch-cn@irc.oftc.net's suggestion.) 

11. let g:ywvim_gb = 1, set it to 1 means only input Chinese in range of gb2312. 

12. let g:ywvim_preconv = 'g2b', define the preferred simplified-traditional conversion direction. 

13. let g:ywvim_conv = 'g2b', direction of auto convertion bwtween Simplified and Traditional Chinese. 'g2b' Simplified -> Traditional, 'b2g' Traditional -> Simplified, '' (Leave it blank) disables feature. 
(Thanks for vace on www.newsmth.net's suggestion.) 

14. let g:ywvim_lockb = 0, 0 means not to lock up the keyboard when there's no charactor matched with. 

15. let g:ywvim_theme = 'light', set color theme of IM bar, value should be 'light' or 'dark'. 

16. let g:ywvim_intelligent_punc=1 Turn on intelligent punctation support, when you input a punctation after numbers, the punctuation will be English punctuation, after input the same punctuation once more time quickly, the English punctuation will be replaced by Chinese one. 
    let g:ywvim_intelligent_punclist='.,:' Set up the punctuations that support the intelligent function. 

17. let g:ywvim_popupwin=1 candidate list supports popupwin feature of vim 8.2。 
    let g:ywvim_popupwin_follow_cursor=1 set the popupwin follows cursor. 
    let g:ywvim_popupwin_horizontal=1 set the candidate list in popupwin arranged horizontally. 
    let g:ywvim_popupwin_force_cmdline force to turn on the popupwin feature when at cmdline. 

Known Bugs: 
=========== 
1. Slow issue on big help mabiao. Workaround: use a relative small mabiao, or set the listmax to a smaller value. 

2. popupwin can't be closed when at cmdline (statusbar). 

3. Can't update the im indicator display when window layout changes (eg Ctrl-w o). 

Feedback: 
========= 
Please send the feedback, patch or advice to ywupub AT 163 DOT com. 

TODO: 
====== 

FAQ: 
============ 
Q: Supports fuzzy searching? Supports auto frequency? 
A: Author doesn't use fuzzy searching at all, but if you have patch, please send 
it to me. 
About auto frequency, it's a hell for shape input method, but maybe useful for pinyin users. If you can patch it, please do it and send the patch to the author. Thanks. 

Mabiao file format: 
=================== 
The mabiao which ywvim uses is just plaintext, so everyone can create his own mabiao easily. Please make sure the mabiao is in utf-8 fileencoding. 

Contains four fields: [Description], [CharDefinition], [Punctuation] and [Main]. They must be appeared in fire in sequences: 
[Description] general parameter of a input method. 
[CharDefinition] For the IM like zhuyin and cangjie that have Chinese alphabets. 
[Punctuation] contains punctuations, [Main] is the main part. 

[Description] 
Name=倉頡五代   <== mabiao's name. 
MaxCodes=5      <== Max code number. 
MaxElement=1  <== max phase length. Thanks for vace on www.newsmth.net's suggestion. 
UsedCodes=abcdefghijklmnopqrstuvwxyz <== All keys that needs to triggle IM input. 
EnChar=;    <= occasional English key. 
PyChar=z    <= occasional PinYin key. 
InputZhSecKeys=; <= Key for input the second candidate. 
Following is for ZhuYin alike IM, other IM don't need to set them at all. 
EndCodes=  <= Why keys mean input Chinese has ended. 
InputZhKeys=  <= Input Chinese's key. 
InputEnKeys=  <= Input English's key. 
AltPageUpKeys= <= Alternative keys for pageup. 
AltPageDnKeys= <= Alternative keys for pagedown. 

[CharDefinition] 
a 日  <== Definition of Chinese alphabets. If hasn't, leave it blank. 

[Punctuation] 
{ 『 
" “ ” 

[Main] 
a 日 曰 <== Char code and Chinese Charactors. 
 
install details
安装: 
===== 
要使用 ywvim, 你需要 ywvim.vim 脚本和至少一个码表. 要使用简繁转换功能, 你需要 g2b 简繁转换表. 要使用只输入 gb2312 里汉字功能, 你需要 gb2312 范围的汉字列表. 

当 ywvim 有新版本时, 一般只需更新脚本即可, 除非有专门通知提示你码表需要更新. 请确保你下的是最新的脚本和码表(版本不一定相同.) 

安装 ywvim： 
附件 ywvim.vim-<version>.tar.bz2 是 ywvim 脚本. 

解压脚本到你的 ~/.vim/plugin 目录下(windows 为 $VIM/vimfiles/plugin). 

        $ cd ~/.vim/plugin 
        $ unzip ywvim.vim.tar.bz2 

安装 ywvim 码表： 
附件 ywvim_mb-<version>.tar.bz2 包含了常用码表, 有注音, 行列, 仓颉, 拼音, 郑码, 五笔86 和 98 的码表, 一个 gb2312 范围的汉字列表, g2b 简繁转换表. 
(感谢在 #arch-cn@irc.oftc.net 上的 medicalwei 对注音提供的建议.) 
(感谢在 newsmth.net 上的 vace 对 g2b 提供的信息) 

解压码表到你的 ~/.vim/plugin 目录下(windows 为 vimfiles/plugin). 

        $ cd ~/.vim/plugin 
        $ unzip ywvim_mb.tar.bz2 

Install: 
======== 
You need both script and at least one of mabiao in order to make ywvim to work. You needs g2b.ywvim for simplified-traditional convertion. You needs gb2312 charactors list for inputing charactors only in gb2312 ranges. 

When ywvim has new version, it's general enough to update only the ywvim script, unless there is announcing that info you should need to update the mabiao. Please make sure you use the lastest version of script and mabiao(the version may not be the same). 

Install ywvim: 
The attachment ywvim.vim-<version>.tar.bz2 is the ywvim script itselt. 

Unpack the script into your ~/.vim/plugin. 

        $ cd ~/.vim/plugin 
        $ unzip ywvim.vim.tar.bz2 

Install ywvim mabiao: 

The attachment ywvim_mb-<version>.tar.bz2 contains some common input methods mabiao(码表): zhuyin, array, cangjie, pinyin, zhengma, wubi 86/98, a gb2312 charactors list, g2b Simplified and Traditional Chinese convertion list. 
(Thanks for medicalwei on #arch-cn@irc.oftc.net's suggestion on zhuyin.) 
(Thanks for vace on newsmth.net's info on g2b.) 

Unpack the mabiaos into your ~/.vim/plugin. 

        $ cd ~/.vim/plugin 
        $ unzip ywvim_mb.tar.bz2 
