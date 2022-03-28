[toc]

# 变量

## 一、系统变量

- 说明：变量由系统提供，不是用户定义，属于服务器层面

- 使用的语法：

1. 查看所有的系统变量

```mysql
show global | [session] variables;
```

2. 查看满足条件的部分系统变量

```mysql
show global | [session] variables like ‘%char%’;
```

3. 查看置顶的某个系统变量的值

```mysql
select @@global | [session].系统变量名;
```

4. 为某个系统变量赋值

- 方式一：

```mysql
set global | [seesion] 系统变量名 = 值;
```

- 方式二：

```mysql
set @@global | [session].系统变量名 = 值;
```

***注意***：如果是全局级别，则需要添加global；如果是会话级别，则需要添加session；如果没有写，则默认会话级别。

### 1》全局变量

1. 查看所有的全局变量

```mysql
show global variables;
```

2. 查看部分的全局变量

```mysql
show variables like ’%char%’;
```

3. 查看指定的全局变量的值

```mysql
select @@global.autocommit;
select @@global.tx_isolation;
```

1. 为某个指定的全局变量赋值

```mysql
set @@global.autocommit = 0;
set global autocommit = 1;
```

### 2》会话变量

- **作用域：**仅仅针对当前会话（连接）有效；
- **使用方式：**

1. 查看所有的会话变量

```mysql
show [session] variables;
```

2. 查看部分的会话变量

```mysql
show [session] variables like ‘%char%’;
```

3. 查看指定的会话变量

```mysql
select @@[session].会话变量名；
```

4. 为某个指定的会话变量赋值

```mysql
set @@[session].会话变量名 = 值;
set [session] 会话变量名 = 值;
```

## 二、自定义变量

- **说明：**变量是用户自定义的，不是由系统提供的；

- **使用步骤：**

1.    声明
2.    赋值
3.    使用（查看、比较、运算等）

### 1》用户变量

- **作用域：**针对当前会话（连接）有效，同于会话变量的作用域。应用在`任何地方`，也就是begin end里面或begin end外面

赋值操作符 = 或 :=

1. 声明并初始化

```mysql
set @用户变量名 = 值;
set @用户变量名 := 值;
select @用户变量名 := 值;
```

2. 赋值（更新用户变量的值）

- 方式一

```mysql
set @用户变量名 = 值;
set @用户变量名 := 值;
select @用户变量名 := 值;
```

- 方式二

```mysql
select column into @用户变量名 from 表;
```

3. 使用

```mysql
select @用户变量名;
```

### 2》局部变量

- 作用域：仅仅在定义它的begin end中有效，**必须应用在begin end中的第一句**！！！
- 使用方式：

1. 声明并初始化

```mysql
-- 声明
declare 变量名 类型;
-- 声明并初始化
declare 变量名 类型 default 值;
```

2. 赋值

- 方式一：使用set或select

```mysql
set 局部变量名 = 值;
set 局部变量名 := 值;
select @局部变量名 := 值;
```

- 方式二：使用select into

```mysql
select columnname into 局部变量名 from tablename;
```

3. 使用

```mysql
select 局部变量名;
```

### 3》对比用户变量和局部变量

|          | 作用域      | 定义和使用的位置              | 语法                            |
| -------- | ----------- | ----------------------------- | ------------------------------- |
| 用户变量 | 当前会话    | 当前会话中的任何位置          | 必须添加@符号，不用限定类型     |
| 局部变量 | begin end中 | 只能是begin end中，且为第一句 | 一般不用添加@符号，需要限定类型 |

### 4》案例

声明两个变量并赋初始值，求和，并打印

1. 用户变量

```mysql
set @m = 1;
set @n = 2;
set @sum = @m + @n;
select @sum;
```

2. 局部变量

```mysql
-- 该语句当前执行有误
declare m int default 1;
declare n int default 2;
declare sum int;
set sum = m + n;
select sum;
```













