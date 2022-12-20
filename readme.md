# Final프로젝트

<p align="center">
  <img src="https://user-images.githubusercontent.com/24247768/203729877-177a09a0-11af-4406-9424-875a21401908.png" width="400" height="400"/>
<p>

---
- 축제 게시판(Fit - 축제다 축제)
- 2022.11.17~2022.11.25

## 시연

- [시연영상](https://www.youtube.com/watch?v=dHSFuy7bUDU)
- [시연사이트](http://fit.deokisys.xyz)


## 화면 구성
- 메인화면
  - 메인에서는 현재 진행중인 축제를 확인 할 수 있습니다.
![메인화면](https://user-images.githubusercontent.com/24247768/208626505-7029ccae-513c-4f6d-aaa7-84f9a3754faa.png)

- 축제 캘린더
  - 날짜별 진행 축제를 확인 할 수 있습니다.
![축제 캘린더](https://user-images.githubusercontent.com/24247768/208626410-851705bc-6764-4fc2-bd93-08f07fb6dbb9.png)

- 축제 지도
  - 지역별 진행 축제를 확인 할 수 있습니다.
![축제 지도](https://user-images.githubusercontent.com/24247768/208626172-fbd1e757-4a79-42ee-912b-67b16a71da6a.png)

- 축제 상세정보
  - 축제별 상세 정보를 확인가능합니다.
  - 축제의 지역, 날짜, 주소, 홈페이지, 연락처, 축제의 개요를 확인 가능 합니다.
![축제 상세정보](https://user-images.githubusercontent.com/24247768/208626579-140b3eb3-03b7-4ce9-95f5-c244de6204cc.png)
## wiki보러 가기

- [wiki](https://lab.ssafy.com/sjb378/finalfestival/-/wikis/home)
  - 개발규칙 회의 등을 작성하였습니다.

## 사용한 api

- [한국관광공사\_국문 관광정보 서비스\_GW](https://www.data.go.kr/tcs/dss/selectApiDataDetailView.do?publicDataPk=15101578#/)
  - `/searchFestival`
    - 행사정보조회
  - `/detailCommon`
    - 공통정보조회(상세 내역)

## version

- node.js v14.17.3

## 이미지 파일 저장 위치

- c:/board/upload
  - 해당위치에 readme의 default.png파일을 위치해줘서 기본 이미지 설정을 해줍니다.

## frontapi의 .env.local생성

- `VUE_APP_BASE_URL=be서버주소`를 작성

## 팀

<b>ssafy 8기 대전 6반 4조</b>

<table>
  <tr>
    <td align="center"><a href="https://github.com/jhyun3315"><img src="https://avatars.githubusercontent.com/u/37072549?v=4" width="75px;" alt="이지현"/><br /><sub><b>이지현</b></sub></a></td>
    <td align="center"><a href="https://github.com/deokisys"><img src="https://avatars2.githubusercontent.com/u/24247768?s=460&v=4" width="75px;" alt="서준배"/><br /><sub><b>서준배</b></sub></a></td>
  </tr>
</table>
