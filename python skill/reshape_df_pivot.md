# DataFrame Reshaping

이 포스트는 [nikgrozev](http://nikgrozev.com/) pivot 포스팅을 정리한 것이며 허락을 받고 인용하였습니다.

## pivot

The [pivot](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.pivot.html) function is used to create a new derived table out of a given one. Pivot takes 3 arguements with the following names: index, columns, and values. 
<code>
	from collections import OrderedDict
	from pandas import DataFrame
	import pandas as pd
	import numpy as np

	table = OrderedDict((
    ("Item", ['Item0', 'Item0', 'Item1', 'Item1']),
    ('CType',['Gold', 'Bronze', 'Gold', 'Silver']),
    ('USD',  ['1$', '2$', '3$', '4$']),
    ('EU',   ['1€', '2€', '3€', '4€'])
	))

	df = DataFrame(table)
</code>

[ex_dp]
![
](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/table.png)


이와같은 data에서 Customertype(CType) 별 USD를 알고 싶으면 **PIVOT** 을 이용해 df을 변활 할 수 있다.

<code>
p = df.pivot(index='Item', columns='CType', values='USD')
</code>

![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/pivoting_simple1.png)

Pivot 이전  DataFrame에서 Item0/ Gold customers 의 가격(USD) 을 찾기 
<code>
     **df[(d.Item=='Item0') & d.CType=='Gold')].USD.values**

</code>

Pivot 이후(**Pivoted DataFrame**)  DataFrame에서 Item0/ Gold customers 의 가격(USD) 을 찾기 

<code> **df[df.index=='Item0'].Gold.values**
</code>
 
 *Pivot을 자유롭게 다루어야 원하는 data를 뽑아낼 수 있다.*
> Written with [StackEdit](https://stackedit.io/).
