## Dataframe - iterrow() 

data frame 에서 iterating을 하면 column순서로 진행하게 된다.

하지만 iterrow()를 이용하면 row 순서대로 iterate할 수 있다.
<code>
df = pd.DataFrame([[1, 1.5]], columns=['int', 'float'])
 row = next(df.iterrows())[1]
row

int      1.0
float    1.5
Name: 0, dtype: float64

print(row['int'].dtype)
float64

 print(df['int'].dtype)
int64
</code>

![](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iterrows.html)

> Written with [StackEdit](https://stackedit.io/).
