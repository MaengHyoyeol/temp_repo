# Quicksort

Quicksort는 **정렬** 알고리즘 으로 **선택 정렬**보다 훨씬 빠르다.

**정의 :  퀵정렬은 정렬할 전체 원소에 대해서 정렬을 수행하지 않는다. **

**먼저  기준 값을 중심으로 전체 원소들을  왼쪽 부분집합과 오른쪽 부분집합으로 분할(Divide)한다.**

**왼쪽 부분 집합에는 기준 값보다 작은 원소들을 이동시키고,**

**오른쪽 부분 집합에는 기준 값보다 큰 원소들을 이동시킨다.**

출처: [http://palpit.tistory.com/126](http://palpit.tistory.com/126) [palpit's log-b]

## Pivot 값 기준으로 정렬
![](http://pds15.egloos.com/pds/200911/15/58/a0119358_4affcec4003e8.jpg)


## Python Code

    def quicksort(array):
	    if len(array) < 2:
		    return array
		else:
			pivot = array[0]
			less = [i for i in array[1:] if i <= pivot]
			greater = [i for i in array[1:] if i > pivot]
			
			return quicksort(less) + [pivot] + quicksort(greater)
 

##  BigO 표기법

![]( https://image.slidesharecdn.com/random-130302184603-phpapp02/95/-7-638.jpg?cb=1410677317)

![]( http://cfile24.uf.tistory.com/image/997C473359EB396712C8FC)

> Written with [StackEdit](https://stackedit.io/).
