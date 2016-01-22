title: 'PHP|MySQL|Smarty中时间格式化'
date: 2015-09-28 22:54:47
categories: [Smarty, PHP, MySQL]
tags: [PHP, MySQL, Smarty, 实习, 时间格式化]
---
这个问题来源于实习时需要在tpl上把时间增加时分秒，代码是使用Smarty模板，但是当时自己往代码中加的是PHP的时分秒“H:i:s”，所以一直不正确。自己后来还查了MySQL中跟时间有关的函数，现在都记录下来。
### PHP:

	<?php 
		echo $showtime=date("Y-m-d H:i:s");
	?>

a - "am" 或是 "pm" 
A - "AM" 或是 "PM" 
d - 几日，二位数字，若不足二位则前面补零; 如: "01" 至 "31" 
D - 星期几，三个英文字母; 如: "Fri" 
F - 月份，英文全名; 如: "January" 
h - 12 小时制的小时; 如: "01" 至 "12" 
H - 24 小时制的小时; 如: "00" 至 "23" 
g - 12 小时制的小时，不足二位不补零; 如: "1" 至 12" 
G - 24 小时制的小时，不足二位不补零; 如: "0" 至 "23" 
i - 分钟; 如: "00" 至 "59" 
j - 几日，二位数字，若不足二位不补零; 如: "1" 至 "31" 
l - 星期几，英文全名; 如: "Friday" 
m - 月份，二位数字，若不足二位则在前面补零; 如: "01" 至 "12" 
n - 月份，二位数字，若不足二位则不补零; 如: "1" 至 "12" 
M - 月份，三个英文字母; 如: "Jan" 
s - 秒; 如: "00" 至 "59" 
S - 字尾加英文序数，二个英文字母; 如: "th"，"nd" 
t - 指定月份的天数; 如: "28" 至 "31" 
U - 总秒数 
w - 数字型的星期几，如: "0" (星期日) 至 "6" (星期六) 
Y - 年，四位数字; 如: "1999" 
y - 年，二位数字; 如: "99" 
z - 一年中的第几天; 如: "0" 至 "365"
可以自由设定显示的内容,连接符号或是显示位置,例如 date("m-d H") 或者date("dmY");?>等

### Smarty:
index.php:

	$smarty = new Smarty;
	$smarty->assign('yesterday', strtotime('-1 day'));
	$smarty->display('index.tpl');

index.tpl:

	{$smarty.now|date_format}
	{$smarty.now|date_format:"%A, %B %e, %Y"}
	{$smarty.now|date_format:"%H:%M:%S"}
	{$yesterday|date_format}
	{$yesterday|date_format:"%A, %B %e, %Y"}
	{$yesterday|date_format:"%H:%M:%S"}

### MySQL：
获取系统日期： NOW()
格式化日期： DATE_FORMAT(date, format)
注： date：时间字段
format：日期格式
返回系统日期,输出 2015-09-29 14:38:59

	select now();

输出 15-09-29

	select date_format(now(),'%y-%m-%d');

format字符串格式化date值:

%S, %s 两位数字形式的秒（ 00,01, ..., 59）
%I, %i 两位数字形式的分（ 00,01, ..., 59）
%H 两位数字形式的小时，24 小时（00,01, ..., 23）
%h 两位数字形式的小时，12 小时（01,02, ..., 12）
%k 数字形式的小时，24 小时（0,1, ..., 23）
%l 数字形式的小时，12 小时（1, 2, ..., 12）
%T 24 小时的时间形式（hh:mm:ss）
%r 12 小时的时间形式（hh:mm:ss AM 或hh:mm:ss PM）
%p AM或PM
%W 一周中每一天的名称（Sunday, Monday, ..., Saturday）
%a 一周中每一天名称的缩写（Sun, Mon, ..., Sat）
%d 两位数字表示月中的天数（00, 01,..., 31）
%e 数字形式表示月中的天数（1, 2， ..., 31）
%D 英文后缀表示月中的天数（1st, 2nd, 3rd,...）
%w 以数字形式表示周中的天数（ 0 = Sunday, 1=Monday, ..., 6=Saturday）
%j 以三位数字表示年中的天数（ 001, 002, ..., 366）
%U 周（0, 1, 52），其中Sunday 为周中的第一天
%u 周（0, 1, 52），其中Monday 为周中的第一天
%M 月名（January, February, ..., December）
%b 缩写的月名（ January, February,...., December）
%m 两位数字表示的月份（01, 02, ..., 12）
%c 数字表示的月份（1, 2, ...., 12）
%Y 四位数字表示的年份
%y 两位数字表示的年份
%% 直接值“%”