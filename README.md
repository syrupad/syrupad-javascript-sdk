# Syrup Ad Javascript SDK Guide

[TOC]

## SDK 정보
> SDK Version : 3.12.2
> SDK URL : http://adddn.adotsolution.com/contents/sdk/js/tad.min.js

## 주의사항
- 실 서비스 적용 시 상용으로 발급 받은 ClientID를 사용해 주세요.
- 동일 지면 상에서 동일한 크기의 배너는 1개만 배치가 가능합니다.

## Standard Banner (320x50)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    slotNo : 2,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT002001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    newWindow : true,
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 플랫폼 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 플랫폼 호출
        }
    }
};
TadSdk.AdView.init(tad_slot2_conf);
</script>
</div>
```

### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|slotNo|O|광고 사이즈(2 - 320x50)|**2**|
|adType|O|광고 타입|**'inline'**|
|tagetId|O|광고를 삽입할 DIV의 ID 값|ex) 'main_banner'|
|clientId|O|매체 등록 시 발급 받은 Client ID 값|ex) 'MXT002001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|

## Large Banner (320x100)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot6_conf = {
    slotNo : 6,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT006001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    newWindow : true,
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    }
};
TadSdk.AdView.init(tad_slot6_conf);
</script>
</div>
```

### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|slotNo|O|광고 사이즈 정의(6 : 320x100)|**6**|
|adType|O|광고 타입|**'inline'**|
|tagetId|O|광고를 삽입할 DIV의 ID 값|ex) 'main_banner'|
|clientId|O|매체 등록 시 발급 받은 Client ID 값|ex) 'MXT006001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|

## Medium Rectangle Banner (300x250)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot5_conf = {
    slotNo : 5,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT005001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    newWindow : true,
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    }
};
TadSdk.AdView.init(tad_slot5_conf);
</script>
</div>
```

### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|slotNo|O|광고 사이즈 정의(5 : 300x250)|**5**|
|adType|O|광고 타입|**'inline'**|
|tagetId|O|광고를 삽입할 DIV의 ID 값|ex) 'main_banner'|
|clientId|O|매체 등록 시 발급 받은 Client ID 값|ex) 'MXT005001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|

## Floating (100x100)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot103_conf = {
    slotNo : 103,
    adType : 'floating',
    targetId : '',
    clientId : 'MXT103001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    },
    zIndex : 'off',
    newWindow : true,
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    }
};
TadSdk.AdView.init(tad_slot103_conf);
</script>
```
### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|slotNo|O|광고 사이즈 정의(103 : 100x100)|**5**|
|adType|O|광고 타입|**'floating'**|
|tagetId|O|광고를 삽입할 DIV의 ID 값 (빈값으로 설정)|**''**|
|clientId|O|매체 등록 시 발급 받은 Client ID 값|ex) 'MXT103001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|
|position||광고 노출 위치<br />**'baseline'** : 기준 위치 ('left-top', 'left-bottom', 'right-top', 'right-bottom')<br />**'offsetX'** : 기준 위치에서 X 축 여백 (px)<br />**'offsetY'** : 기준 위치에서 Y 축 여백 (px)|{<br />'baseline' : 'left-top',<br />'offsetX' : 20,<br />'offsetY' : 20<br />}|
|zIndex||광고 z-index (default : 2000000)<br />**'off'** : z-index 없음<br />**2000000~2999999** : 권장|ex) 2999999|

### Destroy 기능
> 현재 노출 중인 배너를 화면 상에서 제거할 수 있습니다.

