--- 
title: 解决mysql：ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO/YES)
date: 2020-06-29
categories: 
 - backEnd
tags: 
 - mysql
---

## 问题

有时候我们登录Mysql输入密码的时候，会出现这种情况<br>
```shell
mysql -u root -p 
Enter Password > '密码'
错误：ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
或者：错误：ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```
解决办法：
* 1.重启mysql
```shell
net stop mysql;
net start mysql;
```
* 2.进入mysql，登录
```shell
mysql -u root -p
## 不用输入密码，直接回车，即使出现Enter Password，也一样直接回车，可以登录成功
```
* 3.修改root的密码
```shell
use mysql;
update user set authentication_string=password('新密码') where user='root';
flush privileges;
```
* 4.退出
```shell
exit;
```
* 5.再次重启mysql
```shell
net stop mysql;
net start mysql;
```
* 6.测试是否能登录成功
mysql -u root -p
Enter Password>'新密码'


