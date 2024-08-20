---
sort: 3
published: true
---

# Vulnerability Score 표시 방법
- 사용자가 입력한 OSS Name/Nick name, Version이 동일한 Vulnerability가 존재하는 경우, 해당 OSS의 Max Score를 표시합니다.
    - 사용자가 입력한 OSS Version의 Vulnerability가 존재하는 경우, Vulnerability의 Max Score를 표시합니다.
    - 사용자가 입력한 OSS Version의 Vulnerability가 존재하지 않는 경우에는, 값이 존재하지 않으므로 표시하지 않습니다.
    - 사용자가 OSS Version을 공란으로 입력한 경우, 해당 OSS의 모든 Version 중 Max Score를 표시합니다.
- OSS Name이 -인 경우, Vulnerability를 표시하지 않습니다.
