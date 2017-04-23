# for developer

## 环境搭建

## TODOS
*  选择key value数据库
*  抓取豆瓣图片的图书名，并用合适的方式储存，例如储存成纯文本文件，或者放在mysql当中等等
*  实现recall算法，生成key-value, 其中key为用户输入的内容，比如recaller的degision中提到的,`西`,`xiy`,`xi游`,`西yo`,`xyj`,`xy`,`xyouj`,`xiyj`,val为可能的suggesstion，同时把key-value用合适的方式组织起来，比如说直接通过写key-value数据库当中，或者用tries一些数据结构储存在内存当中
*  设计reranker实现方法

## recall算法
比如书名是，三重门，可以生成全拼，sanchongmen，和sanzhongmen，注意多音字因为重可以有两个读音，chong,zhong。

1. 那么，sanchongmen，和sanzhongmen的前缀，都应该召回，三重门，对于sanzhongmen有，s,sa,san,sanc,sanch,sancho,sanchon,sanchong,sanchongm,sanchongme,sanchongmen，11个key，
对于sanzhongmen也是类似的，将也有11个key。

1. san chong men,三个汉字的前缀也应该可以召回三重门。san有三种前缀，s, sa,san ，　chong有5个前缀，c,ch,cho,chon,chong, men，有3个前缀，m, me, men，那么三个前缀的组合将有，353＝45个。
另外 sanzhongmen，也将有45个前缀组合。

所以，三重门，能有11+11+45+45=112　个可能的key,　这里面有重复的key需要去掉，比如sanzhongmen出现在第1部门，也出现在第二部分,　sanzhongm, shanzhongme, 也是，另外对于sanchongmen也会有3个重复的项目，那么三重门，应该112 - 6 = 106个key
