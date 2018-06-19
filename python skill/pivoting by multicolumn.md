# DataFrame Reshaping - 2 

##  Pivoting By Multiple Columns

ach indexed column/row is identified by a unique sequence of values defining the “path” from the topmost index to the bottom index. The first level of the column index defines all columns that we have not specified in the pivot invocation - in this case USD and EU. The second level of the index defines the unique value of the corresponding column. This is depicted in the following diagram:

![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/pivoting_simple_multicolumn.png)

item을 index로 UD/ EU column으로 multi column  indexing

##  Common Mistake in Pivoting

How will the pivot method determine the value of the corresponding cell in the pivoted table? The following diagram depicts the problem:

![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/pivoting_simple_error.png)

위 그림 처럼 pivoting을 할때 Gold/Item0에 어떠한 값이 들어가야 하는지 처리 문제가 발생한다.
  
ValueError: Index contains duplicate entries, cannot reshape

위와 같은 ValueError가 일어나며 이를 해결해주기위해

<code><span>

	table = OrderedDict((
    ("Item", ['Item0', 'Item0', 'Item0', 'Item1']),
    ('CType',['Gold', 'Bronze', 'Gold', 'Silver']),
    ('USD',  ['1',  '2',  '3',  '4']),
    ('EU',   ['1€', '2€', '3€', '4€'])
	))
	d = DataFrame(table)
	p = d.pivot(index='Item', columns='CType', values='USD')

와 같은 방법으로 df를 재정리 해줘야 한다.

In essence _pivot_table_ is a generalisation of _pivot_, which allows you to aggregate multiple values with the same destination in the pivoted table.

</span></code>
> Written with [StackEdit](https://stackedit.io/).
