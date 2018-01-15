## Mobile Service > Mobile Device Info > API Guide

## 검색

[API 도메인]

|환경|	도메인|
|---|---|
|Real|	http://api-mobiledevice.cloud.toast.com|

### 디바이스 검색

#### 요청

[URL]

|Http method|	URI|
|---|---|
|GET|	/mobiledevice/v1.0/appKeys/{appKey}/device|

[Path parameter]

|값|	타입|	설명|
|---|---|---|
|appKey|	String|	고유 appKey|

[Query parameter]

|값|	타입|	필수|	설명|
|---|---|---|---|
|deviceModelCode|	String|	X|	디바이스 모델 코드|
|deviceModelName|	String|	X|	디바이스 모델명|
|sort|	String|	X|	정렬 옵션|
|pageNum|	Integer|	X|	페이지 번호 (기본값=1)|
|pageSize|	Integer|	X|	페이지당 노출할 디바이스 정보 수 (기본값=15)|

* [참고] sort : 정렬 옵션
* 정렬 필드와 정렬 기준(오름/내림차순)을 입력합니다.
    * 정렬 필드 : 여러 개의 필드를 기준으로 정렬할 경우 콤마(,)로 구분하여 입력합니다.
    * 정렬 기준 : 오름차순으로 정렬할 경우 필드 이름을 입력합니다. 내림차순으로 정렬할 경우 필드 이름 앞에 '-'를 추가합니다.
<br>

##### 정렬 필드 정보

|필드 이름|필드 설명|
|---|---|
|deviceModelCode|디바이스 모델 코드|
|deviceModelName|디바이스 모델명|
|osCode| OS 정보|
|launchYear| 출시연도|
|manufactureCompany|제조사|
|telecom|통신사|
|gearTypeName|장비 유형|


##### Sample Request 

디바이스 모델 코드가 SM-G035P인 디바이스 검색
```
GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/TEST/device?deviceModelCode=SM-G935P
```

디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색

```
GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy
```

디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색 - 출시연도(launchYear) 내림차순 정렬
```
GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy&sort=-launchYear
```

디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색 - 통신사(telecom) 필드 오름차순 정렬 후, 출시연도(launchYear) 필드 내림차순 정렬
```
GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy&sort=telecom,-launchYear
```


#### 응답

```
{  
   "header":{  
      "isSuccessful":Boolean,
      "resultCode":Integer,
      "resultMessage":String
   },
   "body":{  
      "pageNum":Integer,
      "pageSize":Integer,
      "totalCount":Integer,
      "data":[  
         {  
            "deviceModelCode":String,
            "osCode":String,
            "deviceModelName":String,
            "launchYear":String,
            "manufactureCompany":String,
            "telecom":String,
            "gearTypeName":String
         }
      ]
   }
}
```

|값|	타입|	설명|
|---|---|---|
|header|	Object|	헤더 영역|
|- isSuccessful|	Boolean|	성공 여부|
|- resultCode|	Integer|	실패 코드|
|- resultMessage|	String|	실패 메시지|
|body|	Object|	본문 영역|
|- data|	List |	데이터 영역|
|-- deviceModelCode|	String|	디바이스 모델 코드 |
|-- osCode| String| OS 정보|
|-- deviceModelName|	String|	디바이스 모델명 |
|-- launchYear|  String| 출시연도 |
|-- manufactureCompany| String| 제조사 |
|-- telecom|  String| 통신사 |
|-- gearTypeName|  String| 장비 유형 |
