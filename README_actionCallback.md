# Syrup Ad Javascript SDK Guide
## closeAd
현재 노출 중인 배너를 화면 상에서 제거할 수 있습니다.
(floating 과 interstitial 광고에만 사용할 수 있습니다.)

### example(Floating)
```javascript
<button onclick="TadSdk.AdView.closeAd(tad_slot103_conf);">Close Banner</button>
```

### example(Interstitial)
```javascript
<button onclick="TadSdk.AdView.closeAd(tad_slot3_conf);">Close Banner</button>
```

## actionCallback
사용자가 광고를 닫는 시점에 어떠한 처리를 위해 콜백을 받아야 하는 경우 아래와 같이 actionCallback을 선언할 수 있습니다.
(floating 과 interstitial 광고에만 사용할 수 있습니다.)

### parameters
| 파라메터 | 필수 | 설명 | 값 |
|:---------|:----:|:-----|:---|
|actionCallback||광고가 닫힌 시점을 처리할 필요가 있는 경우 function 지정|ex) function(actionCode) {...}|

### actionCode
| 코드 | 설명 |
|:-----|:----:|
|1|사용자가 배너를 닫는 경우|
|2|개발자가 배너를 닫는 경우|

### example (Floating)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot103_conf = {
    slotNo : 103,
    clientId : 'MXT103001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    position : {
        'baseline' : 'left-top',
        'offsetX' : 20,
        'offsetY' : 20
    },
    zIndex : 'off',
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if (errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if (errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    actionCallback : function(actionCode) {
    	if (actionCode == 1) {
    		// 사용자가 배너를 닫는 경우 호출
    	} else (actionCode == 2) {
    	    // 개발자가 배너를 닫는 경우 호출
    	}
    }
};
TadSdk.AdView.init(tad_slot103_conf);
</script>
```

### example (Interstitial)
```javascript
<script type="text/javascript" src="http://adddn.adotsolution.com/contents/sdk/js/tad.min.js" charset="utf-8"></script>
<script type="text/javascript">
var tad_slot3_conf = {
    slotNo : 3,
    clientId : 'MXT003001', // 실 서비스 적용 시 상용에서 발급 받은 Client ID를 사용해 주세요.
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if (errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if (errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    actionCallback : function(actionCode) {
    	if (actionCode == 1) {
    		// 사용자가 배너를 닫는 경우 호출
    	} else (actionCode == 2) {
    	    // 개발자가 배너를 닫는 경우 호출
    	}
    }
};
TadSdk.AdView.init(tad_slot3_conf);
</script>
```
