## Upcoming Products > Mobile Device Info > Developer's Guide

> ※ 본 문서는 alpha 개발 단계의 문서입니다.
> 사용에 관심이 있으신 분은 **support@cloud.toast.com**으로 문의해 주시기 바랍니다.

## 조회 

[API 도메인]

|환경|	도메인|
|---|---|
|Real|	https://api-mail.cloud.toast.com|

### 디바이스 조회 

#### 요청

[URL]

|Http method|	URI|
|---|---|
|GET|	/mobiledevice/v1.0/appKeys/{appKey}/device|

[Path parameter]

|값|	타입|	설명|
|---|---|---|
|appKey|	String|	고유의 appKey|

[Query parameter]

|값|	타입|	필수|	설명|
|---|---|---|---|
|deviceModelCode|	String|	X|	디바이스 모델 코드|
|deviceModelName|	String|	X|	디바이스 모델명|
|sort|	String|	X|	정렬옵션|
|pageNum|	String|	X|	페이지 번호(default=1)|
|pageSize|	String|	X|	페이지당 노출할 디바이스 정보 수(default=15)|

[참고] sort : 정렬 옵션
정렬 필드와 정렬기준(오름/내림차순)을 입력합니다.  
 - 정렬 필드 
    - 여러 개의 필드를 기준으로 정렬할 경우 Comma(,)로 구분하여 입력합니다.  
 - 정렬 기준 
    - 오름차순으로 정렬할 경우 필드이름 입력합니다.
    - 내림차순으로 정렬할 경우 필드이름 앞에 '-'를 추가합니다.


##### 정렬 필드 정보 

|필드 이름|필드 설명|
|---|---|
|deviceModelCode|디바이스 모델 코드|
|deviceModelName|디바이스 모델명|
|deviceModelDetailName|디바이스 상세 모델명|
|deviceSeries|디바이스 시리즈|
|osVersion|OS Vers.|
|launchYear| 출시년도|
|manufactureCompany|제조사|
|telecom|통신사|
|launchCountryCode|제조국가|
|gearTypeCode|장비타입|

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
            "deviceModelName":String,
            "deviceModelDetailName":String,
            "deviceSeries":String,
            "osVersion":String,
            "launchYear":String,
            "manufactureCompany":String,
            "telecom":String,
            "launchCountryCode":String,
            "gearTypeCode":String
         }
      ]
   }
}
```

|값|	타입|	설명|
|---|---|---|
|header|	Object|	헤더 영역|
|- isSuccessful|	Boolean|	성공여부|
|- resultCode|	Integer|	실패 코드|
|- resultMessage|	String|	실패 메시지|
|body|	Object|	본문 영역|
|- data|	List |	데이터 영역|
|-- deviceModelCode|	String|	디바이스 모델코드 |
|-- deviceModelName|	String|	디바이스 모델명 |
|-- deviceModelDetailName|  String| 디바이스 상세 모델명 |
|-- deviceSeries|  String| 디바이스 시리즈 |
|-- osVersion| String| OS Version|
|-- launchYear|  String| 출시년도 |
|-- manufactureCompany| String| 제조사 |
|-- telecom|  String| 통신사 |
|-- launchCountryCode| String| 출시국가|
|-- gearTypeCode|  String| 장비타입 |

