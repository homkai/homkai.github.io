## 新接触的sql用法

### 行转列
```sql
/* schema:
event_date  field     content
2018-06-07  'field1'  'content1'
2018-06-08  'field2'  'content2'
 */
SELECT event_date,
MAX(CASE field WHEN 'field1' THEN content ELSE NULL END) AS field1,
MAX(CASE field WHEN 'field2' THEN content ELSE NULL END) AS field2
FROM tb WHERE field IN ('field1', 'field2') 
GROUP BY event_date
```