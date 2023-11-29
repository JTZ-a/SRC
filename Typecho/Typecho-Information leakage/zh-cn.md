# Typecho-Information leakage

## 描述

在向 `http://localhost/admin/manage-users.php?page=` 发送请求时后台限制接受的参数必须为数字， 如果我们传入其他内容则会报错， 在报错信息中泄露网站的安装目录

## 验证

![image-20231129163630661](./assets/image-20231129163630661.png)