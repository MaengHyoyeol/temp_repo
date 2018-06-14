# RAW data 가공하기

**Raw data**에서 필요한 정보를 추출하는 coding.

Raw data가 CSV가 아니라 해석을 하는데 어려움을 격었다.

excel로 읽어본 결과 \n으로 구별된 data이며 한 row에 대한 해석은

포함된 해설 파일에 index가 있어 원하는 곳을 slicing 해야한다.

    
	data_set = []
	with open("file.name", 'rt', encoding='ISO-8859-1') as f:
  
 

 - encoding 방법을 찾는데 어려움을 겪엇다. 엑셀은 cp-949로 잘 읽엇으나  ipython에서는 되지 않았으며 엑셀에서 다른 파일로 변환하거나 ISO-8859로 엔코딩 해야했다.
한글이 깨지는데 np.array의 데이터 타입 문제인지 encoding문제인지 파악이 필요하다.

 
		data=f.readlines()
    
	    for line in data:
        data_set.append(np.array(line.split(',')))` 

    
	    

 - 조건에 맞는 종목ID를 추출하는 함수이다. 종목 위치 index가  18~30이다.

 - 위에 readline으로 읽은 것이 2중 배열로 저장되는데 한 차원을 푸는 방법을 알아봐야겠다. 



		def productIDset(data):
		    product_ID = [ array[0][(17+18):(17+30)] for array in data_set if 
                      ((array[0][17:(17+5)]=='A0016') & (array[0][(17+408):(17+411)] == 'BM3') & (array[0][(17+454):(17+457)] == '001'))]
   
		    return product_ID

 - 필요한 데이터 추출



    
	    def ex_data(data):
		    return_array = [ [array[0][1:9], array[0][(17+23):(17+31)],array[0][(17+31):(17+37)], array[0][(17+228):(17+234)], array[0][(17+144):(17+152)], array[0][(17+135)], \
                array[0][(17+218):(17+225)], array[0][(17+136):(17+143)] ]                                                                 
                    for array in data_set
                             if ((array[0][(5+17):(17+17)] == 'KR4165N30007') & ((array[0][17:(17+5)] == 'A3016') or
                              (array[0][17:(17+5)] == 'G7016')))]
		    return return_array

 - [1:9]. head를 제외한 [23: 31 ] , [31:37], [228:234],  [144: 152], [135,],[218: 225],  [136 :  143] 을 뽑아내는 list comprehension
 - return 값을 여러개로 나누는 방법도 고려 해볼 것.
> Written with [StackEdit](https://stackedit.io/).
