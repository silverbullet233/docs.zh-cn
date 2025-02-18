# CREATE VIEW

## 功能

该语句用于创建一个逻辑视图。

## 语法

```sql
CREATE VIEW [IF NOT EXISTS]
[db_name.]view_name
(column1[ COMMENT "col comment"][, column2, ...])
AS query_stmt;
```

说明：

1. 逻辑视图没有物理存储，所有在视图上的查询相当于在视图对应的子查询上进行。

2. query_stmt 为任意支持的 SQL。

## 示例

1. 在 example_db 上创建逻辑视图 example_view。

    ```sql
    CREATE VIEW example_db.example_view (k1, k2, k3, v1)
    AS
    SELECT c1 as k1, k2, k3, SUM(v1) FROM example_table
    WHERE k1 = 20160112 GROUP BY k1,k2,k3;
    ```

2. 创建一个包含 comment 的逻辑视图。

    ```sql
    CREATE VIEW example_db.example_view
    (
    k1 COMMENT "first key",
    k2 COMMENT "second key",
    k3 COMMENT "third key",
    v1 COMMENT "first value"
    )
    COMMENT "my first view"
    AS
    SELECT c1 as k1, k2, k3, SUM(v1) FROM example_table
    WHERE k1 = 20160112 GROUP BY k1,k2,k3;
    ```
