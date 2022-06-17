# bitmap_union_count 

## 功能

输入一组 bitmap 值，求这一组 bitmap 值的并集，并返回并集的基数

## 语法

```sql
BITMAP_UNION_COUNT(value)
```

### 参数说明

- `value` ：支持的数据类型为 BITMAP

## 返回值说明

返回值的数据类型为 BIGINT

## 示例

可以用该函数来计算网页的 PV 数据，假设 user_id 字段类型为 int，下面两个查询是等价的

```sql
select page_id, bitmap_union_count(to_bitmap(user_id))
from table
group by page_id;
```

```sql
select page_id, count(distinct user_id)
from table
group by page_id;
```