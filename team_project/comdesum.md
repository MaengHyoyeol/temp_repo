#  Walmart Recruiting II: Sales in Stormy Weather (Kaggle)
*Kaggle* 에 있는  [Walmart Sales in Stormy Weather](https://www.kaggle.com/c/walmart-recruiting-sales-in-stormy-weather) 프로젝트를 진행합니다.

# codesum column  전처리

weather.csv 의  codesum 은 특별한  event가 일어났는지를 명시해 주고 있다.

이를 분석하기 위해서 전체 codesum을 Bag of words 방식으로 카테고리 분포형태의 Matrix으로

변환 시켜줘야 한다.

 1. 우선 전체 event에 대한 column을 만들어 주었다.
 빈 df  생성

 <code>

	codesum = pd.DataFrame(columns = ['+FC', 'FC', 'TS', 'GR', 'RA', 'DZ', 'SN', 'SG', 'GS', 'PL', 'IC', 'FG+', 'FG', 'BR', 'UP', 'HZ', 'FU', 'VA', 'DU', 'DS', 'PO', 'SA', 'SS', 'PY', 'SQ', 'DR', 'SH', 'FZ', 'MI', 'PR', 'BC', 'BL', 'VC'])

</code>

2. 다음으로  전체 경우에서 한번도 나오지 않은 event는 제외시켜 주기 위해 각 event가 발생한 횟수를 찾아보았다,

<code>

	count = 0
	for i in codesum.columns:
	    for j in weather_DF['codesum']:
	        if i in j:
	            count += 1
    print(i, count)

</code>

**[결과값]**
![](c/../capture/event_count.PNG)

FC ,  FC+, IC, VA, DS, PO, SA, PY, DR, SH 는 일어난적이 없으므로  제거해주면

<code>

	codesum = pd.DataFrame(columns = ['TS', 'GR', 'RA', 'DZ', 'SN', 'SG', 'GS', 'PL', 'FG+', 'FG', 'BR', 'UP', 'HZ', 'FU', 'DU', 'SS', 'SQ', 'FZ', 'MI', 'PR', 'BC', 'BL', 'VC'])

</code>

로 rename할 수 있다.

3. **Dataframe 만들기**

	 0으로 채운 weather.csv와 raw가 같도 codesum columns를 가진 test dataframe을 만든후 그안에 event가 생길 경우 
	 1로 바꿔주는 코드

<code>

	for i in range(len(weather_DF)):
	    for event in weather_DF['codesum'].loc[i].split(' '):
            if event:
           
                if len(event) >= 4:
                    test[event[:2]].loc[i] = 1
                    test[event[2:]].loc[i] = 1
        
                else:
                    test[event].loc[i] = 1
</code>

	 
> Written with [StackEdit](https://stackedit.io/).