```javascript
<button onclick="TadSdk.destroy(tad_slot103_conf);">Banner Destroy</button>
```
## Interstitial (320x480)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot3_conf = {
    slotNo : 3,
    adType : 'interstitial',
    targetId : '',
    clientId : 'MXT003001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    newWindow : true,
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    zIndex : 'off'
};
TadSdk.AdView.init(tad_slot3_conf);
</script>
```
### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|slotNo|O|광고 사이즈 정의(3 : 320x480)|**3**|
|adType|O|광고 타입|**'interstitial'**|
|tagetId|O|광고를 삽입할 DIV의 ID 값(전면 광고는 빈값으로 설정 함)|**''**|
|clientId|O|매체등록시 발급받은 Client ID값|ex) 'MXT003001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|
|zIndex||광고 z-index (default : 6000000)<br />**'off'** : z-index 없음<br />**6000000 이상** : 권장|ex) 6999999|

## 에러코드 설명
> errorCallback function을 지정한 경우 에러코드를 전달 받을 수 있습니다.

| 에러코드 | 설명 |
|:-----|:-----|
|0| No Ads.|
|1|The Frequency limit may have been reached.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|

## 동일 지면에 여러 개의 배너를 배치하는 방법
> 각 배너의 파라메터를 정의한 후, 광고를 요청할 시점에 init을 호출해 주세요.
> (단, 동일한 slotNo를 갖는 배너는 동일 지면에 배치할 수 없습니다.)

```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    slotNo : 2,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT002001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    test : true // 실 서비스 적용 시 반드시 제거해 주세요.
};
var tad_slot103_conf = {
    slotNo : 103,
    adType : 'floating',
    targetId : '',
    clientId : 'MXT103001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    zIndex : 'off',
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    },
    test : true // 실 서비스 적용 시 반드시 제거해 주세요.
};
TadSdk.AdView.init(tad_slot2_conf);
TadSdk.AdView.init(tad_slot103_conf);
</script>
</div>
```
## Android Hybrid App 개발 시 WebView 설정
### 1. WebView 및 WebSettings 획득
```java
WebView wv = (WebView) findViewById(R.id.webview);
WebSettings webSettings = wv.getSettings();
```
### 2. JavaScript 활성화
```java
webSettings.setJavaScriptEnabled(true);
```
### 3. LocalStorage 활성화
```java
webSettings.setDomStorageEnabled(true);
```
### 4. WebViewClient 구현
```java
wv.setWebViewClient(new WebViewClient() {
    @Override
    public boolean shouldOverrideUrlLoading(WebView view, String url) {
        if (view == null || url == null) {
            return false;
        }

        if (url.contains("play.google.com") ) {
          String[] params = url.split("details");
          if (params.length > 1) {
              url = "market://details" + params[1];
              view.getContext().startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse(url)));
              return true;
          }
        }
        
        Intent intent;
        try {
            intent = Intent.parseUri(url, Intent.URI_INTENT_SCHEME);
        } catch (URISyntaxException e) {
            return false;
        }

        if (intent.getScheme().equals("http") || intent.getScheme().equals("https")) {
            view.loadUrl(url);
            return true;
        }

        try {
            view.getContext().startActivity(intent);
        } catch (ActivityNotFoundException e) {
            if (url.startsWith("intent:") && intent.getPackage() != null) {
                url = "market://details?id=" + intent.getPackage();
                view.getContext().startActivity(new Intent(Intent.ACTION_VIEW,Uri.parse(url) ));
                return true;
            } else {
                return false;
            }
        }
        return true;
    }
});
```
### 5. SAID Library 적용(optional)
``` java
webview.addJavascriptInterface(new SyrupAdInterface(getApplicationContext()), "SyrupAdInterface");
```
> Syrup AD ID를 조회하기 위한 SAID Library의 적용방법은 별도 첨부된 SAID Library 적용 가이드 문서를 참고 바랍니다.

### 6. Syrup AD ID 설정(optional)
> Hybrid App에서 적용 시 Syrup AD ID를 지정(deviceId)하는 것이 좋습니다.(권장사항)

```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    slotNo : 2,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT002001',
    deviceId : (window.SyrupAdInterface) ? window.SyrupAdInterface.getDeviceId() : null, // Syrup AD ID 지정
    test : true // 실 서비스 적용 시 꼭 빼주세요.
};
TadSdk.AdView.init(tad_slot2_conf);
</script>
</div>
```
> Syrup AD ID를 조회하기 위한 SAID Library의 적용방법은 별도 첨부된 SAID Library 적용 가이드 문서를 참고 바랍니다.
<br />
<br />
