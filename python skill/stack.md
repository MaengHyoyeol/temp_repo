# DataFrame Reshaping - 3

##   Stack/Unstack

Stacking a DataFrame means moving (also rotating or pivoting) the innermost column index to become the innermost row index.

![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/stack-unstack1.png)

stack 과  unstack 
stack은 column 에 잇는 series를  index로
unstack은 index에 잇는 series를 column 으로 보내준다.

다중 데이터를 필요한 index로 뽑기위해 상황에 맞게 사용해주어야한다.

##  Common Mistake in Pivoting

How will the pivot method determine the value of the corresponding cell in the pivoted table? The following diagram depicts the problem:

![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/pivoting_simple_error.png)

위 그림 처럼 pivoting을 할때 Gold/Item0에 어떠한 값이 들어가야 하는지 처리 문제가 발생한다.
  
  ![](http://nikgrozev.com/images/blog/Reshaping%20in%20Pandas%20-%20Pivot%20Pivot-Table%20Stack%20and%20Unstack%20explained%20with%20Pictures/stack-simple2.png)

> Written with [StackEdit](https://stackedit.io/).


> Written with [StackEdit](https://stackedit.io/).
