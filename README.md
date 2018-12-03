# Rime-backup
# 由于Rime稳定性欠佳，作者几次修改均深陷Bug推到重来。如无意外，以后本配置不再改动。
## 本篇目录
[TOC]

## 1. 前言 
### 1.1 安装与卸载 
&emsp; [小狼毫安装包](https://rime.im/)  
&emsp; **最简单的使用方法**安装完成后将文件复制到用户文件夹全部进行替换即可使用。(自定义配置，请参考压缩包里的 f-customize.txt 一份简明的配置说明 )。

### 1.2 本篇参考 

&emsp; [致第一次安装RIME的你](https://www.zybuluo.com/eternity/note/81763) （必读） 

&emsp; [RIME-小狼毫](https://www.jianshu.com/p/1ff29f75920a)（参考部分注释）

&emsp; [Rime输入法—鼠须管(Squirrel)词库添加及配置](https://www.jianshu.com/p/cffc0ea094a7)(参考如何自制词库)

&emsp; [我的 Rime](https://blog.dwx.io/my-rime/#Rime)（说明比较全）  

&emsp; 并鸣谢以上文章及其他网上教程的作者。

### 1.3 补丁制作方法 
&emsp; 创建一个文件名的主体部份（「.」之前）与要定制的文件相同、次级扩展名（「.yaml」之前）为.custom的定制文档：
```
patch:
  "一級設定項/二級設定項/三級設定項": 新的設定值
  "另一個設定項": 新的設定值
  "再一個設定項": 新的設定值
  "含列表的設定項/@n": 列表第n個元素新的設定值,从零开始计数
  "含列表的設定項/@last": 列表最後一個元素新的設定值
  "含列表的設定項/@before 0": 在列表第一個元素之前插入新的設定值（不建議在補靪中使用）
  "含列表的設定項/@after last": 在列表最後一個元素之後插入新的設定值（不建議在補靪中使用）
  "含列表的設定項/@next": 在列表最後一個元素之後插入新的設定值（不建議在補靪中使用）
```

### 1.4 其他注意事项 
&emsp; 所有个人的代码文件设置在`用户文件夹`即`~\AppData\Roaming\Rime`中操作。当用户需要对Rime 中的各种设定做小幅的调节，推荐的定制方法是：创建一个文件名的主体部份（「.」之前）与要定制的文件相同、次级扩展名（「.yaml」之前）为.custom的定制文档,修改完代码并保存之后都要重新部署。

## 2. 输入法界面操作 

### 2.1 输入时的切换
&emsp; 利用`ctral + ~ `打开输入法切换，可以切换各种输入法，繁简切换，中英文切换，半角全角切换以及日常字库（输入中文）及增广字库（输入其他语言）的切换

### 2.2 输入法方式和皮肤的快捷切换（慎用）
&emsp; ***慎用，会覆盖重写default.custom.yaml文件，导致其初始化。***    
&emsp; 右击托盘输入法图标打开`输入法设定`选项即可打开并勾选激活输入法页面（红色框中的图标）![avatar](http://ww1.sinaimg.cn/large/720db05fgw1eqljb9qfdwj203t014744.jpg)
再点击`中`打开输入法皮肤切换选项，选择完毕后再点击一次`中`确定并退出。

## 3. Rime常规全局配置

### 3.1 调整候选窗横竖排显示
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`weasel.custom.yaml`。
```
patch:
    "style/horizontal": false   # true为横排
```

### 3.2 调整字体字号
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`weasel.custom.yaml`。
```
patch:
    "style/font_face": "Microsoft YaHei "  # 字体名称，从记事本等系统字体对话框能看到。
    "style/font_point": 15     # 字号，只认数字的，不认「五号」、「小五」等
```

### 3.3 调整候选栏颜色样式
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`weasel.custom.yaml`。  
&emsp; 选择内置样式

```
patch:
    "style/color_scheme": google  # 谷歌皮肤
```
&emsp; 自定义样式
```
patch:
    "style/color_scheme": blue    # 這項用於選中下面定義的新方案
    "preset_color_schemes/blue":  # 在配色方案列表裏加入標識爲 blue 的新方案
    "name": blue
    "author": Cheng6774 , original artwork by Blizzard Entertainment
    "text_color": 0x000000             # 編碼行文字顏色，24位色值，用十六進制書寫方便些，順序是藍綠紅0xBBGGRR
    "candidate_text_color": 0x000000   # 候選項文字顏色，當與文字顏色不同時指定
    "back_color": 0xeceeee             # 底色
    "border_color": 0xeceeee           # 邊框顏色，與底色相同則爲無邊框的效果
    "hilited_text_color": 0x000000     # 高亮文字，即與當前高亮候選對應的那部份輸入碼
    "hilited_back_color": 0xd4d4d4     # 設定高亮文字的底色，可起到凸顯高亮部份的作用
    "hilited_candidate_text_color": 0xffffff  # 高亮候選項的文字顏色，要醒目！
    "hilited_candidate_back_color": 0xfa3a0a  # 高亮候選項的底色，若與背景色不同就會顯出光棒

在[这里](http://pan.baidu.com/s/1mi6vzmC)提供样式生成工具。
```

### 3.4 在特定程序里关闭中文输入
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`weasel.custom.yaml`。【小狼毫】0.9.16 亦开始支持这项设定。  
&emsp; 例如，要在photoshop里面默认关闭中文输入，可如此设定：
```
pathch:
    app_options/photoshop.exe: # 程序名字全用小写字母
    ascii_mode: true
```

### 3.5 定制候选栏词数
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`default.custom.yaml`。  
&emsp; 在RIME中默认是5候选数，而允许的范围是1~9（个别Rime 发行版可支持10个候选）。设定每页候选个数的为6个字。
```
patch:
    "menu/page_size": 6
```

### 3.6 调整输入法开启
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`default.custom.yaml`。
```
patch:
  schema_list:  # “输入选单”中激活的输入方案定义。
    - {schema: luna_pinyin_simp}       # 明月拼音简体
```

### 3.7 方案选项呼出热键
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`default.custom.yaml`。  
&emsp; 如修改热键为`Control+~`：
```
patch:
  "switcher/hotkeys":
    - "Control+grave"
```

### 3.8 中西文切换键设置
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`default.custom.yaml`。  
&emsp; 可选的临时切换策略有三种：
```
inline_ascii ：在输入法的临时西文编辑区内输入字母、数字、符号、空格等，回车上屏后自动复位到中文。
commit_text ：已输入的候选文字上屏并切换至西文输入模式。
commit_code ：已输入的编码字符上屏并切换至西文输入模式。
noop ：屏蔽该切换键。
```
&emsp; 例如要设置快捷键capslock的直接上屏功能:
```
  ascii_composer/good_old_caps_lock: true # 表示打开此功能
  ascii_composer/switch_key:              
    Caps_Lock: commit_code                # 摁capslook直接上屏
    Shift_L: commit_code
    Shift_R: commit_code
    Control_L: noop                       # 无反应
    Control_R: noop
```

### 3.9 输入法快捷键设置
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`default.custom.yaml`。  
&emsp; 如修改热键为`Control+p`，使其在打开输入候选项状态下为向上移动作用
```
patch:
 key_binder:
    bindings:
    - {accept: "Control+p", send: Up, when: composing}
```

### 3.10 输入法同步
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`installation.custom.yaml`。  
* 1.设置导出配置文件名为`E:\OneDrive - whut.edu.cn\software backup\Rime backup`。
```
    sync_dir: 'E:\OneDrive - whut.edu.cn\software backup\Rime backup'
```
* 2.设置导出的文件夹名称自定义名称Cheng。
```
    installation_id: "Cheng"
```
* 3.在桌面托盘中右键点击输入法图标选择`用户词典管理`，选择输入法后单击`输出词典快照`即可导出用户输入习惯数据库到同步路径中。
* 4.对同步路径下的`Cheng`文件夹进行移动或同步到新电脑。
* 5.在新电脑安装小狼毫后将`Cheng`文件夹移动到相同的`E:\OneDrive - whut.edu.cn\software backup\Rime backup`同步路径下。
* 6.在新电脑的桌面托盘中右击输入法图标选择`用户资料同步`并重新部署完成同步。

## 4. 词库设置
### 4.1 词库代码头设置
&emsp; 修改路径：`~\AppData\Roaming\Rime`。对明月拼音输入法的词库修改文件：`luna_pinyin.extended.dict.yaml`。  
&emsp; 词库开头先进行关于该词库的代码设置。
```
    ---                          # 代码开头分隔符
    name: luna_pinyin.sogou      # 这就是你自定义的词库的名字:sogou，后面还要用到
    version: "2015.XX.XX"        # 版本时间，最好填当前时间，要版本控制的意识
    sort: by_weight              # 开启按照字词比重排序方式
    use_preset_vocabulary: true  # 是否导入输入法预置词库
    ...                          # 代码结束分隔符，分隔符以下是具体字词表 
```

### 4.2 在词库中引入其他子词库
&emsp; 修改路径：`~\AppData\Roaming\Rime`。对明月拼音输入法的词库修改文件：`luna_pinyin.extended.dict.yaml`。  
&emsp; 例如引用搜狗核心词库。
```
import_tables:
  - luna_pinyin.sgmain        # 搜狗核心词库
```

### 4.3 手动添加字词到词库
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改相应的补丁词库：`xxx.dict.yaml`。  
&emsp; 在相应的补丁词库文件夹中，按照以下格式添加。
```
    [上屏词语](tab键)[输入的罗马拼音](tab键)[词语比重]
    输入的罗马拼音音节之间用space键分隔
```
&emsp; 例如：
```
    北海    bei hai 100
```

### 4.4 添加中文输入状态下的英文词库
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`luna_pinyin.cn_en.dict.yaml`。  
&emsp; 在该词库文件中按照4.3节方法操作即可。添加的英文单词可以在中文输入状态下输入字母后直接显示到输入候选单上。

### 4.5 从其他输入法导出自制词库
&emsp; 参考[Rime输入法—鼠须管(Squirrel)词库添加及配置](https://www.jianshu.com/p/cffc0ea094a7)

## 5 输入法文件设置(以明月简拼为例)
### 5.1 输入法的模式切换
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`luna_pinyin_simp.custom.yaml`。  
```
patch:
  switches:
    - name: ascii_mode           # 中英文切换
      reset: 0                   # 设置默认输入状态为中文
      states: ["中文", "西文"]    # 在方案选单中显示的样式
    - name: full_shape           # 半角全角切换
      states: ["半角", "全角"]    # 在方案选单中显示的样式
    - name: extended_charset     # 码表设置
      states: ["通用", "增廣"]    # 在方案选单中显示的样式
    - name: zh_simp              # 简繁体切换
      reset: 1                   # 强制简体输入
      states: ["漢字", "汉字"]    # 在方案选单中显示的样式
    - name: ascii_punct          # 中英文标点切换
      states: ["。，", "．，"]    # 在方案选单中显示的样式
```

### 5.2 输入法扩充词库载入
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`luna_pinyin_simp.custom.yaml`。  
```
patch:
  # 載入朙月拼音擴充詞庫
  "translator/dictionary": luna_pinyin.extended
```

### 5.3 标点符号及特殊表情设置
* 1. 先对符号及特殊表情词库symbols.yaml文件进行设置。symbols.yaml文件是系统文件，也可以自定义一份mysymbols.yaml文件覆盖系统文件，此时必须将系统文件symbols.yaml中的所有内容复制到自定义文件中。

* 2.  然后对输入法文件xxx.custom.yaml文件设置导入需要的符号文件(symbols或者mysymbols)。
    修改路径：`~\AppData\Roaming\Rime`。修改文件：`luna_pinyin_simp.custom.yaml`。
```
patch:
  # 标点及特殊表情...
  'punctuator/import_preset': symbols  # 或者将系统文件替换为mysmbols
  'recognizer/patterns/punct': "^/([a-z]+|[0-9])$"
```

### 5.4 模糊音设置
&emsp; 修改路径：`~\AppData\Roaming\Rime`。修改文件：`luna_pinyin_simp.custom.yaml`。  
&emsp; 根据已经写入的模糊音规则，需要哪一组取消对应的注释即可.

## 6. 本配置详细信息
&emsp; 除前文举例的代码已经写入配置文件以外，还有其他一些较为重要的配置情况一并列出:

### 6.1 词库信息
&emsp; 本配置附带所有词库如下:
```
  - luna_pinyin               # 系统自带词库，无意外必须开启。
  - luna_pinyin.anime         # 动漫词汇大全，动画、主要角色、声优等等。3w
  - luna_pinyin.chat          # 日常聊天常用词，请叫我聊天达人。3.5k
  - luna_pinyin.cn_en         # 中英混合词条
  - luna_pinyin.game          # 游戏名词
  - luna_pinyin.hanyu         # 汉语大詞典
  - luna_pinyin.history       # 历史相关
  - luna_pinyin.movie         # 电影相关词汇，片名、演员、导演等。1.3w
  - luna_pinyin.music         # 音乐相关词汇，歌曲、制作人、歌星之类的。2w
  - luna_pinyin.name          # 人名词库，知乎，含中外名人 1w
  - luna_pinyin.net           # 网络流行词，网上聊天常用的语句。3.6w
  # - luna_pinyin.phrase        # 输入拼音弹出的颜文字词库
  - luna_pinyin.poetry        # 常用诗词，来源于唐宋诗词、千家詩、花間集、楚辭、詩經。 2.6w
  - luna_pinyin.website       # 网站大全，百度、知乎等。5k
  # - luna_pinyin.extra_hanzi   # 生僻汉字库
  - luna_pinyin.sgmain        # 搜狗核心词库
  - luna_pinyin.sgplus        # 搜狗扩展词库1
  - luna_pinyin.sgplus2       # 搜狗扩展词库2 
  - luna_pinyin.user          # 词库增强包
  - luna_pinyin.english       # 英文单词库
#  - luna_pinyin.biaoqing      # 输入‘v v’弹出的颜文字词库
  - luna_pinyin.computer      # 计算机术语词库
  - luna_pinyin.place         # 地名词库
  - luna_pinyin.shopping      # 商品词库
  - luna_pinyin.contact       # 常用人名词库
  #以下不常用
  - luna_pinyin.emoji         # emoji表情词库
  - luna_pinyin.i             # 常用英文缩写词库
  - luna_pinyin.kaomoji       # 
  # 来源 搜狗细胞词库
  - c_botany                  # 植物学词汇
  - c_chemistry               # 化学化工词汇
  - c_computer                # 计算机词汇
  - c_finance                 # 金融词汇
  - c_geology                 # 地理地质词汇
  - c_medicine                # 中西医词汇
  - c_nalanxingde_all         # 纳兰性德185首
  - c_shijing_all             # 诗经全文
  - c_stock                   # 股票基金词汇
  - c_popular                 # 网络流行新词
  - c_ship                    # 船舶港口词汇
  - c_place                   # 全国地名大全
  - c_beihai_place            # 北海地名
  - c_beihai_language         # 北海方言
  - c_catering                # 餐饮词汇
  # 用于进行自定义设置
  - f_myphrases
  - f_mysecretphrase
   ```
   
### 6.2 输入法信息
&emsp; 本配置附带所有输入法如下:
```
    - {schema: luna_pinyin_fluency} # 明月拼音语句流
    - {schema: luna_pinyin_simp}    # 明月拼音简拼
    - {schema: BakHoi_JyutPing}     # 北海拼音
    - {schema: jyutping}            # 香港语言学会粤拼（运用最多）
    # - {schema: hkcantonese}         # 广东普通话（符合汉语规律）
    # - {schema: yale}                # 耶鲁粤拼（偏欧美发音）
    # - {schema: bopomofo}            # 注音
    # - {schema: bopomofo_express}    # 注音——快打模式
    # - {schema: bopomofo_tw}         # 注音——台湾正体
    # - {schema: cangjie5}            # 仓颉五代
    # - {schema: cangjie5_express}    # 仓颉五代——快打模式
    # - {schema: luna_pinyin}         # 明月拼音
    # - {schema: luna_pinyin_tw}      # 明月拼音——台湾正体
    # - {schema: luna_quanpin}        # 全拼
    # - {schema: stroke}              # 五笔画
    # - {schema: terra_pinyin}        # 地球拼音
    # - {schema: easy_en}             # easy english
    # - {schema: luna_pinyin_stroke}  # 明月拼音——笔画辅助码
```
