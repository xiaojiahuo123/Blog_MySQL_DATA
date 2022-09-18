```sql
-- select 用于读取数据表中的数据
-- 通过 * 把users表中所有的数据获取到
select * from users
-- 查询表中对应的列中的某些字段（指定），可以像下面一样做，注意字段之间使用 ， 分割
select username,password from users
-- 下面的是像一个表中的列插入对应的数据，insert into 后面是对应的表，而在后面的是要插入数据的
-- 这个表的列，在后面使用VALUES 插入对应的数据，注意因为是string类型所以使用‘’包裹，
-- 后面的values和前面的列应该是一一对应的，从顺序上来说。
-- insert into 用于向数据表中插入数据
insert into users (username,password) values ('tony','098123')
select * from users
-- updata 用于数据表中数据的更新
-- 将id为4的用户的密码更新为 888888
update users set password = '888888' where id=4
-- select * from users
-- 以下是将id为2的用户的密码和状态更改为 admin123 和 1 ，只需要在指定表之后指定多个列,之间
-- 用 ， 分割，最后加上where（执行条件）就可以了
update users set password = 'admin123' , status = 1 where id=2
-- select * from users
-- delete 用于删除数据表中的行
-- delete from 表名 where 列名称 = 值
delete from users where id=4
-- select * from users
-- where 是用来加条件的，在select ,update , delete 中都可以使用，使得他们只对对应条件的数
-- 据进行对应的操作
-- 如下，查询id大于2的用户
select * from users where id>2
-- and 和 or 运算符 ，and表示同时必须满足多个条件，or表示满足其中·1一个条件就行
select * from users where status=0 and id=3
select * from users where status=0 or id=2
-- order by 默认进行升序排序，asc 关键字代表升序排序 desc关键字代表降序排序
select * from users order by id
-- 多重排序,对users表数据，先按照status进行升序排序，再按照 username 的字母顺序进行升序排序
select * from users order by status , username desc
-- count(*)函数用来返回查询结果的总数据条款，语法格式如下：
select count(*) from 表名称
-- select count(*) from users where status=0 //这是查询在users表中，status为0的总数据条数
-- AS为列设置别名，比如：
select count(*) as total from users where status=0

```

![](D:\临时文件\md用的\F5V29T$`OWSL}HNTW}K3H[8.png)

##### 在node.js中操作数据库(MySQL):

###### 导入mysql模块：

```js
npm i mysql//导入mysql模块
const mysql = require('mysql');
//建立于MySQL数据库的连接关系
const db = mysql.createPool({
    host:'127.0.0.1', //数据库的ip地址
    user:'root',          //登录数据库的账号
    password:'2698078621sty', //账号的密码
    database:'my_db_01' //数据库名称
})

// db.query('select 1',function(error,results){
//     if(error) return console.log(error.message);
//      console.log(resu
lts);
// })

//查询
// const sqlStr = 'select * from users'
// db.query(sqlStr,(error,results)=>{
//    if(error) return console.log(error.message);
//    console.log(results);
// })


//插入数据
const sqlStr = 'insert into users (username,password) values (?,?)'
const user = {username:'Spider-Man',password:'pcc321'}
db.query(sqlStr,[user.username,user.password],(error,results)=>{
    if(error) return console.log(error.message);
    if(results.affectedRows === 1){
        return console.log('数据插入成功!');
    }  //注意，数据库插入之后不能再次执行，因为已经存在这个数据
    console.log(results);
})

```





```sql
PK：primary key 主键

NN：not null 非空

UQ：unique 唯一索引

BIN：binary 二进制数据(比text更大的二进制数据)

UN：unsigned 无符号     整数（非负数）

ZF：zero fill 填充0 例如字段内容是1 int(4), 则内容显示为0001 

AI：auto increment 自增

G：generated column 生成列

在mysql查询语句中加\g、\G的意思：

\g  的作用是分号和在sql语句中写“；”是等效的
\G  的作用是将查到的结构旋转90度变成纵向（换行打印）


```


