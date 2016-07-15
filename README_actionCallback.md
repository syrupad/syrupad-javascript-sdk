# Syrup Ad Javascript SDK Guide

## Floating (100x100)
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
    newWindow : true,
    test : true, // 실 서비스 적용 시 반드시 제거해 주세요.
    errorCallback : function(errorCode) {
        if(errorCode == 0) {
            // No Ad. 에러 처리 및 다른 광고 호출
        } else if(errorCode == 1) {
            // Frequency Over. 에러 처리 및 다른 광고 호출
        }
    },
    actionCallback : function(actionCode) {
    	if (actionCode == 1) {
    		// 닫기 버튼이 눌린 경우 호출
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
|clientId|O|매체 등록 시 발급 받은 Client ID 값|ex) 'MXT103001'|
|newWindow||랜딩 페이지의 새창 여부 (default : false)<br />|ex) false|
|errorCallback||광고 요청 결과를 처리할 필요가 있는 경우 function 지정|ex) function(errorCode) {...}|
|actionCallback||광고가 닫힌 시점을 처리할 필요가 있는 경우 function 지정|ex) function(actionCode) {...}|
|position||광고 노출 위치<br />**'baseline'** : 기준 위치 ('left-top', 'left-bottom', 'right-top', 'right-bottom')<br />**'offsetX'** : 기준 위치에서 X 축 여백 (px)<br />**'offsetY'** : 기준 위치에서 Y 축 여백 (px)|{<br />'baseline' : 'left-top',<br />'offsetX' : 20,<br />'offsetY' : 20<br />}|
|zIndex||광고 z-index (default : 2000000)<br />**'off'** : z-index 없음<br />**2000000~2999999** : 권장|ex) 2999999|
