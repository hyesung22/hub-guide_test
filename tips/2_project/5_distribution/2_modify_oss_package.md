---
sort: 2
published: true
---

# OSS Package 수정
배포가 완료되었으나 minor 변경이 필요하여 Package 파일을 수정하고 싶은 경우 사용합니다. (ex. README 파일 보완)
1. Distribution 탭으로 이동합니다.
2. 수정하고자 하는 Package File 오른쪽의 'X'버튼을 클릭합니다.<br/>
   ![DistPackagingDelete](../../images/project/distribution/dist_packaging_delete.png){: width="45%"}
3. Upload 버튼을 클릭하여 변경할 OSS Package 파일을 업로드하고, 'Updated'가 표시되면서 정상적으로 업로드된 것을 확인한 뒤,
   Start to Verify 버튼을 클릭합니다.<br/>
   ![DistPackagingStartVerify](../../images/project/distribution/dist_packaging_start_verify.png){: width="80%"}
4. 정상적으로 verify 성공한 경우, 다음과 같이 Completed로 버튼이 변경되는 것을 확인합니다.<br/>
   ![DistPackagingComplete](../../images/project/distribution/dist_packaging_complete.png){: width="80%"}
   - Verify 실패한 경우 재시도 할 것인지 팝업이 나타납니다. 
   - 계속 실패한다면, 업로드한 파일이 기존 Packaging탭에서 작성한 Path 정보와 일치하는지 다시 확인합니다.
5. Distribution 탭의 저장(![SaveIcon](../../images/common/information_view_button/floppy-disk-solid.png){: width="1.5%"})버튼을 클릭합니다. 
   Distribution Information(To be Updated)화면에 업데이트 되는 정보를 확인한 후 "Distribute" 버튼을 클릭합니다.<br/>
   ![DistPackagingUpdateConfirm](../../images/project/distribution/dist_packaging_update.png){: width="80%"}
