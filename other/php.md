# php

[toc]

---

## 小技巧

`error_log` 打印array变量： `error_log(print_r($array_data, 1));`



`print_r()` 函数用于打印变量，以更容易理解的形式展示；

`var_dump()` 函数用于输出变量的相关信息。

统计list的长度： `count($li)`





### php foreach遍历

link: [url](https://blog.csdn.net/qq_36497590/article/details/90513945)

两次连续遍历同一个数组并且使用相同的变量名，并且第一次使用引用的方式遍历，会导致第二次遍历的最后一个元素和倒数第二个元素变成一样的。

```php
		foreach ($rows as &$row) {
               $detail = self::getAdvertiserAccountDetailByDate($row['uid'], $row['date_format']);
               $row['cash_balance'] = $detail['cash_balance'];
               $row['rebate_balance'] = $detail['rebate_balance'];
        }
            
      	foreach ($rows as $row) {
        		$t = [];
        		foreach ($keys as $key) {
            		$t[] = $row[$key];
        		}
        		$content .= implode(',', $t) ."\n" ;
    	}
```



解决方法：

1. 两次遍历采用不同的变量名

2. 不使用引用遍历，使用索引去遍历，如上第一次遍历采用如下方式

  ```php
  foreach ($rows as $k =>$row) {
              $detail = self::getAdvertiserAccountDetailByDate($row['uid'], $row['date_format']);
              $rows[$k]['cash_balance'] = $detail['cash_balance'];
              $rows[$k]['rebate_balance'] = $detail['rebate_balance'];
       }
  ```

3. 在两次遍历中间，unset($row)
  