---
sort: 5
published: true
---

# OSS Table Warning Message
OSS Table에서 Warning Message를 통해 검토가 필요한 사항을 확인할 수 있습니다.

## Warning message 색깔별 의미
- <span style="color:red"> 빨간색 </span> : 리뷰 요청 또는 Confirm이 불가합니다. 검토 후 수정이 필요합니다.
- <span style="color:blue"> 파란색 </span> : 리뷰 요청 또는 Confirm 가능하지만, 검토가 필요한 사항입니다.
- <span style="color:grey"> 회색 </span> : 정보 전달을 위한 message입니다.


## Warning message에 따른 검토 사항

| Message  | Description |
| ------------- | ------------- |
|**This field is required**| 내용 입력이 필요합니다.|
|**Unconfirmed open source**|등록되지 않은 신규 OSS입니다.|
|**Unconfirmed version**|등록되지 않은 신규 버전입니다.|
|**Unconfirmed license**|등록되지 않은 신규 License 입니다.|
|**Dual license: Select a license**|Dual License임에도 모두 사용된 것으로 쓰여져 있습니다. <br>Dual License인 경우, 사용할 License만 선택합니다.|
|**Specify OSS Name or put 1 license in a row**|OSS Name이 - 또는 공란이면서, 여러 License가 하나의 Row에 쓰여져 있습니다.<br> OSS Name이 - 또는 공란인 경우, License별로 Row를 분리하여 작성하여주십시오.|
|**The address should be started with www**|주소 format이 맞지 않습니다.|
|**Formatting error**|줄바꿈 문자가 포함되어 있습니다. 여러 줄 작성이 필요한 경우, Row를 추가하여 작성하시기 바랍니다.|
|**Not the same as property**|입력한 URL이 FOSSLight Hub에 등록된 해당 OSS의 URL과 다릅니다.|

{% include list.liquid all=true %}
