---
sort: 4
published: true
---

# Vulnerability
> **Info**
>
> Vulnerability의 정보 수집, 알림, Score 표시 방법에 대한 내용입니다.


## Vulnerability 정보 수집. 알림, Score 표시 방법
### Vulnerability 정보 수집 
- Vulnerability 정보는 매일 [NVD Data Feed](https://nvd.nist.gov/vuln/data-feeds) 에서 다운로드되어 FOSSLight Hub에 저장됩니다.
- FOSSLight Hub의 Vulnerability Score는 기본적으로 CVSS v3 Base Score를 기준으로 표기하며, v3 Score가 없는 경우 CVSS v2 Base Score를 대신해서 표기합니다.


### Vulnerability 정보 알림
최초로 기준 점수 이상인 Vulnerability Score가 등록되거나, Vulnerability Score가 기준 점수 이상에서 기준 점수 미만으로 변경될 경우 알림 메일이 발송됩니다.
- Identification이 Confirm된 Project에서 위 조건을 만족하는 OSS가 BOM에 포함된 경우 Project의 Creator, Watcher, Reviewer에 Vulnerability Score 변경 내용이 발송됩니다.


### Vulnerability Score 표시 방법
- 사용자가 입력한 (OSS Name/Nick name, Version)이 동일한 Vulnerability가 존재하는 경우, 해당 OSS의 Max Score를 표시합니다.
    - 사용자가 입력한 OSS Version의 Vulnerability가 존재하는 경우, Vulnerability의 Max Score를 표시합니다.
    - 사용자가 입력한 OSS Version의 Vulnerability가 존재하지 않는 경우에는, 값이 존재하지 않으므로 표시하지 않습니다.
    - 사용자가 OSS Version을 공란으로 입력한 경우, 해당 OSS의 모든 Version 중 Max Score를 표시합니다.
- OSS Name이 -인 경우, Vulnerability를 표시하지 않습니다
