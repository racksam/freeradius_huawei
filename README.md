# 华为Radius属性导入FreeRadius


某些厂家的属性如果在freeradius没有内置的话，可以手工导入。这里以华为Radius属性为例说明导入的方法。

1. 将厂家的dictionary文件保存至`/usr/share/freeradius/`目录下。

    如果厂家没有提供官方文件的话，可以自己编辑一个dictionary。这里是我自己编辑的两个文件：`dictonary.huwei2`以及`dictonary.huawei3`。由于对很多属性不熟悉，所以可能有些属性的数据类型不准确。
    
2. 编辑`/usr/share/freeradius/dictionary`，添加以下两行：

    ```
    $INCLUDE dictionary.huawei2
    $INCLUDE dictionary.huawei3
    ```   
     
3. 重新启动radiusd：

    ```
    systemctl restart radiusd
    ```

4. 【可选】如果需要在daloradius系统中的属性下拉框中出现新添加的厂家属性的话，可以使用SQL语句，将这些属性导入到dictionary表中。

    ```
    mysql> source ./import_dictionary_huawei.sql
    ```
    
参考：[华为RADIUS属性](http://htmlpreview.github.io/?https://github.com/racksam/freeradius_huawei/blob/master/02-RADIUS-Huawei.htm)    