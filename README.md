# Syrup Ad javascript SDK 적용 가이드 v3.12.2

[TOC]

## SDK 정보
> SDK Version : 3.12.2<Br />
> SDK URL : http://adddn.adotsolution.com/contents/sdk/js/tad.min.js

<br />
<br />

==**상용 적용 전에 발급 받은 ClientID로 변경하여 주세요.**==

## Hybrid App 개발 시 설정
### Javascript와 Local Storage 사용 허용
> Javascript와 Local Storage 사용을 허용하도록 설정해 주세요.

Android WebView 설정 예
```
WebView wv = (WebView) findViewById(R.id.webView1);
WebSettings webSettings = wv.getSettings();
webSettings.setJavaScriptEnabled(true); // 이 옵션이 빠져 있으면 추가해 주세요.
webSettings.setDomStorageEnabled(true); // 이 옵션이 빠져 있으면 추가해 주세요.
```
SAID Library를 추가 적용하시는 경우
``` 
webview.addJavascriptInterface(new SyrupAdInterface(getApplicationContext()), "SyrupAdInterface");
```
> Syrup Ad ID를 조회하기 위한 SAID Library의 적용방법은 별도 첨부된 SAID Library 적용 가이드 문서를 참고 바랍니다.

<br />
### Syrup Ad ID 설정
> Hybrid App에서 적용 시 Syrup Ad ID를 지정(deviceId)하는 것이 좋습니다.(권장사항)

```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    slotNo : 2,
    adType : 'inline',
    targetId : 'main_banner',
    clientId : 'MXT002001',
    deviceId : (window.SyrupAdInterface) ? window.SyrupAdInterface.getDeviceId() : null, // Syrup Ad ID 지정
    test : true // 실 서비스 적용 시 꼭 빼주세요.
};
TadSdk.AdView.init(tad_slot2_conf);
</script>
</div>
```
> Syrup Ad ID를 조회하기 위한 SAID Library의 적용방법은 별도 첨부된 SAID Library 적용 가이드 문서를 참고 바랍니다.

