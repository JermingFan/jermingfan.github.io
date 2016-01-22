title: Smarty比较操作符
date: 2015-09-29 12:39:16
categories: [Smarty, PHP]
tags: [PHP, Smarty, 实习, 比较操作符]
---
eq相等，
ne、neq不相等，
gt大于，
lt小于，
gte、ge大于等于，
lte、le 小于等于，
not非， mod求模。 
is [not] div by是否能被某数整除，
is [not] even是否为偶，
$a is [not] even by $b即($a / $b) % 2 == 0，
is [not] odd是否为奇，
$a is not odd by $b即($a / $b) % 2 != 0 示例：
equal/ not equal/ greater than/ less than/ less than or equal/ great than or equal
Smarty 中的 if 语句和 php 中的 if 语句一样灵活易用，并增加了几个特性以适宜模板引擎. if 必须于 /if 成对出现。 可以使用 else 和 elseif 子句。
可以使用以下条件修饰词：eq、ne、neq、gt、lt、lte、le、gte、ge、is even、is odd、is not even、is not odd、not、mod、div by、even by、odd by、==、!=、>、<、<=、>=. 
使用这些修饰词时必须和变量或常量用空格格开。