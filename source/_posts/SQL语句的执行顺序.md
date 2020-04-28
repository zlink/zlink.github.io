---
title: SQL语句的执行顺序
date: 2018-07-20 23:34:08
tags: mysql
---

知道怎么执行的才能更好的优化 sql 的写法。

### FORM

对 FROM 的左边的表和右边的表计算笛卡尔积。产生虚表 VT1

### ON

对虚表 VT1 进行 ON 筛选，只有那些符合`<join-condition>`的行才会被记录在虚表 VT2 中。

### JOIN

如果指定了 OUTER JOIN（比如 left join、 right join），那么保留表中未匹配的行就会作为外部行添加到虚拟表 VT2 中，产生虚拟表 VT3, rug from 子句中包含两个以上的表的话，那么就会对上一个 join 连接产生的结果 VT3 和下一个表重复执行步骤 1~3 这三个步骤，一直到处理完所有的表为止。

### WHERE

对虚拟表 VT3 进行 WHERE 条件过滤。只有符合`<where-condition>`的记录才会被插入到虚拟表 VT4 中。

## GROUP BY

根据 group by 子句中的列，对 VT4 中的记录进行分组操作，产生 VT5.

### CUBE | ROLLUP

对表 VT5 进行 cube 或者 rollup 操作，产生表 VT6.

### HAVING

对虚拟表 VT6 应用 having 过滤，只有符合`<having-condition>`的记录才会被 插入到虚拟表 VT7 中。

### SELECT

执行 select 操作，选择指定的列，插入到虚拟表 VT8 中。

### DISTINCT 对 VT8 中的记录进行去重。产生虚拟表 VT9

### ORDER BY

将虚拟表 VT9 中的记录按照`<order_by_list>`进行排序操作，产生虚拟表 VT10.

### LIMIT

取出指定行的记录，产生虚拟表 VT11, 并将结果返回。

---

### 写的顺序

select ... from... where.... group by... having... order by.. limit [offset,]

### 执行顺序

from... where...group by... having.... select ... order by... limit
