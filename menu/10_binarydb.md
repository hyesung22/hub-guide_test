---
sort: 10
published: true
---
# Binary DB
```note
 이미 분석이 완료된 Base Model의 Binary 정보를 Database화(Binary DB) 하고, 이를 활용하여 파생 Model의 Binary 분석을 자동화할 수 있습니다.
```

## 동작 방식
### 1. Binary 분석 자동화 방법

**Project > Identification > BIN, BIN(Android|Yocto) tab** 또는 **3rd Party SW의 Binary 분석 결과(FOSSLight Report, binary.txt)**를 Upload한 후 Save 버튼 클릭 시, Binary DB와 비교하여 동일 혹은 유사한 Binary의 OSS Name, License 등의 정보를 자동으로 채워줍니다. 
-  binary.txt: checksum, tlsh값을 포함하는 binary 목록

![binarytxt](images/11_upload_binary_txt.PNG)

```note
- [FOSSLight Binary Scanner v4.1.30](https://github.com/fosslight/fosslight_binary_scanner/)이후 버전 사용 시, FOSSLight Report의 Binary Sheet에서 TLSH, Checksum 값 확인 가능. (binary.txt 파일 필요 X)
```

- Binary Name 하단에서는 Binary DB내의 Binary와 동일(또는 유사)한지 여부에 대한 정보를 Warning message로 보여줍니다.
![binaryafterupload](images/11_after_upload.PNG)
#### < Warning Message >

| Message | 의미 |
|---------|------|
|<span style="color:#0000FF">Same</span>| Binary DB에 저장된 동일한 binary에 대하여 OSS 정보가 표시되고 일부 정보가 다름을 의미합니다(ex, License, OSS Name 등)|
|<span style="color:#0000FF">Similar</span>| Binary DB에 저장된 유사한 binary에 대하여 OSS 정보가 표시됩니다. (괄호 안에는 TLSH distance 값이 표시됩니다.)|
|Matched|Binary DB에 저장된 Binary Name, OSS Name, OSS Version, License 가 일치합니다.|
|Modified| 동일한 이름이지만, 유사도가 작은 Binary인 경우입니다.(괄호 안에는 TLSH distance 값이 표시됩니다.)|
|New|Binary DB에 동일한 이름의 Binary가 없습니다. |


```note
Binary DB내의 Binary와 일치하는지 여부는 다음 두가지 data를 통해 확인합니다.    
    1. Binary 이름과 checksum 값이 일치하면 동일한 것으로 간주합니다.    
    2. 또는, Binary 이름이 동일하고 두 Binary간의 TLSH distance가 120이하면 유사한 것으로 간주합니다.    
```



### 2. Binary DB에 Data Insert 과정
- 3rd Party SW, Project의 Identification 단계 Confirm 시, Identification > BIN, BIN(Andoird/Yocto), 3rd Party SW에 기재한 Binary 정보들은 Binary DB에 저장(insert)됩니다.

    {::options parse_block_html="true" /}
    <details>
    <summary markdown="span">**Data Insert시, 상세 내용**</summary>
        - OSS Name이 공백인 경우, 하이픈 "-" 으로 등록됩니다.
        - TLSH 값이 공백인 경우, 0으로 등록됩니다.
        - Binary Name에 Path 정보가 포함되어 있는 경우, Path 정보는 무시하고 파일명만 Binary Name으로 등록됩니다.
    </details>

- 단, Binary 분석결과(FOSSLight Report, binary.txt)가 upload 된 경우에 한하여 동작합니다.
- 동일한 Binary의 경우, OSS 정보가 다르면 기존 정보는 삭제하고 신규 정보로 업데이트합니다.
- 비슷한 Binary의 경우, 기존 OSS 정보는 유지하고 신규 OSS 정보를 추가 업데이트합니다.

    {::options parse_block_html="true" /}
    <details>
    <summary markdown="span">**상세 동작**</summary>
    <table>
        <thead>
            <tr>
                <th>No</th>
                <th>Case</th>
                <th>동작</th>
                <th>설명</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>Binary DB에 Binary Name이 같은 Binary가 존재하지 않는 경우</td>
                <td>신규 Binary로 저장</td>
                <td>신규 Binary로 저장합니다.</td>
            </tr>
            <tr>
                <td rowspan=2>2</td>
                <td rowspan=2>Binary DB에 Binary Name이 같고 checksum이 동일한 Binary가 존재하는 경우</td>
                <td>최신 Binary 정보로 업데이트</td>
                <td>Binary DB 내 기존 Binary 정보를 삭제하고 최신 Binary 정보로 저장하여 업데이트합니다.</td>
            </tr>
            <tr>
                <td>(단, 하나의 Binary에 여러 OSS가 사용된 경우)</td>
                <td>하나의 Project 내에 동일한 Binary에 여러 OSS가 사용된 경우, OSS 정보를 모두 저장합니다.</td>
            </tr>
            <tr>
                <td rowspan=2>3</td>
                <td rowspan=2>Binary DB에 Binary Name이 같지만 checksum이 동일한 Binary가 존재하지 않는 경우	</td>
                <td>TLSH distance <= 120인 경우, OSS 정보에 따라 다르게 동작</td>
                <td> 1. OSS Name과 OSS Version이 같은 경우, 신규 Binary로 저장합니다. 기존 Binary 정보는 checksum이 같을때만 활용될 수 있도록 TLSH 값을 0으로 변경합니다. <br>
                 2. OSS Name은 동일하지만 OSS Version은 다른 경우, 신규 Binary로 저장합니다. <br>
                 3. OSS Name이 다른 경우, 신규 Binary로 저장합니다. 기존 Binary 정보는 Checksum이 같을때만 활용될 수 있도록 TLSH값을 0으로 변경합니다.<br></td>
            </tr>
            <tr>
                <td>TLSH distance > 120인 경우, 신규 Binary로 저장</td>
                <td>TLSH distance가 120보다 큰 경우, 동일하지 않은 binary로 판단하여 신규 Binary로 저장합니다.</td>
            </tr>
        </tbody>
    </table>
    </details>



