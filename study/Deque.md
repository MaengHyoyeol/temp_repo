
---
<!--
page_number: true
$size: A4
footer : 프로그래밍 스터디2 - Deque

-->
# Programming Study
## **[2주차] 덱(Deque)**
###### (자료구조와 알고리즘)
---
# 1. Deque
---
# 1-1. Deque? Double Ended Queue!
#
-  Deque과 Queue와 다른 점은 삽입과 삭제를 한쪽이 아닌 앞, 뒤 양쪽에서 할 수 있다는 것만 다르며 Queue와 같습니다.
>![](http://image.hanb.co.kr/blog/7609/1245239861@stl_05_01.gif)
>Queue
>![](http://image.hanb.co.kr/blog/7609/1245239894@stl_05_02.gif)
>Deque
- FIFO(First In First Out) / LIFO(Last In First Out) : 둘 다 사용 가능.
---
# 1-2. Deque 의 특징
#
1. 크기가 가변적이다. (List <-> array)
2. 앞과 뒤로 삽입/ 삭제 가능. <-> 중간에 데이터 삽입 삭제가 어렵다.
>![](http://image.hanb.co.kr/blog/7609/1245239908@stl_05_03.gif)
> 중간에 데이터를 삽입
>![](http://image.hanb.co.kr/blog/7609/1245239995@stl_05_04.gif)
> 중간 데이터를 삭제
- http://www.hanbit.co.kr/channel/category/category_view.html?cms_code=CMS3942847236
---
# 1-3. Deque의 사용
#
 게임 서버에서 deque를 사용하는 경우 

게임 서버는 클라이언트에서 보낸 패킷을 차례대로 처리합니다. 서버에서 네트워크 데이터를 받는 함수에서 데이터를 받으면 패킷으로 만든 후 받은 순서대로 순차적으로 처리합니다. 이렇게 순차적으로 저장한 패킷을 처리할 때는 deque가 가장 적합한 자료구조입니다. 다만, 실제 현업에서는 이 부분에 STL의 deque를 사용하지 않는 경우가 종종 있습니다. 이유는 네트워크에서 데이터를 받아 패킷으로 만들어 저장하고, 그 패킷을 처리하는 부분은 게임 서버의 성능 면에서 가장 중요한 부분이므로 deque보다 더 빠르게 처리하기를 원하므로 독자적인 자료구조를 만들어 사용합니다(즉, 범용성보다는 성능을 우선시합니다).

---
# 1-4 Deque의 응용
<pre><code>
<<<<<<< HEAD
import collections
 
d = collections.deque([10, 20, 30, 40, 50])
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50])
 
# 오른쪽에 추가
d.append(60)
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50, 60])
</code></pre>
----
<pre><code>
# 왼쪽에 추가
d.appendleft(0)
print('Deque: ', d)
# 'Deque: ', deque([0, 10, 20, 30, 40, 50, 60])
 
# 입력값을 순환하면서 오른쪽에 추가(append)
d.extend([70, 80])
print('Deque: ', d)
# 'Deque: ', deque([0, 10, 20, 30, 40, 50, 60, 70, 80])
</code></pre>
---
<pre><code>
# 입력값을 순환하면서 왼쪽에 추가(appendleft)
d.extendleft([-10, -20, -30])
print('Deque: ', d)
# 'Deque: ', deque([-30, -20, -10, 0, 10, 20, 30, 40, 50, 60, 70, 80])
 
# 값 삭제
d.remove(0)
print('Deque: ', d)
# 'Deque: ', deque([-30, -20, -10, 10, 20, 30, 40, 50, 60, 70, 80])
 
# 오른쪽의 끝값 가져오면서 deque에서 제거
maxValue = d.pop()
print('maxValue:', maxValue)
# maxValue: 80
print('Deque: ', d)
# Deque:  deque([-30, -20, -10, 10, 20, 30, 40, 50, 60, 70])
</code></pre>

---

