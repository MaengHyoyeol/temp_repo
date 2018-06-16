
## Dataframe int 변환

Dataframe 전체의 integer 로 변환 가능한 숫자들을 변환해주는 방법.

그 동안은  apply를 통해 한 row씩 해주었다.
<code>
df.apply(lambda x: int(x)
</code>

 - **새로운 방법!**
 : pd.numeric 을 통해 전체 변환, error 를 핸들링
<code>

df.apply(pd.to_numeric, errors = 'igonre')

</code>

dataframe 전체 변환 가능하며
integer(float)로 변환하지 못하는 예외를 처리해줄수 있다.

> Written with [StackEdit](https://stackedit.io/).
