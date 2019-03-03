---
layout: post
title: Mysql连接数据库的几种方式
date: 2015-10-03
categories: php
tags: [Mysql]
---

* content
{:toc}

### 普通方法

```php
<?php
$con = msql_connect("localhost", "root", "");
if(!$con) {
    die('Could not connect: ' . mysql_error());
}
mysql_close($con);
```

### 面向对象mysqli

```php
<?php
$db = new mysqli("localhost", "root", "", "db1");
if(mysqli_connect_error()) {
    echo 'Could not connect to database';
    exit;
}
$result = $db->query('SELECT id FROM A');
$row = $result->fetch_row();
```

### PDO方法

```php
<?php
$db = new PDO('mysql:host=localhost;dbname=test', 'root', '');
try{
    foreach($db->query('select * from user') as $row) {
        print_r($row);
    }
}catch (PDOException $e) {
    echo $e->getMessage();
}
```

### ADODB连接

```php
<?php  
require_once './adodb5/adodb.inc.php';  
$conn = &ADONewConnection('mysql');  
$conn->connect('localhost','root','','test');  
$conn->Execute("set names utf8");  
$res = $conn->Execute("select * from user");  
if (!$res){  
    echo $conn->ErrorMsg();  
}else{  
    var_dump($res);  
}  
```