<pre><code>
# 왼쪽의 끝값 가져오면서 deque에서 제거
minValue = d.popleft()
print('minValue:', minValue)
# minValue: -30
print('Deque: ', d)
# Deque:  deque([-20, -10, 10, 20, 30, 40, 50, 60, 70])
 
# 값 회전(rotating)
d = collections.deque(range(5))
print('Deque: ', d)
# Deque:  deque([0, 1, 2, 3, 4])
 
d.rotate(1)
print('Deque.rotate(1): ', d)
# Deque.rotate(1):  deque([4, 0, 1, 2, 3])

</code></pre>

---
<pre><code>

=======

from collections
 
d = collections.deque([10, 20, 30, 40, 50])
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50])
 
# 오른쪽에 추가
d.append(60)
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50, 60])
 
# 왼쪽에 추가
d.appendleft(0)
print('Deque: ', d)
# 'Deque: ', deque([0, 10, 20, 30, 40, 50, 60])


</code>
</pre>


---

<pre><code>

import collections
 
d = collections.deque([10, 20, 30, 40, 50])
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50])
 
# 오른쪽에 추가
d.append(60)
print('Deque: ', d)
# 'Deque: ', deque([10, 20, 30, 40, 50, 60])
 
# 왼쪽에 추가
d.appendleft(0)
print('Deque: ', d)
# 'Deque: ', deque([0, 10, 20, 30, 40, 50, 60])
 
# 입력값을 순환하면서 오른쪽에 추가(append)
d.extend([70, 80])
print('Deque: ', d)
# 'Deque: ', deque([0, 10, 20, 30, 40, 50, 60, 70, 80])
</code>
</pre>

-----

<pre><code>
# 입력값을 순환하면서 왼쪽에 추가(appendleft)
d.extendleft([-10, -20, -30])
print('Deque: ', d)
# 'Deque: ', deque([-30, -20, -10, 0, 10, 20, 30, 40, 50, 60, 70, 80])
 
# 값 삭제
d.remove(0)
print('Deque: ', d)
# 'Deque: ', deque([-30, -20, -10, 10, 20, 30, 40, 50, 60, 70, 80])
 
# 오른쪽의 끝값 가져오면서 deque에서 제거
maxValue = d.pop()
print('maxValue:', maxValue)
# maxValue: 80
print('Deque: ', d)
# Deque:  deque([-30, -20, -10, 10, 20, 30, 40, 50, 60, 70])
 
# 왼쪽의 끝값 가져오면서 deque에서 제거
minValue = d.popleft()
print('minValue:', minValue)
# minValue: -30
print('Deque: ', d)
# Deque:  deque([-20, -10, 10, 20, 30, 40, 50, 60, 70])
</code>
</pre>

-----

<pre><code>
# 값 회전(rotating)
d = collections.deque(range(5))
print('Deque: ', d)
# Deque:  deque([0, 1, 2, 3, 4])
 
d.rotate(1)
print('Deque.rotate(1): ', d)
# Deque.rotate(1):  deque([4, 0, 1, 2, 3])
 
>>>>>>> master
d.rotate(1)
print('Deque.rotate(1): ', d)
# Deque.rotate(1):  deque([3, 4, 0, 1, 2])
 
d.rotate(-1)
print('Deque.rotate(-1): ', d)
# Deque.rotate(-1):  deque([4, 0, 1, 2, 3])
 
d.rotate(-1)
print('Deque.rotate(-1): ', d)
# Deque.rotate(-1):  deque([0, 1, 2, 3, 4])
<<<<<<< HEAD
=======
</code>
</pre>

------
<pre><code>

from collections import deque

dQ = deque(maxlen = 4)

dQ.append('aa')

dQ.append('bb')

dQ.append('cc')

dQ.append('dd')

print(dQ)
#deque(['aa', 'bb', 'cc', 'dd'], maxlen=4)


dQ.append('ee')

print(dQ)
#deque(['bb', 'cc', 'dd', 'ee'], maxlen=4)
>>>>>>> master

</code>
</pre>
> Written with [StackEdit](https://stackedit.io/).
