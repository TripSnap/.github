# ✈ 여행의 순간을 기록하는 서비스 TripSnap (개발중)

## 목차

[1. 프로젝트 소개](#프로젝트-소개)  
[2. 주요 기능](#주요-기능)  
[3. 배포 주소](#배포-주소)  
[4. 개발 스택](#개발-스택)  
[5. 구현 내용](#구현-내용)  
[6. 기타 수난기 및 정리 내용](#기타-수난기-및-정리-내용)

## 프로젝트 소개

TrapSnap은 여행 그룹을 만들고, 그룹 내에서 위치 정보와 함께 사진을 등록하고 공유하는 서비스 입니다.

## 주요 기능

### 👉 친구에게만 그룹 신청

- 무분별한 그룹 신청을 막기 위해 그룹을 만드는 유저는 친구로 등록된 유저만 초대 할 수 있습니다.

### 👉 위치와 함께 사진을 업로드

- 그룹 내에서는 사진을 촬영한 장소와 함께 사진을 업로드 할 수 있습니다.
- 업로드 한 사진은 그룹 내부에서 누구나 자유롭게 조회가 가능합니다.

## 배포 주소

👉 [API 문서](https://tripsnap.github.io/server/)

## 개발 스택

### 개발 언어

- `javascript`
- `JAVA 17`

### 프론트엔드

- `React`
- `React Query`
- `MUI`

### 백엔드

- `Spring Boot`
- `Spring Security`
- `JPA`
- `Query DSL`
- `Redis`

### Storage

- `MySQL`
- `AWS S3`

### Others

- `Git`
- `Github`

## 구현 내용

### 📌주요 구현 내용

- 프론트엔드
  - Kakao 지도 API를 사용하여 사용자가 등록한 장소에 마커와 함께 사진 썸네일을 등록할 수 있습니다.
  - MUI의 Grid Layout을 활용하여 반응형 웹으로 제작했습니다.
  - yup, useForm을 사용하여 폼 데이터를 관리하도록 구현했습니다.
- 백엔드
  - Spring Security를 적용하여 API를 호출할 때 토큰에 있는 ROLE 권한 검사를 합니다.
    - 각 사용자의 role을 분리하여 메일 인증 시 서비스 API를 호출할 수 있습니다. (메일 인증은 구현 예정)
  - JWT를 활용하여 인증 상태를 관리합니다.
    - access token 연장에 필요한 refresh token은 redis에서 관리하도록 구현했습니다.
  - Swagger를 활용하여 API 문서를 제공합니다.
    - API 프로젝트에서 추출한 API 문서를 Github Pages에 배포 하기 위해 프로젝트를 분리했습니다.
    - api 문서의 json을 추출하여 저장하는 gradle task를 작성했습니다.
  - 핵심 로직의 테스트 코드를 작성했습니다.
    - JPA Entity 복합 키 사용
    - 로그인, 로그아웃 테스트
    - access token, refresh token 테스트
  - 사용자의 사진을 S3에 업로드 하기위해 Presigned URL 요청 후 업로드를 진행합니다.

### 구현 리스트

1. [x] Kakao map API 연동 및 마커 썸네일 작업
2. [x] 인증 및 권한 체크 기능 개발
3. [ ] 메일 인증 기능 개발
4. [x] 서비스 API 개발
5. [x] API 문서 추출 기능 개발 및 배포
6. [x] Presigned URL 요청 작업 및 S3 사진 업로드 기능 개발
7. [ ] S3 사진 조회 시 권한 체크
8. [ ] dockerfile & docker compose 작성
9. [ ] 커밋 시 자동 배포 작업 설정
10. [ ] 프로젝트 aws ec2 에 배포

## 기타 수난기 및 정리 내용

[[Spring] Filter에 OPTIONS 요청이 들어올 때](https://wary-billboard-150.notion.site/Spring-Filter-OPTIONS-5ba44e20618442e5a0ffc971992fbff0?pvs=4)  
[[TripSnap] swagger api github pages에 배포하기](https://wary-billboard-150.notion.site/TripSnap-swagger-api-github-pages-3f84692758644cdb87af4e14616630a4?pvs=4)
