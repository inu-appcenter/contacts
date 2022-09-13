# contacts

앱센터 서비스 비상연락망

## 개요

앱센터가 운영하는 서비스에 대해 관리자의 비상 연락망을 보여주는 정적 웹 페이지입니다.

## 배경

서비스를 운영함에 있어 시스템 장애나 버그 발생시 즉시 제보를 받아 해결 조치를 수행할 필요가 있습니다. 이를 위해 해당 작업을 수행할 서비스 관리자의 연락처가 공개되어 있어야 합니다.

지금까지는 이를 위해 앱과 서버 상태 페이지에 연락처를 **하드코드**하고 있었습니다. 여기에서 벗어나기 위해 이 웹 페이지를 만들었습니다.

## 활용법

### 기존의 웹 페이지에 추가하기

> 서버의 상태 페이지([예시](https://api.inu-cafeteria.app))에 표시할 때에 좋습니다.

기존의 웹 페이지에 다음을 추가합니다:

```html
<iframe src="https://contacts.inuappcenter.kr?service={서비스 이름}" style="border: none;"></iframe>
```

`{서비스 이름}`을 적절한 서비스 이름으로 바꾸어 주세요. 예를 들어 다음과 같습니다:

```html
<iframe src="https://contacts.inuappcenter.kr?service=cafeteria" style="border: none;"></iframe>
```

### 연락처만 JSON으로 가져오기

> API 형태로 호출하여 가공하여 표시할 때에 좋습니다.

다음 URL로 `GET` 요청을 보냅니다:

```
https://contacts.inuappcenter.kr/services/{서비스 이름}.json
```

여기서도 마찬가지로 `{서비스 이름}`을 적절한 서비스 이름으로 바꾸어 주세요. 이렇게요:

```
https://contacts.inuappcenter.kr/services/cafeteria.json
```

## 정보를 추가하는 법

새로운 서비스가 추가되었거나 관리자에 변동이 생긴 경우와 같이 연락처의 업데이트가 필요한 때에는 `services` 폴더 밑의 `json` 파일들을 수정합니다.

`json` 파일의 이름이 위에서 언급한 `{서비스 이름}`이 됩니다. 예를 들어 카페테리아는 `cafeteria.json`입니다.

### 주의할 점

`json` 파일의 형식이 지정되어 있습니다. `array` 형태로 주어져야 하며, 각 요소들은 `key`가 모두 같은 `object`로 이루어져야 합니다. 아래는 그 예시입니다:

```json
[
  {
    "이름": "potados",
    "전화번호": "010-2922-2661"
  },
  {
    "이름": "말하는 감자",
    "전화번호": "010-1234-5678"
  }
]
```
