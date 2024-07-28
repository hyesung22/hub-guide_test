---
sort: 1
published: true
---

# 파생 모델 프로젝트
기존 모델과 유사한 소프트웨어를 사용하는 파생 모델에 대해 OSC Process를 진행하는 경우, 
이전 모델에 대해 완료한 [프로젝트를 복사](../2_project/2_project.md#프로젝트-재사용하기-프로젝트-복사)하여 진행하면 효율적으로 진행할 수 있습니다.

## 베이스모델에서 몇 개의 오픈소스가 추가로 사용된 경우
- 프로젝트 복사 시, **Identification Progress**를 선택하여 베이스 모델 프로젝트의 오픈소스 목록을 그대로 복사할 수 있습니다.
- 추가된 오픈소스 정보를 Identification 탭에서 입력합니다.

## 새로운 프로젝트 버전이, 기존 프로젝트와 OSS 사용 내역이 동일한 경우
- [BOM Compare](../2_project/2_project.md#프로젝트-간-bom-비교-bom-compare)를 활용하면 최종 OSS 목록이 동일한지 확인 가능합니다.
- OSS 사용 내역 및 공개해야 하는 소스코드가 동일한 경우:
  - 기존 프로젝트에 발급된 OSS 고지문을 활용하여 OSC Process 대체가 가능합니다.
- OSS 사용 내역은 동일하나, 공개해야 하는 소스코드가 다른 경우:
  - OSS Package의 README 파일, 혹은 Notice 파일 수정 등과 같이 변경사항이 minor한 경우에 해당합니다.
  - [프로젝트를 복사](../2_project/2_project.md#프로젝트-재사용하기-프로젝트-복사) 할 때, **Packaging Confirm** 단계 선택
  - [Distribution 탭에서 OSS package 파일 변경](../2_project/2_project.md#oss-package-수정) 후 배포를 진행합니다.
