---
sort: 4
published: true
---

# OSS Table Search
OSS Table의 Header 아래에는 Search를 위한 Filter가 위치하고 있습니다. 이 Filter를 활용하여 Column 내 원하는 값을 검색할 수 있습니다.
![OSSTableSearch](../../images/common/oss_table_functions/oss_table_search.png)
- Filter는 다음과 같이 구성됩니다:
  - 검색조건:

    | **문자**                                             | ~        | ==    | !         | ^          | !^                  | !        | !@                | !~               |
    |----------------------------------------------------|----------|-------|-----------|------------|---------------------|----------|-------------------|------------------|
    | **설명**  <br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Contains | equal | not equal | begin with | does not begin with | end with | does not end with | does not contain |
  - 검색어 입력란
  - 검색어 입력란 초기화 (x 버튼)
