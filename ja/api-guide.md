## Mobile Service > Mobile Device Info > API Guide

Mobile Device Info 서비스를 사용하는 데 필요한 API를 설명합니다.

## API 공통 정보

### 사전 준비

* API 사용을 위해서는 앱 키가 필요합니다.
* 앱 키는 상단 "URL & Appkey" 메뉴에서 확인 가능합니다.

### 요청 공통 정보

[API 도메인]

|환경|	도메인|
|---|---|
|리얼|	http://api-mobiledevice.cloud.toast.com|

[Path 파라미터]

* 모든 API는 앱 키를 path 파라미터에 지정해야 합니다.

|이름|	설명|
|---|---|
|appKey|	콘솔에서 확인한 앱 키|

### 응답 공통 정보

* 모든 API 요청에 대해서 200 OK로 응답합니다. 자세한 응답 결과는 응답 본문의 헤더를 참고합니다.

[성공 응답 본문]
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    }
}
```

[실패 응답 본문]
```json
{
    "header": {
        "isSuccessful": false,
        "resultCode": -1000,
        "resultMessage": "Invalid appKey."
    }
}
```

## 검색

### 디바이스 검색

* 디바이스를 검색하는 API입니다. 결괏값으로 디바이스 목록을 가져옵니다.

#### 요청

[URL]

|메서드|	URI|
|---|---|
|GET|	/mobiledevice/v1.0/appKeys/{appKey}/device|


[필드]

|이름|	타입|	필수 여부|	기본값|	유효 범위| 설명|
|---|---|---|---|---|---|
|deviceModelCode|   String |    선택|	  |	|	디바이스 모델 코드|
|deviceModelName|	String |	선택|	  |	최소 2글자|	디바이스 모델명|
|sort           |	String |	선택|   | |	정렬 옵션|
|pageNum        |	Integer|	선택|	 1|	|	페이지 번호|
|pageSize       |	Integer|	선택|	15|	|	페이지당 노출할 정보 수|


[정렬 옵션 필드 상세정보]

* 정렬 필드와 정렬 기준(오름/내림차순)을 입력합니다.
    * 정렬 필드 : 여러 개의 필드를 기준으로 정렬할 경우 콤마(,)로 구분하여 입력합니다.
    * 정렬 기준 : 오름차순으로 정렬할 경우 필드 이름을 입력합니다. 내림차순으로 정렬할 경우 필드 이름 앞에 '-'를 추가합니다.

|이름|설명|
|---|---|
|deviceModelCode|디바이스 모델 코드|
|deviceModelName|디바이스 모델명|
|osCode| OS 정보|
|launchYear| 출시연도|
|manufactureCompany|제조사|
|telecom|통신사|
|gearTypeName|장비 유형|


[요청 샘플]

* 디바이스 모델 코드가 SM-G035P인 디바이스 검색
    ```
    GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/TEST/device?deviceModelCode=SM-G935P
    ```

* 디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색
    ```
    GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy
    ```

* 디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색 - 출시연도(launchYear) 내림차순 정렬
    ```
    GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy&sort=-launchYear
    ```

* 디바이스 모델 이름에 Galaxy가 포함된 디바이스 검색 - 통신사(telecom) 필드 오름차순 정렬 후, 출시연도(launchYear) 필드 내림차순 정렬
    ```
    GET http://api-mobiledevice.cloud.toast.com/mobiledevice/v1.0/appKeys/{appKey}/device?deviceModelName=Galaxy&sort=telecom,-launchYear
    ```


#### 응답

[응답 본문]
```json
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

[필드]

|이름|	타입|	설명|
|---|---|---|
|header                 |	Object  |	헤더 영역|
|- isSuccessful         |	Boolean |	성공 여부|
|- resultCode           |	Integer |	실패 코드|
|- resultMessage        |	String  |	실패 메시지|
|body                   |	Object  |	본문 영역|
|- pageNum              |	Integer |	페이지 번호|
|- pageSize             |	Integer |	페이지당 노출할 정보 수|
|- totalCount           |	Integer |	전체 정보 수|
|- data                 |	List    |	데이터 영역|
|-- deviceModelCode     |	String  |	디바이스 모델 코드|
|-- osCode              |   String  |   OS 정보|
|-- deviceModelName     |	String  |	디바이스 모델명|
|-- launchYear          |   String  |   출시연도|
|-- manufactureCompany  |   String  |   제조사|
|-- telecom             |   String  |   통신사|
|-- gearTypeName        |   String  |   장비 유형|