<br />
<br />
## Ad Slot 설정
<br />
### Standard Banner
```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    targetId : 'main_banner',
    clientId : 'MXT002001',
    slotNo : 2,
    adType : 'inline',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    newWindow : true,
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    }
};
TadSdk.AdView.init(tad_slot2_conf);
</script>
</div>
```
<br />
#### SDK 파라메터 설정
| 파라메터 | 설명 | 값 | 필수 |
|-----|-----|------|-----|
|tagetId|광고가 등록될 Div 영역 ID값|'main_banner'| O |
|clientId|매체등록시 발급받은 Client ID값|'MXT002001'| O |
|slotNo|광고사이즈 정의(2 : 320*50)|2| O |
|adType|광고타입 설정(Default:inline)<br />**플로팅 광고이나 전면 광고일 경우 필수적으로 명시**<br /><br />- **inline** : 배너 광고<br />- **floating** : 플로팅 광고<br />- **interstitial** : 전면 광고|'inline'| &nbsp; |
|test|테스트 여부<br />개발,테스트용도로 test속성이 true일 경우 모든 에러메세지가  alert 처리 된다.(Default : false)<br />**실 서비스 경우 필히 제거**|&nbsp;| &nbsp; |
| newWindow | 새창 여부<br />클릭 시 이동되는 랜딩 페이지의 새창 여부를 지정한다.(Default : false)<br /><br />- **true** : 랜딩 페이지가 새 창에 보여진다.<br />- **false** : 랜딩 페이지가 현재 창에서 바로 전환된다.|&nbsp;| &nbsp; |
|errorCallback|개발자가 광고 호출 에러를 직접적으로 처리할 필요가 있을때 Function 지정한다.<br />(주로 Mediation 처리에 활용된다.)<br />에러코드는 Function 인자값으로 전달|&nbsp;| &nbsp; |
#### errorCallback 에러코드 설명
| 에러코드 | 설명 |
|-----|-----|
|0| No Ads.|
|1|The Frequency limit may have been reached.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|
<br />
<br />
- - -
<br />
<br />
### Large Banner
```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot6_conf = {
    targetId : 'main_banner',
    clientId : 'MXT006001',
    slotNo : 6,
    adType : 'inline',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
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
<br />
#### SDK 파라메터 설정
| 파라메터 | 설명 | 값 | 필수 |
|-----|-----|------|-----|
|tagetId|광고가 등록될 Div 영역 ID값|'main_banner'| O |
|clientId|매체등록시 발급받은 Client ID값|'MXT006001'| O |
|slotNo|광고사이즈 정의(6 : 320*100)|6| O |
|adType|광고타입 설정(Default:inline)<br />**플로팅 광고이나 전면 광고일 경우 필수적으로 명시**<br /><br />- **inline** : 배너 광고<br />- **floating** : 플로팅 광고<br />- **interstitial** : 전면 광고|'inline'| &nbsp; |
|test|테스트 여부<br />개발,테스트용도로 test속성이 true일 경우 모든 에러메세지가  alert 처리 된다.(Default : false)<br />**실 서비스 경우 필히 제거**|&nbsp;| &nbsp; |
| newWindow | 새창 여부<br />클릭 시 이동되는 랜딩 페이지의 새창 여부를 지정한다.(Default : false)<br /><br />- **true** : 랜딩 페이지가 새 창에 보여진다.<br />- **false** : 랜딩 페이지가 현재 창에서 바로 전환된다.|&nbsp;| &nbsp; |
|errorCallback|개발자가 광고 호출 에러를 직접적으로 처리할 필요가 있을때 Function 지정한다.<br />(주로 Mediation 처리에 활용된다.)<br />에러코드는 Function 인자값으로 전달|&nbsp;| &nbsp; |
#### errorCallback 에러코드 설명
| 에러코드 | 설명 |
|-----|-----|
|0| No Ads.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|
<br />
<br />
- - -
<br />
<br />
### Medium Rectangle Banner
```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot5_conf = {
    targetId : 'main_banner',
    clientId : 'MXT005001',
    slotNo : 5,
    adType : 'inline',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    newWindow : true,
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
<br />
#### SDK 파라메터 설정
| 파라메터 | 설명 | 값 | 필수 |
|-----|-----|------|-----|
|tagetId|광고가 등록될 Div 영역 ID값|'main_banner'| O |
|clientId|매체등록시 발급받은 Client ID값|'MXT005001'| O |
|slotNo|광고사이즈 정의(5 : 300*250)|5| O |
|adType|광고타입 설정(Default:inline)<br />**플로팅 광고이나 전면 광고일 경우 필수적으로 명시**<br /><br />- **inline** : 배너 광고<br />- **floating** : 플로팅 광고<br />- **interstitial** : 전면 광고|'inline'| &nbsp; |
|test|테스트 여부<br />개발,테스트용도로 test속성이 true일 경우 모든 에러메세지가  alert 처리 된다.(Default : false)<br />**실 서비스 경우 필히 제거**|&nbsp;| &nbsp; |
| newWindow | 새창 여부<br />클릭 시 이동되는 랜딩 페이지의 새창 여부를 지정한다.(Default : false)<br /><br />- **true** : 랜딩 페이지가 새 창에 보여진다.<br />- **false** : 랜딩 페이지가 현재 창에서 바로 전환된다.|&nbsp;| &nbsp; |
|errorCallback|개발자가 광고 호출 에러를 직접적으로 처리할 필요가 있을때 Function 지정한다.<br />(주로 Mediation 처리에 활용된다.)<br />에러코드는 Function 인자값으로 전달|&nbsp;| &nbsp; |
#### errorCallback 에러코드 설명
| 에러코드 | 설명 |
|-----|-----|
|0| No Ads.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|
<br />
<br />
- - -
<br />
<br />
### Floating
플로팅 광고의 경우 targetId가 불필요함.
```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot103_conf = {
    targetId : '',
    clientId : 'MXT103001',
    slotNo : 103,
    adType : 'floating',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    newWindow : true,
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    zIndex : 'off',
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    }
};
TadSdk.AdView.init(tad_slot103_conf);
</script>
```
<br />
#### SDK 파라메터 설정
| 파라메터 | 설명 | 값 | 필수 |
|-----|-----|------|-----|
|tagetId|광고가 등록될 Div 영역 ID값<br />(플로팅 광고는 targetId 빈값으로 설정 함)|''| O |
|clientId|매체등록시 발급받은 Client ID값|'MXT103001'| O |
|slotNo|광고사이즈 정의(103 : 100*100)|103| O |
|adType|광고타입 설정(Default:inline)<br />**플로팅 광고이나 전면 광고일 경우 필수적으로 명시**<br /><br />- **inline** : 배너 광고<br />- **floating** : 플로팅 광고<br />- **interstitial** : 전면 광고|'floating'| &nbsp; |
|test|테스트 여부<br />개발,테스트용도로 test속성이 true일 경우 모든 에러메세지가  alert 처리 된다.(Default : false)<br />**실 서비스 경우 필히 제거**|&nbsp;| &nbsp; |
| newWindow | 새창 여부<br />클릭 시 이동되는 랜딩 페이지의 새창여부를 지정한다.(Default : false)<br /><br />- **true** : 랜딩 페이지가 새 창에 보여진다.<br />- **false** : 랜딩 페이지가 현재 창에서 바로 전환된다.|&nbsp;| &nbsp; |
|errorCallback|개발자가 광고 호출 에러를 직접적으로 처리할 필요가 있을때 Function 지정한다.<br />(주로 Mediation 처리에 활용된다.)<br />에러코드는 Function 인자값으로 전달|&nbsp;| &nbsp; |
|position|플로팅 광고 위치 설정값<br />- **baseline** : 시작좌표위치 설정<br />(설정값 : left-top, left-bottom, right-top, right-bottom)<br />- **offsetX** : 시작좌표위치에서 x축으로 설정값만큼 여백 설정(표시단위 : px)<br />- **offsetY** : 시작좌표위치에서 y축으로 설정값만큼 여백 설정(표시단위 : px)|{<br />'baseline' : 'left-top',<br />'offsetX' : 20,<br />'offsetY' : 20<br />}|&nbsp;|
|zIndex|플로팅 광고의 z-index값을 조정|'off' - z-index 제거<br />1~2000000 - 원하는 z-index값(정수)|&nbsp;|
#### errorCallback 에러코드 설명
| 에러코드 | 설명 |
|-----|-----|
|0| No Ads.|
|1|The Frequency limit may have been reached.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|
<br />
#### Destroy 기능
> 현재 노출중인 배너를 제거하고자 할때 사용한다.

```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot103_conf = {
    targetId : '',
    clientId : 'MXT103001',
    slotNo : 103,
    adType : 'floating',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    newWindow : true,
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    zIndex : 'off',
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    }
};
TadSdk.AdView.init(tad_slot103_conf);
</script>
<button onclick="TadSdk.destroy(tad_conf);">Banner Destroy</button>
```
<br />
<br />
- - -
<br />
<br />
### Interstitial
전면 광고의 경우 targetId가 불필요함.
```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot3_conf = {
    targetId : '',
    clientId : 'MXT003001',
    slotNo : 3,
    adType : 'interstitial',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    newWindow : true,
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    }
    zIndex : 'off'
};
TadSdk.AdView.init(tad_slot3_conf);
</script>
```
<br />
#### SDK 파라메터 설정
| 파라메터 | 설명 | 값 | 필수 |
|-----|-----|------|-----|
|tagetId|광고가 등록될 Div 영역 ID값<br />(플로팅 광고는 targetId 빈값으로 설정 함)|''| O |
|clientId|매체등록시 발급받은 Client ID값|'MXT003001'| O |
|slotNo|광고사이즈 정의(3 : 320*480)|3| O |
|adType|광고타입 설정(Default:inline)<br />**플로팅 광고이나 전면 광고일 경우 필수적으로 명시**<br /><br />- **inline** : 배너 광고<br />- **floating** : 플로팅 광고<br />- **interstitial** : 전면 광고|'interstitial'| &nbsp; |
|test|테스트 여부<br />개발,테스트용도로 test속성이 true일 경우 모든 에러메세지가  alert 처리 된다.(Default : false)<br />**실 서비스 경우 필히 제거**|&nbsp;| &nbsp; |
| newWindow | 새창 여부<br />클릭 시 이동되는 랜딩 페이지의 새창 여부를 지정한다.(Default : false)<br /><br />- **true** : 랜딩 페이지가 새 창에 보여진다.<br />- **false** : 랜딩 페이지가 현재 창에서 바로 전환된다.|&nbsp;| &nbsp; |
|errorCallback|개발자가 광고 호출 에러를 직접적으로 처리할 필요가 있을때 Function 지정한다.<br />(주로 Mediation 처리에 활용된다.)<br />에러코드는 Function 인자값으로 전달|&nbsp;| &nbsp; |
|zIndex|전면 배너의 z-index값을 조정|'off' - z-index 제거<br />1~6000000 - 원하는 z-index값(정수)|&nbsp;|
#### errorCallback 에러코드 설명
| 에러코드 | 설명 |
|-----|-----|
|0| No Ads.|
|1|The Frequency limit may have been reached.|
|101|No Require Parameter.|
|300|Unregistered Client ID.|
|301|No Supported Device.|
|302|Wrong Slot Number.|
|500|Internal error.|
<br />
<br />
- - -
<br />
<br />
## 고급 설정
<br />
### 한 지면에 2개 이상의 배너를 배치하는 방법
> 각각 배너의 광고 파라메터를 정의한 다음, 실행해야 할 시점에 init을 호출한다.<br />(단, 동일한 slotNo를 갖는 배너는 동일 지면에 노출할 수 없다.)

```
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js"></script>
<div class="main_banner" id="main_banner">
<script type="text/javascript">
var tad_slot2_conf = {
    targetId : 'main_banner',
    clientId : 'MXT002001',고
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    slotNo : 2
};
var tad_slot103_conf = {
    targetId : '',
    clientId : 'MXT103001',
    test : true, // 실 서비스 적용 시 꼭 빼주세요.
    slotNo : 103,
    zIndex : 'off',
    adType : 'floating',
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    }
};
TadSdk.AdView.init(tad_slot2_conf);
TadSdk.AdView.init(tad_slot103_conf);
</script>
</div>
```
<br />
<br />
