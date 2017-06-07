# MySQL 基础知识

1. 关于行级锁，表锁
   在事物中，只有执行`statement.executeUpdate`的时候才会上锁，SQL语句不同，上的锁也不同。
   `UPDATE test SET name='aaa' WHERE id = 23`，此SQL有`WHERE`条件，上的是行级锁，
   `UPDATE test SET name='aaa' `，此SQL无`WHERE`条件，上的是表锁
