長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
a<-"https://www.ptt.cc/bbs/NBA/index.html"
b<-"https://www.ptt.cc/bbs/NBA/index4630.html"
c<-"https://www.ptt.cc/bbs/NBA/index4629.html"
d<-"https://www.ptt.cc/bbs/NBA/index4628.html"
e<-"https://www.ptt.cc/bbs/NBA/index4627.html"
f<-"https://www.ptt.cc/bbs/NBA/index4626.html"
vec<-c(a,b,c,d,e,f)
Total<-NULL
for(i in vec){
  NBAContent<-read_html(i)
post_title<-NBAContent %>%
html_nodes(".title") %>%
html_text()
post_PushNum<-NBAContent %>%
html_nodes(".nrec") %>%
html_text()
post_author<- NBAContent %>%
html_nodes(".author") %>%
html_text()
tempPage<- data.frame(title=post_title,PushNum=post_PushNum,
                          author=post_author)
  Total<-rbind(Total,tempPage)
  next
}
NBA_posts<-Total
#knitr::kable(NBA_posts[1:100,c("title","PushNum","author")])
```

爬蟲結果呈現
------------

``` r
knitr::kable(
  NBA_posts[1:100,c("title","PushNum","author")]) 
```

| title                                            | PushNum | author       |
|:-------------------------------------------------|:--------|:-------------|
| Re: \[BOX \] Cavaliers 93:99 Bulls 數據          | 22      | youngluke    |
| Re: \[討論\] 勒布朗到底強在哪裡？                | 8       | david1003    |
| \[新聞\] 魯比歐創生涯新高33分　灰狼輕取湖人      | 52      | pneumo       |
| \[新聞\] 35年前的今天 喬丹寫下第一個震驚世人的   | 6       | brandon0415  |
| \[新聞\] NBA》史密斯尬贏豪小子 活塞1分險勝籃網   | 8       | jay0601zzz   |
| Re: \[討論\] 有人跟我一樣比較喜歡以前的LBJ嗎 ?   | 7       | Ayanami5566  |
| \[新聞\] 詹皇總得分超越大歐 騎士遭公牛橫掃       | 21      | james008     |
| Re: \[討論\] 勒布朗到底強在哪裡？                | 5       | wmigrant     |
| \[閒聊\] Caldwell-Pope遭到逮捕                   | 7       | dragon803    |
| \[BOX \] Clippers 124:118 Suns 數據              | 10      | Rambo        |
| \[討論\] Rubio是否之前都在演戲?                  | 10      | c1236        |
| \[討論\] 騎士這季會50勝嗎？                      | 8       | marcus40     |
| \[公告\] 板規6.1                                 |         | kadasaki     |
| \[公告\] 違規檢舉區                              | 爆      | kadasaki     |
| \[情報\] 2016-2017 例行賽 (3/27 - 4/3)           | 72      | gap6060      |
| \[公告\] 2017 板主選舉                           | 25      | kadasaki     |
| \[討論\] 有一種拋投叫？（東尼拋克獲勝！）        | 爆      | gn00167236   |
| \[情報\] Rookie Ladder Week 21                   | 17      | Vedan1213    |
| \[情報\] 溜馬嘗試簽回Lance Stephenson            | 17      | dragon803    |
| \[情報\] 溜馬與Stephenson簽下三年1200萬合約      | 51      | k960674      |
| \[情報\] 前籃網新秀有興趣歸化菲律賓              | 30      | pipi8963     |
| \[Live\] 老鷹 @ 七六人                           | 4       | Rambo        |
| \[Live\] 雷霆 @ 魔術                             | 爆      | Rambo        |
| \[Live\] 公鹿 @ 超賽                             | 14      | Rambo        |
| \[Live\] 黃蜂 @ 暴龍                             | 4       | Rambo        |
| \[Live\] 熱火 @ 尼克                             | 5       | Rambo        |
| \[Live\] 溜馬 @ 灰熊                             | 7       | Rambo        |
| \[Live\] 小牛 @ 鵜鶘                             | 14      | Rambo        |
| \[討論\] Curry+CP3                               |         | harry1234585 |
| \[專欄\] 塞爾蒂克再升級 東區天平正在改變LYS      | X8      | zzyyxx77     |
| Re: \[專欄\] 塞爾蒂克再升級 東區天平正在改變LYS  | 70      | st900278     |
| \[Live\] 勇士 @ 馬刺                             | 爆      | Rambo        |
| (本文已被刪除) \[feyako\]                        | 16      | -            |
| \[情報\] KD復原情況良好                          | 25      | sthho        |
| \[討論\] 07馬刺打騎士，是實力差距最大的總冠嗎    | 爆      | s106667      |
| \[BOX \] Hawks 99:92 Sixers 數據                 | 19      | Rambo        |
| (本文已被刪除) \[MrSatan\]                       | 98      | -            |
| Re: \[討論\] Rose是不是偷了Lebron的MVP啊         | 23      | FeiWenKing   |
| \[討論\] 勇迷會希望KD早早回歸嗎?                 | 22      | omare        |
| \[情報\] Dennis Smith Jr, Harry Giles 投入選秀會 | 31      | thnlkj0665   |
| \[討論\] 哪些球星算是自帶系統的球星？            | 64      | wmigrant     |
| \[公告\]昨日判罰疑問                             | 75      | namie810303  |
| Re: \[討論\] Curry VS CP3 選誰?                  | 39      | yokann       |
| Re: \[情報\] NBA Standings(2017.03.29)           | 3       | sasolala     |
| \[公告\]水桶 改判 以及增加                       | 53      | namie810303  |
| \[花邊\] LeBron James是最難防守的球員? Jimmy Bu  | 34      | hector30618  |
| \[討論\] 現役球隊中，哪一隊打起來最毛躁？        | 34      | fxxk         |
| Re: \[討論\] 現役球隊中，哪一隊打起來最毛躁？    | 41      | carotyao     |
| Re: \[討論\] Curry VS CP3 選誰?                  | 17      | zxc25678     |
| \[情報\] ★今日排名(2017.03.29)★                  | 4       | Rambo        |
| (本文已被刪除) \[Hachiko\]                       | 1       | -            |
| \[新聞\] Marion造訪中興大學 有信心打敗勇士       | 58      | iam168888888 |
| \[情報\] Harden談傷勢                            | 88      | dragon803    |
| (本文已被刪除) \[Turtle100\]                     | 1       | -            |
| \[情報\] 溜馬將裁掉Rodney Stuckey                | 71      | jc0209       |
| \[外絮\] 塞爾提克 將舉辦2008年總冠軍十週年的聚會 | 30      | thnlkj0665   |
| \[BOX \] Nuggets 113:122 Blazers 數據            | 81      | Rambo        |
| \[BOX \] Wizards 119:108 Lakers 數據             | 61      | Rambo        |
| Re: \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩   | X2      | c1236        |
| Re: \[討論\] NBA球員有拿過大滿貫的?              | 29      | Price        |
| Re: \[討論\] 留KD或Curry？                       | 爆      | arbcs        |
| \[情報\] ESPN:馬刺4：0擊敗去年東西冠軍           | 47      | Yui5         |
| \[新聞\] 諾克奇33分轟前東家金塊　拓荒者老8之爭   | 26      | JAL96        |
| \[情報\] NBA Standings(2017.03.29)               | 爆      | kadasaki     |
| \[公告\] NBA 板 開始舉辦樂透!                    | 8       | kadasaki     |
| \[外絮\] Is it time to sit James Harden?         | 40      | djviva       |
| \[新聞\] 史上第一人！哈登總得分與助攻得分破2000  | 24      | adam7148     |
| \[討論\] D.Russell是不是骰子型球員?              | 79      | tiffanycute  |
| Re: \[討論\] NBA球員有拿過大滿貫的?              | 16      | hayuyang     |
| \[新聞\] 尼克如何變強？ 何總：補進更好的防守者   | 21      | pttpepe      |
| (本文已被刪除) \[nogoodlaugh\]                   |         | -            |
| \[討論\] 為什麼雙基奇搭配不起來？                | 21      | eatk         |
| \[討論\] 浪花勇士是否是哈登永遠的痛?             | 27      | yenyu73      |
| (本文已被刪除) \[knic52976\]                     |         | -            |
| \[討論\] Rose是不是偷了Lebron的MVP啊             | X6      | knic52976    |
| \[新聞\] 勇士連3年60勝 公牛王朝後首見            | 61      | lovea        |
| \[Live\] 勇士 @ 火箭                             | 96      | Rambo        |
| \[新聞\] 年度教練競爭激烈 柯爾力挺丹東尼         | 30      | pneumo       |
| \[討論\] 籃網RHJ這個球員......                   | 23      | ronharper    |
| \[BOX \] Bucks 118:108 Hornets 數據              | 37      | Rambo        |
| \[Live\] 金塊 @ 拓荒者                           | 44      | Rambo        |
| \[BOX \] Timberwolves 115:114 Pacers 數據        | 51      | Rambo        |
| \[BOX \] Sixers 106:101 Nets 數據                | 92      | Rambo        |
| \[BOX \] Suns 91:95 Hawks 數據                   | 20      | Rambo        |
| \[新聞\] 上場時間決定MVP？　哈登：我從未缺席比   | 28      | zzyyxx77     |
| \[BOX \] Heat 97:96 Pistons 數據                 | 21      | Rambo        |
| \[Live\] 巫師 @ 湖人                             | 34      | Rambo        |
| \[新聞\] 林書豪關鍵走步失誤　籃網惜敗76人        | 29      | jhemezuo     |
| \[BOX \] Warriors 113:106 Rockets 數據           | 爆      | Rambo        |
| \[新聞\] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗  | 34      | zzzz8931     |
| \[討論\] 沒KD 勇士還是不可小看                   | 14      | feyako       |
| Re: \[討論\] 去年快艇如何守哈登買飯集錦          | 17      | bluestaral   |
| \[情報\] Kerr fastest coach in American sports   | 72      | Angel0724    |
| \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩       | 4       | lcall        |
| \[討論\] 留KD或Curry？                           | 爆      | star1739456  |
| \[討論\] 穩進季後賽的火箭，仍然最多一輪          | X3      | sunnycello   |
| \[討論\]John Wall 算東區第一控了嗎？             | 爆      | h1212123tw   |
| Re: \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥  | 2       | tadshift2    |
| (本文已被刪除) \[MrSatan\]                       | 1       | -            |
| \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳    | 69      | zzzz8931     |

解釋爬蟲結果
------------

``` r
str(NBA_posts)
```

    ## 'data.frame':    116 obs. of  3 variables:
    ##  $ title  : Factor w/ 111 levels "\n\t\t\t\n\t\t\t\t[BOX ] Clippers 124:118 Suns 數據\n\t\t\t\n\t\t\t",..: 13 15 12 9 10 14 11 15 8 1 ...
    ##  $ PushNum: Factor w/ 60 levels "","10","21","22",..: 4 11 7 8 11 9 3 6 9 2 ...
    ##  $ author : Factor w/ 68 levels "Ayanami5566",..: 14 4 11 2 8 1 7 13 5 12 ...

用str()可以看到一共爬出109篇文章。

``` r
table(NBA_posts$author)
```

    ## 
    ##  Ayanami5566  brandon0415        c1236    david1003    dragon803 
    ##            1            1            2            1            3 
    ##      gap6060     james008   jay0601zzz     kadasaki     marcus40 
    ##            1            1            1            5            1 
    ##       pneumo        Rambo     wmigrant    youngluke            - 
    ##            2           27            2            1            8 
    ##   gn00167236 harry1234585      k960674     pipi8963      s106667 
    ##            1            1            1            1            1 
    ##     st900278        sthho    Vedan1213     zzyyxx77     carotyao 
    ##            1            1            1            2            1 
    ##   FeiWenKing         fxxk  hector30618 iam168888888       jc0209 
    ##            1            1            1            2            1 
    ##  namie810303        omare     sasolala   thnlkj0665       yokann 
    ##            3            1            1            2            1 
    ##     zxc25678     adam7148        arbcs       djviva         eatk 
    ##            1            1            1            1            1 
    ##     hayuyang        JAL96    knic52976        lovea        Price 
    ##            1            1            1            1            1 
    ##      pttpepe  tiffanycute      yenyu73         Yui5    Angel0724 
    ##            1            1            1            1            1 
    ##   bluestaral       feyako     jhemezuo        lcall    ronharper 
    ##            1            1            1            1            1 
    ##  star1739456   sunnycello     zzzz8931     BBDurant   ccps970915 
    ##            1            1            2            1            1 
    ##       Gotham   h1212123tw        Jachu  steveparker    tadshift2 
    ##            1            1            1            1            1 
    ##      tmacor1       Wall62    ZaneTrout 
    ##            1            1            1

用table()可以看到在NBA的ptt版上,有一位叫 Rambo的人很常發文,從上面的資料我們可以看到他總共發了26篇文章。

整體分析資料結果: 1.從爬出來的資料我們可看到在NBA這個版上的文章被噓的文章並不是很多,除非太過於主觀支持哪一方的文章才會被噓。 2.我們還可以看到只要\[Live\]文章每一篇都有人推,有些推文數還不少。 3.在讚爆的文章分類中我們可以看到在NBA\[討論\]文章中佔的比例比較多。 4.很多\[Live\]的文章都是Rambo這個使用者Po的。
