---
sort: 2
published: true
---
# License
```note
등록된 License 정보를 확인하고, License를 추가, 수정, 삭제할 수 있습니다.    
License Name을 클릭하면 License 별 상세정보를 확인할 수 있습니다.    
```
## License List
![LicenseList](images/license_list.png)  

### License Name
- License Full name으로 SPDX (<https://spdx.org/licenses/>) 표기 방식을 따르고 있습니다.
- License Name을 클릭하면, License 별 상세정보를 확인할 수 있습니다.

### Identifier
- Standardized short identifier로 License를 더욱 쉽게 식별할 수 있으며 SPDX (<https://spdx.org/licenses/>) 표기 방식을 따르고 있습니다.

### License Type 
- **Permissive**
    - BSD-like 또는 BSD-style License로 불리며 Software 재배포 방법 관련 최소한의 요구사항이 있는 License입니다. 
    - 통상적으로 Copyright Notice와 보증부인 문구를 유지할 것을 요구합니다. 
- **Weak Copyleft**
    - 파생저작물에 동일한 권리가 유지된다는 조건으로 저작물의 복사본과 수정된 버전을 자유롭게 배포할 수 있습니다.
    - 저작물의 복사본과 수정본의 Source Code를 공개해야 합니다.
- **Copyleft**
    - 파생저작물에 동일한 권리가 유지된다는 조건으로 저작물의 복사본과 수정된 버전을 자유롭게 배포할 수 있습니다.
    - 저작물의 복사본과 수정본뿐만 아니라 이와 link 되거나 함께 동작하는 프로그램 전체 Source Code를 공개해야 합니다.
- **Proprietary**
    - Software 권리자의 허락 없이 사용이 불가능하므로 반드시 source code 사용 여부에 대한 계약 관계를 확인하고 사용하시기 바랍니다.
- **Proprietary Free**
    - 추가적인 계약이 필요하지는 않지만 제약된 형태, 특정 이용 약관 또는 조건에서 사용할 수 있습니다.

### Restriction 
|**Restriction 종류**|**내용**|
|-----|---|
|**Non-Commercial Use Only**|Software의 상업적 사용 및 배포를 금지합니다. <br>예) CC-BY-NC-X.X|
|**Network Redistribution**|Network 상으로 이용하도록 Service를 제공하는 것만으로도 배포로 간주하여 Open Source 의무 사항을 이행해야 합니다. <br>예) AGPL-3.0, OSL-2.0|
|**No Modification**|Software의 수정된 버전을 배포할 수 없습니다. 즉 Source code를 수정하지 않고 사용해야 합니다.<br> 예) CC-BY-ND-X.X|
|**Platform Limitation**|운영체제, 기술, 사용된 기술 분야, Device Type 등에 따라 Software의 배포를 제한합니다.<br> 예) Amazon Software License (Amazon.com 혹은 자회사에서 제공되는 웹서비스, 컴퓨팅 플랫폼 혹은 어플리케이션을 위해 사용해야 함)|
|**Purpose Restriction**|Software를 특정 목적(분야)을 위하여 사용할 수 없습니다. <br>예) The Happy Bunny License (군사 목적을 위해서 사용할 수 없음)|
|**Specification Restriction**|특정 Specification 또는 Standard와 관련하여 Software를 사용해야 합니다. <br>예) ETCPACK Software License Agreement (Khronos standard specifications 의 compression/decompression을 위한 목적을 위해 사용)|
|**Redistribution Restriction**|재배포할 수 있는 Software의 하위 구성 요소(Source Code, Binary file 등)를 제한합니다. <br>예) SOFTWARE LICENSE FOR VIVANTE CORPORATION (TM) USER SPACE GRAPHICS DRIVER BINARY (재배포시 Binary form으로만 가능함)|
|**Contract Required**|Commercial 계약 없이는 사용할 수 없는 License로 Source Code 사용에 대한 통제가 있습니다.<br> 예) QT Commercial License, NVIDIA Commercial License|
|**Internal Use Only**|내부적으로 사용하는 경우에만 허용됩니다.<br> 예) Additional-Buildcraft-Objects-Mod License|
|**No Charge**|요금을 부과하지 않는 한 사용할 수 있습니다.<br> 예) Commons Clause License Condition v1.0, SIL Open Font License 1.1|
|**No Change the Name**|이름 변경을 할 수 없습니다. <br>예) IPA Font License|
|**Provide Installation Information Required**|설치 정보를 제공해야 합니다. <br>예) GPL-3.0|
|**Patent Warning**|특허분쟁 가능성이 있으므로 사용시 유의해야 합니다. <br>예) Apple Public Source License|
|**Semi-Copyleft**|제약 사항이 있으나 Source Code를 공개하면 사용시 문제가 없습니다. <br>예) Ruby License|
|**Contact Required**|저작권자에게 연락해서 확인해야 합니다. |
|**Unexpected Termination**|저작권자에 의해 언제든지 License가 Termination 될 수 있습니다. |
|**Use Restriction**|사용자 수, 사용 국가 등 사용에 제한이 있습니다. |

### Obligation
License별로 고지 여부와 소스코드 공개 의무사항을 알 수 있습니다.
- **Notice Obligation**(:page_facing_up:) : 고지 의무가 있습니다.
- **Source Code Obligation** : 소스코드 공개 의무가 있습니다. 

### Web site 
- License 원문의 web site 정보를 제공합니다. URL 클릭 시 해당 사이트로 이동합니다.

### User Guide 
- License 사용 시 주의 사항을 알 수 있습니다.

## (Admin Only) License 추가, 수정, 삭제
### License 추가
![NEW_OSS](images/3_lic_new.png)  
1. License List에서 우측 상단 Add 버튼을 클릭합니다.
2. "New_License" 탭에서 신규 OSS의 정보를 입력합니다.
    - License Name, Nick Name은 중복될 수 없습니다. 
    - Obligation : 
        - Notice가 체크된 경우 OSS Notice에 포함됩니다. 
        - Source Code가 체크된 경우, Packaging탭에서 소스 코드 취합 OSS 목록으로 표시됩니다.
    - User Guide : 해당 OSS에 대한 정보를 입력합니다.
    - Attribution : OSS Notice 발행시 별도로 포함되어야 하는 문구를 기입합니다.
3. 우측 하단의 Save 버튼을 클릭합니다.

### License 수정
1. License List에서 수정할 License Name을 클릭합니다.
2. License 상세정보 탭에서 수정합니다.
3. 우측 하단의 Save 버튼을 클릭합니다.

### License 삭제
1. License List에서 삭제할 License Name을 클릭합니다.
2. License 상세정보 탭에서 Comment란에 삭제 사유를 기입합니다.
3. 좌측 하단의 Delete 버튼을 클릭합니다.