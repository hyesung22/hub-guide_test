---
sort: 2
published: true
---

# B2B 모델 프로젝트
B2B 프로젝트 진행 시에는 프로젝트 생성할 때 다음과 같이 진행해야 합니다.
1. Distribution Type을 B2B로 선택합니다.
2. 고객사에서 요구하는 고지문 형태에 따라 Distribution Site를 다르게 선택해야 합니다.


## 고객사에 납품하지만, 자사명으로 제품이 배포되는 경우
고객사에 패키징 파일, 고지문을 전달하고, 고객사의 요청으로 해당 내용을 자사 LG Open Source 사이트에 개시하는 경우입니다.
이러한 경우, 일반적인 프로젝트와 마찬가지로 Distribution 단계까지 진행하여 LG Open Source 사이트에 고지가 되도록 합니다.
프로젝트 생성 시 옵션은 아래와 같이 선택합니다. <br/>
![B2BDistLGSite](../images/usecase/dist_type/b2b_dist_lgsite.png){: width="80%"}
- Distribution Type: B2B
- Distribution Site: opensource.lge.com

## 고객에 고지문 및 패키징 파일을 전달하고, 고객사명으로 제품이 배포되는 경우
고객사 요청으로 LG Open Source 사이트에 패키징 파일, 고지문이 개시되어서는 안되는 경우입니다.
LG Open Source 사이트에 배포하지 않아야 하므로, Distribution 단계는 진행하지 않고 Packaging단계에서 OSC Process를 종료합니다. 
또한, 고지문에 LG전자 명칭, LG Open Source 사이트 명, written offer 메일명 제거가 필요합니다. 
- 프로젝트 생성할 때 옵션: <br/>
![B2BDistNA](../images/usecase/dist_type/b2b_dist_na.png){: width="80%"}
  - Distribution Type: B2B
  - Distribution Site: N/A

- Packaging 단계에서 입력할 내용: <br/>
![B2BPackagingModify](../images/usecase/dist_type/b2b_packaging_modify.png){: width="80%"}
  - Modified OSS Notice 발급 요청 선택합니다.
  - Company Name, OSS Distribution Site, Email(Written Offer) 선택 해제하여 입력되지 않도록 합니다.
